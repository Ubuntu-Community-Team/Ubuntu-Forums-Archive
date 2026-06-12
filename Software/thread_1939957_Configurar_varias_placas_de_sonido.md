---
title: "Configurar varias placas de sonido"
date: 2012-03-12
forum: Software
---

### Post by anarko on 2012-03-12
Les cuento... me compre una Kworld UB430-AF que aqui entre nos. anda 10 puntos como receptor ISDB-T pero el dongle tambien hace de receptor de TV y radio analogicos. El receptor digital funciona 10 puntos out off the box. 

Mi problema es el siguiente : Este coso me crea ademas de los devices DVB y video0 y radio0 uno de entrada de audio para la parte analogica que hace las veces "entrada" por lo que me figura en la lista de hardware de sonido en el pulse como un input. La cosa es que no puedo hacer que el sonido que "entra" por ese dispositivo sea reproducido por alguna de las 2 placas de sonido que tengo ( HDA intel dejada de lado en linux hasta que la hagan andar bien y una siempre eficiente SB-Live que anda 10 puntos ). Probe seleccionar como entrada el dispositivo USB y como salida la SB pero no pasa nada, incluso el input de la HDA el mic anda y se ve en el monitor de sonidos del pulse "algo" cuando golpeo el microfono. Intente hacerlo con jackd pero ese coso me supera ampliamente, hay alguna forma de hacer lo que quiero. Osea redirigir el input de una placa al output de otra. 

Desde ya muchas gracias. 

PD : Kworld UB430-AF RECOMENDADA para ISBD-T salvo que la quieran hacer andar en una netbook, los canales SD andan 10 puntos pero en los HD el VLC acusa "processor too slow" a la hora de reproducir. En ubuntu anda out of the box y en debian solo hay que bajar el firmware correspondiente o "robarse" el que esta en ubuntu :p

---

