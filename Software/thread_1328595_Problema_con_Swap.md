---
title: "Problema con Swap"
date: 2009-11-16
forum: Software
---

### Post by Air23 on 2009-11-16
Hola!

Tengo un problema con la particion swap, no se si mi ubuntu no la esta montando o si por alguna razon no la usa. Ayer a la noche se corto la luz y hoy al prender la compu note esto.

Dejo algunas salidas de comandos

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=01a927a6-5698-40d4-bc92-0141fe783b6f /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=96f8f268-d9ba-44f9-a5fc-76e479f57552 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=fa5aec17-a46e-4155-a73a-16230679ccee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
```
juan@HAL9000:~$ sudo blkid -c /dev/null
/dev/sda2: UUID="01a927a6-5698-40d4-bc92-0141fe783b6f" TYPE="ext3" 
/dev/sda5: UUID="fa5aec17-a46e-4155-a73a-16230679ccee" TYPE="swap" 
/dev/sda6: UUID="96f8f268-d9ba-44f9-a5fc-76e479f57552" TYPE="ext3" 
```
```
juan@HAL9000:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2012       1283        729          0         41        700
-/+ buffers/cache:        541       1471
Swap:         1906          0       1906

```

Si necesitan que haga algo mas, avisen ;)

¡Gracias!

---

### Post by Mauro22 on 2009-11-16
Gnome??

Con 2gb de RAM, dudo que swapee a menos que hagas algo groso. Ubuntu empieza a usarla uando pasas el 65-70% de la RAM

---

### Post by Air23 on 2009-11-16
> **Mauro22 said:**
> Gnome??

Con 2gb de RAM, dudo que swapee a menos que hagas algo groso. Ubuntu empieza a usarla uando pasas el 65-70% de la RAM

Tenes razon, la exigi mas a la compu y a la larga empezo a swapear.

Debo estar medio  bol***, juraria que hasta ayer empezaba a usar la swap antes.

Gracias y asunto resuelto

---

