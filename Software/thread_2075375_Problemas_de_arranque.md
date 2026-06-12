---
title: "Problemas de arranque"
date: 2012-10-23
forum: Software
---

### Post by DiegoDB on 2012-10-23
Hola a todos.. tuve un grave problema, primero.. hace un par de meses desapareció del grub windows.. era una pavada ponerlo.. pero esta estudiando y no lo hice.
  y bueh hace un mes mas o menos tardaba en iniciar.. pero ponele.. 3 o 4 minutos. cuando inicia aparece un dialogo de comando que no se que es.. y aparecen errores pero ni se que es.. es como una consola.. y salgo de ahi escribiendo exit. Esta es la imagen: 
[IMG]https://mail-attachment.googleusercontent.com/attachment/?ui=2&ik=fe66a72a73&view=att&th=1395f1febed67b89&attid=0.1&disp=inline&realattid=f_h6b2f3va0&safe=1&zw&saduie=AG9B_P-aDTDxt_FBGi5D0OdGdlot&sadet=1349119631648&sads=jeoOcE5z6ux8IpHwt858DbWQOZ0[/IMG]

Entre aca [http://www.ubuntu-es.org/node/52872#.UDkgRKNXk3w](http://www.ubuntu-es.org/node/52872#.UDkgRKNXk3w) y probé por que un vago me dijo capaz el problema era un error del disco.
Nada..

Abri un terminal y  escribi sudo fdisk -l :
Disco /dev/sda: 40.0 GB, 40060403712 bytes
255 cabezas, 63 sectores/pista, 4870 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x0000a1cc

Disposit. Inicio Comienzo Fin Bloques Id Sistema
/dev/sda1 * 1 1216 9764864 83 Linux
/dev/sda2 1216 4871 29353985 5 Extendida
/dev/sda5 1216 4742 28319744 83 Linux
/dev/sda6 4742 4871 1033216 82 Linux swap / Solaris

Disco /dev/sdb: 82.3 GB, 82348277760 bytes
255 cabezas, 63 sectores/pista, 10011 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x0009fb2e

Disposit. Inicio Comienzo Fin Bloques Id Sistema
/dev/sdb1 * 2 4912 39447577 f W95 Ext'd (LBA)
/dev/sdb2 4913 8611 29712217+ 83 Linux
/dev/sdb3 8612 9886 10241437+ 83 Linux
/dev/sdb4 9887 10011 1004062+ 82 Linux swap / Solaris
/dev/sdb5 2 4912 39447576 7 HPFS/NTFS

Disco /dev/sdc: 8006 MB, 8006926336 bytes
39 cabezas, 39 sectores/pista, 10281 cilindros
Unidades = cilindros de 1521 * 512 = 778752 bytes
Identificador de disco: 0xc3072e18

Disposit. Inicio Comienzo Fin Bloques Id Sistema
/dev/sdc1 * 6 10282 7815232 c W95 FAT32 (LBA)


Desdpues me dijeron que haga este tuto.. [http://www.taringa.net/posts/linux/12296990/Test-Disk_-y-recupera-tus-particiones-borradas-o-rotas.html](http://www.taringa.net/posts/linux/12296990/Test-Disk_-y-recupera-tus-particiones-borradas-o-rotas.html)

 pero no dio resultado no aparecian las particiones. 

Hasta ahi quede. 

Cabe destacar que soy muy nuevo en esto de ubuntu y prácticamente soy un ignorante con respecto a ustedes que de seguro saben. Espero que me ayuden. Gracias. Cualquier consejo sirve.

Tenia el ubuntu 12.04 el windows y otro ubuntu 10.04 si no me equivoco (Que es el actual ya que los otros dos no aparecen en el grub.)

---

