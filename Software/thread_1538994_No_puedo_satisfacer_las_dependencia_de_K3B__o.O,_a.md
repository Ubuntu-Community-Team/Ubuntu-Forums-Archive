---
title: "No puedo satisfacer las dependencia de K3B  o.O, ayuda xfa"
date: 2010-07-26
forum: Software
---

### Post by zhelo on 2010-07-26
> zhelo@zhelo-laptop:~$ sudo apt-get install k3b
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  k3b: Depende: kdebase-runtime (>= 4:4.4.2) pero no va a instalarse
       Depende: kdelibs5 (>= 4:4.4.2) pero no va a instalarse
       Depende: libk3b6 (= 2.0.0-0ubuntu1~lucid2) pero no va a instalarse
       Depende: libkcddb4 (>= 4:4.2.96) pero no va a instalarse
E: Paquetes rotos
zhelo@zhelo-laptop:~$ 


eso, trate desde centro de sofware y me tira un error mas o menos parecido al que aparace en terminal
uso ubuntu 10.04 y nunca habia tenido este problema antes

me ayudan?

---

### Post by nopersona on 2010-07-31
Esa versión de K3B necesita librerías de KDE 4.4 o superior, lo tienes instalado?

Repara la lista de paquetes antes de eso sí.

---

