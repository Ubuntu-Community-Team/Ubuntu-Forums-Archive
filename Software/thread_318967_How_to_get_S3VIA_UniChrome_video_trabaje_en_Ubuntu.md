---
title: "How to get S3/VIA UniChrome video trabaje en Ubuntu"
date: 2006-12-14
forum: Software
---

### Post by jpoeta on 2006-12-14
Yo tengo S3 UniChrome" graphics video en mi placa PCChips y estuve como loco por que los driver de video no eran reconocidos en EDGY. Hasta que un buen amigo del foro me ayudo pero no todos saben inglés y tal vez este HOW TO les sea util.

Es Sencillo abrimos el terminal 

> sudo apt-get install subversion build-essential automake1.9 libtool pkg-config xserver-xorg-dev libxvmc-dev x11proto-gl-dev libglu1-mesa-dev x11proto-core-dev libxvmc-dev xserver-xorg-dev x11proto-gl-dev libgl1-mesa-dev cvs

cuando termina la instalación respectiva de los paquetes

> sudo gedit /etc/X11/xorg.conf

Y remplazamos vesa por via 

Reiniciamos y listo tenemos los Drivers de Video ;) Funcionando correctamente ahora a disfrutar del mejor sistema operativo del Planeta.

GRACIAS ARGENTINA LOCO TEAM 
GRACIAS UBUNTU;)

Funciona en EDGY y Daper. No lo probe en versiones anteriores.

---

### Post by jpoeta on 2006-12-20
ESTO NO FUnCIONA PARA KUBUNTU !!!!!!!!!!!!!!!!!!

Alguien me ayuda con el Kubuntu :confused:

---

### Post by instint on 2007-03-12
Te quiero dar las gracias por haber hecho este post, por que yo también he podido resolver mi problema de drivers, es muy útil este post. GRACIAS!!!=D>

---

### Post by felipelerena on 2007-03-12
hoy mismo alguien abrio un post con el mismo problema
[http://ubuntuforums.org/showthread.php?t=382664](http://ubuntuforums.org/showthread.php?t=382664)

---

### Post by jpmorelli on 2007-03-13
> **jpoeta said:**
> ESTO NO FUnCIONA PARA KUBUNTU !!!!!!!!!!!!!!!!!!

Alguien me ayuda con el Kubuntu :confused:

En realidad debería funcionar...porque decis que no, salvo por la aplicación gedit que tal vez no tengas instalada, y en cuyo caso deberías reemplazar por algo como kate, todo lo demás es igual, kubuntu y ubuntu tienen el mismo carozo y pulpa pero con diferente piel !, en que paso te quedas trabado ?

---

### Post by beuno on 2007-03-13
> **jpoeta said:**
> ESTO NO FUnCIONA PARA KUBUNTU !!!!!!!!!!!!!!!!!!

Alguien me ayuda con el Kubuntu :confused:

Cambiar:

```
sudo gedit /etc/X11/xorg.conf
```

por:

```
sudo kate /etc/X11/xorg.conf
```

---

### Post by arieltico on 2009-11-22
ok the gedit part when the file opens the file is blank
what do i do??

---

