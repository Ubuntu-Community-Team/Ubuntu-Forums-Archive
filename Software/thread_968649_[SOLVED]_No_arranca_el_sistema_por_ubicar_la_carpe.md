---
title: "[SOLVED] No arranca el sistema por ubicar la carpeta personal en otra partición"
date: 2008-11-02
forum: Software
---

### Post by LianRome on 2008-11-02
Hola
Acabo de instalar Intrepid y lo que quise hacer fue indicarle al sistema que mi carpeta personal estuviera en otro lado y el problema es que ese lugar queda en otra partición: "/media/disk/julian". Allí está la carpeta personal que tenía en el 8.04.

No puedo recordar muy bien cómo lo hice (y no puedo entrar para verificarlo), pero creo la ruta fue:
"Sistema > Administración > Usuarios y Grupos" y allí hice clic en Propiedades. En alguna celda indiqué la nueva ruta a seguir (/media/disk/julian).
Cuando inicio sale este cartel:
"Su directorio personal está establecido a: pero al parecer no existe.¿Desea iniciar una sesión con el directorio / (raíz) como su directorio personal? Es probable que nada funcione a no ser que utilice una sesión a prueba de fallos."

Marco que iniciaré a prueba de fallos y luego de iniciar sesión sale este otro:
"Se está ignorando el archivo $HOME/.dmrc del usuario. Esto impide que se guarden la sesión predeterminada y el idioma. El archivo debería pertenecer al usuario y tener los permisos 644. El directorio personal del usuario debe pertenecer al usuario y no ser escribible para otros usuarios."
Y luego otros cartelitos más.

