---
title: "error dpkg --configure -a"
date: 2009-01-10
forum: Software
---

### Post by yavoyya on 2009-01-10
ojalá puedan ayudarme...

gente, ni bien instale ubuntu 8.10 lo primero que hice fue actualizar el os desde un ícono que me aparecía en la barra de tareas que era como una flecha de color rojo que decía que habían 223 actulizaciones disponibles... bueno las bajé y las instaló bien...
reinicié y me puse a seguir los pasos que detallan más arriba


"Cosas a hacer despues de instalar ubuntu 8.10 (Intrepid Ibex)"
**[http://ubuntulife.wordpress.com/2008/11/03/cosas-a-hacer-despues-de-instalar-ubuntu-810-intrepid-ibex/](http://ubuntulife.wordpress.com/2008/11/03/cosas-a-hacer-despues-de-instalar-ubuntu-810-intrepid-ibex/)**


bueno, con los dos primeros pasos
* Instalar software mas rapidamente.
* Instalar el software basico de compilacion

para cuando llegué al tercero:
* Instalar los extra restrictivos.

no tuve problemas para bajar los paquetes, el tema es cuando empezó a instalar...
el proceso llegó hasta la actualización del java y ahí quedó parado un tiempo y como pensé que se había colgado reinicié la máquina...
para cuando volví a entrar a la consola para repetir el comando de instalación de los extras restrictivos me dá este error:
**E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.**



y después de esto cuando quiero ingresar al gestor de paquetes synaptic me dá este otro error:

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.[/B]

y se cierra el prog...

y cuando ingreso "**dpkg --configure -a**" en una terminal nueva me dice
"**dpkg: la operación solicitada precisa privilegios de superusuario**"

alguien puede darme una mano para solucionar esto? la verdad soy nuevo y por lo poco que leí no tengo la más mínima idea de qué pasó...

espero que puedan ayudarme...
muchas gracias

---

### Post by santiagoward2000 on 2009-01-11
> **yavoyya said:**
> y cuando ingreso "**dpkg --configure -a**" en una terminal nueva me dice
"**dpkg: la operación solicitada precisa privilegios de superusuario**"

Hola!
Mirá, para poder usar ese tipo de comandos que necesitan privilegios, tenés que agregar **sudo** adelante. Entonces sería:
```
sudo dpkg --configure -a
```
te pide tu contraseña y con eso tendría que andar.
Suerte!

---

