---
title: "¿Como no partir en modo consola? Jaunty"
date: 2009-05-27
forum: Software
---

### Post by Naldylipu on 2009-05-27
[FONT=Verdana][SIZE=2]Hola
al iniciar el computador, me sale el grub, escojo el Ubuntu y ahí comienza una pantalla con letras blancas (modo de consola) ahí me tira un par de errores, muchos números, se queda parado, me dijeron que tenia que poner exit, luego de eso dice cargando archivos para boot, acto segudo más letras blancas ydespués entra al ubuntu, hay alguna manera de que no parta así, lei que parte con una pantalla llamada usplash, pero no he encontrado forma de cambiarlo.

es un vaio vng.nr350f[/SIZE][/FONT][FONT=Verdana][SIZE=2]e
[/SIZE][/FONT][FONT=Verdana][SIZE=2]procesador Intel Core 2 Duo T5550 (1.83 GHz1)
[/SIZE][/FONT][FONT=Verdana][SIZE=2]Mobile Intel GM965 Express Chipset[/SIZE][/FONT][FONT=Verdana][SIZE=2]
Intel PRO wireless 3945AGM network connectio[/SIZE][/FONT][FONT=Verdana][SIZE=2]n
Tarjeta de Video: Mobile Intel Graphics Media Accelerator X3100
Memoria3 Gb DDR SDRam[/SIZE][/FONT]

---

### Post by Carlos C on 2009-05-27
> **Naldylipu said:**
> Hola
al iniciar el computador, me sale el grub, escojo el Ubuntu

:confused:  Hola. Para que podamos ayudarte debes dar más información, ya que con lo que sabemos en este punto no es posible darte una respuesta informada y podemos generarte más problemas. Vamos por partes:

1. En primer lugar si dices que al principio tienes el menú del grub, entonces tienes más de un sistema instalado, ¿no es así? ¿Qué sistema sería ese? Este tipo de datos siempre debes darlo.

2. ¿Qué versión de Ubuntu tienes instalada? Este dato SIEMPRE debes darlo. (te recomiendo mirar mi firma y darte una vuelta por lo que debes y no debes hacer en el foro ;)

3. No se trata de que simplemente cambies el "modo consola" como le llamas, sino que debes ver en qué consisten los errores que se te reportan al principio. Un buen consejo es que no esperes diagnosticar tu sistema y pedir una solución que tú crees es la adecuada, sino más bien, presentar la situación y ver si alguien te puede sugerir el mejor camino para resolverla ;)

Te recomiendo que escribas en el terminal:
```
dmesg
```Eso te mostrará los mensajes del sistema. Ve si encuentras algún error. Si no descubres nada lo más fácil es que veas los mensajes que se generan al iniciar Ubuntu. Una buena opción es habilitar la opción de que el sistema genere un archivo en donde guarde todos esos mensajes (un log). Lo puedes hacer editando el archivo bootlogd. Para ello escribe en el terminal:
```
sudo gedit /etc/default/bootlogd
```Luego editas ese archivo para que quede de esta forma:
```
# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes
```Guardas los cambios y reinicias. Con ello se habrá generado un archivo que puedes ver escribiendo en el terminal:
```
gedit /var/log/boot
```Veamos si puedes encontrar algun error que nos de una pista.
Saludos.

---

### Post by Naldylipu on 2009-05-29
Pensé que se entendía que es el 9.04 por eso puse en el titulo "jaunty", además pense que no era necesario ponerlo ya que está en la cajita con la información de usuario al ado del texto del post, no volveré a hacerlo. Asi que perdón si no me expresé bien, o entendí algo de otra manera
Lo del modo consola, o haberlo llamado asi sin serlo realmente, asi fue como siempre supe que se llamaban las letras blancas en el fondo negro, muy parecido al DOS, donde puedes ingresar algunos comandos.

La verdad es que me salen bastantes errores: 
[81.145628] ata1.00: status { DRDY ERR}
[81.145684] ata1.00: error {UNC}

dp cambia el numero a 
[89.78237]ata1.00: status { DRDY ERR}
[89.788293] ata1.00: error {UNC}

a
[106.716562]ata1.00: status { DRDY ERR}
 [106.716618] ata1.00: error {UNC}

a
[115-116315]ata1.00: status { DRDY ERR}
  [115.116371] ata1.00: error {UNC}

[  123.601746]          res 41/40:80:07:01:00/00:01:00:00:00/40 Emask 0x409 (media error) <F>
[  123.601887] ata1.00: status: { DRDY ERR }
[  123.601943] ata1.00: error: { UNC }
[  123.604913] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  123.604968] end_request: I/O error, dev sda, sector 263
[  123.605036] __ratelimit: 18 callbacks suppressed
[  123.605041] Buffer I/O error on device sda, logical block 32
[  123.605102] Buffer I/O error on device sda, logical block 33
[  123.605167] Buffer I/O error on device sda, logical block 34
[  123.605225] Buffer I/O error on device sda, logical block 35
[  123.605284] Buffer I/O error on device sda, logical block 36
[  123.605343] Buffer I/O error on device sda, logical block 37
[  123.605402] Buffer I/O error on device sda, logical block 38
[  123.605461] Buffer I/O error on device sda, logical block 39
[  123.605518] Buffer I/O error on device sda, logical block 40
[  123.605578] Buffer I/O error on device sda, logical block 41

