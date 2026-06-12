---
title: "No veo mi escritorio!"
date: 2008-10-23
forum: Software
---

### Post by Burro Adelante on 2008-10-23
Hola,
tengo Ubuntu 8.04 junto con Win XP. Funcionaba perfectamente bien pero un problema con un pendrive (no se bien que paso pero al sacarlo quedaba montado en el escritorio y al volver a ponerlo se abria un icono nuevo). La cuestion es que se colgo asi que no pude hacer otra cosa que apagar la laptop. Al iniciar nuevamente, elegi Ubuntu en el grub y luego de ingresar mi usuario y contrasena no aparece el escritorio. El cursor del mouse funciona (es un mouse blootooth) pero no hay nada que hacer! No reponde el teclado ni los botones del mouse. Finalmente lo unico que me queda por hacer es apagar nuevamente la laptop.
Alguien podria decirme que paso? Me da la sensacion de que el SO se carga y esta ahi... pero no hay escritorio para manejarlo.

Agradeceria un poco de ayuda ya que me gusta mucho el SO y quiero seguir usandolo.

Gracias.

---

### Post by hictio on 2008-10-23
Podrias probar lo siguiente, ojo que vas a perder toda configuracion que hayas hecho a tus settings (por ejemplo, si le seteaste a Gnome que te muestre la temperatura ademas de la hora en el Tray)

Prende la maquina, y no te loggees, movete a una consola virtual (Ctrl + Alt + F(1 al 7, para volver al login grafico)), loggeate en la consola, no muerde, y es tu mejor amiga.
Y tipea esto, es un comando por linea, ENTER al final de c/u:
```

mv .gnome .gnome.back
mv .gnome2 .gnome2.back
mv .gconf .gconf.back
mv .gconfd .gconfd.back
mv .metacity .metacity.back

```

Cuando terminas, salis con exit + ENTER.

Volve a la consola virtual que tiene el login grafico, y loggeate.

Tendrias que ver el desktop de Gnome como estaba cuando terminaste de instalar Ubuntu; si llegas a necesitar algo de lo viejo, o queres revertir, tenes backup de todo lo editado en el dir "*.back".

Una cosa que si no entiendo es como un pen drive USB te puede haber ***** toda la cosa asi, acordate que hay que desmontarlos antes de sacarlos, pero eso no te deberia tumbar el sistema de esa forma.

---

### Post by Burro Adelante on 2008-10-24
Hola,
gracias por tu respuesta.
Probe lo que me dijiste, pero a cada entrada que hago me devuelve : -bash: mv.[...].back: command not found

Lo del Pendrive ocurrio mientras transferia fotos desde mi compu. Una vez que lo saque sin desmontar quedo el icono en la maquina. Luego lo leyo un Windows y volvio a mi maquina. En esa sesion tambien instale el Picaza de Google para fotos. Pero todo andaba bien. El pendrive tambien lo usaba en un Windows.

Ayer, viendo otros foros pude ingresar desde gnome y ver todo los archivos. Inclusive cambie de lugar todo aquello que estaba dentro de mi sesion por las dudas.
No se que mas datos te puedo dar...

---

### Post by Burro Adelante on 2008-10-24
Perdon,
estaba escribiendo mal el codigo. Me faltaban los espacios.
Ahora me dice:
mv: target '.back' is not a directory

Alguna idea al respecto?

---

### Post by sajnox on 2008-10-24
Probaste con reconfigurar el xorg.conf?

Te vas a una consola ctrl + alt + f1 y te logueas

Paras al entorno grafico

```
sudo /etc/init.d/gdm stop
```

Reconfiguras el xorg (en el proceso te genera un backup del existente)

```
sudo dpkg-reconfigure -phigh xorg.conf
```

Reinicias gdm

```
startx
```

---

### Post by hictio on 2008-10-24
> **Burro Adelante said:**
> Perdon,
estaba escribiendo mal el codigo. Me faltaban los espacios.
Ahora me dice:
mv: target '.back' is not a directory

Alguna idea al respecto?