Intenté bucear en el Recovery mode, entrando como root, pero no sé qué comandos usar. Entiendo que no debería crear un Home nuevo, sino indicarle la ruta anterior ¿es así?
Vi que es algo similar a lo que se describe en [http://www.ubuntu-es.org/index.php?q=node/80137](http://www.ubuntu-es.org/index.php?q=node/80137) (no arranca el sistema por cambiar el nombre de usuario [solucionado]) y en [http://ubuntuforums.org/showthread.php?t=964897&highlight=$HOME/.dmrc](http://ubuntuforums.org/showthread.php?t=964897&highlight=$HOME/.dmrc) pero no sé muy bien si es aplicable esa solución.

Muchas gracias de antemano,

Julián.

---

### Post by gmunioz on 2008-11-03
Hola jul...:
Dado que no sabes lo que has hecho, es un poco difícil revertir el proceso.
Inicia en modo de recuperación, y del menu de recuperación elige la opción root
Iniciarás como administrador sin contraseña, en consola:
ejecuta:
cd /
ls
Tendrías que tener una salida similar a esta:
bin   cdrom  etc   initrd      lib    mnt  proc  sbin  sys  usr  vmlinuz
boot  dev    home  initrd.img  media  opt  root  srv   tmp  var
Si no aparece home, deberás crearlo, ejecutando
sudo mkdir /home
Una vez que exista /home, ya sea por que estaba creado o porque lo creaste, debes dar de alta un usuario para poder acceder a las gráficas, lo haces ejecutando:
sudo adduser nombre-usuario
Y dandole una contraseña
Completado el procedimiento deberás habilitarlo para que pueda actuar como administrador temporario lo haces ejecutando
sudo visudo
Y en el archivo que se abre buscas las líneas:

# User privilege specification
root ALL=(ALL) ALL

Y le agregas

nombre-usuario ALL = NOPASSWD: ALL
Guardas el archivo, reinicias con el nuevo nombre de usuario y su contraseña y te dedicas a buscar tu directorio personal para montarlo en  /home/usuario/comolollames
Saludos.
Gabriel. Solo doy soporte para Ubuntu.

---

### Post by mhoyos on 2008-11-03
> **LianRome said:**
> Hola
Acabo de instalar Intrepid y lo que quise hacer fue indicarle al sistema que mi carpeta personal estuviera en otro lado y el problema es que ese lugar queda en otra partición: "/media/disk/julian". Allí está la carpeta personal que tenía en el 8.04.

Julián.


hola:

si tu home, esta en otra particion, tenes que agregarlo en el archivo fstab:

```
/dev/sdaX /home/julian users,defaults 0 0
```

una vez que lo montas, como root, tenes que darle permisos y cambiar el owner:

```
chown -R julian:julian /home/julian
```

si asi no te funciona, probamos con otro metodo..

salu2

---

### Post by LianRome on 2008-11-03
¡Muchas gracias Gabriel y Marco!

Acerca del comentario de Gabriel sobre cómo revertir el proceso, pensé que poniendo el liveCD  7.10 que tenía descubriría la ruta. Los pasos descriptos están OK y luego (en inglés) voy a la solapa Advanced y la celda en cuestión es la de Home directory.

Ya que estaba, decidí recorrer el sistema y para mi agradable sorpresa ¡puedo ver mis archivos!

Es por esto que aclaro que todavía no avancé sobre sus aportes, para contarles lo sucedido y ver si esta información contribuía en algo o aclaraba la situación.

Además pude ver las particiones actuales (por favor ver el adjunto). La sda2 es adonde está el sistema instalado y la sda6 es el antiguo Home. ¿Será más fácil reconfigurar algo entrando desde el liveCD?

Gracias otra vez y saludos,

Julián.

---

### Post by gmunioz on 2008-11-04
Hola Julian:
Inicia en modo de recuperación:
Edita tu archivo /etc/fstab
sudo gedit /etc/fstab
Añade esta línea:

[PHP]/dev/sda6 /home           ext3 relatime        0       2[/PHP]

Reinicia, y en teoría tendrías que tener montado tu /home/usuario, siempre y cuando hayas usado el mismo nombre de usuario y la misma contraseña.
Saludos.
Gabriel.
Solo doy soporte para Ubuntu: Un sistema operativo superior, moderno, optimizado, seguro, evolutivo y completo.

---

### Post by LianRome on 2008-11-05
Muchas gracias.
Completé el fstab de la manera que propone Gabriel y el comportamiento es el mismo, habiendo usado el mismo usuario y contraseña.

Cuando estaba en la consola a prueba de fallos, vi esta leyenda: "No directory, logging in with Home=/". Supongo que es más de lo mismo.

Además de los carteles mencionados aparece: "Could not update ICEauthority file /.ICEauthority" (también aparecía antes de hacer este añadido en el fstab).

Y luego uno nuevo: "Hay un problema con la configuración del servidor. (usr/lib/libgconf 2-4/gconf-sanity-check-2 salió con el estado 256)". Busqué en Google, pero no lo encuentro tal cual y las coincidencias parciales de los valores son muy técnicas para mí.

Si pruebo lo que indica Marco, ¿quedaría así, no?


/dev/sda6   /home/julian    users,defaults    0   0


Por favor coméntenme si puedo buscar más datos para que me puedan dar una mano y llegar a la solución.

Muchas gracias y saludos,

Julián.

---

### Post by LianRome on 2008-11-07
Describo la solución aportada por Gabriel (gmunioz):

Iniciar en modo de recuperación. Elegir modo root (como administrador, sin contraseña):
Ejecutar los siguientes comandos:

```
cd /home
ls
```


Si dentro de la salida de ls figura el directorio /julian (nombre de usuario), la partición se ha montado correctamente y puede que existan problemas de permisos.
Lo más practico sería crear un nuevo usuario:

```
adduser usuarionuevo
```


Completar los datos que se vayan pidiendo y habilitarlo para el uso de sudo editando el /etc/sudoers:

```
nano /etc/sudoers
```


Darle permisos de lectura y escritura por todos al directorio del antiguo usuario mediante la orden:

```
sudo chmod -Rf 777 /home/julian
```


Reiniciar con el nuevo usuario y mover de /home/julian a /home/usuarionuevo todos los archivos de datos -no los de configuración.

Una vez que todo esté funcionando correctamente, eliminar el usuario antiguo y sus archivos desde Sistema > Administración > Usuarios y grupos. Nunca borrando directamente el directorio.

Muchas gracias Gabriel (gmunioz) y Marco (mhoyos).

---

