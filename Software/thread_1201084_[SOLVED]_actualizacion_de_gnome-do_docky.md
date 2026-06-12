---
title: "[SOLVED] actualizacion de gnome-do docky"
date: 2009-06-30
forum: Software
---

### Post by granjero on 2009-06-30
buenas gente!

instalé gnome-do en mi flamante ubuntu 9.04

la barrita docky se comporta lindo pero la que tengo instalada tiene algunas cosas que awn me brindaba y esta no. vengo leyendo que la versión 0.8.2 va a tener mas cosas lindas.
mi duda es la siguiente: hoy salió la versión 0.8.2 yo tengo instalada la versión 0.8.1.3 como se realiza la actualización?

en algún momento me ofrecerá la misma barra de actualizarse o hay que hacer algún pase mágico ???

salud!

---

### Post by pablo.s on 2009-06-30
Si lo instalaste desde un
repositorio, cuando este
se actualice, también va
a actualizar el docky.

---

### Post by granjero on 2009-07-01
la instalé con
```

sudo aptitude install gnome-do
```

se va actualizar?

salud!

---

### Post by pablo.s on 2009-07-01
> **granjero said:**
> se va actualizar?

Si. Cuando llegue al
repositorio.
Porque la diferencia sería
que lo hubieras instalado
como paquete descargado
de un sitio con GDebi. Ahi
no hubieras tenido la
actualización a menos que
la descargaras.

---

### Post by granjero on 2009-07-01
ok. entonces me armo de paciencia! 

muchas gracias por tu ayuda!

salud!

---

### Post by granjero on 2009-08-13
retomo el post! 

al final actualice a 0.8.2 agregando estas dos líneas al sources list

```

deb http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main 
```

y después corroborando la key con

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys (nºque está en la pag de gnome-do)
```

al final 

```
sudo apt-get install gnome-do
sudo apt-get install gnome-do-plugins
```

les cuento que me resulta muy cómodo y el skin docky me gusta más que AWN que es la barra que tenía antes.

pero retomo este post para preguntar si alguien sabe por que el weather docklet siempre muestra una luna en vez de mostrar el estado del clima?


muchas gracias!

---

