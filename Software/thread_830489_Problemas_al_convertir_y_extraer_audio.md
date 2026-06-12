---
title: "Problemas al convertir y extraer audio"
date: 2008-06-15
forum: Software
---

### Post by Kabezon on 2008-06-15
Buenas... No tengo idea del por qué, pero intenté pasar un CD a la PC en formato MP3 usando el Audio CD Extractor, pero no me tirá la opción de pasarlo como MP3 en las preferencias :S Otro problema que tengo es al intentar convertir videos de AVI a MP4, me tira error el codec aac :S

> Unknown codec 'aac'

También noté que el Sound Converter no me permite convertir a MP3, como si no tuviera los codecs necesarios instalados... Pero creo tenerlos...
Se agradece toda ayuda =]

---

### Post by Hei Ku on 2008-06-17
el codec para codificar es aparte del que te permite escuchar. Por ejemplo tenes el liblame0.

---

### Post by Kantier on 2008-06-17
> **Hei Ku said:**
> el codec para codificar es aparte del que te permite escuchar. Por ejemplo tenes el liblame0.
A lo que se refiere Hei Ku es que tenes que instalar el paquete **liblame0** (con synaptic, adept, etc. o desde la consola haciendo "apt-get install liblame0" o "aptitude install liblame0")

---

### Post by Hei Ku on 2008-06-17
para aac, tambien tenes el paquete faac.

sudo apt-get install faac

---

### Post by Kabezon on 2008-06-19
El problema sigue :S No entiendo nada =[ Esos codecs ya los tenía instalados :S

---

### Post by Kabezon on 2008-06-20
Bueno, soy un queso :P El problema era que me olvidé por completo de que no volví a instalar los paquetes de Medibuntu una vez reinstalado Linux, cuando decidí hacer dual boot :P Es que fue hace rato largo ya... me sorprende que no haya rippeado CDs desde entonces :P Gracias por la ayuda igual :lolflag:

---

### Post by quill3033 on 2008-08-20
ok yo quiero convertir mp3 a cd audio normal para poner en cualquier tocadiscos normal. pero aunque instale todos (creo que todos) los codecs etc incluidos los de medibuntu, retire ese repositorio porque las acutalizaciones de Skype y Amarok no me gustaban el efecto que tenian - siempre coincidia que cada vez que medibuntu hacia una actualizacion a amarok o skype algo terminaba funcionando mal. 

al marge de esto, alguien sabe como convertir mp3 a cd normal?

---

### Post by Hei Ku on 2008-08-21
Con k3b y las librerias de mp3 se puede armar un CD normal.

---

### Post by FlyerDie on 2008-08-22
> **Hei Ku said:**
> Con k3b y las librerias de mp3 se puede armar un CD normal.

Exacto...y con el que viene con Ubuntu por default (ahora no me acuerdo el nombre..estoy en el laburo :( ) tambien!

---

### Post by Abrilla on 2011-02-22
Hola, prueba con **SoundTaxi Media Converter o MediaBuddy**, que mantienen un montón de formatos**, **soportan tales audio formatos populares como MP3, OGG, AC3, FLAC, WAV, AAC etc., bajar aquí: [http://soundtaxi.org/](http://soundtaxi.org/)
  Saludos

---

### Post by granjero on 2011-02-22
Brasero, el que viene por defecto en ubuntu crea cds de audio.

salud!

---

