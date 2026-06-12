---
title: "Problema de brillo en netbook ubuntu 12.04"
date: 2012-08-16
forum: Software
---

### Post by Robinsxsoad on 2012-08-16
Hola ubunteros! :)
La verdad es que recurro a su ayuda ya que no he podido solucionar este problema. He tratado con muchos métodos y no pasa nada y la verdad es que mis ojos no aguantan más...
No puedo modificar el brillo de a pantalla de mi netbook y la verdad es que no es cómodo, ya que para distintas aplicaciones ocupo distintos niveles de brillo y además quiero que la batería me dure un poquito más :B

Alguna idea?
Es un netbook HP Mini 110 con procesador Intel Atom.

Gracias por la orientación :)

---

### Post by 3nG3ndR0 on 2012-08-16
ya mi me paso esto en mi otro notebook no realice esto y me funciono, prueba a ver que tal te va.

abrir en la terminal:

```
sudo gedit /etc/default/grub

```

en la linea GRUB_CMDLINE_LINUX_DEFAULT hay que agregar acpi_backlight=vendor, quedando de esta manera:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

```
actulizamos el grub y reniciamos:

```
sudo update-grub

```

---

### Post by Robinsxsoad on 2012-08-16
> **3nG3ndR0 said:**
> ya mi me paso esto en mi otro notebook no realice esto y me funciono, prueba a ver que tal te va.

abrir en la terminal:

```
sudo gedit /etc/default/grub

```

en la linea GRUB_CMDLINE_LINUX_DEFAULT hay que agregar acpi_backlight=vendor, quedando de esta manera:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

```
actulizamos el grub y reniciamos:

```
sudo update-grub

```
Lo hice... aparece alguna opción en alguna parte? Debo apretar alguna combinación?

---

### Post by 3nG3ndR0 on 2012-08-17
ose la combinación de tu teclado para probar el brillo, ejemplo mi notebook es tecla Fn + f11 y f12

---

### Post by Robinsxsoad on 2012-08-19
No pasa nada... hice todo tal cual y aún así no puedo modificar el brillo...

---

### Post by Lutho on 2012-11-20
ese problema del brillo lleva bastante tiempo, incluso para la version 10.04 
yo aun tengo el problema del brillo en mi acer aspire 5738

no la he solucionado por que siempre he trabajado conectado a la corriente y batería casi nunca.
espero que algún día eso se solucione :D 
saludos de todas formas realice el mismo podrecimiento para ver si sucede algo :D

---

### Post by juannas on 2013-02-23
hola queria agradecer por la info y agregar que la linea GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backl.ight=vendor" al menos para mi pc asus Eee PC Seashell series esta incompleta debe ser asi:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor acpi_osi=Linux"

---

