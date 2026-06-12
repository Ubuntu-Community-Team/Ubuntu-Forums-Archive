---
title: "conversor de video"
date: 2009-05-18
forum: Software
---

### Post by joseluis on 2009-05-18
hola..necesito saber qué programa puedo usar para pasar videos de windows media (un video hecho con el Windows Movie Maker) a formato .avi.
gracias!!!1

---

### Post by pablo.s on 2009-05-18
Hay varios:

-Avidemux
-Pytube
-WinFF

Probablemente Avidemux sea el
mejor para la tarea. Pytube también
es muy lindo programa.

---

### Post by dirty fingers on 2009-05-18
con winff si tenes puestas las librerías de decodec del mplayer sale con fritas.

---

### Post by luks911 on 2009-05-18
Además de las opciones gráficas de arriba podés usar mencoder en terminal.

Lo instalás: 

```
sudo apt-get install mencoder
```

Y lo usás así

```
mencoder archivo.wmv -ofps 23.976 -ovc lavc -oac copy -o archivo.avi
```

---

### Post by joseluis on 2009-05-18
Graciassssssss

---

### Post by hictio on 2009-05-18
No se de que tamaño de archivos estamos hablando pero una opción que yo uso mucho, especialmente para convertir esos videos familiares que te mandan con un codec propietario de Windows Media, es pasarlo por el servicio de conversión gratuito de esta página: [Media Convert](http://media-convert.com/convert/).

---

### Post by infernus92 on 2009-05-18
gracias por el dato... esta bueno saberlo...
cuando usaba win$ usaba uno que se llama "Free Video Converter" que decia ser de licencia GPL... pero lei el readme y decia algo como "prohibida su modificacion" o algo asi refiriendose al codigo fuente... la verdad, una vergûenza

Saludos

---

### Post by joseluis on 2009-05-19
perdon..algo más...¿en esa conversión se pierde calidad? ¿mucha?

---

### Post by pablo.s on 2009-05-19
Si, siempre que uses un codec con
perdida (como WMV) vas a perder
calidad. Ademas influyen otros
factores, como bitrate, entrelazado,
pasadas de codec y otros aspectos
de la compresión.
Si querés mantener la mejor calidad
desde que bajás el video de la cámara
lo mas acertado es mantener el
proyecto de edición en crudo y cuando
vayas a compilar la edición, guardarlo
en un codec como Theora o x264.
Todo depende de que software y que
cámara uses, no es lo mismo usar una
cámara digital de 3 CCD que usar una
palmcorder del año 2000.

---

