---
title: "ayuda con anjuta"
date: 2008-11-06
forum: Software
---

### Post by Barasuishou on 2008-11-06
Hola bueno en la facu me estan empezando a enseñar c++, así que instalé anjuta, y el gcc(el compilador), compilar lo hace perfecto, pero no puedo ejecutar los programas, me tira estos errores el anjuta, bueno antes de actualizar ubuntu me tiraba otro error ahora quise probar devuelta para copiarlo pero me tira un error diferente

El programa «/home/karasu/Facu/c++/practica/punteros/ej6/src/main.cc» no tiene permiso de ejecución

como que no tengo permiso, ya probé abriendo el anjuta desde terminal con sudo, pero me sige tirando eso, como lo arreglo???,

de todas formas el error que me tiraba antes era que me faltaban unas libs para poder ejecutarlo, había bajado e instalado algunas, pero había una que no encontraba, pero ahora parece que actualizé y tengo un problema diferente, espero alguna ayuda, chauuuu

---

### Post by Hei Ku on 2008-11-06
El problema es que para ejecutar cualquier archivo le tenes que dar permisos de ejecucion, si no, no te va a dejar.

```

chmod +x <nombre de archivo>

```

---

### Post by Barasuishou on 2008-11-06
gracias por lo anterior me funcionó de maravilla, lastima que tenga que hacerlo archivo por archivo x_x, pero bueno, ahroa tengo otro tema, cuando lo ejecuto me aparece esto en la terminal, en lugar de lo que yo programe que me muestre 

EXECUTING:
/home/karasu/Facu/c++/practica/punteros/ej1/src/main.cc 
----------------------------------------------
/home/karasu/Facu/c++/practica/punteros/ej1/src/main.cc: 1: /bin: Permission denied
/home/karasu/Facu/c++/practica/punteros/ej1/src/main.cc: 1: indent-tabs-mode:: not found
/home/karasu/Facu/c++/practica/punteros/ej1/src/main.cc: 1: c-basic-offset:: not found
/home/karasu/Facu/c++/practica/punteros/ej1/src/main.cc: 1: tab-width:: not found
/home/karasu/Facu/c++/practica/punteros/ej1/src/main.cc: 2: /bin: Permission denied
/home/karasu/Facu/c++/practica/punteros/ej1/src/main.cc: 3: Makefile.am: not found
/home/karasu/Facu/c++/practica/punteros/ej1/src/main.cc: 4: /bin/bash:: not found
/home/karasu/Facu/c++/practica/punteros/ej1/src/main.cc: 5: /bin/bash:: not found
/home/karasu/Facu/c++/practica/punteros/ej1/src/main.cc: 6: Syntax error: "(" unexpected

----------------------------------------------
Program exited successfully with errcode (2)
Press the Enter key to close this terminal ... 

estoy haciendo algo mal yo cuando programo??, por que en la facultad en windows funciona bien :S

---

### Post by Hei Ku on 2008-11-07
Parecieras tener algun path mal, porque /bin no existe.

---

### Post by sherwoodinc on 2008-11-10
Me parece que el problema es otro. "main.cc" parece el nombre de un archivo de código fuente, y NO el de un archivo binario ejecutable compilado.

Probá abrir "main.cc" con el gedit:

```
gedit /home/karasu/Facu/c++/practica/punteros/ej6/src/main.cc
```

Si lo que ves son puros chirimbolitos, está ok, pero si ves tu propio código tal como lo ves en el Anjuta para editar, entonces algo está mal en la configuración del proyecto...

Yo actualmente uso el kdevelop y el codeblocks, que me parecen más fáciles de usar, pero tratemos de resolver tu problema con el Anjuta! :)

EDIT:

Otra cosa es que los archivos ejecutables resultantes de compilar ya se crean con el permiso de ejecución seteado, por lo que no deberías necesitar setearlo a mano. Esa es otro inidicio de que el ejecutable no se llama "main.cc".

Vos abriste tu código fuente directamente con el anjuta, o primero creaste un proyecto vacío y luego lo agregaste? Al editar código sin un proyecto creado, creo que se complica correr o debuggear el resultado de la compilación...

(5 minutos más tarde)

