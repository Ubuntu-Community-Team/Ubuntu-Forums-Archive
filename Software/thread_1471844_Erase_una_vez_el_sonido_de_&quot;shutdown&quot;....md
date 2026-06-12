---
title: "Erase una vez el sonido de &quot;shutdown&quot;..."
date: 2010-05-03
forum: Software
---

### Post by atari130xe on 2010-05-03
¿Alguien sabe en que anda el "fix" del bug que viene arrastrando Ubuntu desde hace un par de versiones? Una vez leí cosa de uno o dos años atrás cuando apareció junto con PulseAudio que los desarrolladores dijeron que era un "tema irrelevante" ahora digo yo, si uno hace algo y lo entrega incompleto, no les parece que algo está mal? estuve chusmeando sobre el bug: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-sounds/+bug/61530]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-sounds/+bug/61530") y tmb sobre este otro: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/214370]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/214370") que seguimos como recién llegados del viejo mundo... :(

---

### Post by guillermolisi on 2010-05-03
> **atari130xe said:**
> ¿Alguien sabe en que anda el "fix" del bug que viene arrastrando Ubuntu desde hace un par de versiones? Una vez leí cosa de uno o dos años atrás cuando apareció junto con PulseAudio que los desarrolladores dijeron que era un "tema irrelevante" ahora digo yo, si uno hace algo y lo entrega incompleto, no les parece que algo está mal? estuve chusmeando sobre el bug: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-sounds/+bug/61530](https://bugs.launchpad.net/ubuntu/+source/ubuntu-sounds/+bug/61530) y tmb sobre este otro: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/214370](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/214370) que seguimos como recién llegados del viejo mundo... :(
Venias bien hasta que hiciste la pregunta.

Si queres saber si alguien sabe algo del fix sobre ese bug, el resto sobra salvo que tengas participacion activa en la solucion o sepas como arreglarlo. Mientras eso no ocurra, podes quejarte pero no aportara nada positivo a la solucion, sera parte del problema.

Reportaste el problema oportunamente ? Si no lo hiciste, lo harias ahora ? Eso si seria ser parte de la solucion porque uno de los factores que influyen en la prioridad que le asignan a los bugfixes es la cantidad de casos reportados y la falta de solucion alternativa temporal.

Recuerden que la gente que esta solucionando los bugs lo hace de buena voluntad, si alguno esta arancelado el que paga es otro, que esa gente sabe y mucho sobre lo que hace, que tambien se pueden equivocar y que gracias a ellos nosotros podemos disfrutar de lo bueno y lo malo de Ubuntu, sin mayor costo que nuestro tiempo y dedicacion como simples usuarios, entusiastas, techies, nerds, developers o geeks.

---

### Post by atari130xe on 2010-05-03
Ey Guillermo, entiendo tu punto, pero lo que me parece poco "lógico" más allá de que quien haga este tipo de cosas puede hacerlas "ad honorem" es que diga: bueno no es importante o es irrelevante. Yo no critico por criticar y el bug ya tiene muchos reportes. No importa si lo solucionan ahora o en 5 años el tema es que digan semejante cosa me entendés? si dependiera de mi, ya hubiera aportado la solución, pero soy de "a pié" y como usuario tengo todo el derecho de dar mi opinion. :)
Cabe aclarar que no "ataco" a nadie de ubuntu solo me molestó enormente que digan eso, no es una respuesta a un problema a resolver, simple como eso.

---

### Post by juancarlospaco on 2010-05-04
*No entendi..., se puede poner un sonido de shutdown, y anda...*
:s

---

### Post by alfplayer on 2010-05-04
Ubuntu no es el Mac OS X de las MacBook. Si tienen que elegir, me gustaría que los desarrolladores se concentren en bugs críticos.

---

### Post by atari130xe on 2010-05-05
Tendría que ver si funciona en otras distros como PCLinuxOS o Mepis, voy a chequear unas ISO's que bajé en estos días y les cuento.

---

### Post by atari130xe on 2010-05-05
Bueno dicen que el que busca "encuentra", y yo encontré ;) conseguí agregar el shutwdown (log off) sound a Ubuntu Lucid Lynx:

Abrir una consola y ejecutar lo siguiente:

```
sudo gedit /etc/gdm/PostSession/Default

``` (escribir tu contraseña)

luego:
agregar estas lineas 
```
/usr/share/gnome/shutdown/libcanberra-logout-sound.sh

``` antes de "exit 0"

Les quedaría asi:
```
#!/bin/sh
/usr/share/gnome/shutdown/libcanberra-logout-sound.sh
exit 0
```

cerrar y voilá! el sonido aparece como debe ser.

Probado cerrando sesión y reiniciando la máquina y funciona perfecto.

espero les sirva.

Solución brindada en este thread: [http://ubuntuforums.org/archive/index.php/t-789858.html]("http://ubuntuforums.org/archive/index.php/t-789858.html")

---

