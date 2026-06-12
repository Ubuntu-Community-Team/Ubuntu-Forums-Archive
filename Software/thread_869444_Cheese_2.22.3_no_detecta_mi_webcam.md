---
title: "Cheese 2.22.3 no detecta mi webcam"
date: 2008-07-24
forum: Software
---

### Post by atari130xe on 2008-07-24
Por esas casualidades, alguien que tenga instalado este pequeño programa de fotos, tiene idéa de como hacer para que tome la webcam en lugar de la placa de tv?

gstreamer-properties y elijo v4l y la webcam como predeterminada para video pero... cuando inicia Cheese toma la webcam pero elige automáticamente la placa sintonizadora de tv cosa que obviamente hace que en lugar de la imagen de la webcam, la pantalla quede totalmente de color negro. :confused:

Webcam Genius Look 316 (USB)

---

### Post by luks911 on 2008-07-25
No, no sé cómo hacer que tome la webcam en lugar de la placa de video, pero me atrevo :wink: a recomendarte otro programa muy parecido pero que al menos en mi caso funcionó mejor, más rápido, graba el video a la velocidad correcta y, por lo que leí, en algunos casos solucionaba algunos problemas a la hora de detectar cámaras. Así que tal vez quieras probarlo. Es el Wxcam. No está en repositorios pero de su página ([http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)) se puede descargar un .deb.
Y de paso probás, porque si con la prueba de gstreamer-properties funciona, entonces la cámara está bien configurada.
Saludos

---

### Post by User21 on 2008-07-25
Si estas usando Gnome, basta con ejecutar en consola:
```
 sudo gconf-editor
```y buscar la clave que le dice a Cheese que origen de video usar.
 Ahora no estoy en Ubuntu, pero creo que es: Apps, Gnome2, Cheese, y buscar una clave a editar, con la ruta del dispositivo. Por ejemplo: /dev/video1

Si no encuentras, el programa tiene una busqueda de cadenas de texto. Solo busca cheese y te dara cuantas veces aparece cheese en el arbol. 

Disculpa no sea mas especifico, pero no estoy en Ubuntu ahora. Si te fijas, en CADA CLAVE, abajo hay una breve descripcion. Por lo menos yo, la tengo en español.

---

### Post by atari130xe on 2008-07-28
> **luks911 said:**
> No, no sé cómo hacer que tome la webcam en lugar de la placa de video, pero me atrevo :wink: a recomendarte otro programa muy parecido pero que al menos en mi caso funcionó mejor, más rápido, graba el video a la velocidad correcta y, por lo que leí, en algunos casos solucionaba algunos problemas a la hora de detectar cámaras. Así que tal vez quieras probarlo. Es el Wxcam. No está en repositorios pero de su página ([http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)) se puede descargar un .deb.
Y de paso probás, porque si con la prueba de gstreamer-properties funciona, entonces la cámara está bien configurada.
Saludos

Gracias pero sigo con el mismo problema :(

---

### Post by atari130xe on 2008-07-28
> **User21 said:**
> Si estas usando Gnome, basta con ejecutar en consola:
```
 sudo gconf-editor
```y buscar la clave que le dice a Cheese que origen de video usar.
 Ahora no estoy en Ubuntu, pero creo que es: Apps, Gnome2, Cheese, y buscar una clave a editar, con la ruta del dispositivo. Por ejemplo: /dev/video1

Si no encuentras, el programa tiene una busqueda de cadenas de texto. Solo busca cheese y te dara cuantas veces aparece cheese en el arbol. 

Disculpa no sea mas especifico, pero no estoy en Ubuntu ahora. Si te fijas, en CADA CLAVE, abajo hay una breve descripcion. Por lo menos yo, la tengo en español.

Gracias hice el cambio pero sigue la pantalla en negro :(

---

