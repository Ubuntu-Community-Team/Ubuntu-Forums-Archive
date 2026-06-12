---
title: "[Ayuda] Nuevo en ubuntu y con problemas..."
date: 2012-03-15
forum: Software
---

### Post by usuarioraiz on 2012-03-15
Hola amig@s!!! es mi primer mensaje y lamento que sea con una duda :S

Hoy por la mañana instale ubuntu 11.10 y todo perfecto pero no puedo  encontrar la forma de instalar la placa de video que es una geforce  7200GS para poder usar unity,wine(para ponerle algunos juegos de  windows)etc...etc... 

Otra cosa es que no se como mandar accesos directos al escritorio :S, no encuentro la forma :S 

Espero que me puedan dar una mano[IMG]http://o1.t26.net/images/space.gif[/IMG] 

Abrazo.-

---

### Post by asterix77 on 2012-03-16
¿haz intentado descargar el controlador de la página de nvidia?. 

Al menos en mi caso descargué el controlador de dicha página y me funcionó de maravillas.

El link es el siguiente:  [http://www.nvidia.es/Download/indexsg.aspx?lang=es](http://www.nvidia.es/Download/indexsg.aspx?lang=es)
aquí escoges gforce, luego gforce 7 series, luego 32 0 72 bit según tu distro, y finalmente el idioma y a descargar.

Lo que se descarga es un archivo xxxxxxxx.run que es un ejecutable, una vez descargado me parece que le debes dar permiso de ejecución, para ello abres una terminal, te diriges a la carpeta donde está el archivo xxxxx.run y escribes lo siguiente:

$sudo chmod +x xxxxx.run

Con esto ya está listo para que se ejecute e instala el controlador.

Saludos y espero que te sirva

PD: Con respecto a tu otra consulta, deberías abrir otro hilo según normas del foro, pero es tan simple como agarrar, arrastrar y dejar en el escritorio; o hacer click derecho y crear un enlace y luego dejarlo donde quieras.

---

### Post by usuarioraiz on 2012-03-16
> **asterix77 said:**
> ¿haz intentado descargar el controlador de la página de nvidia?. 

Al menos en mi caso descargué el controlador de dicha página y me funcionó de maravillas.

El link es el siguiente:  [http://www.nvidia.es/Download/indexsg.aspx?lang=es](http://www.nvidia.es/Download/indexsg.aspx?lang=es)
aquí escoges gforce, luego gforce 7 series, luego 32 0 72 bit según tu distro, y finalmente el idioma y a descargar.

Lo que se descarga es un archivo xxxxxxxx.run que es un ejecutable, una vez descargado me parece que le debes dar permiso de ejecución, para ello abres una terminal, te diriges a la carpeta donde está el archivo xxxxx.run y escribes lo siguiente:

$sudo chmod +x xxxxx.run

Con esto ya está listo para que se ejecute e instala el controlador.

Saludos y espero que te sirva

PD: Con respecto a tu otra consulta, deberías abrir otro hilo según normas del foro, pero es tan simple como agarrar, arrastrar y dejar en el escritorio; o hacer click derecho y crear un enlace y luego dejarlo donde quieras.

Gracias bro pero nada de nada, incluso creo que me mande un moco :S ahora la pantalla esta en 600xno recuerdo cuanto. (no tengo wifi tengo que llevar el cable de internet a la pieza por ubuntu).

Me quiero morir estuve intentando miles de cosas no hay un instalador simple :confused: o algo! hasta en la bios marque que solamente cargue la pci express

Lo de los iconos sabia que era arrastrando pero el inicio me ocupe toda la pantalla y yo los arrastraba pero nada :S y no tengo la opción de crear un enlazzador

No quiero volver a windows

Abrazo.-

---

### Post by usuarioraiz on 2012-03-17
Alguien plis!?

---

### Post by juancarlospaco on 2012-03-19
Primero, instala todas las actualizaciones.

Luego tenes que ir al engranaje que esta arriba a la derecha, configuracion de sistema, luego al de drivers adicionales, se abre una ventana, instala lo que te dice ahi, reinicia.

---

### Post by usuarioraiz on 2012-03-19
> **juancarlospaco said:**
> Primero, instala todas las actualizaciones.

Luego tenes que ir al engranaje que esta arriba a la derecha, configuracion de sistema, luego al de drivers adicionales, se abre una ventana, instala lo que te dice ahi, reinicia.

Ya lo hice bro, pero nada de nada, incluso instale el recomendado y probe con los otros que me aparecen como recomendados y la pantalla se me quedo en 600x300, me quiero morir.

El nvidia x server setting lo tengo en su version reciente e incluso dice el nombre de mi placa pero es como que el sistema no la reconose. 

En cambio en windows instalo el dirvers del cd y funciona a las mil maravillas

A>brazo.-

P.D: En el setting de nvidia dice en el bus id: ?@?:?:?

---

### Post by juancarlospaco on 2012-03-19
Podrias probar con un 12.04 desde LiveCD y si funciona bien instalalo.
:)

---

### Post by usuarioraiz on 2012-03-20
> **juancarlospaco said:**
> Podrias probar con un 12.04 desde LiveCD y si funciona bien instalalo.
:)

