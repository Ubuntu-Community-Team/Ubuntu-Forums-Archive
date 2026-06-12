---
title: "Copiar o mover un archivo a cualquier directorio con un script"
date: 2010-02-01
forum: Software
---

### Post by hatteras22 on 2010-02-01
Para copiar o mover un archivo, de forma gráfica,  desde /home/usuario a un directorio del sistema ( directorio / y sus subdirectorios ) hay que hacerlo ejecutando un Nautilus con permisos de root, con la orden: gksu nautilus. Esto es así porque los directorios del sistema no tienen permisos de escritura para un usuario que no sea el root.

Los pendrives y/o discos duros externos o particiones adicionales creadas en formato fat32 o ntfs, o incluso en ext3 o ext4 para almacenar datos si que suelen tener permisos de escritura para el usuario normal, pero si solo  tuvieran permisos de escritura para el usuario root, podríamos copiar o mover a ellos archivos desde /home/usuario con los scripts de este tema: [http://hatteras.wordpress.com/2010/02/02/copiar-o-mover-un-archivo-a-cualquier-directorio-con-un-script/](http://hatteras.wordpress.com/2010/02/02/copiar-o-mover-un-archivo-a-cualquier-directorio-con-un-script/)

---

