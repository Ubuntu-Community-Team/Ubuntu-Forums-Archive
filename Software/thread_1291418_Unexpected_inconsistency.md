---
title: "Unexpected inconsistency"
date: 2009-10-14
forum: Software
---

### Post by tintre on 2009-10-14
Hola:

Hoy estaba tratano de ver un archivo de texto que abro habitualmente y me apareció un aviso que decía-según recuerdo-que faltaba el programa o algo así. Luego se quedó pegado y tuve que reiniciar "a la fuerza". Luego lo que me aparece repetidamente es: 
/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
(i,e., whithuot -a or -p options)
fsck died with exit status 4

* An automatic file system check (fsck) ot the root file system failed
The fsck shoukd be performed in maintenence mode with the root file system mounted
in read-only mode
* The root filesystem is currently mounted in read-only mode.
A maintenace shell will now be started
After performing system maintenance, press CONTROL-D to terminate the maintenance
shell and restart the system.

No tengo CD de instalación y tengo ubuntu 9.04 hace un par de meses. Estoy preocupada porque tengo archivos de pega que son urgentes y que cometí el error de no respaldar, además de otras cosas importantes.

¿Mepueden ayudar?

---

### Post by gmunioz on 2009-10-14
Hola tint...:

Tal como el trueno, que llega después del rayo, te

informo que nunca debes resetear al estilo Microsoft

puedes entre otros mecanismos pulsar:

```
Alt Gr más Iprm pant y manteniendolas pulsadas pulsar

y soltar la secuencia R E I S U B  
```

Al problema:

Impresiona como que estas usando inicio dual

Microsoft GnuLinux, si es asi instala Total Commander

[www.ghisler.com](www.ghisler.com)

Y su plugin para ext3 y reiserfs y podrás acceder a tus 

particiones linux para copiar tus archivos.

Luego baja un live liviano, puppy linux

[http://distro.ibiblio.org/pub/linux/distributions/puppylinux/puppy-4.3/pup-430.iso](http://distro.ibiblio.org/pub/linux/distributions/puppylinux/puppy-4.3/pup-430.iso)

Son un poco mas de 100 megas

inicia con este live-cd, luego de grabar la imagen.iso con la

opción grabar imagen, no la de crear cd, de tu grabador preferido

(nero) y corre fsck sobre las particiones linux sin montar, de tu

instalación de Ubuntu

---

### Post by tintre on 2009-10-15
No entendí nada, en todo caso bajé lo que me dijiste, pero no sé cómo hacer que funcione.
Saludos.

---

### Post by moreback on 2009-10-15
tintre: cuando el chequeo falla con Ubuntu, el sistema te deja una consola de root para que puedas aplicar el comando fsck directamente:

```
fsck -y /dev/hda1
```

Después que arreglas todos los discos que te indica como erróneos, presionas Ctrl+D para finalizar y hacer que el pc se reinicie.

Saludos.

---

### Post by tintre on 2009-10-15
Hice lo que me aconsejaste y apareci{o lo siguiente:

fsck -y/dev/hda1

invalid option

usage: fsck.ext4 [- panyrcdf vtDFV] [-b superblock] [-B blocksize]

[-I inode_buffer_blocks] [ Pprocess_inode_size]

[-l : -l bad_blocks_file][-c fd] [-j external_journal]

Emergency Help:
-p                     automatic repair(no questions)
-n                make no charges to the filesystem        
-y                asume "yes" to all questions
-c                check for bad blocks and add the to the badblock list
-f                force checking even ifthe filesystem is marked clean
-v                be verbose
-b superblock           use alternative superblock
-B blocksize            force blocksize when looking for superblock
-j external_journal        set location of the external journal
-I bad_blocks_file        add to badlocks list
-l bad_blocks_file        set badlocks list

---

### Post by moreback on 2009-10-15
No, no hiciste lo que dije. Yo te dije que usaras este comando

```
fsck -y /dev/hda1
```pero no sé por qué razón hiciste esto.
```
fsck -y/dev/hda1
```¿Logras notar la diferencia?

---

### Post by tintre on 2009-10-15
Sí noté la diferencia, y traté también con ese código y me aparece los siguiente:

fsck 1.41.4 (27-jan-2009)
fsck. ext2: No such file or directory while trying to open  /dev/hda1

The superblock could not be read or does not describe a correct ext2 filesystem. If the devide is valid it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, an you might try running e2fsck with an alternate superblock:
 
e2fsck -b 8193  <device>

---

### Post by moreback on 2009-10-15
Leí mal tu post y pensé que era un disco IDE, pero al parecer es un SATA ya que el que sale es un /dev/sda1, sólo tienes que cambiar el comando a:

```
fsck -y /dev/sda1
```

Saludos.

PD: Aprender inglés no te haría mal, sale todo en el mensaje de error que copiaste en tu post.

---

### Post by tintre on 2009-10-15
Ehm, muchas gracias por el consejo, pero inglés hablo bastante bien, lo que no sé es el lenguaje de la informática.

---

### Post by tintre on 2009-10-15
Lo resolví, bastaba escribir en el root :
[FONT=monospace]fsck, y darle enter y se reparò solito.

Gracias por la ayuda y la paciencia.
[/FONT]

---

