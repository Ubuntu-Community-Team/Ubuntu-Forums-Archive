---
title: "How-To: PekWM"
date: 2009-06-12
forum: Software
---

### Post by Iced_R on 2009-06-12
No sé si irá aquí, pero por si acaso lo dejo no más. Que algún moderador lo mueva donde corresponda xDDD.


Primero que todo, PekWM es un simple gestor de ventanas, con un menú extremadamete reducido (si apretamos la tecla derecha del mouse, salen 4 opciones xDD) y deja casi todo el procesador para lo que queramos. Las desventajas que tiene es que no carga por defecto un panel para minimizar nuestras aplicaciones y además que, al tener por defecto un fondo negro, como que no se ve muy amistoso... Pero, con un poco de trabajo, podemos dejarlo extremadamente genial, y podemos ponerle lo que queramos.

Primero, un truquito que aprendí del foro antiguo de Ubuntu-Cl, que es para modificar GKT y hacer que nuestras aplicaciones se vean como en GNOME. El link al post original es [este]("http://foros.ubuntu-cl.org/viewtopic.php?t=3171&postdays=0&postorder=asc&start=0&sid=f6b4bcd69350adc2638998db648c71ab").

Lo primero es definir nuestro tema GTK y los íconos en la sesión de Gnome. Sí, en Gnome.  

Es preferible que el tema sea con colores definidos, así nos ahorramos una cuántos ajustes.  
 
Luego copiamos el tema y los íconos en: 
 
/usr/share/themes 
/usr/share/icons 

En nuestro home se encuentra un archivos llamado “.gtkrc-2.0” (si no es así, simplemente lo creamos) En ese archivos podemos indicar ciertas características que deseamos para nuestro entorno, por ejemplo, algunas personas aceleran la carga de los menús insertando un pequeño script. Lo que nosotros haremos será forzar la carga del tema definido anteriormente, le indicaremos a nuestro navegador de ficheros y a todas las aplicaciones, qué tema y qué iconos deben emplear. Si gtkrc-2.0 tiene algo escrito, podemos hacer una copia o simplemente borrarla, no sucederá nada si borramos su contenido (pueden conservar el script de los menús) al contrario, las cosas se complicarán ( en Gnome) si escribimos algo erróneo. Lo que copiaremos en gtkrc-2.0 será:       

```
gtk-font-name = "Sans 11" 
include "/usr/share/themes/ClearClossy-grey/gtk-2.0/gtkrc" 
gtk-icon-theme-name = "Oxygen-Gnome" 
```**Donde:** 
 
**gtk-font-name:** corresponde a la tipografía y al tamaño de esta para nuestras aplicaciones. 
 
**include:** la ruta exacta de nuestro tema GTK 
 
**gtk-icon-theme-name:** el nombre de nuestro tema de íconos en /usr/share/icons 

La gracia de este archivo es que fuerza a cualquier gestor de ventanas o escritorio que trabaje con GTK a leer los archivos que aparecen indicados. Ahora bien, si hay problemas, lo mejor es simplemente borrar el archivo creado y rehacerlo en GNOME (como se fuerza a GTK a parecerse a GNOME, es como lógico que cualquier modificación a lo que contiene el script deba hacerse en GNOME xD).

Ahora, PekWM.

[B]INSTALANDO PEKWM

[/B]Este gestor de ventanas se puede instalar desde los repositorios oficiales de Ubuntu. No es la última versión, pero es estable, y funciona. Simplemente hay que aplicar en una consola **sudo apt-get install pekwm**. Y, para tenerlo relativamente completo, debemos instalar los siguientes programas:

1.- hsetroot (para ponerle fondo de pantalla al escritorio)
2.- fbpanel (una barra de herramientas para minimizar nuestras aplicaciones)
3.- xcompmgr (un programa que emula cierta clase de efectos a lo Compiz, pero mucho más básico y obviamente mucho más liviano)
4.- pcmanfm (el gestor de archivos de LXDE, rápido y relativamente bonito xD)

Esta parte es sencilla. Lo "complicado" viene ahora

[B]CONFIGURANDO PEKWM

[/B]Cuando entramos a PekWM en Inicio, vemos un escritorio negro sin nada, y si hacemos click con el botón derecho en cualquier parte del escritorio, vemos lo que dije anteriormente, un menu muy reducido. Primero, vamos a la carpeta /home/tu_tusuario/.pekwm, donde se encuentran todos los archivos de configuración de PekWM. El más importante de todos es uno que se llama start, que es el que "marca" los programas que deben ejecutarse al inicio. Ahi es donde comenzamos a agregar programas.

Si se fijan en la sintaxis de los comentarios del mismo start, se darán cuenta que basta con llamar al programa y poner al final un signo &. Por ejemplo, para llamar al panel (fbpanel) basta con agregar al final del documento **fbpanel &**. Para el fondo de pantalla hay que llamar a hsetroot, con la orden **hsetroot -fill ruta_de_la_imagen &**. Y para los efectos de escritorio, usamos xcompmgr con la orden **xcompmgr -l-10 -t-10 -D5 -cfF &**. El resto de programas los saqué de GNOME (por ejemplo el ícono de Network Manager, que se llama con la orden **nm-applet &**, el de volumen que se llama con la orden **gnome-volume-control-applet &, **y el montado automático de dispositivos USB, que se hace con el comando **gnome-volume-manager &**)


Y eso es todo! Si reiniciamos PekWM, tendremos un escritorio bonito, liviano, y amigable... y por sobre todo, configurable por nosotros mismos.


Saludos!

---

### Post by Carlos C on 2009-06-12
Es posible tener un enlace a imageshack (o algún sitio alternativo) para ver el resultado?

---

### Post by Iced_R on 2009-06-23
Algunas capturas de pantalla de PekWM (tuve medio botado el how-to xq me ha tocado mucho que hacer en la Universidad xD)

[[IMG]http://img37.imageshack.us/img37/2779/pantallazo1h.th.png[/IMG]](http://img37.imageshack.us/i/pantallazo1h.png/)

[[IMG]http://img91.imageshack.us/img91/7286/pantallazo2x.th.png[/IMG]](http://img91.imageshack.us/i/pantallazo2x.png/)

[[IMG]http://img341.imageshack.us/img341/2981/pantallazo1j.th.png[/IMG]](http://img341.imageshack.us/i/pantallazo1j.png/)


Intenté ponerle una barra como AWN, pero lamentablemente me tiró un sector negro de como todo el ancho de la pantalla. Cuando aprenda más acerca de PekWM y de AWN para hacerlos convivir juntos en el mismo entorno, lo posteo.


Saludos.

---

### Post by Carlos C on 2009-07-06
[Post de la semana]("http://ubuntuforums.org/showthread.php?t=1176055"): [6 de julio]("http://ubuntucl.wordpress.com/2009/07/06/usando-pekwm-como-gestor-de-ventanas-en-ubuntu/") de 2009

---

