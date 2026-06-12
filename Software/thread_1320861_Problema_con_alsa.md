---
title: "Problema con alsa"
date: 2009-11-09
forum: Software
---

### Post by oscarenzo on 2009-11-09
Hola a todos,

Les planteo mi problema a ver si alguien me puede echar un cable, por favor.

Tengo un portatil con las siguientes caracteristicas.

amd athlon de 64 bits
tarjeta ati
disco de 256 GB
y tarjeta de audio intel

y tengo instalado ubuntu de 32 bits, el so no me da problemas todo va genial, pero cuando abro por ejemplo, el virtualbox, usando alsa, luego si quiero usar exaile pa escuchar musica, este no tira, osea es o uno o lo otro, pero no puedo, lo mismo me pasa con el skype, mientras estoy con la maquina virtual no puedo reproducir audio en la principal, alguien me puede echar un cable en esto.

Gracias de antemano.

---

### Post by josecuervo86 on 2009-11-09
Te hago una consulta, tenes configurado VirtualBox para que use ALSA? Es esencial habilitar los sonidos en la Maquina Virtual o es puramente accesorio? Si no es esencial podes probar deshabilitando la salida de sonido en la Virtual Machine y fijarte si asi anda

---

### Post by oscarenzo on 2009-11-09
Gracias por tu respuesta, josecuervo86, si estaba habilitado con alsa, pero creo que lo he solucionado e instalar el driver alsa en su ultima version, e reiniciado, y ahora me va bien, bueno cuando uso el alsa en el virtualbox, y estoy escuchando musica el winxp se me lentea un poco, pero le he cambiado a que use pulseaudio ( ahora si bota sonido ), y ya esta todo bien, gracias josecuervo86.

Un abrazo.

---

### Post by josecuervo86 on 2009-11-09
De nada! Suerte!

Saludos

---

### Post by oscarenzo on 2009-11-09
Gracias tio, hasta otra. ):P

---

