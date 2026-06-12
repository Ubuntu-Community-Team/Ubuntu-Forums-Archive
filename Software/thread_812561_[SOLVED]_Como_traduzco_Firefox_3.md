---
title: "[SOLVED] Como traduzco Firefox 3?"
date: 2008-05-30
forum: Software
---

### Post by pablo0469 on 2008-05-30
Muchachos, hace horas se me actualizo el FF y esta todo "in inglish". Por mi no hay drama, pero en esta casa hay gente que no caza ni media palabra de ese idioma. Busque en san google y aun no pude encontrar ninguna solucion (si la hay).

Gracias de antemano y saludos a todos.

---

### Post by vk-cdg on 2008-05-30
A mi me pasó lo mismo. 
Quizas todavía no estén los paquetes, ya que con la instrucción con la que suelo "localizar" mi firefox a es-AR no pude.

Habrá que esperar!

---

### Post by pablo0469 on 2008-05-30
Es lo que temia, de ultima por el momento cualquier otro que este en castizo, hay unos cuantos disponibles para GNU/Linux.

Gracias y saludos.

---

### Post by Mauro22 on 2008-05-30
Hola!!


Lo que podes hacer es: (medio engorroso)

1) Anda a la pagina oficial de mozilla y bajate la misma version que tenes pero en español.

2) Cuando la bajes descomprimila.

3) Abri la consola y anda a esta carpeta:

```
cd /usr/lib/firefox-3.0b5/chrome
```Esto corresponde a v3.0 beta 5 (cambialo de acuerdo al tuyo)

Dentro de esa carpeta 'chrome' vas a ver algo asi:

```

mauro@darkfire-desktop:/usr/lib/firefox-3.0b5/chrome$ ls
browser.jar       classic.jar       en-US.jar       icons
browser.manifest  classic.manifest  en-US.manifest

```Bueno, en-US.jar y en-US.manifest es el idioma. Aunque yo lo tengo en español aparece asi.

4) Borras (o hace backup) de esos archivos.

```
sudo mv en-US.jar en-US.jar.bkp
``````
sudo mv en-US.manifest en-US.manifest.bkp
```5) Copias los mismos archivos pero de la carpeta que descomprimiste. (seguro van a hacer ar-ES o ar-AR)

```
sudo cp /dondelodescomprimiste/chrome/ar-AR.* ESPACIO /usr/lib/firefox-3.0b5/chrome/
```6) Renombra ar-AR (o ar-ES) a en-US

```
sudo mv ar-AR.jar en-US.jar
``````
sudo mv ar-AR.manifest en-US.manifest
```7) Si te salio bien, lo tendras en español, sino tenes el backup...



:guitar:

---

### Post by pablo0469 on 2008-05-31
Gracias Mauro por tu ciudadosa y larga explicacion, en cuanto emboque un poco de tiempo, procurare seguir estos pasos. La version que se me instalo post-actualizacion es la 3rc1.

Saludos.

---

### Post by pablo0469 on 2008-05-31
Encontre una forma mucho mas simple, hay que instalar este complemento desde este enlace:

[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0rc1/linux-i686/xpi/es-ES.xpi](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0rc1/linux-i686/xpi/es-ES.xpi)

Y listo, en un par de segundos Firefox 3 rc1 queda todo "in spanish".

Saludos y ojala les sirva.

---

### Post by Vulcano on 2008-05-31
> **pablo0469 said:**
> Encontre una forma mucho mas simple, hay que instalar este complemento desde este enlace:

[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0rc1/linux-i686/xpi/es-ES.xpi](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0rc1/linux-i686/xpi/es-ES.xpi)

Y listo, en un par de segundos Firefox 3 rc1 queda todo "in spanish".

Saludos y ojala les sirva.

Probé tal como vos dijiste y en cuestión de segundos tenia el firefox en español!! Pruebenlo

---

