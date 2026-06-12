---
title: "Alguien Utilizó el servicio Cam24 de Speedy en Ubuntu?"
date: 2009-10-08
forum: Software
---

### Post by atari130xe on 2009-10-08
Gente nuevamente en el foro... mis tios a los que les instalé e instruyo sobre el uso de Ubuntu (Intrepid en este caso), tienen el servicio contratado de Cam24 con Speedy, es una cam instalada en su local y la cuál puede ser monitoreada desde "cualquier" PC, eh aqui que (sin saberlo) les dije que desde Ubuntu se podía al ser un servicio prestado via web browser. Eh aqui que hoy cuando intenté hacerlo funcionar entre los requisitos estan (adivinen...siii Windows 2000 o XP), 512MB de ram y DirectX 9, pero SOLO funciona con IE, o sea que no corre ni en Firefox, ni ningún otro navegador, siendo esto una gran bronca de mi parte, procedí a instalarles IE4Lin, Wine tricks (para DirectX 9) y sencillamente al intentar acceder literalmente "cuelga" la PC (no la aplicación), tengo que reiniciar la PC porque ni siquiera responde Ctrl+Alt+Backspace). Estoy un poco frustrado por así decirlo y me gustaria saber si por esas casualidades alguien tiene alguna sugerencia u orientación con este tema (si conoce a alguien que lo utilice o que lo esté usando de manera personal). Mil gracias como siempre:)

---

