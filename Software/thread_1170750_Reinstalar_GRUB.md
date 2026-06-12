---
title: "Reinstalar GRUB"
date: 2009-05-26
forum: Software
---

### Post by Gpafundi on 2009-05-26
Buenas. Como vengo diciendo siempre, soy novato a si que, a los que me respondan: Por favor, sean claros.

Mi situación es la siguiente. Tenía Ubuntu 9.04 y Windows XP particionados en un mismo disco. Como suele pasar de vez en cuando, tuve que reinstalar Windows XP. Al reinstalarlo no aparece mi GRUB y no puedo volver a acceder a mi Ubuntu 9.04.

Ya me había pasado esto una vez y lo había solucionado con el Auto Super Grub Disk. Pero esta vez no se por qué no puedo instalar el GRUB. Quizá sea que la versión de Super Grub Disk no sea compatible con el Ubuntu 9.04. ¿Puede ser?

Desde ya. Muchas gracias.

---

### Post by staar on 2009-05-26
para que podamos ser claros, tenemos que conocer el problema bien, decir 'no se porqué no puedo instalar GRUB' no ayuda mucho, intentá nuevamente y anotá el error que sale para que podamos tener una idea más clara...

SGD si es 'compatible' (que palabra antigua, me hace acordar a IBM :-P :-D) con Ubuntu 9.04

te adelanto que SGD no es 100% efectivo, puede fallar, en cuyo caso tendriamos que guiarte para que instales nuevamente GRUB desde el livecd de ubuntu, proceso delicado para un novato, pero que, con paciencia y atención, sale...

saludos

---

### Post by gmunioz on 2009-05-27
Hola gpa.....:


La instalación del GRUB puede separarse en tres partes:

```
1. Instalación del "stage1" en el MBR.

2. Montar la dirección y la localización, "stage2".

3. Establecer un menu de inicio o organizar las opciones para escoger 

cual es el sistema a inicializar. 
```

Para instalar el Grub, debes hacerlo desde una sesión live de Jaunty.

Comienza averiguando la partición donde esta instalado Ubuntu, esto lo 

haces en consola Aplicaciones - Accesorios - Terminal Ejecutando:

```
sudo fdisk - l (es ele no i)
```

Te dara una salida como esta:

```
Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xf362f362

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1829    14691411   83  Linux
/dev/sda2            1830        9729    63456750    5  Extendida
/dev/sda5            1830        1951      979933+  82  Linux swap / Solaris
/dev/sda6            1952        3653    13671283+  83  Linux
/dev/sda7            3654        9729    48805438+  83  Linux
```
 
La partición identificada con id 83 Linux, con asterisco en inicio es

la que corresponde a /, donde en /boot/grub/ se alojan los archivos del

Grub.

Una vez conocidos estos datos, debes tener presente que para el Grub el

primer disco, que para Ubuntu es /dev/ sda, es hd0 y la primer partición 

del primer disco que para Ubuntu es /dev/sda1, es hd0,0

Aclarado y comprendido lo expuesto, empieza instalando el Grub mediante 

la siguiente orden en consola:

```
sudo grub
```

Esa orden explora los recursos del sistema para adivinar los recursos de

la BIOS y producir un mensaje de salida. Ese procedimiento tarda un poco

en completarse, tendrás una salida parecida a esta:

[HTML]end_request: I/O error, dev 02:00 (floppy), sector 0 GRUB version 0.5.96.1 (640K lower / 3072K upper memory)
[/HTML]

y a continuación te aparecerá una línea para ejecutar los comandos del 

Grub, similar a esta:

```
grub> 
```

Suponiendo que tienes instalado Ubuntu en la primera partición lógica de 

la partición  extendida del primer disco rígido  /dev/sda5. Que 

según la convención de nombres del GRUB  se recoce la partición citada 

como (hd0,4). 

Para instalarlo deberas escribir el siguiente comando:

```
grub> install (hd0,4)/boot/grub/stage1 (hd0) (hd0,4)/boot/grub/stage2 p (hd0,4)/boot/grub/menu.lst
```

Detalladamente esta orden lo que hace es:

```
install
   * Una orden incorporada que indica al GRUB que instale el (hd0,4)/boot/grub/stage1 en el (hd0), el Master Boot Record (MBR). *

(hd0,4)/boot/grub/stage2
    *Dice al grub donde está localizada la imagen del stage2. *

p con las siguientes opciones: (hd0,4)/boot/grub/menu.lst
    *Establece la configuración del archivo para que se muestren los menús.*

Que resumidamente significa:

   1. instalación
   2. código_del_stage1
   3. donde_instalar
   4. código_del_stage2
   5. p codigo_del_archivo_de_configuración

```

A esta altura, habrías completado la instalación del Grub en el disco 

rígido, solo queda salir del grub con la orden:

```
quit
```

Cerrar la sesión live y reiniciar desde el disco rígido.

Saludos.

---

### Post by biale on 2009-05-27
Por las dudas aclaro que existe la posibilidad de incompatibilidades entre el grub en MBR y el formato de la partición desde donde se intenta arrancar, incluso si es ext3. Es una novedad documentada y ya tuve la experiencia.

La logre diagnosticar usando el comando find del grub: justo en la partición recientemente formateada y desde donde quería arrancar, el find no podía encontrar nada de nada. 

O sea que si al seguir las instrucciones descriptas la situación no se arregla, tendrás que conseguir un cd con una versión de grub compatible. Calculo que el live CD de Jaunty tendría que funcionar (?).

Solo a titulo informativo informo que en *mi caso*, hice la viceversa, sabiendo que el grub en MBR provenía de Hardy, hice un formato ext3 de la partición de arranque con el CD live de Hardy y luego bajé un backup de la misma.

Saludos!

---

### Post by Gpafundi on 2009-05-29
¡¡Gracias Gmunioz!! Hice lo que me pusiste y anduvo todo perfecto. Es más, te estoy respondiendo desde mi Ubuntu. Suerte.

---

