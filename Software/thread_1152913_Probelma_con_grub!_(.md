---
title: "Probelma con grub! :("
date: 2009-05-08
forum: Software
---

### Post by okitos on 2009-05-08
Buenas a todos, disculpen si este no es el lugar para el tema, pero he estado horas con esto y no puedo solucionarlo de ninguna manera, se que hay varios "tutos" para resolver esto, pero ninguno me ha resultado, lamentablemente. 

Mi problema es el siguiente, mi grub no me funciona, en un reinicio inesperado de mi máqina el grub dejó de funcionar, mi menu.lst muestra entradas que no son (se modificaó al tratar de repararlo con un tutorial), y mi fstab no se si está correcto.. 
La única manera de poder acceder a Ubuntu 9.04 por cierto, es a través del programita Super Grub Disc, con ese mismo programita intenté reparar el grub, mne dice que está todo "hecho" pero al iniciar dsp, grub me sale con el "error 2" y queda ahí sin más.. 
Estoy a estas alturas medio desesperado.. no he encontrdo ni una esperanza de solución..
En mi maquina tengo un solo disco duro de 80 gb, separad en 3 particiones, windows xp, ubuntu y una swap..

el **fdisk -l** es así

[B]Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        6542    52548583+   7  HPFS/NTFS
/dev/sda2            6543        9729    25599577+   f  W95 Ext'd (LBA)
/dev/sda5   *        6543        9460    23438803+  83  Linux
/dev/sda6            9461        9729     2160711   82  Linux swap / Solaris[/B]

mi **fstab**:

[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=15b91492-8efd-4485-a067-6aec061d39ae /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=46c7b9cb-490a-4d8d-9eec-dc012ab60cc6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0[/B]

y finalmente, mi **menu.lst**:

[B]## ## End Default Options ##

title        Debian GNU/Linux, kernel 2.6.28-11-generic
root        15b91492-8efd-4485-a067-6aec061d39ae
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=15b91492-8efd-4485-a067-6aec061d39ae ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-generic
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
[/B]      
Si me pudieran ayudar estaría eternamente agradecido, desde ya muchas gracias, espero haber dado todos los detalles necearios.

Saludos.

---

### Post by staar on 2009-05-08
en la entrada de debian (supongo que es un ubuntu, y que algún programa lo actualizó mal, podés modificarlo sin drama, simplemente escribí ubuntu donde dice debian :-P ) esta linea ```
root 15b91492-8efd-4485-a067-6aec061d39ae
``` está mal, tiene que ser así ```
uuid 15b91492-8efd-4485-a067-6aec061d39ae
``` cambiando la palabra root, por uuid...

OJO, la modificación es sólo en esa linea, la línea del kernel está bien...

saludos

---

### Post by okitos on 2009-05-08
Muchas gracias por tu respuesta staar hice eso que me decís, y el menu.lst "parece" ser correcto.. pero sigo teniendo problemas :S

Grub ni siquiera se inicia.. dsp q pone "grub 1.5" salta un error "Grub error 2" y más de ahí no sigue.. he intentado varias cosas y no lo logro sacar...
Lo otro que pasa es que, si entro con el Super Grub Disk, en una opción me dice para elegir el menu.lst que prefiero.. si eligo el que tengo (ese q modificamos), me llegan a aparecer las opciones (ubuntu 9.04, Ubnuntu 9.04 (recovery mode), etc) pero al presionar sobre una de ellas, me manda "error 13: Invalid or unsupported executable format"

Otra vez, gracias.

---

### Post by rubioo on 2009-05-08
Fijate si algo de esto te sirve: [Como Recuperar GRUB en 5 minutos]("http://www.versvs.net/anotacion/como-recuperar-grub-en-cinco-minutos")

---

### Post by staar on 2009-05-08
chee, el error 2 de grub significa que el disco seleccionado no existe, para mi que ese grub está mal instalado en el disco, concretamente tiene mal asignado el root, mejor lo reinstalamos manualmente...

1- iniciá con el livecd

2- abrí una terminal y poné ```
sudo grub
```

3- se te abre el intérprete de comandos de grub, poné ```
find /boot/grub/stage1
```

4- te va aparecer el nombre de una partición de la forma (hdX,Y) donde X es el número del disco y Y el número de partición...

5- poné ```
root (hdX,Y)
``` reemplazando la X y la Y por lo que te haya salido en el paso anterior...

6- poné ```
setup (hdX)
``` obviamente reemplazando la X (OJO en este paso NO va la Y, ni la coma)...

7- salí con ```
quit
``` y reiniciá

probá con eso, y contanos...

saludos

---

### Post by okitos on 2009-05-09
Gracias Rubio, voy a intentar por este camino y sino funca vicho eso.

Staar, hice todos los pasos correctamente, todo ok, cuando reinicié, Otra vez, el maldito "Error 2"... :(

La diferencia más notorica esta vez fue que, cuando seleccioné el menu.lst desde el Super Grub Disk, me aparecio, ubuntu 9.04 y el recovery mode, y además entró lo más bien a ubuntu, eso nunca había apsado antes, atribuyo eso al setup eso q me dijistes.. es un avance.. ahora falta sacar el maldito error 2.. >.<

Gracias por todo che.

---

### Post by staar on 2009-05-10
probá con un ```
sudo update-grub
``` desde una consola...

saludos

---

### Post by okitos on 2009-05-10
Hice eso, pero nada... lpm.. :(, el error 2 me empezó a aparecer dsp que traté de "reinstalar" el grub desde el Super Grub Disk ..

Una pregunta dese la ignorancia.. no será que quedó otro grub instalado con root en otra partición y por eso no lo reconoce? porque dentro de la carpeta /boot existe otra carpeta que se llama boot o sea..

/boot/grub

y

/boot/boot/grub

me explico? esa se creo en su momento, y no se saló más.. podría ser algo relacionado con eso?

---

