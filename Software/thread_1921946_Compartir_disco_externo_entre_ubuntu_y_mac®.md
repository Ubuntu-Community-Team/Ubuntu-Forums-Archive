---
title: "Compartir disco externo entre ubuntu y mac®"
date: 2012-02-07
forum: Software
---

### Post by granjero on 2012-02-07
Hola, como les va? Tengo otra duda! 

Que formato le doy a un disco externo que necesito que pueda escribirse tanto desde OSX y ubuntu?

FAT32 tiene la restricción de los 4Gb. HFS+ con journaling no tiene soporte w+r en ubuntu. ext4 no tiene soporte w+r en OSX. La única que me queda es NTFS???  :confused:

¿Qué se les ocurre?

salud!

---

### Post by juancarlospaco on 2012-02-07
Ext3 ?
(creo que se le instala un programa, pero es Freeware)

---

### Post by granjero on 2012-02-08
JuanCarlos, estuve leyendo más y parece que tendría que ser en ext2. 
También lei que puede ser reiserFS pero ese filesystem no lo conozco...

voy a probar y les cuento...

salud!

---

### Post by juancarlospaco on 2012-02-08
Si no recuerdo mal ReiserFS habia que defragmentarlo igual que NTFS,
se penso para escribir muy rapido, para un uso especifico, 
el que lo hizo esta preso y quedo trunco el FS.

---

### Post by biale on 2012-02-08
El formato para máxima compatibilidad sigue siendo fat...

Revisando hace un par de meses las cosas llegue a la conclusión que los discos externos usb mas o menos encajaban en tres grandes grupos. 

El primero sería una caja de buena marca a 220 V y con un disco común adentro: el que menos problemas tiene. El segundo grupo serían las unidades selladas mas antiguas,un caso intermedio. 

El tercer caso serían los discos mas nuevos, que suelen tener una lógica bastante compleja y no muy predecible. O sea que hay que investigar que piensa el fabricante al respecto.

---

### Post by euzkoarima on 2012-02-08
Como dicen en mac se puede usar Reiser y ext2, no soportado por apple.
Si bien un poco viejo, esta pág [0] da una buena idea de que soporta OSX

Lo otra es ir al revés y tratar de montar HFS+ (el formato de OSX) en linux.
Al respecto, les dejo estas otras dos páginas [1] y [2]

[0] [osxbook.com]("http://osxbook.com/book/bonus/ancient/whatismacosx/arch_fs.html")
[1] [linuxquestions.org]("http://www.linuxquestions.org/questions/linux-software-2/mounting-hfs-volumes-under-linux-521189/")
[2] [magarto.com]("http://magarto.com/blog/archivo/2007/03/27/howto-montar-lecturaescritura-chequear-y-reparar-hfs-en-ubuntu/")

Saludos,
Eduardo

---

### Post by EnriqueK on 2012-02-09
si las Macs no tienen problemas en leer/escribir en NTFS, te recomiendo a este por que así no vas a tener problemas de propietarios ni de permisos, este en mi opinión es un aspecto importante si se quiere guardar información que deberán ser compartidas en diferentes tipos de equipos.

---

### Post by granjero on 2012-02-15
Gracias a todos por sus aportes. Al final terminé usando NTFS ya que es fácil de configurar en OSX y en Ubuntu.

Para hacer andar Ext2 en OSX me costó mucho encontrar drivers que anden bien. Y los que supuestamente andaban bien no los pude compilar nunca. OSX me decía que le faltaban dependencias y no supe como cumplirlas. ;)

NTFS anduvo bien en ambos sistemas. Y más allá de la fragmentación no creo que tenga mayores inconvenientes. Doy el tema por cerrado. 

Salud!

---

