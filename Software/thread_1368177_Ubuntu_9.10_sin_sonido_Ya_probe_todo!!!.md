---
title: "Ubuntu 9.10 sin sonido Ya probe todo!!!"
date: 2009-12-30
forum: Software
---

### Post by sebacastro21 on 2009-12-30
Tengo el mismo problema que varios usuarios que al instalar la nueva versión de Ubuntu el sonido no funciona. El driver de la placa lo detecta paro no sale nada. Ya probé actualizando todo, desinstale e instale el pulse, vi los volúmenes de salida, configure el alsa y sigue sin salir sonido. La pc es una HP Compaq DC5800.
Bueno espero que alguien me pueda ayudar con esto porque ya he probado un millón de cosas que encontré pero nada me funciono.
Saludos

---

### Post by Sargento_Loco on 2009-12-31
Tengo el mismo problema desde que actualice a la versión 9, tengo que formatear y volver a la versión 8? que me recomiendan?
Además de eso ahora el monitor funciona solo en 800 x 600 cuando antes lo hacia en 1152 x 834 y cada vez que inicio tengo que cambiar la resolución de la pantalla y me pregunta si quiero usar el driver de la placa de vídeo cosa que antes no hacia y funcionaba a la perfección. como se solucionan estos problemas??

---

### Post by luks911 on 2009-12-31
> **sebacastro21 said:**
> Tengo el mismo problema que varios usuarios que al instalar la nueva versión de Ubuntu el sonido no funciona. El driver de la placa lo detecta paro no sale nada. Ya probé actualizando todo, desinstale e instale el pulse, vi los volúmenes de salida, configure el alsa y sigue sin salir sonido. La pc es una HP Compaq DC5800.
Bueno espero que alguien me pueda ayudar con esto porque ya he probado un millón de cosas que encontré pero nada me funciono.
Saludos

Con respecto al sonido, miren en este thread[0], en el final recomiendan 
ir a Sistema > Preferencias > Sonido y ponerlo en "ALSA PCM on front: 0 (AD198x Analog) via DMA" para que funcione la salida de auriculares. Esa opción tiene que estar en la pestaña Hardware. Como hubo algunos cambios en Karmic con respecto a versiones anteriores, lo más seguro es que funcione el sonido, pero antes tengan que jugar con las opciones de sonido, probando combinaciones en las pestañas Hardware y Salida del lugar que les señalaba. Me pasó con otra máquina y es cuestión de probar un poco.

[0] [http://ubuntuforums.org/showthread.php?t=948308](http://ubuntuforums.org/showthread.php?t=948308)

> **Sargento_Loco said:**
> Tengo el mismo problema desde que actualice a la versión 9, tengo que formatear y volver a la versión 8? que me recomiendan?
Además de eso ahora el monitor funciona solo en 800 x 600 cuando antes lo hacia en 1152 x 834 y cada vez que inicio tengo que cambiar la resolución de la pantalla y me pregunta si quiero usar el driver de la placa de vídeo cosa que antes no hacia y funcionaba a la perfección. como se solucionan estos problemas??

Lo mejor sería que abras un thread nuevo con el problema del video e incluyas el resultado del comando lspci de modo de ver que placa tiene.

Saludos

---

### Post by sebacastro21 on 2009-12-31
Muchas gracias, en realidad justo antes de leer esto lo habia podido solucionar. Lo que hice fue algo bastante pareciado a lo que vos decias, instale el alsa-gnome y desde ahi pude habilitar el front y comenzo a funcionar de maravilla. 
Saludos

---

### Post by Sargento_Loco on 2010-01-01
Entonces mi problema esta en otro lado porque cuando fui a Sistema>preferencias>sonido. solo tengo los efectos de sonidos y todo lo que es hardware esta en blanco no tengo opciones, en Entradas no me figura tampoco nada cuando tengo el micrófono conectado, y lo mismo pasa en salida ninguna opción todo esta en blanco.

---

### Post by luks911 on 2010-01-01
> **Sargento_Loco said:**
> Entonces mi problema esta en otro lado porque cuando fui a Sistema>preferencias>sonido. solo tengo los efectos de sonidos y todo lo que es hardware esta en blanco no tengo opciones, en Entradas no me figura tampoco nada cuando tengo el micrófono conectado, y lo mismo pasa en salida ninguna opción todo esta en blanco.

Mmmm... es raro porque algo debería aparecer. Si hacés click derecho sobre el ícono de volumen del panel superior y vas a Preferencias de Sonido, ¿tampoco? Si ahí tampoco hay nada, pasá el resultado del comando lspci y de los comando que aparecen en thread del link que dejé antes.

---

