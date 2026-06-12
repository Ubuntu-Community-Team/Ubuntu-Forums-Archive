---
title: "Me ayudan con esta pregunta en Ubuntu Questions?"
date: 2012-07-22
forum: Software
---

### Post by luispotro on 2012-07-22
[https://answers.launchpad.net/ubuntu/+source/ubuntu-meta/+question/203418]("https://answers.launchpad.net/ubuntu/+source/ubuntu-meta/+question/203418")

Básicamente está relacionada a que mi Ubuntu tarda más de 4 minutos (4:20 en el último booteo, descontando el tipeo de la contraseña en el login).

---

### Post by papibe on 2012-07-22
Hola.

Por casualidad estás montando algún NFS remoto, o usando autofs?

Saludos.

---

### Post by luispotro on 2012-07-22
> **papibe said:**
> Hola.

Por casualidad estás montando algún NFS remoto, o usando autofs?

Saludos.

No a lo primero (NFS remoto). De lo segundo (autofs) no hasta donde mis conocimientos básicos llegan. En la pregunta está toda la info del arranque. Se podrá saber a partir de eso?

Espero no estar diciendo una burrada, pero lo qué sí hice fue hacer que se monte al inicio una partición NTFS, porque siendo una máquina dual boot, tengo mis archivos en ésa. 

Para ayudar un poco con info para resolver el problema, aclaro que esta configuración tiene 1 año ya, aunque con los 2 upgrades de 11.04 a 11.10 y a 12.04, y este problema viene pasando desde hace 1 mes mas o menos.

---

### Post by luispotro on 2012-07-22
Acá está la salida de mount
```
/dev/sda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda7 on /media/Datos type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
gvfs-fuse-daemon on /home/luis/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=luis)
```

acá está /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc         proc  nodev,noexec,nosuid                     0  0  
# / was on /dev/sda5 during installation
UUID=c016a54f-5b56-4f36-adcc-a8cb375febe5  /             ext3  errors=remount-ro                       0  1  
/dev/sda6                                  none          swap  sw                                      0  0  
/dev/sda1                                  /media/sda1   ntfs  nls=iso8859-1,umask=000                 0  0  
/dev/sda7                                  /media/Datos  ntfs  nls=iso8859-1,umask=000,owner,uid=luis  0  0
#192.168.1.15:/home/rodrigo/Música	/mnt/musicas	nfs	defaults	0	0  
```

---

### Post by papibe on 2012-07-22
```
#192.168.1.15:/home/rodrigo/Música	/mnt/musicas	nfs	defaults	0	0
```

Eso podría ser el culpable en caso de que no estuviera comentado (si la máquina 192.168.1.15 no estuviera disponible).

Noté que el syslog hay muchos intentos fallidos en la conexión inalmámbrica. 

Puedes hacer la prueba de iniciar tu máquina conectado con un cable para salir de dudas?

Saludos.

---

### Post by luispotro on 2012-07-22
> **papibe said:**
> ```
#192.168.1.15:/home/rodrigo/Música	/mnt/musicas	nfs	defaults	0	0
```

Eso podría ser el culpable en caso de que no estuviera comentado (si la máquina 192.168.1.15 no estuviera disponible).

Noté que el syslog hay muchos intentos fallidos en la conexión inalmámbrica. 

Puedes hacer la prueba de iniciar tu máquina conectado con un cable para salir de dudas?

Saludos.

El comentado de esa línea está relacionada a un bug cuando hibernaba, ([link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/898615")) problema que sigue sin resolver, y que tal vez esté relacionado con éste problema.

No tengo acceso a un cable de red, pero probé de iniciar con el hardware switch de la antena apagado y booteó en 50 segundos menos (de 4m 20s a 3m30s). Vamos! Que de a poco se va acortando! 
:guitar:

---

