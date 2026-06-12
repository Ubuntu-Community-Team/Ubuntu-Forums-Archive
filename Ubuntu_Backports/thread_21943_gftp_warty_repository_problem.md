---
title: "gftp warty repository problem"
date: 2005-03-24
forum: Ubuntu Backports
---

### Post by fabiang on 2005-03-24
Hi,

my /etc/apt/sources.list
> 
#seguridad
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted


#repositorios normales:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty-updates main restricted universe multiverse

#repositorios de xfce4.2
#deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main
#deb-src [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main

#proyecto backports
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-extras main universe multiverse restricted
 



> 
fabian@xlyon:/etc/apt $ apt-get intall gftp
E: Operación inválida: intall
fabian@xlyon:/etc/apt $ sudo apt-get install gftp
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.

Como sólo solicito una única operación, es extremadamente posible que el
paquete simplemente no sea instalable y debería de rellenar un informe de
error contra ese paquete.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  gftp: Depende: gftp-gtk (= 2.0.17-6) pero 2.0.17-6ubuntu0.2 va a ser instalado        Depende: gftp-text (= 2.0.17-6) pero no va a instalarse
E: Paquetes rotos




i feel somebody was updated gftp-gtk but dont updated gftp package.

---

### Post by jdong on 2005-03-24
I don't think I've made a gftp backport at all! Umm, are you *sure* this is caused by backports?

---

### Post by fabiang on 2005-03-25
i think it's not a backport repository problem, i feel it's a ubuntu official repository, but we in backports can fix it.

---

