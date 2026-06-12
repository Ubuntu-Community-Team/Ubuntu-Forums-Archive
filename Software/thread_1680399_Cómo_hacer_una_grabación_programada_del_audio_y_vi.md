---
title: "Cómo hacer una grabación programada del audio y video de la pc"
date: 2011-02-02
forum: Software
---

### Post by martin cocco on 2011-02-02
Hola, qué tal. Estoy con un problema. Tengo que hacer un viaje este sábado y necesito grabar una conferencia virtual desde mi pc, mientras yo no estoy.
La pregunta es si saben como hacer para programar la pc para grabar a determinada hora y finalizar la grabación también a determinada hora.

Hasta ahora: probé dos programas, recordmydesktop y xvidcap screen capture, pero en ambos casos no pude grabar sonido. De todas maneras me faltaría saber cómo hacer para programarlos.

Muchas gracias de antemano.
Saludos,
Martín

---

### Post by granjero on 2011-02-02
para programarlos podes hacer un script que grabe ya sea con recordmydesktop o lo que elijas y después agregalo al crontab para que se ejecute cuando vos necesites.


hace unos días mama21mama postió un script de su autoría para grabar el escritorio.

fijate acá

[http://ubuntuforums.org/showthread.php?t=1673192](http://ubuntuforums.org/showthread.php?t=1673192)

salud!

---

### Post by EnriqueK on 2011-02-03
Para programar  recomiendo el "alarm-clock". lo que no ae es en que formato está el sonido, ssupongo que será un streaming y suponiendo que pueda reproducirse por mplayer, podés usar el siguiente comando 
**mplayer -dumpstream url**
Por ejemplo si qoerés grabar Radio del Plata, ponés
mplayer -dumpstream mms://delplata.telecomdatacenter.com.ar/delplata

Para parar la grabación, ponés
**killall mplayer**
a ambos comandos los ponés em el **alarm-clock**

---

