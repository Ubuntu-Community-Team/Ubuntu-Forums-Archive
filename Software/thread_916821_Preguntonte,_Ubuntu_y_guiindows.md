---
title: "Preguntonte, Ubuntu y guiindows"
date: 2008-09-11
forum: Software
---

### Post by vampichoke on 2008-09-11
ya se q es mala palabra y hoy mas q nunca, es q estaba haciendo unos laburos en corel y de paso pase un tp para la facu lo guarde en el escritorio y dije mañana me levanto y los imprimo (me dormi re caliente por el partido con peru.) me levanto y q raro no. EquisPe no arrancaba se clavaba en la pantalla q carga la barrita.

bueno arranco ubuntu y no me deja montar las particiones (por lo menos para imprimir esos archivos e ir a cursar. corro el live cd para ver las particiones y si. error fatal en disco C.


mi preguntonta noobzord es. 

disco de 160 dividido en 3 en el siguiente orden:
Win(30gb)Dañado quien sabe por q
Ubuntu(30gb)Dios como te quiero
Datos(100Gb)esta part no me salta error pero no me la lee ubuntu.

reinstalare guind en donde iba, y espero q me lea archivos del disco datos.

**el grub no se modifica y no pasa naranja no? (yo por miedo q xp sea tan joputa de querer tocarme ubuntu.. (miedo de principiante)**

---

### Post by Afkael on 2008-09-11
Desde linux.. no se... si tenés datos importantes, no conozco software para rescatarlo.. sino.. Gpart, si te lo reconoce (a mi no me funcionó, no se porqué) y formateas la partición.
Después.. si, si reintalás windows te va a reescribir la MBR y va a bootear el (egoista). Supongo que hay forma de revertirlo... quizá con gpart también.. pero no se.
No dejés de probar Inskape para vectores que es muy bueno.. quizá puedas desligarte de windows. Saludos

PD: te están sobrando 60GB, o te has equibocado o los tienes sin uso

---

### Post by faktorqm on 2008-09-11
para montarlo lo que podes hacer es mirar tu /etc/fstab con

```
cat /etc/fstab
```

y te aparece algo como esto:

```
faktorqm@the-edge:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5430a0a1-0ca4-4304-b2b5-d682a2ff0f43 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=A44CCF4A4CCF1648 /media/appz     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=98D8CB3CD8CB1780 /media/datos    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=12ECC503ECC4E259 /media/windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=77d32be4-949e-4eb7-9ee6-ace2419cf5f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
faktorqm@the-edge:~$ 

```

entonces en mi caso seria:

```
sudo ntfs-3g /dev/sdb2 /media/datos -o force
```

la opcion -o force te limpia el journalling de ntfs y te lo monta igual. si la particion esta dañada, o no existe, o no encuentra que sistema de archivos es no te lo monta y ahi te recomendaria que pruebes con el hiren's algun recuperador de datos para discos asi no perdes los archivos.
el comando ntfs-3g es el equivalente (por decirlo de alguna manera) a hacer sudo mount -t ntfs blablabla. Salu2!!

---

### Post by vampichoke on 2008-09-11
mariano@mariano-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=a0e6c75e-133d-4e77-b0b2-de34274dbf0b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=a70acff0-68a8-4dec-9a93-2fa930a764f4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


[B]al horno nomas me reconoce los de ubuntu. 

en si me chupa el disco C. por eso siempre guardo en Datos.por suerte no esta dañado pero me parecio raro q no me lo montara ubuntu. 

nomas queria saber q si meto cd de windows, instalar. en c formatee haga todo . 
despues reinicie la pc y el grub me cargue normal nada mas ^^)

muchas gracias =D[/B]

---

### Post by pol666 on 2008-09-11
eh si, pero se te va a romper el grub y vas a  poder acceder a Windows nomas, eso lo reparas despues

---

### Post by faktorqm on 2008-09-11
no, cuchame, en fstab solo se guardan las particiones que queres montar cuando arrancas ubuntu. si queres ver todas las particiones, pone "sudo fdisk -l" y de ahi las montas. Vos seguro lo que estas haciendo es q las estas montando con el nautilus y no te das cuenta, por que si no la monta al inicio y vos guardas datos igual tonces es por que la montaste. a menos que te hayas referido a que eso lo haces desde el windows.

---

### Post by Thalskarth on 2008-09-11
> **Afkael said:**
> Después.. si, si reintalás windows te va a reescribir la MBR y va a bootear el (egoista). Supongo que hay forma de revertirlo... quizá con gpart también.. pero no se.

Si, pero eso se soluciona muy facilmente,
una vez instalado windows y que este alla pisado el MBR, quitandote GRUB,.

bootea desde el livecd de ubuntu. Abris una consola y pones estos comandos:

```
sudo grub    --> ejecutamos el intérprete de comandos del GRUB
root (hdX,Y) --> indicamos dónde está ubicada la partición de Ubuntu
setup (hdX)  --> instalamos el GRUB en ese disco
quit         --> salimos del intérprete de comandos del GRUB
```

X representa el numero de disco rígido
Y es el número de partición. ej: hd0,0: es la primera partición del primer disco duro

Para saber bien que numero tiene la particion de Ubuntu, podes abrir el gparted que ahi te lo dice.


PD: la info la extraje de la Guia Ubuntu: [http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

---

### Post by vampichoke on 2008-09-11
mariano@mariano-desktop:~$ sudo fdisk -l
[sudo] password for mariano: 

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x8cd48cd4

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       19457   125572072+   f  W95 Ext'd (LBA)
/dev/sda5            7650       19457    94847728+   7  HPFS/NTFS
/dev/sda6            3825        7486    29414952   83  Linux
/dev/sda7            7487        7649     1309266   82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco
mariano@mariano-desktop:~$ 
[B]
ahora ta eso tons tengo q poner en las opciones del grub la 6 no?


muchas gracias =)[/B]

---

### Post by faktorqm on 2008-09-12
Bueno te quedaria algo asi. No entiendo por que tenes 15000 particiones. ¿Hacen falta? estoy seguro que no. 
Si en /media no tenes los directorios creados (les podes poner el nombre que mas te guste) vas a una terminal y escribis:

```
cd /media
```
```
mkdir nombre
```
donde nombre obviamente es el el nombre de la carpeta q vas a crear.

Tu fstab deberia que darte algo parecido a esto:

```
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=a0e6c75e-133d-4e77-b0b2-de34274dbf0b / ext3 relatime,errors=remount-ro 0 1
# /dev/sda7
UUID=a70acff0-68a8-4dec-9a93-2fa930a764f4 none swap sw 0 0

[COLOR="Red"]/dev/sda1 /media/windows ntfs defaults,umask=007,gid=46 0 1
/dev/sda2 /media/datos vfat defaults 0 1
/dev/sda5 /media/otra_de_windows ntfs defaults,umask=007,gid=46 0 1[/COLOR]

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

y te comento algo, la linea del sda1 esta bien. pero la de la particion sda2 no me acordaba las opciones para vfat asi que lo unico que tiene son las defaults... capaz va otra cosa. hace tanto que no uso fat que ni idea. (si, si, en el pendrive si, no jodan... ¬¬) y la sda5 tambien esta ok, probalo y fijate que onda. Salu2!

---

### Post by vampichoke on 2008-09-12
no re entendi ni medio.  
yo no hice mil particiones y nose son las q saltaron solas. O.º) !!
nomas tenia xp y datos. despeus instale ubuntu desde ese entonces nose =P
lo de montarlas ya fue. pude solucionar el problema mas urgente( q eran 3 archivos de corel y 2 de word). Muchas gracias =) 

hoy instalo again win. y veo lo del grub y los vuelvo a molestar.


P.D q no tiene nada q ver, pol666 en taringa posteo los nombres de los proximos ubuntu , un idolo =P

---

### Post by c4d0rn4 on 2008-09-13
modo a prueba de fallos con f8 no sale? (win)

un programa no muy común que te arregla casi seguro todo eso es el winternals erd commander.

htp://www.katzforums.com/showthread.php?t=59489

me morfé una t adrede

---

### Post by vampichoke on 2008-09-13
no si entre en todos los modos a prueba de fallos posibles.llega al logo de las ventanitas con la barrita abajo. la cual sigue andando lo mas pancha por su casa. lo deje 45 min. 

la posta ultimamente me saltaba un error de windows y run cuando ponia apagar equipo desde win. le ponia finalizar ahora. puesto q no crei q no me iba a dejar arrancar win luego =/

**es un booteable eso no ... ahi estoy leyendo q copado mil gracias**

---

