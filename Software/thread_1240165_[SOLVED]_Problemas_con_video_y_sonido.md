---
title: "[SOLVED] Problemas con video y sonido"
date: 2009-08-14
forum: Software
---

### Post by tyjsiskurvysyn on 2009-08-14
Tengo Xubuntu 9.04 y no puedo ver ni oir videos de internet.. 

He instalado todos los plugins que he encontrado y sigue sin fucionar.

¿alguien puede ayudarme? 

Gracias

---

### Post by staar on 2009-08-14
que navegador usas?
con videos te referis a los flash, como youtube?
que plugins tenés instalados? (para que funcione solo puede haber uno, sino entran en conflicto)
instalaste el paquete *xubuntu-restricted-extras*?

saludos

---

### Post by tyjsiskurvysyn on 2009-08-14
> **staar said:**
> que navegador usas?
con videos te referis a los flash, como youtube?
que plugins tenés instalados? (para que funcione solo puede haber uno, sino entran en conflicto)
instalaste el paquete *xubuntu-restricted-extras*?

saludos

Uso Firefox. Si me refiero a los flash como youtube.

Voy a descargar Xubuntu-restricted-extras a ver si se arregla

---

### Post by tyjsiskurvysyn on 2009-08-14
Sigue sin funcionar, no puedo oir los videos :(

---

### Post by josecuervo86 on 2009-08-14
proba bajando, si es que no lo tenes instalado ya, los siguientes paquetes

flashplugin-nonfree
flashplugin-installer

---

### Post by tyjsiskurvysyn on 2009-08-14
Los instalé y sigue sin funcionar el sonido

---

### Post by guillermolisi on 2009-08-14
Tenes sonido cuando escuchas otras fuentes, tipo mp3, CDs de audio, radios por Internet, etc. ?

Por las dudas, entra en una consola/terminal y ejecuta "alsamixer" (sin las comillas), levanta los niveles de todos los canales y desmarca los que esten silenciados.

---

### Post by tyjsiskurvysyn on 2009-08-14
Ya conseguí arreglarlo. Tenia un problema con el mezclador.

Gracias a todos :)

---

