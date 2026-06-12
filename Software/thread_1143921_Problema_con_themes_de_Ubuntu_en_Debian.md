---
title: "Problema con themes de Ubuntu en Debian"
date: 2009-04-30
forum: Software
---

### Post by ramiro_md on 2009-04-30
Buenas actualmente estoy usando la versión Lenny de Debian, pero el otro día me vi obligado a usar la notebook de mi hermana con Ubuntu 8.10. 
Como sus themes e iconos y demases no me gustaban, cree una cuenta de usuario nueva para mi y la configuré con el theme darkroom (viene por defecto instalado en ubuntu) y los iconos oxygen que ya venian también por defecto instalados.
La cuestión es que me copó como dejé el desktop, y quise migrar la configuración a mi debian.
Lo primero quen hice fue localizar la carpeta del theme de ubuntu en /usr/share/themes y copiarla en mi /home/armiro/.themes. Luego instalar desde synaptic kde-oxygen-icons (creo que así se llama el paquete). COn eso ya tenía el theme y los iconos que me habían quedado tan copados en el ubuntu de mi hermana.
El problema es que tanto los iconos como el theme se visualizan de una forma no correcta en Debian.
POr ejemplo, los iconos no se aplican a todo el sistema, es decir, hay carpetas (todas) y algunos otros iconos como los del escritorio que no se les aplica  el cambio :S. Por otro lado el theme gtk se ve algo mal en el aspecto de los botones..se genera un relieve (cuadrado) horrible que en ubuntu es más redondeado y menos rustico xD.
Acá dejo unos screens para que entiendan bien mi problema y me puedan dar una mano.
Un saludo y muhas gracias gente :).

---

### Post by sdennie on 2009-04-30
Lo que pasa es que falta el paquete gtk2-engine-ubuntulooks.  Asi que estas poniendo los colores y lo de metacity pero gtk no sabe hacer los widgets y esta usando la tema de gtk por defecto.  Fijate si podes bajar gtk2-engine-ubuntulooks.deb y instalarlo.

---

### Post by sdennie on 2009-04-30
> **sdennie said:**
> Lo que pasa es que falta el paquete gtk2-engine-ubuntulooks.  Asi que estas poniendo los colores y lo de metacity pero gtk no sabe hacer los widgets y esta usando la tema de gtk por defecto.  Fijate si podes bajar gtk2-engine-ubuntulooks.deb y instalarlo.

Edit:
A buscar un poco un una maquina virtual, en lugar de instalar ubuntulooks, fijate el paquete gtk2-engines de Ubuntu.  A ver el screenshot un poco mas, me parece que esta tema usa Clearlooks o capaz que Murrine.

---

### Post by ramiro_md on 2009-04-30
Chabon gracias por la data !...me parece que usa clearlooks...xq las barras de descargas son al estilo de clearlooks..ahora me fij oeso que me decis, si funciona te pago una birra la proxima RP (?) jaja.
Un abrazo.

---

### Post by sdennie on 2009-04-30
No se si es Clearlooks o Murrine (a ver mas cosas ahora pienso Murrine).  Pero, alguno de los dos van a funcionar.

Saludos

(Y acepto la birra ;) )

---

### Post by ramiro_md on 2009-04-30
A pesar de haberme dado una respuesta muy convincente, no funcionó :S.
Instalé gtk2-engine.clearlooks y murrine (gtk2-engines ya estaba instalado) y no hubo cambios :S.

---

### Post by sdennie on 2009-04-30
Pero, cambiaste el tema despues?  Despues de instalar un engine nuevo, hay que cambiar el tema a otra despues a volver.

---

### Post by ramiro_md on 2009-04-30
Si, tenioa el clearlooks clasico. Instale el engine, reinicié X, y cambié a darkroom (el cual volví a instalar en ese momento).

---

### Post by sdennie on 2009-04-30
Bueno, dame un segundo.  Me fijo en una maquina virtual.  Es posible que necesitas gtk2-engine-pixbuf tambien.

