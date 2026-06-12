---
title: "Error no tan grave al inicio"
date: 2009-06-18
forum: Software
---

### Post by picknick on 2009-06-18
Hace unos días instalé Xubuntu 9.04. Actualicé los paquetes de idiomas que me interesaban (inglés y español-castellano). Y ayer logré usar samba para comunicar Xubuntu como server con una Xp via red local (tengo una carpeta compartida).

Esos son los cambios que podrían estar relacionados con el error. Luego del inicio y antes de que aparezca el desktop salta un error:

> Se está ignorando el archivo $HOME/.dmrc del usuario. Esto impide que se guarden la sesión predeterminada y el idioma. El archivo debería pertenecer al usuario y tener los permisos 644. El directorio personal del usuario debe pertenecer al usuario y no ser escribible para otros.

La carpeta compartida está en /home/mariano/publico (/home/mariano es mi carpeta personal) y tudo que usar $sudo chmod 0777 /home/mariano/publico para poder escribir desde windows.

Comenté lo que me pareció que podía llegar a influir.

mariano

---

### Post by clasificado on 2009-06-18
eso suele pasar cuando se hace alguna operación con sudo que se debió haber ejecutado sin sudo.

al cambiarle el owner cambia la perspectiva de los permisos y ya nadie entiende nada.

¿puede ser?

clasificado

---

### Post by Mauro22 on 2009-06-18
> sudo chown mariano:mariano $HOME/.dmrc
chmod 644 $HOME/.dmrc

Con eso deberia bastar.

---

### Post by picknick on 2009-06-21
No funcionó. Pero me acabo de dar cuenta que el archivo .dmrc no está en la carpeta /home (ni siquiera oculto).
Está en /home/mariano.

Mariano

Edit: esto es lo que me salta y porqué busqué la carpeta dónde se aloja el archivo:
> 
input: sudo chown mariano:mariano $home/.dmrc
output: chown: no se puede acceder a «/.dmrc»: No existe el fichero ó directorio


---

### Post by WanderingKnight on 2009-06-21
```
sudo chmod 644 ~/.dmrc
```

Saludos.

---

### Post by picknick on 2009-06-21
No funciona tampoco. 
Que bronca!

---

### Post by staar on 2009-06-22
posteá la salida de correr ```
ls -la
``` para que sepamos como están los permisos en tu home...

saludos

---

### Post by picknick on 2009-06-22
Dale.
> total 92
drwxr-xr-x  21 root root  4096 2009-06-14 19:47 .
drwxr-xr-x  21 root root  4096 2009-06-14 19:47 ..
drwxr-xr-x   2 root root  4096 2009-06-14 19:48 bin
drwxr-xr-x   4 root root  4096 2009-06-14 19:47 boot
lrwxrwxrwx   1 root root    11 2009-06-14 19:34 [COLOR=DeepSkyBlue]cdrom[/COLOR] -> media/cdrom
drwxr-xr-x  15 root root  4040 2009-06-22 01:57 dev
drwxr-xr-x 130 root root 12288 2009-06-22 01:58 etc
drwxr-xr-x   7 root root  4096 2009-06-15 13:30 home
lrwxrwxrwx   1 root root    33 2009-06-14 19:47 [COLOR=DeepSkyBlue]initrd.img[/COLOR] -> boot/initrd.img-2.6.28-11-generic
drwxr-xr-x  19 root root  4096 2009-06-14 19:48 lib
drwx------   2 root root 16384 2009-06-14 19:33 lost+found
drwxr-xr-x   5 root root  4096 2009-04-20 11:51 media
drwxr-xr-x   2 root root  4096 2009-04-13 06:33 mnt
drwxr-xr-x   2 root root  4096 2009-04-20 11:51 opt
dr-xr-xr-x 131 root root     0 2009-06-22 01:57 proc
drwx------  10 root root  4096 2009-06-18 02:41 root
drwxr-xr-x   2 root root  4096 2009-06-17 22:29 sbin
drwxr-xr-x   2 root root  4096 2009-03-06 14:21 selinux
drwxr-xr-x   2 root root  4096 2009-04-20 11:51 srv
drwxr-xr-x  12 root root     0 2009-06-22 01:57 sys
drwxrwxrwt   6 root root  4096 2009-06-22 02:05 [COLOR=Teal]tmp[/COLOR]
drwxr-xr-x  13 root root  4096 2009-06-17 00:57 usr
drwxr-xr-x  16 root root  4096 2009-06-15 13:30 var
lrwxrwxrwx   1 root root    30 2009-06-14 19:47 [COLOR=DeepSkyBlue]vmlinuz[/COLOR] -> boot/vmlinuz-2.6.28-11-generic