--> no se si tiene algo que ver, pero la unidad optica está mala

Espero con eso puedan ayudarme... o decirme que más necesito buscar para que parta como corresponde

---

### Post by Carlos C on 2009-05-29
Hola. Si pues, tienes razón, fui yo el que no se fijó bien en el título, efectivamente dice jaunty, así que creo que para la próxima debo recordar leer con más atención.

Reitero mi pregunta anterior ¿tienes otro sistema instalado en el computador además de Ubuntu?

Sobre el error que te aparece, creo que tienes un problema con tu disco. Al parecer es un tipo de error que sugiere un sector malo en el disco. Puedes mirar más información al respecto en **[esta pagina]("http://ata.wiki.kernel.org/index.php/Libata_error_messages#ATA_error_expansion")**.

Te sugiero que revises el disco para estar seguros de eso. Una opción es que uses la herramienta *e2fsck. *Para hacerlo tu disco no puede estar montado, así que lo más recomendable es que inicies una sesión desde el LiveCD y corras e2fsck desde la consola. Para revisar la superficie del disco primero debes tener claro cuál es la ruta de tu partición. Esto es especialmente importante si tienes más de un sistema instalado, e2fsck no debe ser usado para revisar otro tipo de particiones que no sean ext2/3/4. Puedes saber la la ruta de tu partición escribiendo el siguiente comando:
```
Sudo fdisk -l
```Luego puedes revisar la superficie de la partición con el comando:
```
sudo e2fsck -c <partición>
```Si, por ejemplo, tu partición está en /dev/sda1 lo que debes hacer es escribir:
```
sudo e2fsck -c /dev/sda1
```Luego verificaría el sistema de archivos:
```
sudo e2fsck <partición>
```Para más información sobre como usar e2fsck puedes mirar [acá]("http://blockdeubuntu.blogspot.com/2009/01/escaneando-el-sistema-de-archivos-de.html").

---

### Post by Naldylipu on 2009-05-29
si, tengo instalado también el windows vista.
cuando instalé ubuntu y use después el vista me pidió revisar el disco duro, lo revisó automáticamente y luego inició el windows... pero no mostró errores, pensé que era una forma de "defenderse" del nuevo sistema operativo. 

Voy a hacer lo que me dices... el problema es que no puedo usar un live cd, porque la unidad optica esta mala, ¿se puede hacer con el pendrive booteable como lo hice cuando instalé ubuntu?

Estas son las particiones que me aparecen
Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        1103     8852480   27  Desconocido
/dev/sda2   *        1103       18450   139342127+   7  HPFS/NTFS
/dev/sda3           18451       24321    47158807+   5  Extendida
/dev/sda5           18451       24075    45182781   83  Linux
/dev/sda6           24076       24321     1975963+  82  Linux swap / Solaris


Muchas gracias por la ayuda

---

### Post by Carlos C on 2009-05-29
> **Naldylipu said:**
> si, tengo instalado también el windows vista.
cuando instalé ubuntu y use después el vista me pidió revisar el disco duro, lo revisó automáticamente y luego inició el windows... pero no mostró errores, pensé que era una forma de "defenderse" del nuevo sistema operativo. 

Voy a hacer lo que me dices... el problema es que no puedo usar un live cd, porque la unidad optica esta mala, ¿se puede hacer con el pendrive booteable como lo hice cuando instalé ubuntu?

Estas son las particiones que me aparecen
Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        1103     8852480   27  Desconocido
/dev/sda2   *        1103       18450   139342127+   7  HPFS/NTFS
/dev/sda3           18451       24321    47158807+   5  Extendida
/dev/sda5           18451       24075    45182781   83  Linux
/dev/sda6           24076       24321     1975963+  82  Linux swap / Solaris


Muchas gracias por la ayuda
Sí, se puede hacer con el pendrive. En este caso tendrías que revisar tu partición /dev/sda5

---

### Post by moreback on 2009-05-29
> **Naldylipu said:**
> ```

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        1103     8852480   27  Desconocido
/dev/sda2   *        1103       18450   139342127+   7  HPFS/NTFS
/dev/sda3           18451       24321    47158807+   5  Extendida
/dev/sda5           18451       24075    45182781   83  Linux
/dev/sda6           24076       24321     1975963+  82  Linux swap / Solaris
```

mmh... así se ve mejor tu tabla de particiones, supongo que sda1 es una partición de recuperación, no? notebook cierto?

---

### Post by pagondel on 2009-05-30
con [UNetbootin](http://unetbootin.sourceforge.net/) puedes hacer facilmente un pendrive booteable ;)
Saludos!

---

### Post by Naldylipu on 2009-05-31
> **moreback said:**
> mmh... así se ve mejor tu tabla de particiones, supongo que sda1 es una partición de recuperación, no? notebook cierto?

si es un notebook, tendré presente para la proxima vez como poner los datos :)

---

