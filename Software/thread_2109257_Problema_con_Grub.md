---
title: "Problema con Grub"
date: 2013-01-27
forum: Software
---

### Post by yairdaniel on 2013-01-27
Tengo una netbook Positivo BGH, de las que reparte el Conectar Igualdad, es decir que viene con Windows 7 y con Ubuntu. Linux me ofreció actualizar a la última versión (12 y pico, no anoté cuál). Una vez que termina el proceso de descarga e instalación de los archivos, me pide que reinicie el equipo. Cuando lo hago, me aparece una pantalla celeste con la leyenda "Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions...". Se clava ahí y no me permite, tampoco, iniciar windows.

Es la primera vez que me manejo con Linux, así que les agradecería su ayuda. No quisiera perder lo que tengo instalado de Windows. Muchas gracias!

---

### Post by gmunioz on 2013-01-31
Inicia con un live-cd/dvd/usb, abre una terminal y ejecuta

> sudo su
fdisk -l
Copia y pega la salida en el post.
Esto es para saber como está particionado tu disco
y si Ubuntu está instalado separado o dentro de Windows

---

