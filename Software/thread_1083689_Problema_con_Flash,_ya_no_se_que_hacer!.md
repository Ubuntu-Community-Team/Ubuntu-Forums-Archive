---
title: "Problema con Flash, ya no se que hacer!"
date: 2009-03-01
forum: Software
---

### Post by chipakero on 2009-03-01
Buenas que tal!, les paso a comentar mi problema, soy nuevecito en todo este gran mundo de ubuntu. 

Lo instale hace poco, instale varios programas y que se yo. Pero tengo un GRAN problema a la hora de ver videos online desde CUALQUIER pagina.

Ya instale todo lo que se me cruzo a la vista y sigue sin andar, se me traba la pagina y tengo que reiniciar firefox cada vez que intento ver algun video.

Tengo instalado ya:

ubuntu-restricted-extras
flashplugin-non free
Tengo tb ya el flash 9 y el 10 (no se porque ambos, me fije en firefox mediante about:plugins)
Actualize el flash desde repositorios.

Bueno en fin, ya no se que mas puedo hacer, espero puedan ayudarme. muchas gracias desde ya, saludos!

---

### Post by staar on 2009-03-01
bueno, primero te aviso que el plugin de flash para linux siempre fue un asco, esta lleno de bugs, y funciona como quiere, a veces bien, otras mal, pero con las ultimas versiones la cosa esta mejorando...

el problema debe estar pasando por el hecho de que tenes varios flash instalados :-P, proba desinstalando todos menos el que tenga la ultima version

saludos

---

### Post by chipakero on 2009-03-01
Bien, buenisimo... Ahora... como hago para desinstalar todo? :)

Soy nuevo en esto y no entiendo mucho.

Gracias saludos!

---

### Post by staar on 2009-03-01
la forma mas facil es:

-abri synaptic
-click en buscar (no busqueda rápida, no es lo mismo)
-busca 'flash'
-marca para _remover completamente_ todos los paquetes que hayas instalado, menos el que tenga version 10.0.22.87...
-si el problema sigue seguramente es porque hay alguno instalado de manera 'no convencional' :-P, en ese caso vas a tener que borrarlos a mano (fijate donde estan instalados con el about plugins de firefox, aunque generalmente se instalan en /usr/lib/firefox, /usr/lib
/mozilla, o /usr/lib/flashplugin)

saludos

---