Acabo de crear un proyecto de 0 con el Anjuta. Ni bien creado, fui al menú Construir->Construir proyecto. En la ventana de abajo dijo "Completado correctamente".
Seguidamente elegí Ejecutar->Ejecutar el programa (F3) y me apareció un diálogo con el nombre del programa vacío, así que elegí "Abrir".
Me apareció la lista de archivos con el contenido de la carpeta "src", entre los que estaba "main.cc".
Pero también había un archivo "foobar_cpp" con el icono de "ejecutable".
Eligiendo ese, pude correrlo normalmente.
Calculo que (en mi ejemplo) el ejecutable se llama "foobar_cpp" porque en las Propiedades del proyecto el nombre del paquete es "foobar_cpp". Eso podés verlo en el menú Proyecto->Propiedades.

Espero que te sirva de algo lo que te comento.
Saludos!

---

### Post by Barasuishou on 2008-11-10
a ver si puedo terminar con esto, por que a este paso me van a bochar en la materia si sigue así XS, al parecer tenías razón con lo del .cpp, tenía que ejecutar eso, pero creo el proyecto de 0 sin tocarlo(que supuestamente tira el mensaje hello world), y cuando lo ejecuto tira esto 
EXECUTING:
/home/karasu/Facu/c++/practica/prueba/foobar_cpp.anjuta 
----------------------------------------------
/home/karasu/Facu/c++/practica/prueba/foobar_cpp.anjuta: 1: Syntax error: newline unexpected

----------------------------------------------
Program exited successfully with errcode (2)
Press the Enter key to close this terminal ... 


:S, sino más fácil decime como instalar el codeblocks y listo, aunque toy tan cerca de solucionar esto :P

---

### Post by sherwoodinc on 2008-11-11
Probá elegir un archivo que se llama "foobar_cpp" SIN EXTENSIÓN. En mi proyecto estaba dentro de la carpeta "src" del proyecto.
Subo screenshot del archivo elegido en el dialog.
Fijate que es el único de la carpeta con el ícono de ejecutable (que en mi tema de escritorio es un rombo con un engranaje adentro).

Espero que esto te ayude!

---

### Post by Barasuishou on 2008-11-11
el archivo ese te lo crea cuando compilas??, por que recién hize un archivo de 0 y probé de abrir ese archivo pero no está, compile pero no aparece :S, en algunos proyectos que hize anteriormente está, pero no cuando creo uno de 0

---

### Post by faktorqm on 2008-11-11
Che no es mas facil cuando compilas de apretar F11 para ejecutar el ejecutable (valga la redundancia) automaticamente? Si no me falla tanto la memoria las teclas eran F9 y despues F11, entonces compila y ejecuta. Salu2!

---

### Post by sherwoodinc on 2008-11-11
> **Barasuishou said:**
> el archivo ese te lo crea cuando compilas??, por que recién hize un archivo de 0 y probé de abrir ese archivo pero no está, compile pero no aparece :S, en algunos proyectos que hize anteriormente está, pero no cuando creo uno de 0

Sí, es el ejecutable que se crea una vez que el programa se compiló correctamente.

Creaste un archivo o un proyecto? Mirá que son distintos. En el proyecto se incluye la información de cómo compilar el/los archivos fuente, y cómo se llamará el ejecutable, etc...

No se me ocurrió preguntarte con qué versión del Ubuntu estás, pero yo probé crear un proyecto vacío en los Anjutas del 8.04 y del 8.10 (el screenshot que incluí es del 8.10). Ambos compilaron y crearon el ejecutable src/foobar_cpp.

---

### Post by Barasuishou on 2008-11-11
cree un proyecto, y uso ubuntu 8.10 x64, ahora al parecer me crea un archivo.exe, pero se llama main.cc~ , y cuando elijo ese para ejecutar no pasa nada, :S, probé recién de tratar de ejecutar alguno de los archivos que hize en la facu(en windows), y me tira algo raro XS,

---

### Post by sherwoodinc on 2008-11-12
Mmmm los archivos que terminan en "ñuflo" (~) son generalmente copias de seguridad de un archivo creadas por los editores de texto. Por ejemplo, "pepito.txt~" es backup de "pepito.txt".
En tu caso, ese archivo "main.cc~" debería ser igual a "main.cc", o a una versión anterior de éste.
O sea que ese archivo también es de código fuente (y no ejecutable).

Con respecto a los ".exe" que hayas compilado en windows, en ubuntu pueden o no funcionarte (si lo que decís es que los corriste con wine).

