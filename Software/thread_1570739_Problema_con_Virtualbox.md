---
title: "Problema con Virtualbox"
date: 2010-09-08
forum: Software
---

### Post by dam1977 on 2010-09-08
Estoy intentando instalar una máquina virtual con Virtualbox. Es un poco pobre el espacio y las condiciones, pero deber{ia poderse instalar. Intento colocarle un Windows 7 con 512 d RAM y un disco virtual de 10 Gigas. Pero me aparece el siguiente mensaje:

Fallo al crear el almacenamiento de disco duro Exoz-Daniel-Seven.vdi.
Could not create the medium storage unit '/home/daniel/.VirtualBox/HardDisks/Exoz-Daniel-Seven.vdi'.
VDI: disk would overflow creating image '/home/daniel/.VirtualBox/HardDisks/Exoz-Daniel-Seven.vdi' (VERR_DISK_FULL).

¿Será que no alcanzan las condiciones para instalarla? ¿O es algo que yo pueda corregir?
Gracias....

---

### Post by alfplayer on 2010-09-08
Lo que dice es disk full, disco lleno.

---

### Post by Mazzza on 2010-09-08
Qeu tranza dam1977, el problema es que no cumples con los requisitos minimos para el Win7, te dejo la lista de los requisitos minimos de tu Host y Guest para que veaz lo que te hace falta.


**       If you want to run Windows 7 on your PC, here's what it takes:     **


[LIST]
[*]           1 gigahertz (GHz) or faster 32-bit (x86) or [64-bit (x64)]("http://windows.microsoft.com/en-us/windows7/products/features/64-bit-support") processor.         
[*]1 gigabyte (GB) RAM (32-bit) or 2 GB RAM (64-bit).
[*]16 GB available hard disk space (32-bit) or 20 GB (64-bit).
[*]DirectX 9 graphics device with WDDM 1.0 or higher driver.
[/LIST]

**[SIZE=2]Ubuntu Desktop Edition[/SIZE]**

 
[LIST]
[*]1 GHz x86 processor 
[*]1 Gb of system memory (RAM) 
[*]15 GB of hard-drive space (although this can be split onto 2 drives, a 5Gb / and a 10Gb /home fairly easily) 
[*]Graphics card and monitor capable of 1024 by 768 
[*]Either a Cd/Dvd-drive or a Usb socket (or both) 
[*][Internet access]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript") is helpful 
[/LIST]

---

### Post by guillermolisi on 2010-09-08
Mas alla de los requerimientos aconsejados para correr Win7, el error que te aparece en tiempo de creacion del disco para la VM es que no tenes esa cantidad de espacio libre en el disco real.
Casi que te esta ahorrando trabajo ya que 10Gb no alcanzaran, segun parece, para instalar y correr Win7.

Creo que en estos casos amerita el famoso cartel "Esta seguro ?" :) (no offense)

---

### Post by juancarlospaco on 2010-09-08
*Windows 7 = 20 GB HDD*

---

### Post by dam1977 on 2010-09-15
Gracias a todos de nuevooooo. Hice cirugía mayor. Lo que sucedía era que tenía el disco casi todo ocupado entre Win XP y Ubuntu (es un chiquitín de 80 gigas). Así que formateé el disco, instalé sólo Ubuntu, y luego creé una máquina virtual de 20 gigas para el XP. Ahora estoy trabajando solo con Ubuntu. Uso XP solo para unas bases de datos que necesito en Access. Una maravilla.

---

