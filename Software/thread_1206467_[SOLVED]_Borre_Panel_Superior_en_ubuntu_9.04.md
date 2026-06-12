---
title: "[SOLVED] Borre Panel Superior en ubuntu 9.04"
date: 2009-07-07
forum: Software
---

### Post by jpoeta on 2009-07-07
Hola Amigos de Loco Team Argentina, 

de casualidad borre el panel superior en ubuntu y quisiera recuperarlo 

con el comando 

sudo gnome-panel 

aparece de nuevo pero solo mientras estoy como root 

quisiera recuperar mi panel Gracias de antemano:guitar:

Jpoeta

---

### Post by Hei Ku on 2009-07-07
Probá sin el sudo.

---

### Post by ramiro_md on 2009-07-07
Dale botón derrecho al panel inferior (si todavía lo tenés xD), "añadir nuevo panel" y le dás orientación superior.

---

### Post by jpoeta on 2009-07-08
Sin Sudo me dice esto:

jpoeta@jpoeta-laptop:~$ gnome-panel
Cannot register the panel shell: there is already one running.

No quiero uno nuevo quiero recuperar el por defecto

Gracias 

Jpoeta;)

---

### Post by jpoeta on 2009-07-09
Ayudaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa:(:(:(:(:(:(:(:(

---

### Post by Hei Ku on 2009-07-09
Probaste dandole click-derecho al panel inferior?

---

### Post by jpoeta on 2009-07-10
Si pero no es lo mismo que el antiguo que tenia los programas activos mi configuración de red configuración  de compiz, etc
Y le añadí todo lo que podí pero igual no es lo mismo:(

---

### Post by totolinux on 2009-07-10
Hola fijate si te funciona esto yo no lo use nunca uso kde

[https://answers.launchpad.net/ubuntu/+source/yelp/+question/37203](https://answers.launchpad.net/ubuntu/+source/yelp/+question/37203)

otra solución mas radical (no se que opinan los demas ) no creo que se justifique...
tendras que hacer un usuario nuevo y de esta manera te encontraras con un sistema con la configuración original. luego tendras que recuperar tus datos del anterior usuario.
Saludos y paciencia siempre alguien ayuda..

---

### Post by jpoeta on 2009-07-11
Solucione mi problema y aqui les dejo como por si a alguien le pasa :guitar:

Primero vamos al Terminal

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

Eso nos dejara sin paneles 

Luego nos vamos a la consola ctrl alt f5 p(ara volver al modo grafico luego alt f7)

En la consola nos logeamos 

y luego escribimos

sudo apt-get install gnome-panel gnome-panel-data

volvemos al modo grafico 

y reiniciamos

Luego tendremos nuevamente nuestros antiguos paneles de nuestro amado Ubuntu:p

Jpoeta:guitar:

---

