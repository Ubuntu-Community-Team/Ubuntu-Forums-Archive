---
title: "Escritorio remoto"
date: 2009-05-22
forum: Software
---

### Post by aledruetta on 2009-05-22
Hola Comunidad!

Tengo una portátil Acer 4310 con Ubuntu Jaunty, conectada por wifi a un router TP-Link modelo TL-WR542G. 

Soy profesor de lenguas, y a veces doy clases en línea. Antes, cuando tenía instalado Windows, usaba Microsoft SharedView para compartir el escritorio con mis alumnos y, la verdad que estoy extrañando la sencillez del procedimiento.

Los equipos y formas de conexión de mis alumnos son muy diversas y, muchas veces, directamente, no se cuál es la configuración.

He intentado con el Cliente de Terminal Server, el Visor de Escritorios Remotos, instalé FreeNX y NoMachine NX, pero nunca conseguí una conexión. Obviamente, esto se debe a mi falta de conocimientos en la materia y no al sistema ni a las aplicaciones que deben ser tanto o más buenas que la de Microsoft.

Incluso, instalé VirtualBox y virtualicé un XP con el Microsoft SharedView, y no es posible la conexión. No sé si es que Ubuntu cierra algún puerto que la aplicación precisa para comunicarse o qué. 

Ojalá Ustedes, o cualquier ubuntero que se defienda con estas cuestiones, me pueda dar una mano.

Saludos y gracias,
Alejandro.

---

### Post by Patriciologico on 2009-05-23
Hola aledruetta, he visto que publicaste la misma inquietud en ubuntu-ar, y sinceramente no se me ocurren mas soluciones que las [ahi dadas]("http://ubuntuforums.org/showthread.php?p=7329505#post7329505")

Algo mas que puedes probar, es correr la aplicación usando wine, pero no se que calidad de funcionamiento tiene de esa forma.

Saludos!

---

### Post by aledruetta on 2009-05-23
Hola Patriciologico,

Con wine no probé, porque pensé que para eso había que tener Windows en otra partición ¿Me equivoco? Solamente tengo instalado Ubuntu y, para intentar resolver el problema planteado, instalé un XP en virtualizado en VirtualBox. Pero, como ya expliqué, tampoco tuve suerte de esa forma.

Y sí, es cierto que posteé la misma pregunta en Ubuntu-ar, soy miembro de varias comunidades. Pregunto, porque no sé ¿está mal hacer eso? ¿lo importante no es resolver el problema? Si esta u otra comunidad lo resuelve ¿no redunda en un beneficio para todos los usuarios de Ubuntu, independientemente de su nacionalidad o comunidad de pertenencia?

Sigo sin poder resolver el problema y necesito ayuda.

Saludos y muchas gracias,
Alejandro.

---

### Post by gmunioz on 2009-05-23
Hola Alejandro:

Ya publiqué en ubuntu-ar, lo único que conozco parecido a lo que utilizabas.

Sin embargo, para quede claro, no se trata de escritorios remotos, se trata 

de una aplicación de Microsoft Office 2007, que permite compartir 

documentos en línea.

Saludos.

---

### Post by Patriciologico on 2009-05-23
> **aledruetta said:**
> Hola Patriciologico,

Con wine no probé, porque pensé que para eso había que tener Windows en otra partición ¿Me equivoco? Solamente tengo instalado Ubuntu y, para intentar resolver el problema planteado, instalé un XP en virtualizado en VirtualBox. Pero, como ya expliqué, tampoco tuve suerte de esa forma.


Para wine no es necesario tener windows, en otra partición.

> Y sí, es cierto que posteé la misma pregunta en Ubuntu-ar, soy miembro de varias comunidades. Pregunto, porque no sé ¿está mal hacer eso? ¿lo importante no es resolver el problema? Si esta u otra comunidad lo resuelve ¿no redunda en un beneficio para todos los usuarios de Ubuntu, independientemente de su nacionalidad o comunidad de pertenencia?

No hay ningun problema que lo postees en otra comunidad (el error es cuando se postea la misma pregunta varias veces en un mismo foro, pero no es el caso), a lo que me refería es que ya te dieron ahí las respuestas que te podría haber dado, por eso solo agregue wine.

> Sigo sin poder resolver el problema y necesito ayuda.

Saludos y muchas gracias,
Alejandro.

Espero llegue la ayuda que necesitas,

Saludos!

---

### Post by moreback on 2009-05-23
A lo mejor el problema con el VirtualBox es el asunto de la red, ya que esta es un poco complicada ya que hay que usar un puente de red y también hacer que el host Linux haga IP forwarding.

No tengo una guía de como hacerlo, sólo se que la cosa va por ahí. Yo también tengo que hacer funcionar la MV, pero me falta hacer estas configuraciones.

Si alguien se las sabe que lo postee.

Gracias.

---

### Post by kamus on 2009-05-24
> **moreback said:**
> A lo mejor el problema con el VirtualBox es el asunto de la red, ya que esta es un poco complicada ya que hay que usar un puente de red y también hacer que el host Linux haga IP forwarding.

