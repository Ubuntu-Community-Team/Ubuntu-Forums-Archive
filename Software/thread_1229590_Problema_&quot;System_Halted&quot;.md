---
title: "Problema &quot;System Halted&quot;"
date: 2009-08-02
forum: Software
---

### Post by klaussmeine on 2009-08-02
Hola Ubunteros Soy nuevo por estos lares pero llevo usando Ubuntu desde hace bastante tiempo. El problema es que aun estoy algo verde. En mi computador funciona perfectamente (un HP Pavilion dv6000 que venía previamente con un tal Vista que dejé ciego a las dos semanas). El caso es que lei en alguna parte que en los computadores viejos el Ubuntu funcionaba mejor y más rápido ya que consumía menos recursos bla bla... Mi hermana tiene en su habitación, la pobre, **un computador del año de la pera**, que con Windows xp Home iba obviamente a pedales. Me lancé a la aventura de instalarle el **Ubuntu 9.04** con el mismo Live CD que utilicé para instalarmelo a mí.
 Al principio parecía haber problemillas con la pantalla y la resolución pero eso se solucionó en seguida, aunque sigue habiendo conflictos con la pantalla de inicio y la de apagado (me sale un mensaje en la pantallita con un error que dice algo así como :"system overload". Pero ni caso. Ese no es el mayor problema.
 Hay, pues, dos cosas que me gustaría saber si alguien me pudiera ayudar a resolver:

 1. **Al apagar el ordenado**r, hace todo el paripé y cuando llega el momento de la verdad la torre hace el sonido que hacía con windows cuando se apagaba peeeero se queda encendido y en la pantalla me pone el siguiente mensaje: " **353.067059] System Halted** " y ahí se queda esperándote a que le apagues manualmente (o a ver que cara se te queda cuando despues de 10 minutos ves que no piensa apagarse por que no le da la gana)

2. Con Windows XP ese computador funcionaba. Mal, pero funcionaba. Lentísimo, te daba tiempo a bailarte una cueca hasta que se abriera cualquier programa que quisieras usar. Tan lento que cuando abrías el MSN cuando por fin estabas conectado ya odiabas tanto a la humanidad que preferías cerrarlo para no insultar a nadie. Y con Ubuntu pensé que la cosa sería distinta. Y lo es, el Pidgin se abre de inmediato por ejemplo, el Firefox tarda un poquito pero no tanto como para desesperarse. En fin que *algo* mas rápido si que va pero aun así sigue siendo bastante lento. Estaría bien que se me informara si es que hay algo que pudiera hacer para que esta pobre mujer tenga un computador ***decentemente rápido***.

 Mientras iba escribiendo esto me dió por "apagar" el ordenador de mi hermana pero no del todo. Es decir lo puse a **hibernar**. Ahora lo he vuelto a encender para ver las especificaciones de éste y ponerlas aquí por que sé que me las van a preguntar y se encendió rápidamente (dentro de lo posible). Así que por lo menos hay una vía para "apagarlo sin tener que forzar el botón de apagado" Si no encuentro solución le diré que lo ponga a hibernar en lugar de apagar. ¿No? (espero que no se nos vaya la luz)

Aquí estan las características del equipo. Por favor no me aconseje nadie que me compre otro computador... Ya sé que es antiguo pero no quiero tirarlo a la basura si se puede hacer algo.

Ubuntu
Versión 9.04 (jaunty)
Núcleo Linux 2.6.28-14-generic
GNOME 2.26.1

Hardware
Memoria 481,8MiB (con pedales incuídos)
Procesador AMD Duron(tm) Processor 
HD disponible: 30.7 GiB (Cualquier iPod se mearía de la risa)

En fin espero respuestas. Gracias por escuchar

---

### Post by nopersona on 2009-08-02
Hola klaussmeine, un gusto. Mira, ese pc malo no es, un poco viejo sí, pero tiene recursos de sobra para brillar. Por partes. Sobre "**System Halted** " pordría ser por el ACPI, al ser un equipo relativamente viejo.  Una forma de solucionarlo sería forzando el ACPIy agregando un modulo.

```
sudo gedit /etc/modules
```Y agregas

```
apm power_off=1
```Luego agregas la opción de forzar acpi al kernel

```
sudo gedit /boot/grub/menu.lst
```Para ver qué kernel usa, en caso de tener más de uno instalado

```
uname -r
```Luego, en la linea kernel agregas:

```
acpi=force
```Rebotas y listo.  Si no llegase a funcionar, [revisa este hilo]("http://ubuntuforums.org/showthread.php?t=1219262"), hay más información útil similar. El problema no es el mismo, pero puede ayudarte a diagnosticar. 

Ahora sobre el entorno en si, creo que poner gnome, y más aún, ubuntu (so pena de que me llegue una) a un equipo un tanto viejo, no es lo óptimo. Por ejemplo, pordrías probar LXDE como entorno, es muy versatil y "usable" que es lo más importante, no sacamos nada con usar entorno ligeros si para el usuario común son un lío. O XFCE, hay mucho de dónde elegir. Ahora bien, también le podrías dar un ojito a la distro de mi firma, un lujo, liviana y potente. [Te dejo otro link. ]("http://www.google.cl/linux?hl=es&q=distros+para+pc+viejos&btnG=Buscar&meta=")

Saludos.

---

### Post by klaussmeine on 2009-08-02
Muchísimas gracias nopersona, la verdad es que cuando vi lo lento que iba (a pesar de todo algo más rápido que con windows) se me pasó por la mente la idea de usar un entorno que ocupara menos recursos. Verás llevo tiempo usando Ubuntu pero estoy recién familiarizándome con la terminal y todas sus "diferencias" por así decirlo con Windows. 
 Supongo que por usar una distribución más conocida, me decantaría por Xubuntu que es como me aconsejas XFCE (que lo acabo de aprender viendolo en el link que me has puesto)
 Y la pregunta siguiente hace completamente off-topic pero es simple curiosidad y con algún ejemplo me conformaría :) ¿Sin qué se queda Xubuntu para ser más ligero?
 Nuevamente muchísimas gracias por la respuesta. A veces tienes las ideas dandote vueltas por encima de la cabeza pero hace falta una ayudita de alguien para atraparlas y aplicarlas. Gracias
 
