---
title: "Necesito que Ubuntu sea reconocido en Grub (a secas, no Grub 2)"
date: 2012-05-20
forum: Software
---

### Post by 53RG10 on 2012-05-20
Hola a todos

Tengo el siguiente problema. Tengo instalada la última versión de Ubuntu y también la última versión de PCLinuxOS.

PCLinux utiliza el Grub y no Grub 2, es por esta razón que no me reconoce la partición de Ubuntu como sistema operativo, y al ser el Grub 2 mucho más complicado que el Grub (para mí :)), no quiero instalar el Grub 2 de Ubuntu encima del otro (perdón si los ofende, pero así lo quiero :). Gustos, que le dicen).

Lo que no entiendo, es como agregar la entrada de Ubuntu, ya que entro al Grub.cfg que está en el /boot de Ubuntu (sda3), y son demasiados datos, no sé cuales son los importantes y cuales no, para poder agregar al menu.lst del PClinuxOS (sda2).

¿Alguien podría darme una mano? Todo lo que encontré en internet, o es viejo, o no es la solución que estaba buscando.
Muchas gracias

Sergio

---

### Post by gmunioz on 2012-05-20
#----
title Ubuntu
root (hd0,2)
kernel /boot/vmlinuz-3.2.0-24-generic root=/dev/sda3
boot
#----

---

### Post by 53RG10 on 2012-05-21
> **gmunioz said:**
> #----
title Ubuntu
root (hd0,2)
kernel /boot/vmlinuz-3.2.0-24-generic
boot
#----
Gracias :)
¿Eso significa que debo copiar el archivo "vmlinuz-3.2.0-24-generic" que está en la carpeta /boot de Ubuntu a la carpeta /boot de PCLinuxOS?
Yo no aclaré que tengo a cada Sistema Operativo con su carpeta /boot, por eso pregunto.
Saludos

---

### Post by gmunioz on 2012-05-21
No, de ninguna manera:

Lo mejor del GRUB (legacy) es que permite cargar cualquier Kernel en cualquier partición. 

Es conveniente saber como GRUB (legacy) entiende los discos duros y la información de las particiones. Primero de todo, empieza contando los las particiones desde 0, no a partir de 1. En el Gnu/Linux, el primer disco duro adjunto al master primario es nombrado “sda”. En el GRUB se convierte en el “hd0”. De la misma forma, el primer disco flexible en el GRUB es “fd0”. Pero la primera, segunda y tercera partición en el primer disco duro (sda1, sda2 y sda3), se convierten en “hd0,0”, “hd0,1” y hd0,2” en GRUB, la coma es una parte integral de la nomenclatura del GRUB.

Para integrar los dos campos (el número del disco y de la partición) alrededor de la coma, utiliza los paréntesis. Por ejemplo: (hd0,0) (hd0,1) (hd0,2) y así sucesivamente. (hd0,0) es la primera partición en el primer disco duro. De forma parecida és el (hd1,5) és la sexta partición en el Segundo disco duro y (hd2,0) es la primera partición en el tercer disco duro.

Procedimiento de arranque soportado por el GRUB (legacy). 
   1. Establece el dispositivo root o dile al GRUB como es tu sistema de ficheros de root.
   2. Dile al GRUB donde está tu imagen de arranque del Kernel y pasa los parámetros al Kernel.

Para iniciar el Gnu/Linux, si tienes tu kernel en /boot/ como bzImage y tu sistema de archivos root en /dev/sda5, o (hd0,4) en el GRUB (legacy). 
El procedimiento de arranque es el siguiente:

   1. root (hd0,4)   *[Eso establece la partición root]*
   2. kernel /boot/bzImage root=/dev/sda5  * [Establece el Kernel]*
   3. boot  * [Eso empieza a arrancar el Linux] *

Por lo expuesto, no debes mover el archivo del kernel, sino solo indicarle desde donde debe cargarlo.

---

### Post by 53RG10 on 2012-05-22
Muy buena tu explicación, además de la solución, gracias. Todo quedó más claro.
Ya lo hice y funciona perfecto :)
Saludos

---

