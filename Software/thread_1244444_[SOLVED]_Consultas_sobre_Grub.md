---
title: "[SOLVED] Consultas sobre Grub"
date: 2009-08-19
forum: Software
---

### Post by tinoq3 on 2009-08-19
Hola gente, se que mucho se habló de este tema pero no encontré respuestas a las preguntas que detallaré mas abajo.

El panorama es el siguiente, tengo 2 discos SATA Samsung de 200 GB y 320 GB. Están conectados en ese orden, master y slave respectivamente.
En el 1ro tenía instalado XP, pero como comenzó a fallar según acusa el booteo de la pc, me decidí por instalar XP en el disco de 320 GB y dejar el otro para Ubuntu.
Hasta acá todo perfecto, solo que cuando instalo Karmic dejo de ver XP. Ejecuto "update-grub2" y nada...

Ahora bien, más allá de necesitar solucionar esto, mis preguntas son:


- Grub no reconoce XP porque el disco está conectado como esclavo?

- Me convendría instalr Grub en el MBR del disco de XP (320 GB) para que mas allá de las instalaciones de Ubuntu que haga, siempre bootee XP sin problemas?

- Tengo forma de devolverle el control del MBR al NTLDR de Win?


Desde ya gracias y disculpen lo extenso del post. Saludos!

---

### Post by staar on 2009-08-19
el problema es que karmic instala grub2, y no se si está muy pulido lo de agregar otros OS desde el instalador todavía, pero podés hacerlo a mano...

tenés que agregar un script en /etc/grub.d/ y llamarlo, por ejemplo, 11_windows (el 11 es para que salga después de los ubuntu, pero antes del memtest, si querés que salga después del memtest podés poner 21, más info en el README que está en /etc/grub.d), con este contenido ```

#! /bin/sh -e

    cat << EOF
    menuentry "Microsoft Windows XP Professional" {
    set root=(hd0,1)
    chainloader +1
    }
    EOF
``` obviamente modificando el título como te guste, y la partición de inicio como corresponda, teniendo en cuenta que en grub2 los discos empiezan a contarse desde 0 y las particiones desde 1, en tu caso sería (hd1,1) si Ventanas está en la primera partición del segundo disco...

después le das permisos de ejecución al script ```
sudo chmod +x /etc/grub.d/11_windows
``` y, ahora si, corres ```
sudo update-grub
```

saludos

---

### Post by tinoq3 on 2009-08-19
Gracias Staar, lo pruebo mas tarde y te aviso.

Respecto a la pregunta que hice antes, como configuro el Grub durante la instalación de ubuntu como para que se grabe en el MBR del disco con XP?
De esta forma no tendría mas problemas cuando instale nuevas versiones, no? (si estoy diciendo burradas avisen...)

Saludos.

---

### Post by staar on 2009-08-19
GRUB tiene que estar en la MBR del disco que inicia primero, sino no funciona (a menos que la MBR del otro disco esté vacía, pero casi nunca lo está), ponerlo en el disco con XP no va a hacer que reconozca ese sistema automáticamente, eso se hace de otra forma (como te expliqué arriba), no tiene que ver adonde esté (en realidad, en la MBR está una mitad del GRUB, la otra, que tiene todas las configuraciones, está en /boot, en el sistema de archivos del linux instalado)...

saludos

---

### Post by gmunioz on 2009-08-19
Hola tin...:

Tienes algunos conceptos confusos:

1- Los discos sata no son master ni slave, son

sata1 sata2 sata3 etc. etc.

master y slave, son los discos ide ó pata, segun

los jumpers del dispositivo o segun la punta o

el medio del conector ide.

2- Los discos ide o pata, inician siempre desde

ide0 a ide3, segun esten en punta - medio de los

conectores ide0 - ide1.

Los discos sata inician segun esten en sata1 sata2

etc. etc.

3- Tanto el Grub legacy como el Grub 2, para recibir

el mando de inicio del ordenador por parte de la bios

deben estar instalados en el mbr del primer disco.

Por ejemplo si hubieran dos ide en ide1, serían ide3

e ide4, siempre iria en ide3, en ide4 o en una partición

nunca recibiria el comando desde la bios, en el caso de

sata2 y sata3, iria en el mbr de sata2, en sata2 o en

una partición no iniciaría.

4- En el caso de mothers nuevas, desde el setup se puede

alterar el orden de inicio, pero como sea siempre el Grub

debe estar instalado en el mbr del disco que inicia.

5- sobre el Grub 2 lee esto:

[http://ubuntuforums.org/showthread.php?t=1221784&highlight=grub](http://ubuntuforums.org/showthread.php?t=1221784&highlight=grub)

---

### Post by tinoq3 on 2009-08-19
A ver si entendí bien, recopilando ambos posts...


1. Tengo instalado Grub en el MBR del disco de 200GB que posee actualmente a Ubuntu. Esto se debe a que está conectado en sata1 (gracias por la corrección, me confundió el hecho de que el BIOS me los muestra como "HDSAMSUNG**M**" y "HDSAMSUNG**S**").

2. El gestor de arranque de Win en el disco sata2 de 320GB se supone que está intacto, no? pero por instalarse Grub en el MBR del sata1 este tiene preponderancia, es esto así?

3. Cambié el orden de booteo desde el BIOS, pero si mal no recuerdo arranco Grub sin problemas en ambos casos...

4. Como dijiste Staar, Grub se instala parte en el MBR y la config dentro de /boot, si elimino las particiones de Ubuntu...  me quedo sin poder bootear toda la PC?
Se que la preg suena tonta, pero quiero terminar de entendar si existe alguna config de discos que me permita seguir experimentando con Ubuntu sin afectar a Win. Por ejemplo, que pasa si el día de mañana quiero darle formato NTFS por X motivo...


Muchas gracias de antemano, Win te mantiene tan al margen de estas cosas que cuando empezas a mirar te volves loco :???:.

---

### Post by gmunioz on 2009-08-19
Hola tin...:

1- Si

2- Si

3- Puede ser

4- Si, en /boot esta el resto de los archivos

del Grub, si los borras no inicia, esto lo 

solucionas desde el cd de MsWindows ejecutando

fdisk /mbr, esto hará que inicie con ntldr.

5- Puedes desconectar los discos en forma 

alternada e instalar, con solo uno de ellos 

los operativos, uno para Ubuntu otro para

MsWindows, mas no es aconsejable, lo ideal es

instalar Mswindows primero, Ubuntu despues y

agregar al Grub 2 la opción de MsWindows.

De borrar Ubuntu, el disco formateado en ntfs

estaria apto para MsWindows, que iniciaria a

partir de ejecutar fdisk /mbr

---

### Post by EnriqueK on 2009-08-19
Por eso siempre es mejor tener los SO en un mismo disco. 
Aclaro que nunca lo hice pero te recomiendo incestigar y  probar con el GAG (gestor de arranque gráfico) 
[http://gag.sourceforge.net/es-index.html](http://gag.sourceforge.net/es-index.html)

---

### Post by tinoq3 on 2009-08-23
Solucionado, agregué el script y ya tengo Win en el Grub!
Muchas gracias gente.

EnriqueK, preferí continuar utilizando Grub. Gracias de todas formas.

---