Edit:

Si, en una maquina virtual cambiada a usar ese tema, los engines gtk son: gtk2-engines, gtk2-engine-murrine y gtk2-engine-pixbuf.  Proba, gtk2-engine-pixbuf.

---

### Post by ramiro_md on 2009-04-30
No, dejá, instaló los 5 o 6 engines que tengo y me fijo. SI anda..desinstalo uno por uno aver que pasa.

---

### Post by ramiro_md on 2009-04-30
Pixbuf me vino instyalado x defecto :S voy a hacer lo que comentaba anteriormente.

Edit: No anduvo :S

---

### Post by sdennie on 2009-04-30
Otra cosa que podes hacer es aprender gnome-control-center desde un terminal para ver los errores que pasan cuando cambias temas.

---

### Post by ramiro_md on 2009-04-30
> **sdennie said:**
> Otra cosa que podes hacer es aprender gnome-control-center desde un terminal para ver los errores que pasan cuando cambias temas.
Lo ejecute como root y para empezar me tiro el sigiente cartelon:
> No se puede iniciar el gestor de configuración «gnome-settings-daemon».
Si el gestor de configuración de GNOME no se está ejecutando, es posible que algunas de las preferencias no surtan efecto. Ésto puede ser el síntoma de un problema con Bonobo o que un gestor de configuración que no es de GNOME (por ejemplo KDE) ya esté activo y en conflicto con el gestor de configuración de GNOME.

EDITO:
EJecutó igual y al cambiar me tira lo siguiente:
> (gnome-appearance-properties:4742): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,
(gnome-appearance-properties:4742): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,
(gnome-appearance-properties:4742): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,
(gnome-appearance-properties:4742): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,
(gnome-appearance-properties:4742): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,
(gnome-appearance-properties:4742): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,
(gnome-appearance-properties:4742): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,
(gnome-appearance-properties:4741): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,
(gnome-appearance-properties:4741): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,
(gnome-appearance-properties:4741): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,
(gnome-appearance-properties:4741): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,
(gnome-appearance-properties:4741): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,
(gnome-appearance-properties:4741): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,
(gnome-appearance-properties:4741): Gtk-WARNING **: Imposible encontrar el motor de temas en la ruta al _modulo: «murrine»,

Murrine :O :O :O :O

---

### Post by sdennie on 2009-04-30
> **ramiro_md said:**
> Lo ejecute como root y para empezar me tiro el sigiente cartelon:


EDITO:
EJecutó igual y al cambiar me tira lo siguiente:

Murrine :O :O :O :O

VISTE?!  Te dije!  ;)

Hacete un:

```

find /usr/lib -name "*murrine*"

```

Decime lo que pasa

---

### Post by ramiro_md on 2009-04-30
> 
ramiro@ramiro-desktop:~$ find /usr/lib -name "*murrine*"
ramiro@ramiro-desktop:~$ 

No devuelve nada :O

---

### Post by sdennie on 2009-04-30
Y:

```

dpkg -l | grep -i murrine

```

?

Me parece que no tenes murrine instalado, che.

---

### Post by ramiro_md on 2009-04-30
> **sdennie said:**
> Y:

```

dpkg -l | grep -i murrine

```

?

Me parece que no tenes murrine instalado, che.

Puede ser, ese comand oque me pasaste no devuelve nada...voy a instalar gtk2-engine-murrine y murrine-theme nuevamente a ver que pasa.

---

### Post by ramiro_md on 2009-04-30
ejecuté gnome-control-center e intenté cambiar el theme nuevamente y la consola devolvió esto:
> /root/.themes/DarkRoom/gtk-2.0/gtkrc:79: error: unexpected identifier `colorize_scrollbar', expected character `}'

Y por supuesto no cambió el theme.

---

