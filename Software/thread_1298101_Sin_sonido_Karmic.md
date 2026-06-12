---
title: "Sin sonido Karmic"
date: 2009-10-22
forum: Software
---

### Post by kito0 on 2009-10-22
Hola gente:

Bueno así es la cosa... instalé karmic hace un par de días y hoy se actualizó, a otra versión supongo porque no me fijé bien si hubo algún cambio ahí... bueno, la cosa es que no tengo sonido... reinicié y apague y encendí varias veces el equipo y no suena nada de nada. Lo peor de todo es que no me arroja ni un error como pa hacerme una idea de que está pasando.

Agradecería mucho su ayuda porque me gusta mucho la musica y la pega no es lo mismo en un silencio sepulcral.

---

### Post by kronstadt on 2010-01-18
> **kito0 said:**
> Hola gente:

Bueno así es la cosa... instalé karmic hace un par de días y hoy se actualizó, a otra versión supongo porque no me fijé bien si hubo algún cambio ahí... bueno, la cosa es que no tengo sonido... reinicié y apague y encendí varias veces el equipo y no suena nada de nada. Lo peor de todo es que no me arroja ni un error como pa hacerme una idea de que está pasando.

Agradecería mucho su ayuda porque me gusta mucho la musica y la pega no es lo mismo en un silencio sepulcral.


Lo mismo, hace una semana instalé karmic,actualicé hace un par de dias, y hoy ya no tengo sonido, cualquier cosa agardeceria alguna ayuda, gracias!:D

---

### Post by Carlos C on 2010-01-18
Parte por verificar lo básico, en el terminal escribe "alsamixer" y revisa que el volumen no esté al mínimo. Lo otro que puedes hacer es reiniciar la configuración de tu tarjeta:
```
alsactl init
```
Saludos.

---

