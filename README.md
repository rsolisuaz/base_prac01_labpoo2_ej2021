# PRACTICA 1. CREACIÓN DE UN SET PERSONALIZADO Y REVISIÓN DE COMO SUBIR LAS PRÁCTICAS Y PROGRAMAS DE POO2.

## COPIA DEL REPOSITORIO REMOTO EN SU COMPUTADORA LOCAL
Como primer paso, será necesario crear una copia local del repositorio remoto creado en Github al aceptar la tarea. Para ello, es necesario hacer los siguientes pasos:
1)	Entrar a la página cuyo URL les fue proporcionado al aceptar la tarea, en tal página dé click en el botón Code y copie el URL que aparece en el cuadro de texto de nombre **Clone with HTTPS** (comienza con https://)
2)	En una consola de Git Bash en Windows (o en una terminal en Linux o Mac), cree una carpeta donde quiera que se contengan sus prácticas del semestre (si es que aun no la creado) y colóquese en tal carpeta. La carpeta la puede crear desde el Git Bash o terminal Linux/Macusando el comando mkdir (o con el explorador de archivos de su sistema operativo) y en la consola de Git Bash o terminal de Linux/Mac se puede cambiar a la carpeta mencionada usando el comando cd
3)	Clone el repositorio privado dando el comando **git clone URL practica01**
 (donde **URL** es el URL que copió en el paso 1)
 Este comando creará dentro de la carpeta creada en el paso 2) una subcarpeta de nombre practica01 donde estará una copia local del repositorio remoto
4)  Colóquese en el directorio recién creado dando el comando **cd practica01** 


## MODIFICACIÓN DEL CÓDIGO PROPORCIONADO
Una vez que tenga el repositorio local y esté ubicado en la consola o terminal, su trabajo consiste en lo siguiente:
1. Crear un proyecto usando Gradle emitiendo el comando **gradle init** y especificando las siguientes opciones:
   - type of project to generate: **2** *(Application)*
   - implementation language: **3** *(Java)* 
   - funcionality across multiples subprojects?: **1** *(no)*
   - build script DSL: **1** *(Groovy)*
   - test framework: **4** *(JUnit Jupiter)*
   - project name: **prac01**
   - source package: **poo2.prac01**
 
2. Usando el editor de su preferencia, abra el archivo build.gradle ubicado en la carpeta app y haga los siguientes cambios:
   - Agregue a la sección plugins la siguiente línea:

    `id 'java'` 
   - Agregue a la sección tasks.named('test') las siguiente líneas:

     `testLogging { events 'PASSED', 'FAILED', 'SKIPPED'}`
     
     `testLogging.showStandardStreams = true`

3. Usando el editor de su preferencia, crear el archivo **ConjuntoEnteros.java** dentro de la carpeta app/src/main/java/poo2/prac01

4. Usando el editor de su preferencia, crear el archivo **ConjuntoEnterosTest.java** dentro de la carpeta app/src/test/java/poo2/prac01

5. Ejecute el comando `git add .` seguido de `git commit -m "Inicialización de Proyecto"` para tomar el primer snapshot del proyecto.

6. En el archivo **ConjuntoEnterosTest.java** colocar el código que se puede encuentra de la siguiente dirección: https://pastebin.com/Ut4Mt9eM (dando click en raw, copiando y pegando en el archivo)

7. Ejecute el comando `git add app/src/test/java/poo2/prac01/ConjuntoEnterosTest.java` seguido de `git commit -m "Se agrega código al archivo de pruebas ConjuntoEnterosTest"`.

8. En el archivo **ConjuntoEnteros.java** debe crear la clase **ConjuntoEnteros** la cual deberá cumplir con lo siguiente:
   - Heredar de **HashSet &lt;Integer&gt;**
   - Tener dos atributos de tipo `Integer` y de nombre `limInf` y `limSup`, que representarán los límites mínimo y máximo que deberán tener los enteros a aceptarse en el `Set`, por ejemplo, si limInf=2 y limSup=100 solo se podrán agregar números al conjunto que estén en el rago de 2 al 100. 
   - Tener un atributo `valMax` de tipo `Integer` que represente el valor más grande que se pudiera haber guardado en el conjunto(null indicando que no hay aún datos)
   - Tener un atributo `valMin` de tipo `Integer` que represente el valor más pequeño que se pudiera haber guardado en el conjunto (null indicando que no hay aún datos)
   - Todos los atributos deberán ser privados y por tanto la clase deberá tener getters públicos para obtener el valor actual de cada uno de estos atributos (`getLimInf, getLimSup, getValMin, getValMax`) y dos setters públicos para modificar los límites mínimo y máximo de los valores a aceptar (`setLimInf` y `setLimSup`)
   - Un constructor que reciba los valores a asignarse a `limInf` y `limSup` respectivamente, y que los asigna de tal forma que en limInf queda el menor valor de los recibidos y en limSup el valor mayor de los recibidos.
   - Un constructor vacío que inicializa limInf en cero y limSup en 100 (ayudándose del otro constructor)
   - El método add (`public boolean add(Integer dato)`) deberá redefinirse para que se comporte de la siguiente manera:
   - Si el elemento recibido (`dato`) no está dentro de los límites especificados por los valores actuales de `limInf` y `limSup` debe regresar false. 
   - Si el elemento recibido (`dato`) cumple con los límites, debe llamar al método add de la clase padre para agregar el dato y si tal llamada regresa true, deberá también actualizar el valor de los atributos `valMin` y `valMax` según corresponda. En este caso en que el elemento recibido cumple con los límites, debe regresar lo que regrese la llamada a add de la clase padre.  

## NOTAS IMPORTANTES
1)	Es necesario estar guardando los cambios realizados en el punto 8 de manera atómica usando **git add** y **git commit**
2)	Una vez que esté seguro de que funciona correctamente (verificando con **gradle test**) suba su copia local al repositorio remoto usando el comando **git push**
3)	Cada vez que haga git push se realizaran automáticamente pruebas sobre su código para verificar si funciona correctamente. La calificación será mostrada al final de la prueba en un mensaje de salida que tiene el formato `ConjuntoEnterosTest STANDARD_OUT Calificacion:XX/100` (**NO ES LA QUE DICE `POINTS XX/100`**). Verifique que en la página de su repositorio en la sección **Pull Requests**, se encuentra una subsección de nombre **Feedback**, ahí podrá encontrar los resultados de las pruebas en la sección **Check** (dando click en Github Classroom Workflow->Autograding->Run education/autograding@v1) y cualquier comentario general que el profesor tenga sobre su código en la pestaña **Conversation**. También es posible que haya comentarios sobre líneas de código específicas en la pestaña **Files Changed**. **NO BORRE ESTA SUBSECCIÓN DE FEEDBACK NI CIERRE EL PULL REQUEST**. Si tiene preguntas sobre los comentarios que le haya dejado el profesor, escríbalas en la pestaña **Conversation** usando el área de texto que se encuentra hasta abajo asegurándose de dar click en **Comment** una vez tecleada la pregunta.
