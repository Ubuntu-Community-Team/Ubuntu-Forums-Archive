---
title: "Beep en tarjeta madre"
date: 2009-09-06
forum: Software
---

### Post by Grasber on 2009-09-06
Hola, cada vez que apago el pc suena un beep en la tarjeta madre. Esto no pasa con Windows así que no es problema de hardware. ¿Qué estará pasando?

(estoy usando Ubuntu 9.04)

---

### Post by CdK1 on 2009-09-07
Desactiva el modulo del pcspeaker;

sudo modprobe -r pcspkr

Luego, para que sea permanente;

sudo gedit /etc/modprobe.d/blacklist

Y le agregas;  blacklist pcspkr

Listo...

---

### Post by Grasber on 2009-09-07
Gracias, funcionó perfecto. No entiendo cómo uno puede aprenderse tantos comandos.. y tan rebuscados xD.

---

### Post by robertor on 2009-09-08
> **Grasber said:**
> Gracias, funcionó perfecto. No entiendo cómo uno puede aprenderse tantos comandos.. y tan rebuscados xD.

Jejejeje... no son tantos comandos ni tampoco tan rebuscados. Ademas, es lo mismo que aprenderse unos cuantos pasos para llegar alguna parte con los clicks. Yo a veces me pierdo con tanto click (y no es chiste).
saludos!

---