No tengo una guía de como hacerlo, sólo se que la cosa va por ahí. Yo también tengo que hacer funcionar la MV, pero me falta hacer estas configuraciones.

Si alguien se las sabe que lo postee.

Gracias.

En la ultima version de virtualbox puedes configurar la tarjeta de red en modo bridge, esto permite emular que esa maquina estuviera conectada directamente en la red local (recordar que antes solo era posible hacer NAT y no habia forma de llegar desde el exterior).

Puedes descargarlo desde [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) , un par de lineas estan publicados los repositorios para ubuntu en sus distinta versiones que puedes agregar siguiendo las instrucciones publicadas en ese wiki. Nunca use la aplicacion que mencionas de todas maneras vncserver para compartir y visualizar el escritorio de forma remota me ha funcionado super bien tanto para Linux y Windows (excepto vista que tiene un comportamiento aveces no esperado).

Saludos;)

{1} [http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756) (Extensa documentacion sobre virtualizacion!)

---

### Post by aledruetta on 2009-05-25
> **gmunioz said:**
> Hola Alejandro:

Ya publiqué en ubuntu-ar, lo único que conozco parecido a lo que utilizabas.

Sin embargo, para quede claro, no se trata de escritorios remotos, se trata 

de una aplicación de Microsoft Office 2007, que permite compartir 

documentos en línea.

Saludos.

Posteo aquí también, la respuesta en ubuntu-ar:

> Hola gmunioz,

Puede que me esté equivocando, pero hay una aplicación de Office que es OfficeLive, que responde mucho a la descripción que vos hiciste. La aplicación que yo mencioné, Microsoft SharedView, creería que no es una aplicación de Office. Lo que hace es compartir el escritorio y cualquier aplicación que se esté ejecutando en él. 

Por ejemplo, en estos días estoy haciendo un cursito de Flash. Yo estoy viviendo en Sao Paulo, Brasil, y mi hermana y mi cuñado en Santa Fe, Argentina. Entonces yo les estaba pasando lo que aprendía por medio de esa aplicación. Es decir ellos veían en mi escritorio, la ventana de Macromedia, yo les mostraba los pasos a seguir, si ellos querían me pedían el control y eran ellos los que actuaban sobre la aplicación, etc. Lo mismo podía hacer sobre cualquier aplicación.

Con mis alumnos empleaba, por ejemplo, Power Point, Rosetta Stone, diccionarios como el Ultralingua, el de la RAE, textos en Word, les mostraba, ejemplificando en mi escritorio, cómo activar alguna opción o instalar una aplicación. Inclusive, si ellos me dan el control de su escritorio, se las instalo yo ¿Se entiende? No es simplemente escritura colaborativa, cosa que podría resolverlo perfectamente con Google Docs.

Ahora, en Ubuntu, se me complicó la cosa. Creo, por lo que voy viendo hasta ahora, que implementar la tecnología VNC o NX, no va a ser factible, ya que requeriría adaptarla a cada situación concreta que me presenta cada alumno, cosa que varía permanentemente.

Creo que lo ideal sería, lograr que el Microsoft SharedView funcione por medio de Wine o del XP que virtualicé con VirtualBox. Hasta ahora no lo conseguí.

Saludos y muchas gracias,
Alejandro.

---

### Post by gmunioz on 2009-05-25
Hola Alejandro:

Efectivamente segun Microsoft:

```
Microsoft SharedView
Conecte hasta con 15 personas de diferentes ubicaciones y muéstreles el contenido de su pantalla para no perder su atención. Comparta, revise y actualice documentos con diferentes personas en tiempo real. Se necesita un Id. de Windows Live ID (de Passport, Hotmail o MSN) para iniciar sesiones pero no para unirse a otras sesiones.
Información general
Mantenga unas reuniones y conferencias más eficaces
Conecte hasta con 15 personas de diferentes ubicaciones y muéstreles el contenido de su pantalla para no perder su atención.
Colabore con otros en tiempo real
Comparta, revise y actualice documentos con diferentes personas en tiempo real.
Úselo en cualquier momento y lugar
SharedView es fácil de usar, desde cualquier lugar y de un modo instantáneo.
Novedad de la versión 1.0: se ha agregado una experiencia conjunta basada en web para hacer que SharedView sea aún más fácil de usar.
Requisitos del sistema
Sistemas operativos compatibles: Windows Server 2003 Service Pack 1; Windows Vista Home Premium; Windows Vista Service Pack 1; Windows Vista Ultimate; Windows XP Service Pack 2; Windows XP Service Pack 3
Un equipo con un procesador de al menos 700 MHz que reúna los siguientes requisitos:
# Memoria: mínimo de 256 MB de RAM (se recomienda 512 MB).
# Disco duro: 10 MB de espacio libre en disco.
# Pantalla: resolución de pantalla mínima de 800 × 600 (se recomienda 1024 × 768).
# Aplicaciones: DirectX 8.0 o superior instalada en el equipo.
```

Con estos requisitos estimo que en una pc con al menos 2 gigas de RAM 

y Virtualbox configurado con 1 giga de RAM y coriendo un Windows XP sp3

es posible que funcione.

Saludos.

---

