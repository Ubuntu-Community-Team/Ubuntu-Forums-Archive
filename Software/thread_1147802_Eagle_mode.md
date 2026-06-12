---
title: "Eagle mode??"
date: 2009-05-03
forum: Software
---

### Post by erdosain9 on 2009-05-03
Se puede usar esto en Ubuntu??? no sé bien qué es? sólo se que se maneja con zoom...

[http://eaglemode.sourceforge.net/](http://eaglemode.sourceforge.net/)

Saludos y gracias

---

### Post by josecuervo86 on 2009-05-03
Estuve viendo un video y esta buenisimo!! Re loco el manager ese. Ya lo estoy bajando a ver que onda

---

### Post by goldenfox on 2009-05-03
si se puede instalar 
habia visto un deb en un blog
pd: es un gestor de ventanas muy loco y divertido XDDD

---

### Post by erdosain9 on 2009-05-03
Si me dice cómo se usa en ubuntu!!! agradecido!!!

---

### Post by erdosain9 on 2009-05-03
Hice un deb por primera vez...

[http://www.amics-mania.com/amics/blog/?p=341](http://www.amics-mania.com/amics/blog/?p=341)


ehhhhhhhhhhhh!!!!

Bueno, ahora lo estoy instalando, espero funcione todo bien!

---

### Post by josecuervo86 on 2009-05-03
Ya lo instale! Esta buenisimo!!! Hice un videito que despues lo subo!

Para instalarlo vayan a la pagina que dio erdosain9, se bajan el archivo tar.gz, lo descomprimen y de ahi van a la carpeta donde lo descomprimieron y ponen

```

sudo perl make.pl build
sudo perl make.pl install

```
Despues, una vez terminado le dan doble click al archivo **eaglemode.sh** y listo, tienen eagle mode funcando en su maquina.

En cuanto suba el video lo pongo aca para que vean

---

### Post by erdosain9 on 2009-05-03
La verdad que no!! se hizo el deb... lo instalé y pues, no sé dónde está el programa ni cómo ejecutarlo... vi que se encuentra en el sistema de archivos pero no sé qué hacer..,.. :-(

---

### Post by erdosain9 on 2009-05-03
recién veo... ahora me fijo

y la put!!!!!!!!!!!!!!!!! ah!

bueno, me salió este error:

src/emX11/emX11Clipboard.cpp:206: error: &#8216;CWOverrideRedirect&#8217; no se declaró en este ámbito
src/emX11/emX11Clipboard.cpp:207: error: &#8216;XCreateWindow&#8217; no se declaró en este ámbito
src/emX11/emX11Clipboard.cpp:208: error: &#8216;XStoreName&#8217; no se declaró en este ámbito
src/emX11/emX11Clipboard.cpp: In destructor &#8216;virtual emX11Clipboard::~emX11Clipboard()&#8217;:
src/emX11/emX11Clipboard.cpp:220: error: &#8216;Disp&#8217; no se declaró en este ámbito
src/emX11/emX11Clipboard.cpp:220: error: &#8216;Win&#8217; no se declaró en este ámbito
src/emX11/emX11Clipboard.cpp:220: error: &#8216;XDestroyWindow&#8217; no se declaró en este ámbito
src/emX11/emX11Clipboard.cpp: At global scope:
src/emX11/emX11Clipboard.cpp:224: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
---
Building emX11 failed!

Era más largo pero supongo que el tema es emX11 failed!

Alguna respuesta a esto??

Saludos y gracias

---

### Post by sergiom99 on 2009-05-03
asi les quedo? [http://eaglemode.sourceforge.net/video.html](http://eaglemode.sourceforge.net/video.html)

Muy grosso!

---

### Post by josecuervo86 on 2009-05-03
Lo prometido es deuda, aca esta el videito que acabo de grabar
[URL="http://www.youtube.com/watch?v=P-zG-Gk7Y3Y"]
http://www.youtube.com/watch?v=P-zG-Gk7Y3Y[/URL]

Pd: Esta como medio acelerado, pasa que como no lo se usar todavia, tocaba todo, jeje

---

### Post by josecuervo86 on 2009-05-03
> **erdosain9 said:**
> recién veo... ahora me fijo

y la put!!!!!!!!!!!!!!!!! ah!

bueno, me salió este error:

src/emX11/emX11Clipboard.cpp:206: error: ‘CWOverrideRedirect’ no se declaró en este ámbito
src/emX11/emX11Clipboard.cpp:207: error: ‘XCreateWindow’ no se declaró en este ámbito
src/emX11/emX11Clipboard.cpp:208: error: ‘XStoreName’ no se declaró en este ámbito
src/emX11/emX11Clipboard.cpp: In destructor ‘virtual emX11Clipboard::~emX11Clipboard()’:
src/emX11/emX11Clipboard.cpp:220: error: ‘Disp’ no se declaró en este ámbito
src/emX11/emX11Clipboard.cpp:220: error: ‘Win’ no se declaró en este ámbito
src/emX11/emX11Clipboard.cpp:220: error: ‘XDestroyWindow’ no se declaró en este ámbito
src/emX11/emX11Clipboard.cpp: At global scope:
src/emX11/emX11Clipboard.cpp:224: error: expected constructor, destructor, or type conversion before ‘*’ token
---
Building emX11 failed!

Era más largo pero supongo que el tema es emX11 failed!

Alguna respuesta a esto??

Saludos y gracias

Por que no te bajas el tar.gz en vez del deb, resulto bastante facil la compilación

---

### Post by erdosain9 on 2009-05-03
Uy che! qué bueno!!! cómo soluciono lo que pasó al mío...??? qué se hace??

---

### Post by josecuervo86 on 2009-05-03
A ver, vos bajaste el deb no? y lo instalaste? Despues fuiste a la carpeta donde esta instalado y ejecutaste eaglemode.sh? y no anda?

Si repondes que si a todo, ni idea que puede pasar. Por otro lado me bajaria el tar de la pagina que pusiste vos y lo volveria a instalar compilandolo

---

