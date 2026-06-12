---
title: "Dejar fija una Unidad"
date: 2010-01-05
forum: Software
---

### Post by efis22 on 2010-01-05
Hola a todos;
es posible dejar fija mi otra partición?, que quiero decir..... que cada ves que quiero entrar a mi otro disco, tengo que poner la contraseña... lo mismo si quiero escuchar musica, ya que todos las canciones esta en esa partición. Lo que quiero simplemente es no volver a poner la contraseña cada ves que abro el otra unidad de disco.

Espero su respuesta, un saludo.

---

### Post by moreback on 2010-01-06
Hola, bienvenido a los foros, como veo que eres nuevo te aviso que tenemos [algunas normas]("http://ubuntuforums.org/showthread.php?t=1162750") para mantener el orden y una de ellas es [publicar en el sub-foro que corresponda]("http://ubuntuforums.org/showthread.php?t=1319475"). Como verás son sólo 4 sub-foros por lo que no creo que tengas problemas.

Ahora respecto de tu consulta, que te pida contraseña para montar unidades se debe a que tu usuario no tiene los permisos suficientes. Para corregirlo tienes que ir a **Sistema -> Administración -> Usuarios y grupos**, pulsar las llaves para desbloquear, seleccionar tu usuario y pulsar **Propiedades**. En la diálogo que se abrirá, te cambias a la pestaña **Privilegios de usuario** y luego en el listado marcas la opción **Montar sistemas de archivos en espacio de usuario (FUSE)**.

Después de esto tienes que cerrar tu sesión y entrar de nuevo para que se apliquen estos privilegios.

Ahora si quieres montar automáticamente tus unidades, podías darte una vuelta por [este post de mi blog]("http://pcarmona.wordpress.com/2009/04/12/montar-discos-de-windows-al-logearse-en-gnome/").

Saludos cordiales.

---

### Post by efis22 on 2010-01-06
Hola Pablo:
Hice tal cual me lo describiste, pero aún así me sigue pidiendo la contraseña al ingresar a la otra partición del disco.
Cerré Sesión e incluso cree un usuario nuevo con todas las acciones activadas, pero no paso nada.

Lo que dice es:** Authentication is required to mount the device.**
[B]"Una aplicación está intentando realizar una acción que necesita permisos especiales."
[/B]
Habrá que hacer algo más??.... o simplemente no se puede dejar montando la otra partición siempre?.

Saludos.

---

### Post by CdK1 on 2010-01-06
Déjalo automáticamente desde /etc/fstab, mas información "man fstab"

---

### Post by moreback on 2010-01-06
A lo mejor no es la opción que dije, pero recuerdo que en diálogo que te pide la contraseña puedes indicarle que te la almacene. Con eso debieras resolver tu problema.

Saludos.

---

### Post by Carlos C on 2010-01-07
Podrías copiar acá tu /etc/fstab. ¿En qué formato está la partición?

---

### Post by efis22 on 2010-01-07
Acá esta lo que sale en mi fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=645ecf80-3043-4b4d-bef9-9133728adf71 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by moreback on 2010-01-07
¿Guardando la contraseña se resuelve el problema?

---

### Post by efis22 on 2010-01-07
Si.... solamente necesito que la contraseña quede guardada y no tenga que estar poniéndola cada vez que entre a esa unidad o que prenda el Pc.

---

### Post by Carlos C on 2010-01-08
Veo que la partición a la que te refieres no está agregada a tu fstab. Una solución sería que lo hicieras. Escribe en el terminal:
```
sudo fdisk -l
```
y copia acá lo que te salga. De esa manera podemos decirte lo que debes añadir en el archivo para que la partición sea montada automáticamente cada vez que inicias el equipo.

Saludos.

---

### Post by efis22 on 2010-01-08
Hola Carlos, esto sale:

Disco /dev/sda: 82.3 GB, 82348277760 bytes
255 cabezas, 63 sectores/pista, 10011 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x8db18db1

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        7013    56331891   83  Linux
/dev/sda2            7014       10011    24081435    f  W95 Ext'd (LBA)
/dev/sda5            7014       10011    24081403+   7  HPFS/NTFS

---

### Post by efis22 on 2010-01-10
Ya lo solucione.... dejo aqui la explicación, por si alguien tiene el mismo problema.

- Abrir el Terminal y escribir: **sudo gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy**

 - Una ves dentro del archivo, buscar la parte donde dice **auth_admin_keep** y la cambiamos por **yes**

 - Guardan el archivo, reinician el computador.... y listo.

Saludos a todos.

---

### Post by moreback on 2010-01-10
> **efis22 said:**
> 
 - Una ves dentro del archivo, buscar la parte donde dice **auth_admin_keep** y la cambiamos por **yes**


Hay varias secciones dentro de ese archivo donde aparece **auth_admin_keep**, ¿en cual sección modificaste? tengo la impresión que debiera ser donde marca la acción **<action id="org.freedesktop.devicekit.disks.filesystem-mount">**

Saludos.

---

### Post by efis22 on 2010-01-10
> **moreback said:**
> Hay varias secciones dentro de ese archivo donde aparece **auth_admin_keep**, ¿en cual sección modificaste? tengo la impresión que debiera ser donde marca la acción **<action id="org.freedesktop.devicekit.disks.filesystem-mount">**

Saludos.

Correcto... en esa sección.

---

### Post by _ZeTa on 2010-01-18
no funciona la solución men...

modifique y no resultó...
tal vez si lo explicas con manzanitas... :P
ya que puede ser error 600 jejeje

saludos!

---