Te da ese error porque estas poniendo un espacio entre: ".gnome" y ".back"

Es asi:
```

mv ESPACIO .gnome ESPACIO .gnome.back ENTER

```

Lo que estas haciendo es renombrar el directorio ".gnome" a ".gnome.back", le podes poner el nombre que quieras, siempre y cuando sea diferente del original.

---

### Post by Burro Adelante on 2008-10-24
> **sajnox said:**
> Probaste con reconfigurar el xorg.conf?

Te vas a una consola ctrl + alt + f1 y te logueas

Paras al entorno grafico

```
sudo /etc/init.d/gdm stop
```

Reconfiguras el xorg (en el proceso te genera un backup del existente)

```
sudo dpkg-reconfigure -phigh xorg.conf
```

Reinicias gdm

```
startx
```
Probe lo que me dijiste pero no funciono:
Cuando ingreso la segunda linea de reconfigure aparece un texto dentro del cual indica que: Cannot set LC-Type, LC-Messages, LC-all to default locale: no such file or directory.
Package xorg-cofig is not installed or no info is available.
No puedo ingresar todo el texto ya que una vez que fallo debo ingresar a Win XP para escribirte.

Alguna idea con esta informacion?

---

### Post by Burro Adelante on 2008-10-24
> **hictio said:**
> Te da ese error porque estas poniendo un espacio entre: ".gnome" y ".back"

Es asi:
```

mv ESPACIO .gnome ESPACIO .gnome.back ENTER

```

Lo que estas haciendo es renombrar el directorio ".gnome" a ".gnome.back", le podes poner el nombre que quieras, siempre y cuando sea diferente del original.

Volvi a ingresar pero no funciona. Vuelve a indicarme que no existe ' gnome'

---

### Post by hictio on 2008-10-24
> **Burro Adelante said:**
> Volvi a ingresar pero no funciona. Vuelve a indicarme que no existe ' gnome'

Mhhmmm... Estas tipeando el punto adelante de 'gnome', verdad?
Especialmente del primero de los dos, que es el que existe, lo mismo para los otros directorios.

---

### Post by Burro Adelante on 2008-10-25
Si, lo puse tal cual me dijiste.

---

### Post by anarko on 2008-10-25
Solamente con .gnome te da el error? 
o con todos los directorios que te dijo hictio?

.gnome creo que no exista mas, porlomenos en la beta del 8.10.

---

### Post by Burro Adelante on 2008-10-25
me da error con todos.

---

### Post by anarko on 2008-10-25
Entonces no existen esos directorios.
Postea el contenido de la salida de "ls -a ." de tu directorio home.
Por ejemplo: 
```
anarko@anarka:~$ ls -a .
.              .cache      Escritorio   .gconfd          .gstreamer-0.10  Imágenes  .mozilla-thunderbird  Público                    .themes               Videos
..             .config     .esd_auth    .gksu.lock       .gtk-bookmarks   .lircrc   Música                .pulse                     .thumbnails           .Xauthority
.bash_history  .dbus       Examples     .gnome2          .gvfs            .local    .nautilus             .pulse-cookie              .tvtime               .xsession-errors
.bash_logout   .dmrc       .fontconfig  .gnome2_private  .ICEauthority    .mc       Plantillas            .recently-used.xbel        .update-manager-core
.bashrc        Documentos  .gconf       .gnupg           .icons           .mozilla  .profile              .sudo_as_admin_successful  .update-notifier
 
```

---

### Post by hictio on 2008-10-25
Que version de Ubuntu estas usando?

---

### Post by sajnox on 2008-10-26
> **Burro Adelante said:**
> Probe lo que me dijiste pero no funciono:
Cuando ingreso la segunda linea de reconfigure aparece un texto dentro del cual indica que: Cannot set LC-Type, LC-Messages, LC-all to default locale: no such file or directory.
Package xorg-cofig is not installed or no info is available.
No puedo ingresar todo el texto ya que una vez que fallo debo ingresar a Win XP para escribirte.

