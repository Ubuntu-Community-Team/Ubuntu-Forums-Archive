---
title: "problemas de sonido ubuntu 12.04"
date: 2013-01-05
forum: Software
---

### Post by ladykaoru on 2013-01-05
Hola, soy nueva tanto en la comunidad como en el uso de Ubuntu. Tengo este problema en mi netbook hp, con tarjeta HDA Intel 92HD81B1X5, xubuntu precise 12.04, 2G de ram. Cada vez que apago la netbook y la enciendo de nuevo o la reinicio, no tengo sonido. Intenté todos los trucos y soluciones existentes en google y en un montón de foros de ubuntu, pero sigo sin solución. Instalé y desinstalé los packs de pulseaudio y alsa, por terminal, con synaptic, reinstalé y maté un montón de veces pulseaudio, e instalé de nuevo el pack de alsa, sin ningpun resultado. Hasta ahora, la única cosa que funciona es reinstalar algunos de los packs de alsa y pulse }audio por synaptic cada vez que enciendo la netbook, lo que no me garantiza que siempre funcione. A veces reinstalo, reinicio o apago 2 o 3 veces para tener sonido. Cuál podría ser el problema? O mejor, la solución?

---

### Post by eduardog2005 on 2013-01-07
Tienes instalado Ubuntu 12.04 en tu PC. No se si es la mejor solución pero muchos problemas fueron solucionados instalando Ubuntu 12.04.1 desde el inicio y luego actualizando. Si es lo que supongo el tema estaría solucionado.

---

### Post by biale on 2013-01-07
... o eventualmente probar con 12.10. Previo una googleda como para ver si alguien ha tenido esos mismos problemas.

---

### Post by guillermolisi on 2013-01-08
> **eduardog2005 said:**
> Tienes instalado Ubuntu 12.04 en tu PC. No se si es la mejor solución pero muchos problemas fueron solucionados instalando Ubuntu 12.04.1 desde el inicio y luego actualizando. Si es lo que supongo el tema estaría solucionado.

Solo para aclarar un poco este comentario: Ubuntu 12.04.1 es igual a la 12.04 pero actualizado a la fecha. Es decir que si alguien tiene instalado 12.04 con llevar a cabo una actualizacion de paquetes, que a la fecha debe rondar alrededor de los 200 o mas, obtiene la 12.04.1

---

### Post by ladykaoru on 2013-01-15
Llevo una rigurosa actualización de paquetes. Así que imagino que debo tener el 12.04.1; sino, como hago para saber la version? y de nuevo la misma pregunta, cómo hago con el tema del sonido al arrancar la netbook? Cada encendido, una reinstalación completa de los paquetes alsa... 
Y si, estuve googleando y hay en muchos casos este problema, pero lo han solucionado con determinado codigo por terminal, lo cual hice y no resultó o reisntalaron paquetes por synaptic y les resultó. Me fijé en inicio de sesion y teóricamente debería reconocer desde inicio el pulseaudio también, pero nones. Siempre me salta que tengo "salida boba" ja.
Excepto eso, adoro Ubuntu.

---

### Post by guillermolisi on 2013-01-16
> **ladykaoru said:**
> Llevo una rigurosa actualización de paquetes. Así que imagino que debo tener el 12.04.1; sino, como hago para saber la version?

```
[guille@guillenb ~]$ **lsb_release -a**
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:        12.04
Codename:       precise
```

---

### Post by guillermolisi on 2013-01-16
> **ladykaoru said:**
>  Cada encendido, una reinstalación completa de los paquetes alsa... 
Y si, estuve googleando y hay en muchos casos este problema, pero lo han solucionado con determinado codigo por terminal, lo cual hice y no resultó o reisntalaron paquetes por synaptic y les resultó. Me fijé en inicio de sesion y teóricamente debería reconocer desde inicio el pulseaudio también, pero nones. Siempre me salta que tengo "salida boba" ja.
Excepto eso, adoro Ubuntu.
Cual es ese "codigo por terminal" ?

Los niveles de volumen estan por encima de cero o todos los canales aparecen silenciados cuando inicias la maquina ? Que informacion te brinda el mixer de audio ?

---

