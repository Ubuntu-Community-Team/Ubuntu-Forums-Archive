---
title: "Grub: Ubuntu Natty vs. Fedora 15"
date: 2011-05-31
forum: Software
---

### Post by aledruetta on 2011-05-31
Hola Comunidad,

Tengo instalado Ubuntu 11.04 e instalé la última versión de Fedora con Gnome 3 para probar el escritorio. En el momento de la instalación del Grub únicamente reconocía Fedora y no listaba Ubuntu. Pensé que iría a aparecer después, pero no, no apareció. Tuve que recurrir al LiveCD de Ubuntu y recuperar el Grub. Pero ahora no aparece Fedora.

Por qué se rechazan estas dos distribuciones?

Alguna idea de cómo se puede solucionar esto?

Gracias,
Alejandro

---

### Post by granjero on 2011-05-31
hola, seguiste esta guía?

[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

Salud!

---

### Post by aledruetta on 2011-05-31
> **granjero said:**
> hola, seguiste esta guía?

[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

Salud!

Sí, esa es la guía que seguí. Recuperé el Grub para acceder a Ubuntu, pero ahí ya no pude entrar en Fedora.

---

### Post by granjero on 2011-05-31
y con Super Grub Disk probaste?

salud!

---

### Post by guillermolisi on 2011-05-31
> **aledruetta said:**
> Sí, esa es la guía que seguí. Recuperé el Grub para acceder a Ubuntu, pero ahí ya no pude entrar en Fedora.
Las versiones de Grub usadas en ambos casos, son la misma ?

Hay una sola instancia de Grub instalada o una para cada sistema operativo ?

---

### Post by aledruetta on 2011-06-01
> **guillermolisi said:**
> Las versiones de Grub usadas en ambos casos, son la misma ?

Ni idea... :confused:

> **guillermolisi said:**
> Hay una sola instancia de Grub instalada o una para cada sistema operativo ?

La verdad que no sé. Yo seguí el proceso de instalación normal de Fedora y después, la guía de recuperación de Grub 2 que fue citada más arriba. Teóricamente, Grub fue instalado en dev/sda.

---

### Post by aledruetta on 2011-06-01
Mil disculpas... No había ejecutado un paso de la guía:

```
 
$ sudo update-grub2
```Ahora sí...

Editado desde Fedora 15 con Gnome 3 y probando...

---

### Post by biale on 2011-06-02
De acuerdo con distrowatch.com parece que Fedora 15 usa grub 0,97 mientras que Ubuntu usa 1,99. Entonces si alguien instala Fedora para probar Gnome 3 va a tener ese problema.

---

### Post by guillermolisi on 2011-06-02
> **biale said:**
> De acuerdo con distrowatch.com parece que Fedora 15 usa grub 0,97 mientras que Ubuntu usa 1,99. Entonces si alguien instala Fedora para probar Gnome 3 va a tener ese problema.
Me imagine que el tema venia por ahi, por eso mi pregunta.

No soy nadie para dar consejos, pero antes de largarse a instalar algun SO, es conveniente leer algunas cuestiones basicas para luego no estar "mas perdido que turco en la neblina" :) (No offense)

---