### Post by sdennie on 2009-04-30
Me da mucho miedo que tenes algo de "/root" asi.  Si los paquetes estan bien instalados, haciendo algo como root puede arruinar todo por la tema de permissiones.  Pero, igual, fijate con las pruebas mias de arriba.  A ver si hay un cambio.

---

### Post by ramiro_md on 2009-05-01
Bueno sigo con esto, instalé mil vexces as cosas pero siempre me instala el theme en la carpeta /home/root, no hay caso ! :S debe haber algun parametro de aptitude o dkpg ara forzar la instalación en un directorio.

---

### Post by staar on 2009-05-01
chee, ojo que el del motor murrine hay nuevas versiones a cada rato, y algunos temas no funcionan con versiones viejas, no se, puede que la versión en los repos de debian (si es que está en los repos) sea más vieja que la de los de ubuntu...

saludos

---

### Post by ramiro_md on 2009-05-01
> **staar said:**
> chee, ojo que el del motor murrine hay nuevas versiones a cada rato, y algunos temas no funcionan con versiones viejas, no se, puede que la versión en los repos de debian (si es que está en los repos) sea más vieja que la de los de ubuntu...

saludos

En debian está la version 0.53.1-1 en ubuntu cuál está ? si hay una más nueva no me arman el .deb lo atacchean en el post ? :)
De todas formas sigo preguntandome por qué instala el theme en el home de root y no en el de mi usuario...:confused:

---

### Post by staar on 2009-05-01
jojo algo viejita :-P en jaunty ya van por la 0.90.3-1, bajate el deb de acá: [http://packages.ubuntu.com/jaunty/gtk2-engines-murrine]("http://packages.ubuntu.com/jaunty/gtk2-engines-murrine")

y, la verdad, ni idea porque tenés el theme en el /root, decís que lo copiaste vos desde el ubuntu? no tendrás un link simbólico desde el .themes de tu home hasta el .themes de root? yo lo tengo para que las aplicaciones de root usen el mismo tema que las del usuario...

saludos

---

### Post by ramiro_md on 2009-05-05
Gracias por la ayuda, hoy instalé lenny en una partición más grande, así que haré las pruebas de los themes en el "debian viejo" y postearé los avances.
Un saludo, y ya volverán a tener noticias misa xD

---

### Post by ramiro_md on 2009-05-06
Bueno, como ya decia iban a volver a tener noticias mías con respecto a este tema. Activé los repositorios unstable y me aparecian la últimas versiones de gtk2-engine (2.18.0) gtk2-engine-murrine (0.90.1) y gtk2-engines-pixbuf (2.16)..las instalé e instalé el theme dark room compacto (una variante de dark room, porque este último no lo tenía a mano).
El tema es que mejoró la visualización de algunos botones, pero en otros (como en los del navegador de archivos y los menu Gnome) ssiguen algo rústicos. Lo podrán ver en la imagen atacheada.
Por otro lado instalé la nueva versión de kde-icons-oxygen pero no se aplican a todos los iconos, fijense en el escritorio que el icono del home y de los discos no ha cambiado por ejemplo, lo mismo con las carpetas del navegador.
Bueno espero qu e me puedan ayudar a terminar este tema de una vez por toda, presiento que estamos cerca jeje.
Un saludo y gracias !

---

### Post by ramiro_md on 2009-05-06
Por si no atacheo je:
[http://es.tinypic.com/view.php?pic=99mlop&s=5]("http://es.tinypic.com/view.php?pic=99mlop&s=5")

---

### Post by ramiro_md on 2009-05-06
En a consola me devuelve estas líneas:
> /home/ramiro/.themes/DarkRoomCompact/gtk-2.0/gtkrc:97: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/ramiro/.themes/DarkRoomCompact/gtk-2.0/gtkrc:98: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/ramiro/.themes/DarkRoomCompact/gtk-2.0/gtkrc:164: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/ramiro/.themes/DarkRoomCompact/gtk-2.0/gtkrc:285: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.


---

