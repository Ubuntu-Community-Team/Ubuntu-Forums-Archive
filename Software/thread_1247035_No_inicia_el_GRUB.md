---
title: "No inicia el GRUB"
date: 2009-08-22
forum: Software
---

### Post by Slay_ on 2009-08-22
Bueno pues en Windows trastenado un poco con las particiones me cargué la D, hice del espacio libre otra particion y le asigne e nuevo la D.
El problema es que al iniciar de nuevo el PC me salía un error 17. Me bajé el Super Grub Disk y le di a arreglar el arranque de Linux primero y luego de Windows, el problema es que ahora al inciar el ordenador se me queda cargando en GRUB Loading stage1.5

¿Qué pasa?

---

### Post by gmunioz on 2009-08-22
Hola sla....:

Reinstala el Grub.

---

### Post by Slay_ on 2009-08-22
Como? Lo he intentado todo, he buscado mil tutoriales para recuperar el GRUB, pero nada.. 
Gracias.

---

### Post by rafaelca on 2009-08-22
Prueba Re-Instalando 'UBuntu 9.04'

---

### Post by santiagoward2000 on 2009-08-22
No hace falta que reinstales todo el sistema para arreglar el Grub. Existen programas como [Super Grub Disk]("http://www.supergrubdisk.org/"), que te dejan recuperarlo.
Saludos!

---

### Post by rubioo on 2009-08-22
Es verdad, con Grub Super Disk podés hacerlo.
 Acá te dice como hacerlo [Recuperar GRUB]("http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB")

       Saludos!

---

### Post by gmunioz on 2009-08-22
Hola sla....:

Empieza instalando el Grub desde una sesión live de
Ubuntu mediante la siguiente orden en consola:

```
sudo grub
```

Esa orden explora los recursos del sistema para adivinar
los recursos de la Bios y producir un mensaje de salida 
como este: 

[HTML]end_request: I/O error, dev 02:00 (floppy), 
sector 0 GRUB version 0.5.96.1 (640K lower / 
3072K upper memory)[/HTML]

El Grub puede soportar unas ordenes mínimas parecidas al Bash. 
Para la primera palabra, la tecla Tab muestra la lista para 
completar los comandos posibles. Tab muestra los posibles 
terminaciones de dispositivos y nombres de archivos.  
Aparece una línea como esta:

[HTML]grub> [/HTML]

Suponiendo que se ha instalado Linux en la primera partición
 extendida en el primer disco o /dev/hda5. Que según la 
convención de nombres del GRUB  se renombra la partición 
citada a (hd0,4). 

Se debe escribir el siguiente comando:

[HTML]grub> install (hd0,4)/boot/grub/stage1 (hd0) (hd0,4)/boot
/grub/stage2 p (hd0,4)/boot/grub/menu.lst[/HTML]

Ahora si examinas detalladamente esa orden, veras que:

[HTML]install[/HTML]
    Es la orden incorporada que indica al GRUB que instale 
el (hd0,4)/boot/grub/stage1 en el (hd0), el Master Boot 
Record (MBR). 

[HTML](hd0,4)/boot/grub/stage2[/HTML]
    Le dice al grub donde está localizada la imagen del stage2. 

[HTML]p con las siguientes opciones: (hd0,4)/boot/grub/menu.lst[/HTML]
    Establece la configuración del archivo para que se muestren los simpáticos menús del Grub.

Resumiendo se trata de aplicar estas ordenes:

   1. instalación
   2. código_del_stage1
   3. donde_instalar
   4. código_del_stage2
   5. p codigo_del_archivo_de_configuración

Del Grub se sale con quit

Ahora has completado la instalación del disco duro, cambiando
obviamente los parámetros de las particiones por las tuyas,
para averiguarlas solo hace falta ejecutar en consola

[HTML]sudo fdisk -l[/HTML]

---

### Post by Slay_ on 2009-08-23
> **rafaelca said:**
> Prueba Re-Instalando 'UBuntu 9.04'
¿Cómo? ¿Desde el Live-CD en la misma particion?

> **santiagoward2000 said:**
> No hace falta que reinstales todo el sistema para arreglar el Grub. Existen programas como [Super Grub Disk]("http://www.supergrubdisk.org/"), que te dejan recuperarlo.
Saludos!

> **rubioo said:**
> Es verdad, con Grub Super Disk podés hacerlo.
 Acá te dice como hacerlo [Recuperar GRUB]("http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB")

       Saludos!

