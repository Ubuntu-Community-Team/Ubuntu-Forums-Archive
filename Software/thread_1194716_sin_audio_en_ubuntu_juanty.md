---
title: "sin audio en ubuntu juanty"
date: 2009-06-23
forum: Software
---

### Post by -Wzzrd- on 2009-06-23
Hola muchachos estoy sin audio en ubuntu juanty, despues de actualizar el mismo ubuntu juanty9.04 me kede sin sonido y el dia anterior me vi una peli sin problemas, espero y me puedan ayudar, revise con el alsamixer y nada estan todos los controles al max, los reproductores funcionan pero no sale audio, esto es reproduccion de audio y video, solo falla la salida del audio, Salu2 WzzrD

---

### Post by moreback on 2009-06-23
No podemos ayudar mucho si no das detalles del hardware que estás usando.

---

### Post by Carlos C on 2009-06-24
Para tener una mejor idea de tu hardware, por favor escribe en el terminal:
```
lspci
```
y publica acá lo que te salga.

Saludos.

---

### Post by kamus on 2009-06-24
> **-Wzzrd- said:**
> Hola muchachos estoy sin audio en ubuntu juanty, despues de actualizar el mismo ubuntu juanty9.04 me kede sin sonido y el dia anterior me vi una peli sin problemas, espero y me puedan ayudar, revise con el alsamixer y nada estan todos los controles al max, los reproductores funcionan pero no sale audio, esto es reproduccion de audio y video, solo falla la salida del audio, Salu2 WzzrD

Por casualidad tienes en tu equipo dual boot (windows - linux) ?  Me paso algo parecido el otro dia y tuve que entrar a windows, luego reiniciar y entrar nuevamente a Linux y ahi funciono :/

---

### Post by crufio62 on 2009-08-06
A mi me pasó lo mismo
Seguramente se debe a que se te ha añadido una nueva versión del kernel (kernel .14) y ésta no es compatible con tu sistema.

Prueba de cargar la segunda configuración que te aparece en los módulos de arranque (kernel.13) y casi seguro que te funciona sin problemas

---