### Post by ermeyers on 2009-10-08
English translation: [http://babelfish.yahoo.com/translate_txt](http://babelfish.yahoo.com/translate_txt)
People again in the forum&#8230; my uncles to which I installed to them and I instruct on the use of Ubuntu (Intrepid in this case), have the contracted service of Cam24 with Speedy, is one cam installed in their premises and which can be monitored from " cualquier" PC, eh here that (without knowing it) I said to them that from Ubuntu served via web browser could to the being. Eh that today when I tried to make it work between the requirements estan (guesses&#8230; siii Windows 2000 here or XP), 512MB of ram and DirectX 9, but ONLY work with IE, that is that does not run nor in Firefox, nor no other navigator, being this great quarrel of my part, I came to install IE4Lin, Wine to them tricks (for DirectX 9) and simply when trying to accede literally " cuelga" the PC (not it application), I must reinitiate the PC because not even Ctrl+Alt+Backspace responds). I am a little frustrated so to speak gustaria to know and me if by those chances somebody has some suggestion or direction with this subject (if it knows uses which it or is using that it personally). Thousand thanks as always.

---

### Post by atari130xe on 2009-10-08
> **ermeyers said:**
> English translation: [http://babelfish.yahoo.com/translate_txt](http://babelfish.yahoo.com/translate_txt)
People again in the forum&#8230; my uncles to which I installed to them and I instruct on the use of Ubuntu (Intrepid in this case), have the contracted service of Cam24 with Speedy, is one cam installed in their premises and which can be monitored from " cualquier" PC, eh here that (without knowing it) I said to them that from Ubuntu served via web browser could to the being. Eh that today when I tried to make it work between the requirements estan (guesses&#8230; siii Windows 2000 here or XP), 512MB of ram and DirectX 9, but ONLY work with IE, that is that does not run nor in Firefox, nor no other navigator, being this great quarrel of my part, I came to install IE4Lin, Wine to them tricks (for DirectX 9) and simply when trying to accede literally " cuelga" the PC (not it application), I must reinitiate the PC because not even Ctrl+Alt+Backspace responds). I am a little frustrated so to speak gustaria to know and me if by those chances somebody has some suggestion or direction with this subject (if it knows uses which it or is using that it personally). Thousand thanks as always.

Hey dude, thanks for the "babel translation" but it is just a Translation :lolflag: are you practicing? :P

---

### Post by emiliano_raso on 2009-10-09
Podrías pasar Links de información sobre el servicio?
Preferentemente del que vos tenes.

Saludos.

---

### Post by faktorqm on 2009-10-09
&#26222;&#25176;&#22577;&#38357;&#21033;

---

### Post by atari130xe on 2009-10-09
[https://www.cam24.speedy.com.ar/]("https://www.cam24.speedy.com.ar/") ese es el link pero los requisitos maso son los que detalle mas arriba ahora estoy en casa y no tengo el usuario para acceder (se requiere de un usuario y un password).

Este es el link con la info sobre el servicio:

[http://www.telefonica.com.ar/telefoniafija/pymes/cam24/]("http://www.telefonica.com.ar/telefoniafija/pymes/cam24/")

---

### Post by Mauro22 on 2009-10-09
Si mal no recuerdo hay un plugin para Firefox que se hace "pasar" por otro navegador...


Si lo encuentro, lo posteo... por ahi sirve :)

Edit:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

Lo que hace es decirle a la web que usa XXXX navegador... si es eso solo, zafas!! si es algo del renderizado hay que ver.

---

### Post by mama21mama on 2009-10-09
con wine solo tendría que andar.

---

### Post by chronos00 on 2011-02-18
Alguna novedad con este tema??

Pasaron 2 años y todavia no lo puedo hacer andar!! Tambien probe de todo: wine con winetricks, crossover con IE6 e IE7, etc, etc, etc.

El gran problema es q es necesario usar ActiveX (y firefox no soporta ni nunca soportara ActiveX). Por mas q configure a firefox para q se haga pasar por IE, nunca voy a poder instalar ActiveX...

Alguna idea?

---

### Post by gmunioz on 2011-02-20
Me parece que lo más sencillo, es instalar Virtualbox y ejecutar  en él una máquina virtual con un Windows 98 o XP liviano y ejecutar IE desde él.

---

### Post by atari130xe on 2011-02-20
> **chronos00 said:**
> Alguna novedad con este tema??

Pasaron 2 años y todavia no lo puedo hacer andar!! Tambien probe de todo: wine con winetricks, crossover con IE6 e IE7, etc, etc, etc.

El gran problema es q es necesario usar ActiveX (y firefox no soporta ni nunca soportara ActiveX). Por mas q configure a firefox para q se haga pasar por IE, nunca voy a poder instalar ActiveX...

Alguna idea?

Como estás? yo abrí este post allá lejos y hace tiempo, solucioné el tema con VirtualBox y Win XP en él (funciona perfecto -comprobado-), de otra manera no hay forma de hacer que funcione.

---

### Post by chronos00 on 2011-02-20
La verdad es q no queria caer en el Virtual Box por q:
a) la maquina es bastante vieja y no es mia (estoy haciendo esto para un amigo). Esa es la maquina q tiene, y justamente le ofreci Ubuntu como alternativa por q le iba a funcionar bien A PESAR del hardware mediocre.

b) por q es una clara mala publicidad para alguien q va a empezar con Linux, ver q algo q el estuvo usando con "tranquilidad" tanto tiempo, no le quede otra alternativa q seguir usando Wind0ze dentro de Linux.

Pero bueno, la verdad q estoy resignado a instalarle la maquina virtual con Win98 y 48MB de RAM.

Me sorprende q nadie haya podido encontrar el stream del video correspondiente para verlo con VLC o algo asi. No existe ni siquiera un "hack" para ver esta transmision??

Gracias por sus respuestas!

---

### Post by biale on 2011-02-21
Sería interesante conocer que codecs utiliza el servicio (etc). Despues de todo, no todos los usuarios W$ usan IE..

---

### Post by quedefantasma on 2011-02-24
Yo tuve el mismo problema con un sistema de cámaras GEO-VISION... Lamentablemente, no encontré solución.

Este sistema, también instala controles activeX y utiliza un codec propietario. Tuve que caer en un win98.

Slds.

---

### Post by chronos00 on 2011-02-24
Es tristitsimo ver como al dia de hoy, año 2011, siguen ocurriendo estas cosas. Incompatibilidad sin sentido... Pero lo mas extraño, es q a pesar de todos los intentos, no podamos usar el IE a traves de wine o de CrossOver.

Este ultimo me sorprendio, la verdad. En su utlima version (la 10) se jactan de q pueden correr perfectamente el IE. Yo corri entusiasmado a ver si podia finalmente resolver este problema, pero me encontre exactamente en la misma situacion q antes!

---

### Post by biale on 2011-02-24
Forzar un wine, para que pueda correr alguna versión de IE (cual de todas?) + codec propietario + instalar controles activeX...

En esos casos me gusta mas la idea de considerar una PC dedicada, como parte necesaria del Sistema de Telecámaras, e instalar un W7 original. Lo tomo como un requerimiento del sistema. Y después de todo VBox hace mas o menos eso.

Se venden cámaras IP con wireless, algunas con resoluciones importantes. Quizás alguien tenga experiencia en como acceder a esas cámaras por Internet, y si requieren de alguna instalación especial.

---

### Post by granjero on 2011-02-24
[http://www.zoneminder.com/](http://www.zoneminder.com/)

Yo en algún momento voy a probarlo.

---

### Post by chronos00 on 2011-02-25
Yo probe el Zoneminder y realmente funciona muy bien. Lamentablemente, las camaras del servicio Cam24 vienen completamente bloqueadas, e incluso el router viene completamente bloqueado. Llame a los de soporte tecnico y no quisieron darme ningun dato... Su respuesta era siempre: "el servicio es asi".

Le escanee los puertos a la camara, sniffie el trafico q generaba... pero nada. Necesitas los accesos correspondientes. Podria incluso haber obtenido la contraseña de administrador llamando al tecnico y escuchando el trafico de red mientras se loguea, pero periodicamente cambian las configs remotamente desde la central, asi q es lo mismo...

En definitiva, el servicio es una basura. Pero lamentablemente es el q tiene mi amigo. Por supuesto q yo hubiera comprado mi propia camara IP, y la hubiera configurado con Zoneminder, pero no es una opcion para él...

---