Alguna idea con esta informacion?

Perdon, es que escribi mal la segunda linea

donde dice:

```
sudo dpkg-reconfigure -phigh xorg.conf
```

Deberia decir:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by faktorqm on 2008-10-27
```
sudo displayconfig-gtk
```

---

### Post by Burro Adelante on 2008-10-28
Bueno, paso a hacerles una actualizacion general:

Con respecto a renombrar gnome, gnome2, etc, finalmente pude hacerlo pero no funciono. (gnome no existe, el resto si). Pero una vez que salgo y me logeo en f7 no pasa nada.

Con respecto a reconfigurar el xorg o xserver, una vez que completo los pasos y me logueo lo unico que cambia es que aparece toda la pantalla mas pixelada y por un momento el puntero se pone en cruz pero luego vuelve a la flecha. No hay mas cambios que eso.

Puedo entrar desde Failsafe Gnome (xterm) y a traves del nautilus ver todos los archivos. Incluso aparece el wallpaper de ubuntu, pero dado que soy un asno al respecto no tengo idea que hacer. Vi en otros foros que hay gente con el mismo problema. Uno lo resolvio creando un nuevo usuario pero no se como hacer eso. 
Aqui hay algunos: [http://ubuntuforums.org/showthread.php?t=959894&referrerid=689052](http://ubuntuforums.org/showthread.php?t=959894&referrerid=689052)

Si pueden explicarme que hizo sigo las instucciones que me den. Igualmente no se si tenga el mismo problema.

---

### Post by hictio on 2008-10-29
Hola,

> 
Con respecto a renombrar gnome, gnome2, etc, finalmente pude hacerlo pero no funciono. (gnome no existe, el resto si). Pero una vez que salgo y me logeo en f7 no pasa nada.


Que version de Ubuntu estas usando? No entiendo como no tenes el directorio .gnome en tu home.

> 
Con respecto a reconfigurar el xorg o xserver, una vez que completo los pasos y me logueo lo unico que cambia es que aparece toda la pantalla mas pixelada y por un momento el puntero se pone en cruz pero luego vuelve a la flecha. No hay mas cambios que eso.


Cuando decis que es una pantalla pixelada, es como [esta](http://cgacimartin.files.wordpress.com/2007/06/errortightvncserver.png) (pero sin la ventana del terminal), cuando aparece eso, tenes el Panel de Gnome, la fecha y hora, etc?

> 
Uno lo resolvio creando un nuevo usuario pero no se como hacer eso. 


Si tenes el Panel de Gnome, selecciona: "System -> Administration -> Users and Groups".
Te aparece una ventana, "User Settings", click en 'Unlock', tipea tu password, y despues en la ventana de "User Settings", click en 'Add User', dale nombre password, etc.

---

### Post by Burro Adelante on 2008-10-29
La version de Ubuntu es la 8.04.1
Kernel 2.6.24-21
Kernel 2.6.24-19

La pantalla pixelada no tiene esa trama con cuadrados, es totalmente lisa pero pixelada.

Voy a probar agregar un nuevo usuario y te cuento

---

### Post by panchosnake on 2009-09-05
> **Burro Adelante said:**
> La version de Ubuntu es la 8.04.1
Kernel 2.6.24-21
Kernel 2.6.24-19

La pantalla pixelada no tiene esa trama con cuadrados, es totalmente lisa pero pixelada.

Voy a probar agregar un nuevo usuario y te cuento

Hola, he vuelto a abrir esta discusión porque estoy con el mismo problema, he probado con las soluciones que han dado, pero sin resultados.

Lo último que hice fue crear un usuario desde una consola virtual, sin embargo este usuario no tiene ningún privilegio, no puedo logearme como un root en la terminal tampoco acceder a ninguna configuración.
Por eso quiero preguntarles si uds entontraron una solución para este fallo en ubuntu o bien si saben cómo darle más privilegios a este usuario nuevo (los del root si es posible)

Les agradezco su tiempo y ayuda. adiós

Tengo ubuntu  9.04

---