Lo intente cuando tenia el error 17 y no hice más que complicarlo

> **gmunioz said:**
> Hola sla....:

Empieza instalando el Grub desde una sesión live de
Ubuntu mediante la siguiente orden en consola:

```
sudo grub
```Esa orden explora los recursos del sistema para adivinar
los recursos de la Bios y producir un mensaje de salida 
como este: 

[html]end_request: I/O error, dev 02:00 (floppy), 
sector 0 GRUB version 0.5.96.1 (640K lower / 
3072K upper memory)[/html]El Grub puede soportar unas ordenes mínimas parecidas al Bash. 
Para la primera palabra, la tecla Tab muestra la lista para 
completar los comandos posibles. Tab muestra los posibles 
terminaciones de dispositivos y nombres de archivos.  
Aparece una línea como esta:

[html]grub> [/html]Suponiendo que se ha instalado Linux en la primera partición
 extendida en el primer disco o /dev/hda5. Que según la 
convención de nombres del GRUB  se renombra la partición 
citada a (hd0,4). 

Se debe escribir el siguiente comando:

[html]grub> install (hd0,4)/boot/grub/stage1 (hd0) (hd0,4)/boot
/grub/stage2 p (hd0,4)/boot/grub/menu.lst[/html]Ahora si examinas detalladamente esa orden, veras que:

[html]install[/html]    Es la orden incorporada que indica al GRUB que instale 
el (hd0,4)/boot/grub/stage1 en el (hd0), el Master Boot 
Record (MBR). 

[html](hd0,4)/boot/grub/stage2[/html]    Le dice al grub donde está localizada la imagen del stage2. 

[html]p con las siguientes opciones: (hd0,4)/boot/grub/menu.lst[/html]    Establece la configuración del archivo para que se muestren los simpáticos menús del Grub.

Resumiendo se trata de aplicar estas ordenes:

   1. instalación
   2. código_del_stage1
   3. donde_instalar
   4. código_del_stage2
   5. p codigo_del_archivo_de_configuración

Del Grub se sale con quit

Ahora has completado la instalación del disco duro, cambiando
obviamente los parámetros de las particiones por las tuyas,
para averiguarlas solo hace falta ejecutar en consola

[html]sudo fdisk -l[/html]
Lo hice y pone:
```
Error 12: Invalid device requested

```Gracias a todos, espero poder arreglarlo pronto.
Por cierto, no dudaría en reinstalar el Ubuntu si consigo saber como.
EDIT: Vale, he instalado de nuevo el Ubuntu y he conseguido arreglar el GRUB, pero ahora al meterme en el Gparted para borrar el anterior Ubuntu, me dice que tengo que desmontar la particion. ¿Cómo puedo hacer eso?

---

### Post by Hei Ku on 2009-08-23
Generalmente con click derecho sobre la particion, debería aparecer la opcion de desmontar.

---

### Post by guillermolisi on 2009-08-23
> **rafaelca said:**
> Prueba Re-Instalando 'UBuntu 9.04'
No es correcto sugerir semejante cosa en forma liviana, asi como asi.

Primero, reinstalar sin investigar e intentar otras alternativas no te permite entender por que paso lo que paso, luego no aprendes y cuando te vuelva a pasar solo te queda lo que hiciste, una y otra vez, como toda solucion "a ciegas".

Ademas, hay que considerar cuales son las implicancias de reinstalar para la otra persona. Cada maquina es un mundo aparte.

La alternativa de reinstalar es la ultima de las ultimas, cuando ya se probo todo lo que se podia probar, se verifico todo lo relativo que se tenia que verificar.

Tomar nota de esto para proximas intervenciones.

---

### Post by lexer98 on 2009-08-23
hola amigo mira yo ayer tube que reinstalar windows xp y me saco el grub para recuperarlo use estos comandos lo hice en live cd con el super grub ese no me sirvio no lo recuperaba capas que sirven

los comandos
$ sudo grub                *--> ejecutamos el interprete de comando de grub*
> find /boot/grub/stage1   *--> busca donde esta la partición de ubuntu*
> root (hdX,Y)             *--> poner el valor devuelto anterior*
> setup (hd0)              *--> instala grub en nuestro primer disco duro (hd0), *
                               *que es con el que inicia la computadora*
> quit                     *--> salimos del interprete de comando de grub*

---