Las carpetas que pinté estaban de ese color y el resto de azul. Por lo que vi en el help de *ls* no dice nada el color pero por las dudas lo copié.

Mariano

---

### Post by staar on 2009-06-22
pero esa es la salida de /, yo quería la de /home/mariano, así ```
ls -la /home/mariano
``` perdoná si no fui explicito, supuse que estarías ubicado en tu home y no en /

saludos

---

### Post by picknick on 2009-06-22
No, está bien. Ya entendí como funciona el comando ;).

Ahora sí:* ls -la /home/mariano*

> total 844
drwxrwxrwx 31 mariano mariano   4096 2009-06-22 02:49 .
drwxr-xr-x  7 root    root      4096 2009-06-15 13:30 ..
drwx------  2 mariano mariano   4096 2009-06-22 00:42 .AbiSuite
-rw-------  1 mariano mariano   3619 2009-06-22 02:15 .bash_history
-rw-r--r--  1 mariano mariano    220 2009-06-14 19:44 .bash_logout
-rw-r--r--  1 mariano mariano   3115 2009-06-14 19:44 .bashrc
drwxr-xr-x  6 mariano mariano   4096 2009-06-18 00:56 .cache
drwxr-xr-x 12 mariano mariano   4096 2009-06-22 02:04 .config
drwx------  3 mariano mariano   4096 2009-06-14 17:06 .dbus
-rw-r--r--  1 mariano mariano     25 2009-06-17 19:33 .dmrc
-rw-r--r--  1 mariano mariano    834 2009-06-20 20:26 Documento 1 no guardado
drwxr-xr-x 11 mariano mariano   4096 2009-06-22 00:29 Documentos
drwxr-xr-x  2 mariano mariano   4096 2009-06-22 02:31 Escritorio
-rw-------  1 mariano mariano     16 2009-06-14 17:07 .esd_auth
-rw-r--r--  1 mariano mariano 558592 2009-06-21 17:19 fleets TROL(1).doc
drwxr-xr-x  2 mariano mariano   4096 2009-06-22 02:47 .fontconfig
drwx------  3 mariano mariano   4096 2009-06-22 02:49 .gconf
drwx------  2 mariano mariano   4096 2009-06-22 02:58 .gconfd
drwx------  2 mariano mariano   4096 2009-06-17 20:40 .ggz
-rw-r-----  1 mariano mariano      0 2009-06-22 02:39 .gksu.lock
drwx------  7 mariano mariano   4096 2009-06-18 00:58 .gnome2
drwx------  2 mariano mariano   4096 2009-06-14 17:06 .gnome2_private
drwxr-xr-x  2 mariano mariano   4096 2009-06-21 16:52 .gstreamer-0.10
-rw-------  1 mariano mariano    225 2009-06-18 20:37 .gtk-bookmarks
drwx------  2 mariano mariano   4096 2009-06-14 17:06 .gvfs
-rw-------  1 mariano mariano    875 2009-06-22 02:49 .ICEauthority
drwxr-xr-x  2 mariano mariano   4096 2009-06-18 13:46 Imágenes
drwxr-xr-x  3 mariano mariano   4096 2009-06-22 02:46 .java
drwxr-xr-x  4 mariano mariano   4096 2009-06-18 20:43 .listen
drwxr-xr-x  3 mariano mariano   4096 2009-06-14 17:06 .local
drwxr-xr-x  2 mariano mariano   4096 2009-06-16 21:43 .lyrics
drwx------  5 mariano mariano   4096 2009-06-22 01:51 .mozilla
drwxr-xr-x  2 mariano mariano   4096 2009-06-14 17:06 Música
-rw-r--r--  1 mariano mariano   1056 2009-06-17 01:27 .nvidia-settings-rc
-rw-r--r--  1 mariano mariano  97979 2009-06-20 20:16 pantalla launch.png
drwxr-xr-x  2 mariano mariano   4096 2009-06-14 17:06 Plantillas
-rw-r--r--  1 mariano mariano    675 2009-06-14 19:44 .profile
drwxr-xr-x 11 mariano mariano   4096 2009-06-22 00:25 Público
drwx------  5 mariano mariano   4096 2009-06-22 01:21 .purple
-rw-------  1 mariano mariano  10924 2009-06-22 02:47 .recently-used.xbel
-rw-r--r--  1 mariano mariano      0 2009-06-14 17:14 .sudo_as_admin_successful
drwxr-xr-x  4 mariano mariano   4096 2009-06-18 02:40 .thumbnails
drwxr-xr-x  2 mariano mariano   4096 2009-06-15 02:14 .update-manager-core
drwx------  2 mariano mariano   4096 2009-06-14 17:09 .update-notifier
drwxr-xr-x  2 mariano mariano   4096 2009-06-22 02:31 Vídeos
-rw-------  1 mariano mariano    125 2009-06-17 19:33 .Xauthority
drwx------  3 mariano mariano   4096 2009-06-16 21:09 .xchat2
-rw-r--r--  1 mariano mariano     88 2009-06-17 00:03 .xscreensaver-getimage.cache
-rw-r--r--  1 mariano mariano   4163 2009-06-22 02:58 .xsession-errors
Y además, me di cuenta el porqué de los colores.

