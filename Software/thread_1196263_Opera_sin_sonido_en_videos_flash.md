---
title: "Opera sin sonido en videos flash"
date: 2009-06-24
forum: Software
---

### Post by aregnando on 2009-06-24
Hola a todos, desde hace unos días estoy usando Opera como navegador principal pero me encontré con que no reproduce el sonido en los videos como por ejemplo en youtube, cosa que según recuerdo hace un tiempo atrás, antes de actualizar a Intrepid si hacía.
Como dato en Firefox el audio sale normal así que no se que pueda ser.
Si tienen alguna idea la voy a agradecer.
Saludos.
Disculpen por postear en el general, muevanlo al que corresponda.

---

### Post by aregnando on 2009-06-27
Bueno, viendo que no desperto mucho interes el tema planteado empeze a darle vueltas al asunto así que pude resolverlo.
El problema radicaba a mi parecer en que Opera estaba usando un plugin anterior de Adobe Flash versión 9 y ya tenía instalada la versión 10 y no la reconocía, lo único que hice fue reemplazar el archivo libflashplayer.so ubicado en /usr/lib/opera/plugins por el mismo archivo ubicado en /usr/lib/flash-plugin, creo que con esto cambie la versión del plugin que estaba utilizando Opera por el más nuevo.
Lamento que el tema no haya sido de interés como para poder darme una mano, en general solo pido ayuda cuando luego de buscar no encuentro soluciones.
Saludos a todos.

---

### Post by alfplayer on 2009-06-27
Seguramente hubo interés, lo que no hubo fue una solución. Un saludo a vos.

---

### Post by anarko on 2009-06-30
Ami me pasaba algo parecido, yo tengo 2 placas de sonido la onboard y una sound blaster ( que uso pa los jueguitos en windows, todo original por si se preguntan ), el tema es que el sonido salia en algunos programas por un lado y en otros por otro lado, la solucion que encontre yo fue instalar todos los "mixers" del pulseaudio hasta que encontre uno muy interesante que permite decidir que programa manda sonido por que device.
Espero que te sirva.

---

### Post by aregnando on 2009-06-30
Gracias Anarko, ya lo resolví con el tema del plugin copiandolo como dije más arriba, tendría que haberle puesto solved a este thread pero no se como se pone.
Gracias nuevamente.

---

### Post by faktorqm on 2009-06-30
Hola, yo uso opera como navegador principal por que me parece es uno de los mas rapidos y completos. Uso ubuntu 8.04 y el plugin del flashplayer se actualiza automaticamente cuando hay una actualizacion de repositorio. ¿A vos no?

Un truco que usaba antes yo, era hacer un enlace simbolico al mismo archivo pero que esta en la parte de plugings de firefox, entonces cuando se me actualizaba por repo el opera lo hacia tambien por que a actualizacion "automatica" por decirlo de alguna manera actualiza solo el firefox. Si queres mas info sobre esto, pregunta. Digo antes por que desde 8.04 lo hace solo. Fijate de hacer "ls -la /usr/lib/opera/plugins" y postea a ver que te dice. Igual ahora ya no se si lo va a mostrar por que lo pisaste con la nueva version xD pero vemos. Salu2!

---

### Post by staar on 2009-06-30
también uso Opera como navegador principal, y siempre que lo instalé (a través de debs, no de repos), utilizó el path /usr/lib/mozilla/plugins (al menos como secundario, pero lo incluyó) para buscar plugins, igual eso es totalmente modificable desde Herramientas > Opciones > Avanzado > Contenido > Opciones de conectores

saludos

---

### Post by aregnando on 2009-07-01
Hola Faktorqm, hasta el 8.04 utilizé alternativamente FF y Opera y los dos funcionaban sin problemas, cuando actualizé a 8.10 por algún motivo que no tengo presente dejé de utilizar Opera y no se si ahí fue que no me actualizó el plugin, luego actualizé a 9.04 y hace poco como veia que FF andaba un poco lento le quise dar una gran oportunidad a Opera en pasar a ser el navegador por defecto pero me encontré con ese tema que describí.
Resolví el problema copiando el libflashplayer.so tal como contaba en un post anterior, no se si es la mejor manera, fue la que se me ocurrió observando un poco los listados de plugins de Opera y viendo por algún lado que el que estaba en uso no era el mismo que utilizaba FF, no se si fui claro.
Acá está lo que me devuelve "ls -la /usr/lib/opera/plugins":

aldo@ANRH:~$ ls -la /usr/lib/opera/plugins
total 9920
drwxr-xr-x 2 root root     4096 2009-06-27 17:21 .
drwxr-xr-x 3 root root     4096 2009-06-24 19:29 ..
-rwxr-xr-x 1 root root 10131640 2009-02-03 00:06 libflashplayer.so
aldo@ANRH:~$ 

De paso te cuento que estoy usando Opera 10 y la verdad  que es un avión, me encanta la interface y la velocidad con que trabaja.

Staar, el opera lo instalé segun recuerdo desde deb ya desde la primera vez, esta versión también la instalé con el deb desinstalando previamente el Opera 9.65 y tal como vos decís viendo la lista de plugins figura un path a "/usr/lib/mozilla/plugins/flashplugin-alternative.so" no se si lo estaba tomando bien pero el tema es que en FF funcionaba todo bien y en Opera no reproducía el sonido.
En fin por el momento está funcionando bien no se cuando se produzca alguna actualización de Shochwave flash que pueda pasar.

Saludos y gracias por sus consejos.

---

