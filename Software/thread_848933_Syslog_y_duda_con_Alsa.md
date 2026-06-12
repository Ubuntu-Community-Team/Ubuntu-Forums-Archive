---
title: "Syslog y duda con Alsa"
date: 2008-07-04
forum: Software
---

### Post by EnriqueK on 2008-07-04
Se me dio por revisar los logs que genera el sistema , abro syslog mediante  gedit /var/log/syslog y fuera de que no entiendo nada de lo que muestra, me llamó la atención la siguiente linea.
Jul  3 21:29:53 enrique-desktop pulseaudio[5686]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Lo que no entiendo es por que no soporta la frecuencia de sampleo mas común que es precisamente la de 44100 Hz , podría por ejemplo generar un mp3 que no pueda ser reproducido en un equipo de audio, a lo mejor opino cualquier verdura, no se , por eso pregunto.

---

### Post by Hei Ku on 2008-07-04
la decodificacion y transformacion para escuchar por los parlantes es independiente de la grabacion y codificacion, asi que en principio no deberias tener ningun problema.

O sea, para darte una idea, podrias convertir un CD de audio a un mp3 sin necesidad de tener placa de sonido.

---

### Post by pendortxo on 2008-08-10
Bueno a mi me tira exactamente ese error como podria hacer para arreglarlo y que no aparesca mas?

 Tambien tengo el siguiente error y este aparece en cantidad

Aug 10 12:01:03 Sasuke kernel: [ 1220.271526] ACPI: Invalid passive threshold

gracias

---

### Post by faktorqm on 2008-08-11
Tienen compus marca HP? Estuve mirando y es un error en la implementacion del ACPI 2.0 en determinados bios de compus de marca HP... vista tambien lo tiene, pero sacaron un (otro y van...) parche q lo soluciona.
El problema es que HP quizo manejar las tamperaturas  de los dispositivos de la compu, pero hay una que devuelve 0 grados kelvin, o sea, -273 grados centigrados, y entonces "detecta" que algo anda mal y se te apaga la compu de una. 
La cosa es que en gnu/linux la cosa esta un poco mas salada, vi porciones de codigo parcheadas en el "thermal.c" en el codigo del kernel, pero van a tener que parchear el .c, y recompilar el kernel. (en realidad no estoy muy seguro de esto, quiza si parchean el .c ya esta)

[http://bugzilla.kernel.org/show_bug.cgi?id=8333](http://bugzilla.kernel.org/show_bug.cgi?id=8333)
[http://readlist.com/lists/vger.kernel.org/linux-kernel/87/437886.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/87/437886.html)
[http://lkml.org/lkml/2008/7/24/286](http://lkml.org/lkml/2008/7/24/286)

implementacion entera en c para manejo de acpi, no se que tiene que ver, pero me gusto :P: [http://www.gelato.unsw.edu.au/lxr/source/drivers/acpi/thermal.c](http://www.gelato.unsw.edu.au/lxr/source/drivers/acpi/thermal.c)

se me ocurrio algo: que version de kernel tienen? por que capaz no prueban una nueva? capaz ya lo corrigieron el bug... salu2!

---

### Post by pendortxo on 2008-08-11
lo de actualizar ya lo intente y sigue igual. ahora me voy a poner a leer eso a ver si puedo sacar algo que me ayude a arreglar eso.

gracias.

---

