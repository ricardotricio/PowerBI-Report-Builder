# Power BI Report Builder
<aside>
❔

**When should I use a paginated report vs. a Power BI report?**

Power BI reports are optimized for exploration and interactivity.  A sales report where different salespeople want to slice the data in the same report for their specific
 region/industry/customer and see how the numbers change would be best 
served by a Power BI report. Paginated reports are operational reports optimized for printing. Examples of paginated reports include invoices, financial statements 
and, inventory report. For more information, see [When to use paginated reports in Power BI](https://learn.microsoft.com/en-us/power-bi/guidance/report-paginated-or-power-bi).

</aside>

<aside>
❕

Es Importante saber el origen de datos porque según cuál usemos algunas cosas cambian

</aside>

<aside>

https://www.youtube.com/watch?v=yDFsrV_aX_k

</aside>

<aside>

https://www.youtube.com/watch?v=1zKAjfeaItI

</aside>

<aside>

https://www.youtube.com/watch?v=A7ByU1bTyH8

</aside>

1. Instalar Power Bi
    1. Instalar MySQL database connector
    2. Instalar Report Builder
- En Power BI te puedes conectar a la Base de Datos MySQL
    1. Servidor: 127.0.0.1:3306
    2. Base de datos: gbase11
    
    En Power Bi Report builder no se puede, hay que rear odbc (Open Database Connectivity) para mysql. Descargar  https://dev.mysql.com/downloads/connector/odbc/
    
1. Para obtener la ODBC como Origen de datos en Report Builder en la barra de datos 
    1. Clic derecho en Orígenes de datos > Agregar origen de datos… 
    2. Tipo de conexión: ODBC
    3. Click en Generar cadena de conexión: 
    4. Seleccionar: Use user or system data source name: 
    
    ![image.png](attachment:8b89993e-4561-4df9-8491-a37c34ce96d5:image.png)
    
    Una vez creado el origen de datos se mostrará en la barra lateral izquierda, tendremos que agregar conjuntos de datos para poder usarlos: 
    
2. Agregar conjuntos de datos: 
    1. Clic derecho en el Origen de datos que hemos creado > agregar conjunto de datos
    2. Ir haciendo consultas de todas las tablas para añadirlas como conjuntos de datos separados. 
    
    En la pestaña Campos se puede cambiar el nombre de visualización de los campos. 
    
    ![image.png](attachment:bf8fadc0-9e3b-4b2c-9772-faec8d35c3df:image.png)
    

## Power Bi Report Builder

---

**Establecer parámetros por defecto**

- Del cuerpo: (Rellenos y borde)
    
    Hacer click en una parte en blanco del fichero > propiedades del cuerpo… > 
    
- Del informe: (Orientación, tamaño de márgenes etc.)
    
    Hacer click en la parte gris de fuera de la página > propiedades del informe… > 
    

**Imprimir texto como Placeholder: valor base de datos**

- Insertar cuadro de texto.
- Clicar para que te deje escribir y pulsar click derecho > crear marcador de posición…
- En el Value poner el texto que queremos mostrar entre comillas y precedido por =
    
    ```jsx
    ="CLIENTE"
    ```
    
    Esto creará un <<Expr>> en el cuadro de texto. Si se establece como Ctrl+B el valor se mostrará en negrita.  
    
- Crear otro marcador de posición y establecer el valor al valor del conjunto de datos deseado. =First(Fields!name.Value, "users")
    
    El cuadro de texto se mostrará así: **«Expr»** «Expr»
    
- También se puede Crear un único placeholder y establecer el valor a: `="Cliente: " & First(Fields!name.Value, "users")`
    
    
       
    

**Tips**

- Si se seleccionan varios elementos y se hace clic derecho se pueden alinear, establecer mismo alto o ancho y más acciones.
- Es muy útil utilizar los parámetros de Posición de la barra de Propiedades para ajustar el Layout
- Usar preferiblemente la barra lateral de propiedades a la barra superior de Inicio. Algunas acciones me han fallado al establecerlas con la barra superior y han funcionado con la barra lateral.
- Para seleccionar solo los elementos que deseamos en el caso de querer hacer un report específico (no de toda la base de datos) Se puede ajustar la consulta del conjunto de datos. por ejemplo en lugar de añadir todas las filas, añadir solo: *SELECT * FROM gbase11.actividades where id = 9;*
- Para filtrar por currency (tiene floats) hay que filtrar por Int(valor*100) en lugar de directamente el valor