No es la idea bro, por que de que me vale tener que ir actualizando por cada vez que no me toma la placa u.u

Pero mira, me tira este error. baje el controlador:

[IMG]http://k36.kn3.net/2DAFA0541.jpg[/IMG]

Esa imagen justo la vi, buscando como solucionar mi error, es exactamente lo que me tira a mí [IMG]http://static.forosdelweb.com/fdwtheme/images/smilies/negar.gif[/IMG]
 
Abrazo.-
 
P.D: Es de 32bits mi ubuntu 11.10

---

### Post by juancarlospaco on 2012-03-21
Tu OS es x86_**32** ese programa que bajaste es x86_**64**
Lo dice en el Titulo, no va funcionar, necesitas el de 32 bits.

Ese programa se ejecuta en modo seguro, desde linea de comandos, sin interfaz grafica.

---

### Post by usuarioraiz on 2012-03-21
> **juancarlospaco said:**
> Tu OS es x86_**32** ese programa que bajaste es x86_**64**
Lo dice en el Titulo, no va funcionar, necesitas el de 32 bits.

Ese programa se ejecuta en modo seguro, desde linea de comandos, sin interfaz grafica.

Bro aclare que esa imagen la encontré justo en youtube buscando mi solución.

Pero mi so es de 32bits :KS

Abrazo.-

---

### Post by usuarioraiz on 2012-03-22
Creo que estoy llegando a la solución, pero tengo un problema, después de todos los inventos que hice necesito probar si mi teoría es cierta instalando los controladores [recomendados] por el sistema pero cuando voy a controladores me dice este error:

> Lo sentimos, la instalación de este controlador falló.
 
 Revise el archivo de registro para ver más detalles: /var/log/jockey.log

Alguien sabira decirme como puedo instalar el controlador [recomendado] de los 3, o 4 que figura para instalar puedo con todos pero cuando quiero darle al recomendado me arroja ese error :S

Y otra cosa mas, no se por que no funciona el teclado pero es lo demos debe ser por que le puse gnome :S

ABrazo.-

---

### Post by silpablo on 2012-03-23
hola, creo que se lo que te pasa:

tenes una 7200gs - pensa que salio la serie 8xxx 9xxx 2xx 4xx 5xx y ya van por la 6xx

seguramente tu placa ya esta descontinuada y no existen drives privativos para la version de kernel que estas usando ( si no me ekivoco oneiric usa la 3 )

checkeaste esto?

si es asi, las opciones que te quedan son, usar el driver libre o bien bajar la version de distro para usar el driver privativo
----------------------------------------------
en terminal escribi, glxinfo | grep OpenGL
 
y postea lo que devuelve (talves necesites instalar mesa-utils)

------------------------------------------------
lo de los iconos en el escritorio, tenes que cerrar sesion y elegir gnome sin efectos, ahi te va a dejar hacer lo que decis

---

