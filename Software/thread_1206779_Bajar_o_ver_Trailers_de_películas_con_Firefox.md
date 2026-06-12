---
title: "Bajar o ver Trailers de películas con Firefox"
date: 2009-07-07
forum: Software
---

### Post by leosr on 2009-07-07
Hola.
Cómo hago para bajar o ver los trailers de películas de la página de Apple? La página es [http://www.apple.com/trailers](http://www.apple.com/trailers)

Tengo instalados los plugins de Quicktime. Quisiera poder verlos en HD 480p que están en formato .mov

Saludos.

PD: uso Firefox 3.5 en Ubuntu JJ

---

### Post by pablo.s on 2009-07-07
> **leosr said:**
> Hola.
Cómo hago para bajar o ver los trailers de películas 

Necesitás el plug-in mozilla-mplayer

```
sudo apt-get install mozilla-mplayer
```

> **leosr said:**
> Quisiera poder verlos en HD 480p que están en formato .mov

480p no es HD. Es SD 
(standard definition)
por mas que diga otra cosa.

---

### Post by leosr on 2009-07-22
> **pablo.s said:**
> Necesitás el plug-in mozilla-mplayer

```
sudo apt-get install mozilla-mplayer
```



480p no es HD. Es SD 
(standard definition)
por mas que diga otra cosa.

Hola.
Tengo instalado el plugin pero no pasa nada cuando quiero abrirlo. Uso Firefox 3.5 bajado de la página de Mozilla.

Salu2

---

### Post by Celeb on 2009-07-22
No tira ningun error? Te muestra el espacio en blanco? 
En ultima instancia podrias bajarte los trailers y verlos local.

Pero necesitamos mas info para ayudarte :)

Saludos

Celeb

---

### Post by leosr on 2009-07-22
> **Celeb said:**
> No tira ningun error? Te muestra el espacio en blanco? 
En ultima instancia podrias bajarte los trailers y verlos local.

Pero necesitamos mas info para ayudarte :)

Saludos

Celeb
cuando hago clik en el link del video en 480p no hace nada y cuando lo hago en el VGA intenta abrirlo pero no muestra nada.
Abrí la Consola de errores de Firefox y dice lo siguiente:
```
Error: uncaught exception: [Exception... "Security error"  code: "1000" nsresult: "0x805303e8 (NS_ERROR_DOM_SECURITY_ERR)"  location: "http://movies.apple.com/trailers/scripts/trailer.js Line: 459"]
```
Tampoco puedo bajarlos, al guardarlo desde el menu contextual baja sólo unos kb.
Antes, cuando usaba WinXP, me abria una ventana de Quicktime y luego lo guardaba.


Salu2

---

