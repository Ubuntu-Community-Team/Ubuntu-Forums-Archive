---
title: "[SOLUCIONADO] Problemas con Wallpaper en Ubuntu 9.4"
date: 2009-06-02
forum: Software
---

### Post by dcorrea on 2009-06-02
Hola a todos!!!
Hace poco que instale Ubuntu 9.4...antes tenia Mandriva...
y he tenido algunos problemas...
1.- Cada vez que cambio el wallpaper y luego reinicio el equipo...mi wallpaper se pierde y me queda un fondo anaranjado.
2.- Activo los efectos de escritorio y funcionan bien, tengo una ATI 200M, pero luego inicio otra vez el equipo y ya no los puedo activar nuevamente por problemas con un controlador...
Todo lo demas no he tenido problemas.

Saludos!!

---

### Post by Carlos C on 2009-06-02
Hola, como el título del thread se refiere al wallpaper ese debiera ser el tema a tratar en esta conversación. Respecto al problema de tu tarjeta (yo tengo la misma), por favor abre otro thread en donde especifiques tu modelo, versión de ubuntu y drivers usados (privativos o libres). La idea es que si otra persona tiene tu mismo problema pueda dar fácilmente con tu post y así las preguntas no se repitan.

Volviendo al tema del wallpaper, ¿el archivo está ubicado en la misma partición que tu /home o se ubica en otra?

Saludos.

---

### Post by dcorrea on 2009-06-02
ok, gracias por la sugerencia...
llevaremos esto en orden entonces...
No, la imagen que puse de wallpaper esta en un disco NTFS, ya que mi PC tiene instalado ubuntu y windows xp

---

### Post by magicdrums on 2009-06-02
hola eso puede ocurrir porque tu particion NTFS no se encuentra en el FSTAB definido para que se monte automaticamente...

(la explicacion se parece a un comercial de cristal...)

---

### Post by radixs on 2009-06-02
> **dcorrea said:**
> ok, gracias por la sugerencia...
llevaremos esto en orden entonces...
No, la imagen que puse de wallpaper esta en un disco NTFS, ya que mi PC tiene instalado ubuntu y windows xp

 	 	 Ese es el problema al tener el wallpaper en la partición NTFS, al momento de reiniciar para que te vuelva a tomar el wallpaper tienes que montar la partición, de esa forma el wallpaper aparecerá. Otra opción es monatar la partición automáticamente al momento de iniciar la sesión o también puedes guardar el wallpaper en el directorio /home.

---

### Post by magicdrums on 2009-06-02
> **radixs said:**
> Ese es el problema al tener el wallpaper en la partición NTFS, al momento de reiniciar para que te vuelva a tomar el wallpaper tienes que montar la partición, de esa forma el wallpaper aparecerá. Otra opción es monatar la partición automáticamente al momento de iniciar la sesión o también puedes guardar el wallpaper en el directorio /home.


Si pudieras enviarnos tu FSTAB este se encuentra en /etc/fstab, te ayudamos a modificarlo

---

### Post by dcorrea on 2009-06-02
gracias por las respuestas....
por lo tanto ya movi la imagen a mi /home
En todo caso aqui esta lo solicitado;

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=7d614bf7-5bd8-46f2-ad66-e870e5b38049 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=e9da930b-f79d-4169-b6e3-b08021bffe77 /home           ext3    relatime        0       2
# swap was on /dev/sda7 during installation
UUID=1b646cae-53dd-4612-add8-84adef0640b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Patriciologico on 2009-06-02
Lo mejor es que copies el wallpaper y lo dejes en una carpeta que ubuntu monte automaticamente, como tu carpeta de usuario.

Saludos!

---

### Post by Carlos C on 2009-06-03
Al mover el archivo a tu home ya debieras haber resuelto el problema. En caso de que quieras montar tu partición ntfs automáticamente al iniciar puedes mirar acá:

[http://blockdeubuntu.blogspot.com/2008/07/cmo-montar-particiones-de-windows-o.html](http://blockdeubuntu.blogspot.com/2008/07/cmo-montar-particiones-de-windows-o.html)

---

### Post by dcorrea on 2009-06-03
Hola a todos...
Despues que colocar la imagen en mi /home no he tenido problemas!!
Gracias por sus respuestas.

SOLUCIONADO!!!

---