PD El foro de Ubuntu Chile funciona mil veces mejor que el de España... Bueno al de España directamente no puedo entrar.

---

### Post by Carlos C on 2009-08-05
Xubuntu usa programas más livianos. No trae instalado OpenOffice, por ejemplo, sino que usa abiword y gnumeric. Además, Xfce es un entorno gráfico más liviano. Por lo mismo, algunas configuraciones pueden ser un poco más complejas, pero en ningún caso estamos hablando de algo extremo, es muy facil de usar. Por otra parte, siempre es posible instalar los programas que usas en Ubuntu, en caso de necesidad, ya que el sistema base es el mismo y las herramientas de instalación también. Lo más fácil es que descargues el LiveCD y lo pruebes sin instalarlo.
Saludos.

---

### Post by klaussmeine on 2009-08-05
Hola de nuevo. Al final instalé Xubuntu en el ordenador este. Va bastante más rápido (aunque probé puppylinux y dreamlinux y van como cohetes pero hice no sé que destrozo en el disco duro y para no seguir cagándola instalé xubuntu que se instala solo y no meto la pata por ninguna parte) El caso es que persisten os problemillas. Sigo teniendo problemas con lo de apagar el ordenador. No se apaga. Me sale el mensaje con la pantalla en negro y ahí se queda. Tengo que forzar el cierre para que se apague. :confused:
 
 Probé a utilizar los comandos que se me dieron aquí para solucionar el mismo problema en ubuntu pero no funcionan en Xubuntu. (Supongo que error de novato)
 También tengo otro problema. Al encender el ordenador, se inicia el sistema con la pantalla con una resolución que no hay manera de cambiar y que se quede quieta. Quiero decir, se inicia directamente con una resolución que me deja un buen cacho de pantalla inutilizada. Asi que cada vez que inicio tengo que cambiar la resolución a 1024x980 que es la que mejor se ve. Si apago el ordenador y lo velvo a encender vuelve a cambiarse la resolucion a la misma de antes... Alguna idea? Gracias por la ayuda :)

---

