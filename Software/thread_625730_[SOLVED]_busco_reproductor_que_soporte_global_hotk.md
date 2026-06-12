---
title: "[SOLVED] busco reproductor que soporte global hotkeys"
date: 2007-11-28
forum: Software
---

### Post by Skavenger on 2007-11-28
buenas, en windows siempre use winamp y estoy **MUY** acostumbrado a usar la opcion que tiene de las global hotkeys, pero el problema es que no encontre ningun reproductor que soporte esto en ubuntu -.-

lo que necesito es lo basico:
- play/pause
- stop
- next/previous track
- jump to file [que muestra la playlist]

espero alguien sepa de alguno, gracias!

---

### Post by kowal on 2007-11-28
1) Amarok hace eso perfectamente

2) En KDE se pueden introducir *global hotkeys *a **cualquier aplicación**

3) Según leí por ahí en Gnome esto también es posible, instalando un programa extra como xbindkeys:
[http://ubuntuforums.org/showpost.php?p=431698&postcount=7](http://ubuntuforums.org/showpost.php?p=431698&postcount=7)

---

### Post by niko_3100 on 2007-11-28
a que llaman hotkeys??

---

### Post by kowal on 2007-11-28
[quote=niko_3100]a que llaman hotkeys??[/quote]

*Hotkeys* o *shortcuts* vendrían a ser los "atajos del teclado" o combinaciones de teclas que producen cierto tipo de acciones (para hacerlo mas ilustrativo: apretás una tecla y se abre un programa o apretás control+v y se adelanta una canción en el reproductor, etc.)

*Global hotkeys * serían atajos del teclado generales que funcionan sin importar el programa que se esté usando

---

### Post by monofluor on 2007-11-28
Con exaile se pueden usar las global hotkeys...

---

### Post by vk-cdg on 2007-11-28
En mi caso tengo un teclado con teclas multimedia (play, pause, next, etc) y el Totem me las toma sin haber especificado nada. 
El Amarok no, pero tampco le di mucha vuelta de investigación como para saber si tiene o no.

---

### Post by niko_3100 on 2007-11-28
AAhhh eso jajaja!! si yo tengo el rhtymhbox y me tomo las hotkeys sin especificar nada. Es mas quiero ver si puedo configurar para que el xmms me las tome pero no lo consigo GRGR!!!

---

### Post by Skavenger on 2007-11-28
> **kowal said:**
> 3) Según leí por ahí en Gnome esto también es posible, instalando un programa extra como xbindkeys:
[http://ubuntuforums.org/showpost.php?p=431698&postcount=7](http://ubuntuforums.org/showpost.php?p=431698&postcount=7)
gracias, con eso lo solucione
si a alguien le interesa, asi fue como lo deje [uso xmms]:

```
(xbindkey '(XF86AudioPlay) "xmms --play-pause")
(xbindkey '(Mod4 x) "xmms --play-pause")

(xbindkey '(XF86AudioPrev) "xmms --fwd")
(xbindkey '(Mod4 Prior) "xmms --fwd")

(xbindkey '(XF86AudioNext) "xmms --rew")
(xbindkey '(Mod4 Next) "xmms --rew")

(xbindkey '(XF86AudioStop) "xmms --stop")
(xbindkey '(Mod4 s) "xmms --stop")

(xbindkey '(XF86AudioPlay) "xmms -j")
(xbindkey '(Mod4 j) "xmms -j")
```

si usan compiz tienen que tener cuidado de que no sea la misma tecla que usan para algun efecto o lo que sea porque sino no funca

---

### Post by lrenjifo on 2009-11-18
Pues si me sirivio, pero lo que quiero es hacer que el "Saltar a archivo" o "j" funcione con la tecla buscar del teclado multimedia, xq es molesto tener que abrir el xmms y teclear "j", recuerdo que en windows el winamp funciona de manera directa con "AltGr + J"

Alt GR = ISO Level3 Shift

asi que probe con lo siguiente y no obtube resultados...
> 
1)
(xbindkey '(XF86Search) "xmms --j")
(xbindkey '(Mod4 j) "xmms --j")

2)
(xbindkey '(XF86Search) "xmms -j")
(xbindkey '(Mod4 j) "xmms --j")

3)
(xbindkey '(XF86Search) "xmms --jump")
 (xbindkey '(Mod4 j) "xmms --j")

Que estoy haciendo mal, alguna otra idea???

---

### Post by Skavenger on 2009-11-18
> **lrenjifo said:**
> Pues si me sirivio, pero lo que quiero es hacer que el "Saltar a archivo" o "j" funcione con la tecla buscar del teclado multimedia, xq es molesto tener que abrir el xmms y teclear "j", recuerdo que en windows el winamp funciona de manera directa con "AltGr + J"

Alt GR = ISO Level3 Shift

asi que probe con lo siguiente y no obtube resultados...

Que estoy haciendo mal, alguna otra idea???

Proba instalar Audacious, la última versión que instalé tenía soporte para global hotkeys, y de paso te olvidas de todo este problema ;)

---

### Post by lrenjifo on 2009-11-23
Pues la verdad me cambie a "Audacius" y estaba feliz con las teclas multimedia hasta que no se que hize pero por mas que "suba" o "baje volumen" este sigue igual :S (me refiero al sistema en general), solo se ve el dibujo que sube y baja pero el sonido no se mueve y tengo que bajarlo y subirlo haciendole click (que molesto).

---

