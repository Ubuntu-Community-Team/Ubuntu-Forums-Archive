---
title: "I HATE the Cashew"
date: 2009-05-24
forum: Software
---

### Post by emiliano_raso on 2009-05-24
Simple. Quiero sacar el iconito molesto ese de KDE 4.x que permite editar plasma, o lo que sea xD

Cuestion, starr me habia pasado esto de kde-look, pero no me funciona [http://www.kde-look.org/content/show.php/I+HATE+the+Cashew?content=91009](http://www.kde-look.org/content/show.php/I+HATE+the+Cashew?content=91009)

La lista de comandos dice:
```
tar -xjf iHateTheCashew.tbz
cd iHateTheCashew
mkdir build
cd build
ccmake ..
[setup configuration, adjust INSTALL_PREFIX, maybe check ENABLE_FINAL...]
make && sudo make install
```

Seguramente en "[setup configuration, adjust INSTALL_PREFIX, maybe check ENABLE_FINAL...]" algo hay que modificar, pero realmente no se que es.

---

### Post by Hei Ku on 2009-05-24
ehh, la linea de setup configuration no es para poner en la consola.

En realidad, pone "cmake .." en vez de "ccmake .." y despues si no te tira errores seguis con el make.

---

### Post by emiliano_raso on 2009-05-24
> **Hei Ku said:**
> ehh, la linea de setup configuration no es para poner en la consola.

En realidad, pone "cmake .." en vez de "ccmake .." y despues si no te tira errores seguis con el make.

Me parecía que algo raro habia xD
Ahi pruebo

---

### Post by emiliano_raso on 2009-05-24
Está bien. El problema no era ese.
El problema era que cuando tiro "ccmake .." me dice lo siguiente:
[http://i276.photobucket.com/albums/kk2/emiliano_raso/Screenshots/cashew.png](http://i276.photobucket.com/albums/kk2/emiliano_raso/Screenshots/cashew.png)

---

### Post by Hei Ku on 2009-05-24
tenes algun problema con los macros de kde para cmake.

---

### Post by emiliano_raso on 2009-05-24
> **Hei Ku said:**
> tenes algun problema con los macros de kde para cmake.

I como lo soluciono? xD

---

### Post by Hei Ku on 2009-05-24
Viendo el mensaje con mas detalle, en realidad me parece que el problema es en el script de compilacion. Yo lo reportaria en la pagina del programa.

---

### Post by emiliano_raso on 2009-05-24
> **Hei Ku said:**
> Viendo el mensaje con mas detalle, en realidad me parece que el problema es en el script de compilacion. Yo lo reportaria en la pagina del programa.

No encontré como solucionarlo ni como reportarlo. KDE volvió a perder mas o menos la decima oportunidad que le dí, volví a LXDE

---

### Post by staar on 2009-05-24
en los comentarios de kde-look figura que necesitas instalar kdebase-dev y kdelibs-dev para poder compilarlo en kubuntu...

saludos

---

### Post by emiliano_raso on 2009-05-24
> **staar said:**
> en los comentarios de kde-look figura que necesitas instalar kdebase-dev y kdelibs-dev para poder compilarlo en kubuntu...

saludos

Ultimo intento, gracias staar.. ahi pruebo

---

### Post by Hei Ku on 2009-05-25
El paquete en ubuntu se llama kdelibs5-dev. Mandalo a instalar y buscate un cafe, porque es grande la cosa.

---

### Post by emiliano_raso on 2009-05-25
> **Hei Ku said:**
> El paquete en ubuntu se llama kdelibs5-dev. Mandalo a instalar y buscate un cafe, porque es grande la cosa.

Ayyyy nooo!!! Instalé el 4 xDDDDDDDDDDDDDDDD
Ahi instalo el 5 xD Gracias

---

### Post by Hei Ku on 2009-05-25
Je! Caiste!

Por una cuestion de nomenclatura de Debian, los paquetes de kdelibs de KDE3, llevan el nombre kdelibs4, y los de kde4 se llaman kdelibs5. :P

---

### Post by emiliano_raso on 2009-05-25
> **Hei Ku said:**
> Je! Caiste!

Por una cuestion de nomenclatura de Debian, los paquetes de kdelibs de KDE3, llevan el nombre kdelibs4, y los de kde4 se llaman kdelibs5. :P

Y eso porque es? xD

Volviendo al tema, ahora si funciona pero... termina de configurar y ahora que hago? 
Me tira esto y no se que hacer: [http://i276.photobucket.com/albums/kk2/emiliano_raso/Screenshots/yahora.png](http://i276.photobucket.com/albums/kk2/emiliano_raso/Screenshots/yahora.png)

Soy re gallego para estas cosas

---

### Post by staar on 2009-05-25
> **Hei Ku said:**
> En realidad, pone "cmake .." en vez de "ccmake .." y despues si no te tira errores seguis con el make.

;)

---

### Post by emiliano_raso on 2009-05-25
> **staar said:**
> ;)

Seeeeeeeee!!! no lo habia visto xD jajaja

Ya se instaló! Y ahora? xD
No aparece para agregar como un plasmoide

---

### Post by staar on 2009-05-25
ahora veo (por la screenshot) que lo instalaste en /usr/local y lo correcto es en /usr, no problem, corré el cmake así ```
cmake -DCMAKE_INSTALL_PREFIX=/usr ../
``` y después el make y el sudo make install

saludos

---

### Post by emiliano_raso on 2009-05-25
> **staar said:**
> ahora veo (por la screenshot) que lo instalaste en /usr/local y lo correcto es en /usr, no problem, corré el cmake así ```
cmake -DCMAKE_INSTALL_PREFIX=/usr ../
``` y después el make y el sudo make install

saludos

Funciona :'( Es digno de hacer un tutorial sacar ese iconito

Gracias gente...

---

### Post by emiliano_raso on 2009-06-01
En KDE 4.2.3 no funciona :-S

---

### Post by staar on 2009-06-01
Uso KDE 4.2.3 desde que salió, y siempre me funcionó (aclaro que la distro es arch)...

probaste reinstalándolo?

saludos

---

### Post by emiliano_raso on 2009-06-01
Si. Ya probé. Ahora voy a borrar todo y pruebo de nuevo.
Me re copé con KDE... lastima que me anda medio lento, pero we...

---

### Post by emiliano_raso on 2009-06-01
Leeeeeesto... funcionó...
El problema que no se cual era el problema ahora u.u

---

