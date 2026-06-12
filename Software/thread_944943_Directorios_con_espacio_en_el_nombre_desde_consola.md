---
title: "Directorios con espacio en el nombre desde consola"
date: 2008-10-11
forum: Software
---

### Post by sartrejp on 2008-10-11
Hola, escribo para hacer la siguiente consulta.
Quiero acceder desde la consola a unas carpetas que tienen espacios en el nombre, no puedo cambiárselos ya que están dentro de windows ](*,) (Archivos de programa por ejemplo) y no puedo hacerlo. ¿Alguien sabe como?
quiero ejecutar con wine algunas cosas que tengo instaladas en la partición de windows, cuando voy con nautilus no hay drama, pero por consola no se como llegar.
Desde ya... gracias

---

### Post by santiagoward2000 on 2008-10-11
Yo recién puse esto:
```
cd '/media/WinXP/Archivos de programa'
```
y me lo tomó sin problemas.

---

### Post by sartrejp on 2008-10-11
Volví a probar pero no hay caso

No se en que le estoy errando


Volví a probar, no sabía de la comilla simple, ahora sí.
Gracias

---

### Post by santiagoward2000 on 2008-10-11
> **sartrejp said:**
> Volví a probar, no sabía de la comilla simple, ahora sí.
Gracias

De nada! :)

---

### Post by faktorqm on 2008-10-11
Esto ya lo explique en otro thread, si queres buscalo. (caracteres de escape)
Deberias escribir cd /blablabla/Archiv<TAB> (tecla TAB) y te autocompleta el comando y te va a aparecer algo asi:

```
cd /hola/chau/Archivos\ de\ prorama/
```

esas barras invertidas se llaman caracteres de escape. Apretar la tecla tab te autocompleta el comando o un archivo o una carpeta en cualquier ubicacion que pongas. Esto igual es solo cuando BASH es la consola (caso de ubuntu) cuando por ejemplo en otros gnu/linux's usas ksh, esas funciones no estan. Salu2!

---

### Post by sartrejp on 2008-10-11
Interesante para tenerlo encuenta, porque estoy probando otras distribuciones en Virtualbox.
Gracias

---

