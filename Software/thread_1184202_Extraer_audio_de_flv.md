---
title: "Extraer audio de flv"
date: 2009-06-10
forum: Software
---

### Post by ramiro_md on 2009-06-10
Buenas gente re aparezco con una consulta, resulta que quiero extraerle el audio (en formato mp3) a un video flv. Estoy utilizando winff (front end para ffmpeg)..la cuestión es que al llamar al video con winff e intentar convertirlo con las opciones "convertir en: audio" y "elegir variante: mp3", por consola me sale el siguiente error "/home/ramiro/Desktop/1.flv: Unknown format".
Me fijé en synaptic si tenía algún que otro paquete para manejo de flv y encontré flvtool2, el cual instalé.
COn este nuevo paquete instalado volví a intentar pero de nuevo el mensaje de error (/home/ramiro/Desktop/1.flv: Unknown format).
Alguien sabe como puedo solucionar esto ?. Aclaro, de las paginas que ofrecen este servicio no me anduvo ninguna.
Un saludo y espero que me den una mano !.

---

### Post by pablo.s on 2009-06-10
Pytube lo hace!

---

### Post by santiagoward2000 on 2009-06-10
Yo lo logré hacer un par de veces con el **soundconverter**, si querés probar con otro programa.
Saludos!

---

### Post by staar on 2009-06-10
y con ffmpeg, pero desde la consola? ```
ffmpeg -i video.flv -f mp3 audio.mp3
```

saludos

---

### Post by Air23 on 2009-06-11
Otra opcion es Mobile Media Converter

[http://www.ubuntips.com.ar/2009/01/15/mobile-media-converter-141/](http://www.ubuntips.com.ar/2009/01/15/mobile-media-converter-141/)
[http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)
[http://www.miksoft.net/products/mmc_1.4.3_i386.deb](http://www.miksoft.net/products/mmc_1.4.3_i386.deb)

---

### Post by josecuervo86 on 2009-06-11
> **staar said:**
> y con ffmpeg, pero desde la consola? ```
ffmpeg -i video.flv -f mp3 audio.mp3
```

saludos

+1, ffmpeg es una masa

---

### Post by ramiro_md on 2009-06-11
Gente gracias por la data. Para aquellos que aconsejaron ffmpeg, winff es un frontend para ffmpeg, es decir que usa ffmpeg para hacer las conversiones :S. Ahora estoy por probar el mobile media converter, que recordé que lo usé en ubuntu mucho tiempo.
Por otro lado leí mucho de pytube asique también lo probaré.
Gracias!

---

### Post by ramiro_md on 2009-06-11
Mobile Media Converter al parecer usa ffmpeg por lo que me sigue diciendo que no reconoce flv. Hay algún paquete que haya que instalar de adobe u algo ?.
Ahora me voy a estudiar :P más tarde pruebo con pytube.
Un saludo y gracias.

---

### Post by anarko on 2009-06-11
Tb esta la opcion del avidemux, anda muy lindo

---

### Post by clasificado on 2009-06-11
> **josecuervo86 said:**
> +1, ffmpeg es una masa

ffmpeg es LA respuesta, lo he hecho un par de veces

lo que suele ser problema es que puede que tu compilación no tenga soporte para flv :P

de última es cuestion de recompilar

clasificado

---

### Post by ramiro_md on 2009-06-11
Si, es obvio que la respuesta es ffmpeg, notesé que fue a lo único que recurrí.Y para los que solo leen el título, el problema no es buscar una variante a ffmpeg sino hacer que ffmpeg ande.
EL tema es que ffmpeg no me está reconociendo el formato flv por más de que al ejecutar ffmpeg -formats, me aparezca entre los cocecs y formatos soportados :S

---

### Post by staar on 2009-06-11
che, que raro, el flv no estará corrupto? mirá que ese formato se corrompe muy fácilmente, podés bajarlo de nuevo?

saludos

---

### Post by ramiro_md on 2009-06-11
Al parecer lo tengo casi resuelto con pytube, si no fuese porque me elimina el video descargado, es decir yo pego el link, elijo que convierta solo a mp3 y le doy ubicación en Desktop. EL archivo lo veo cuando esta descargando pero al finalizar se elimina automaticamente :S

---

### Post by pablo.s on 2009-06-11
Hay una opción para
que no le elimine, fijate.

Incluso se puede bajar el
video a tu máquina y 
extraer la parte que quieras.

---

### Post by pol666 on 2009-06-13
Tambien sirve JDownloader
Pones la URL de un video de youtube y te da la opcion de extraer el audio ;)

---

### Post by pablo.s on 2009-06-13
Es más, ni le tenés que
dar la URL, en la última 
versión te lee la mente y
si tenés frio te desactiva
el cooler de la computadora.

---

