---
title: "Ctrl+Tab+back space No responde"
date: 2009-04-28
forum: Software
---

### Post by prostata on 2009-04-28
Compañeros, he instalado recien  la Jaunty, pero mi sorpresa es que la combinación de teclas Ctrl-+Alt-Back Space no surte ningún efecto.

Tengo una AMD 2.8 Gh suficiente disco y una gráfica Nvidia GeForce 6200.

La instalación la he hecho en limpio, recien termino ahora  estoy probando si todo va "normal" y a lo que veo ahí tengo un problema. Estan activados los controladores restringidos de la tarjeta, de modo que ahora no se que puedo hacer para solucionar esta situación...

Saludos

---

### Post by pol666 on 2009-04-28
lo desactivaron por defecto.
Google me dijo [que...]("http://ubuntulife.wordpress.com/2009/04/15/activar-ctrlaltbackspace-en-ubuntu-jaunty-jackalope/")

dicen que sirve tambien un Alt Gr + Imp Pant + K

---

### Post by lindsay7 on 2009-04-28
La programa "dontzap" es en el Synaptic Package Manager tambien.

Command en el terminal es    sudo dontzap -d

password

despues, reboot

---

### Post by clasificado on 2009-04-28
Al final se usaba un montón :P

he visto que también te tira una linea en el xorg.conf para dontzap.

clasificado

---

### Post by prostata on 2009-04-28
> **lindsay7 said:**
> La programa "dontzap" es en el Synaptic Package Manager tambien.

Command en el terminal es    sudo dontzap -d

password

despues, reboot

gracias por tu respuesta, encontré la solución en:

[http://electrobuntu.blogspot.com/](http://electrobuntu.blogspot.com/)

merece la pena visitarlo

Saludos

---

### Post by lindsay7 on 2009-05-06
.

---