Y como el error me tira "$home/.dmrc" también *ls -la /home*:

> total 40
drwxr-xr-x  7 root    root     4096 2009-06-15 13:30 .
drwxr-xr-x 21 root    root     4096 2009-06-14 19:47 ..
drwx------  2 root    root    16384 2009-06-14 19:34 lost+found
drwxrwxrwx 31 mariano mariano  4096 2009-06-22 02:49 mariano
drwxr-xr-x  2 root    root     4096 2009-06-15 13:30 netlogon
drwxrwxrwx  2 root    nobody   4096 2009-06-15 13:30 pdf-documents
drwxrwxrwx  2 root    root     4096 2009-06-18 01:18 publico
Mariano

---

### Post by staar on 2009-06-22
primero que nada te aclaro una cosa que te estás confundiendo, $HOME (es con mayúsculas) es una variable que indica tu directorio personal, en tu caso /home/mariano, no indica la carpeta /home

otra cosa, pero creo que viene por lo mismo, en tu /home veo la carpeta publico (que supongo es la compartida) y en tu /home/mariano está la carpeta Público (con mayúscula y acento, en sistemas Unix las mayúsculas y minúsculas se distiguen) creada automáticamente por el sistema para lo que necesitas, no es obligatorio, pero te recomendaría que corrijas eso...

los permisos de .dmrc están bien, lo que está mal son los permisos de tu home hace un ```
chmod 700 /home/mariano
```

saludos

---

### Post by picknick on 2009-06-22
Muchas gracias staar por las aclaraciones!!!!
Funcionó a la perfección el cambio de permiso. Además, puse a compartir publico y no Público.
Le eché un vistazo a esta página para entender un poco más sobre el comando *chmod*. 
[http://ubunturoot.wordpress.com/2007/12/07/permisos-en-linux-con-chmod/](http://ubunturoot.wordpress.com/2007/12/07/permisos-en-linux-con-chmod/)
Realmente este es un mundo nuevo y muy versátil. Estoy fascinado!

Agradezco a todos por su tiempo y dedicación.
Hasta la próxima!

Mariano

---

### Post by staar on 2009-06-23
para ilustarte sobre el uso de un comando en gnu/linux, lo más fácil y recomendado es que corras ```
man *nombredelcomando*
``` que te permite revisar la página del manual de dicho programa (OJO, requerido conocimiento, o al menos entendimiento, del idioma del Imperio)

saludos

---