Yo te recomendaría probar con el cdeblocks o con el kdevelop. Te podés instalar cualquiera de los dos con el synaptic o con
```
sudo apt-get install kdevelop
sudo apt-get install codeblocks
```
A mí me gustan las dos, ambas son más que suficientes para programar, aunque estoy más acostumbrado al kdevelop porque lo uso en el laburo.
La ventaja del codeblocks es que el tema de los proyectos es más flexible que el kdevelop, así que te recomiendo que la pruebes primero.

En realidad el Anjuta también sirve, pero si te hace perder tiempo probá con el codeblocks, o en su defecto el kdevelop, y así te concentrás en programar :) y no seguís a las puteadas...

Bueno, cualquier cosa chiflá!

---

### Post by Barasuishou on 2008-11-12
bueno mira instalé el codeblocks y anda de 10 ni un problema por ahora, igual voy a tratar de hacer un par de ejercicios a ver si no surge nada raro, por lo que estoy mirando está bueno, después sino voy a tratar de instalar el kdevelop para probar, ya que por lo que había leido creo es el más usado, desde ya muchas gracias por la ayuda, si tengo otro problema lo volveré a comentar, pero no creo que los tenga :P, chauuuu

---

### Post by Barasuishou on 2008-11-12
eee ahora no tengo un problema, solo una duda como uso las clases en el codeblocks??, por que creo los archivos "header" y el "source" correspondientes a la clase que quiero crear, pero cuando los trato de incluir en el main no me los encuentra dice :S, los estoy guardando en el mismo directorio y todo, me despido chauuuuuuuuuu

---

### Post by sherwoodinc on 2008-11-12
Muy bien!

Mirá que no alcanza con que los archivos que creás estén en el mismo directorio, también tienen que estar agregados al proyecto (o sea, estar visibles en el "workspace" de la izquierda). Probá hacer clic derecho sobre tu proyecto y elegir "Add Files...", y elegí los header y source que hayas creado...

Me alegro de haber podido ayudar...

---

### Post by Barasuishou on 2008-11-12
mm los tengo agregados, y los incluyo haciendo #include "nombre", pero me sigue diciendo que no los encuentra XS

---

### Post by Hei Ku on 2008-11-13
No solo en el include, sino q tienen q estar en el workspace. Esto es porque se agregan a unos archivos Makefile, que en el momento de compilar ubican los archivos. Por eso tenés que hacer el "Add Files..." ademas de poner el include.

---

### Post by sherwoodinc on 2008-11-13
Qué raro, si podés posteáq un screenshot del error...

---

### Post by Barasuishou on 2008-11-16
acá pongo una screen /home/karasu/Pantallazo.png  , a ver nose si la adjunte bien :S, sino ahora pruebo devuelta

---

### Post by Barasuishou on 2008-11-16
acá pongo una screen [IMG]http:///home/karasu/Pantallazo.png[/IMG]  , a ver nose si la adjunte bien :S, sino ahora pruebo devuelta

---

### Post by Barasuishou on 2008-11-16
genial alguien que me diga como adjunto la foto

---

### Post by Hei Ku on 2008-11-16
Cuando pones Go Advanced, abajo tenes un lugar que dice Manage Attachments. Ahi podes agregar imagenes.

---

### Post by Barasuishou on 2008-11-17
ahora si, grax por la ayuda, av er si con la foto algo me pueden ayudar

---

### Post by sherwoodinc on 2008-11-18
Me parece que ya sé qué pasa!

Fijate que en el workspace tenés lo siguiente:

```
Workspace
  - Test
     *Sources
        Vertice.cpp
        main.cpp
     ***Others**
        **Vertice**

```

Fijate que en "Others" está "Vertice": Me da la impresión que tu archivo header le falta la extensión ".h".

Si tuviera la extensión, el codeblocks te lo mostraría en el workspace dentro de la categoría "Header Files" en lugar de "Others".

Renombrá el archivo (si estoy en lo cierto) y volvé a agregarlo al proyecto...


Suerte!!

---

### Post by Barasuishou on 2008-11-19
sip tenías razón XP, yo pensé que la extención se ponía sola, parece que no, ahora cuando creo los archivos les pongo la extención y los toma, gracias por todo, chauuuuuuuu

---

