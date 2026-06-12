---
title: "Lectura y Escritura de Ext4 con dual boot en Ubuntu 9.04"
date: 2009-05-28
forum: Software
---

### Post by atari130xe on 2009-05-28
Tengo una duda, tengo un sobrino que tiene muchos juegos en Windows y obviamente siempre tengo dual boot en mi PC pero yo no uso uso más Windows, tengo ganas de instalar Jaunty en particiones EXT4 pero, antes de hacer eso quiero asegurarme que si voy a poder leer/escribir desde Win en caso de ser necesario, alguien ya lo probó? o tiene alguna sugerencia?, Estuve indagando en Google y encontré este link, pero como dice por todos lados "should work" (debería funcionar) quisiera más opiniones... Gracias! :D

[http://www.msfn.org/board/index.php?showtopic=132124]("http://www.msfn.org/board/index.php?showtopic=132124")

---

### Post by sajnox on 2009-05-28
Hace poco probe lo mismo con el ext2ifs y no me dio ni cinco de pelota....y la verdad que tampoco insisti demasiado

---

### Post by atari130xe on 2009-05-28
> **sajnox said:**
> Hace poco probe lo mismo con el ext2ifs y no me dio ni cinco de pelota....y la verdad que tampoco insisti demasiado

Está bién seguiré con Ext3 entonces no quiero hacer lio y volver a re instalar todo nuevamente, gracias Sajnox!

---

### Post by Tosh78 on 2009-05-28
Yo tambien lo intente varias veces y de varias formas distintas y nunca pude hacerlo andar.

---

### Post by gmunioz on 2009-05-29
Hola ata...:

Dices:

[I]```
"...tengo ganas de instalar Jaunty en particiones EXT4 pero, 

antes de hacer eso quiero asegurarme que si voy a poder leer/escribir 

desde Win en caso de ser necesario...."
```[/I]

Pregunto: ¿Qué lees/escribes en / de Ubuntu desde Windows? 

No es aconsejable que Windows acceda a / de ninguna manera, además

¿Para qué?

El uso ext4 en Gnulinux / Ubuntu, es  conveniente en la partición / y 

eventualmente en la partición /home si tienes la precaución de poner

todos tus archivos en una partición separada. montada por ejemplo en

/home/usuario/datos, en sistema de archivos ext3, reiserfs o xfs, según

necesidad, y no en ext4.

A esta partición podrías acceder desde Windows si esta en ext3 con los 

distintos  drivers y en reiserfs con Totalcommander y su plugin para ext3

y reiserfs.

Por ahora, no es conveniente tener los archivos personales en ext4, debido

a que ante cualquier emergencia no se podrían acceder desde cualquier 

livecd, solo con alguno de una distribución que lo soporte, además tiene

en el caso de archivos grandes, ciertos problemas al eliminarlos con 

congelamiento del sistema.

Conclusión: Puedes y es conveniente, que aproveches las ventajas de ext4

en Jaunty, utilizandolo como sistema de archivos en /, y si quieres en

/home, siempre y cuando en este último caso, tus archivos personales esten

en partición aparte con sistema de archivos distinto a ext4.

Saludos.

---

### Post by atari130xe on 2009-05-29
> **gmunioz said:**
> Hola ata...:

Dices:

[I]```
"...tengo ganas de instalar Jaunty en particiones EXT4 pero, 

antes de hacer eso quiero asegurarme que si voy a poder leer/escribir 

desde Win en caso de ser necesario...."
```[/I]

Pregunto: ¿Qué lees/escribes en / de Ubuntu desde Windows? 

No es aconsejable que Windows acceda a / de ninguna manera, además

¿Para qué?

El uso ext4 en Gnulinux / Ubuntu, es  conveniente en la partición / y 

eventualmente en la partición /home si tienes la precaución de poner

todos tus archivos en una partición separada. montada por ejemplo en

/home/usuario/datos, en sistema de archivos ext3, reiserfs o xfs, según

necesidad, y no en ext4.

A esta partición podrías acceder desde Windows si esta en ext3 con los 

distintos  drivers y en reiserfs con Totalcommander y su plugin para ext3

y reiserfs.

Por ahora, no es conveniente tener los archivos personales en ext4, debido

a que ante cualquier emergencia no se podrían acceder desde cualquier 

livecd, solo con alguno de una distribución que lo soporte, además tiene

en el caso de archivos grandes, ciertos problemas al eliminarlos con 

congelamiento del sistema.

Conclusión: Puedes y es conveniente, que aproveches las ventajas de ext4

en Jaunty, utilizandolo como sistema de archivos en /, y si quieres en

/home, siempre y cuando en este último caso, tus archivos personales esten

en partición aparte con sistema de archivos distinto a ext4.

Saludos.

Gracias por los consejos, que necesito Leer/Escribir desde win? bueno usualmente en mi PC realizo muchas (muchisimas) pruebas y experimento con nuevo soft y hard cuando llega a mis manos, entonces lo que usualmente hago es cuando voy a formatear y/o hacer una modificación "grande" en mi sistema es ahi (para no utilizar incontables CDs/DVDs para hacer backups, simplemente "muevo" el contenido de mi Home a la partición de Windows) y una vez instalado lo que deseo, simplemente vuelvo a su lugar dicha carpeta, más que nada es la "utilidad" por la que deseo saber lo que planteé en el thread. Me parece razonable lo que decís sobre hacer una partición / ext4 y la /home ext3, de echo hace varias versiones de Ubuntu que instalo el sistema de esa manera tengo particiones separadas / y /home, inclusive eh llegado a tener más particiones, pero ya no lo suelo hacer, sino que solo las 3 básicas: /, /home, /swap, solo eso.

De echo quiero "Volar" Windows 7 Beta de la PC y volver a XP para los juegos de mi sobrino para que el la utilice, sinceramente como que me acostumbre tanto a Ubuntu y Linux que me siento "perdido" en Win cuando inicio sesión en el.:D

---

### Post by EnriqueK on 2009-05-29
Tampoco veo la necesidad de que tengas acceso desde windows, lo que podeés hacer es crear una partición en formato NTFS y tener allí los documentos a compartir, para ello esta partición debes configurarla para que monte al inicio y si querés podés crear en tu carpeta de usuario un enlace simbólico a las carpetas de esa partición y lo mismo hacés en windows creando enlaces directos al escritorio , lógicamente con esta solución vas a tener que hacer desfragmentaciones periódicas desde windows, pero creo que es lo mejor que podés hacer , además es muy conveniente hacer respados en etro medio distinto al DD , te lo dice alguien que sabe lo que es pasar por una falla catastrófica del DD y no tener respaldos.... pérdida total de datos.

---

