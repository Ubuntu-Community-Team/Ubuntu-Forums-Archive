---
title: "Skype + Webcam"
date: 2009-01-27
forum: Software
---

### Post by loopeando on 2009-01-27
Me compre una camara Satellite WB-C12 (en otras palabras, generica) que utiliza el driver gspca para capturar video.

Para probar la camara use el programa Cheese (una especie de cabina fotografica) y la camara funciona perfectamente pero cuando quise probar la camara en Skype el video que capturaba la camara se veia asi:

[IMG]http://img136.imageshack.us/img136/2853/screenshotsp1.png[/IMG]

¿Tiene alguien idea de como solucionar este problema?

Btw, Ubuntu Intrepid actualizado y Skype 2.0

---

### Post by loopeando on 2009-01-28
Nada de nada?

---

### Post by SLA_leandrin on 2009-01-28
Mismo problema con el Skype. 

En Ubuntu 8.10 pasa esto, no lo pude resolver. En 8.04 Hardy no tuve ese problema, esa es la razón por la cual no lo cambio en la notebook...

---

### Post by loopeando on 2009-01-28
Mmm...

Bueno, tendre que usar aMSN entonces. Por razones que desconozco funciona la camara en este programa, aunque lo detesto.

---

### Post by hollywoods on 2009-09-11
aki les dejo un script para hacer una interposición de librerías para ke funcione la webcam en skype  

creamos 2 script  

ScreenSkype.sh 
Code: 
[INDENT] dijo:
#!/bin/sh 
screen -d -m ~/bin/skype/SkypeLauncher.sh

[/INDENT] 

SkypeLauncher.sh 
Code: 
[INDENT] dijo:
#!/bin/sh 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 
exit 0

[/INDENT] 

y los ponemos en la carpeta ~/bin/skype 

despues desde una consola nos ubicamos en la carpeta skype y le damos permiso de ejecucion y ejecutamos: 

$ sudo chmod +x SkypeLauncher.sh 
$ ./Skypelauncher.sh 

para tener un acceso directo creamos un lanzador y ponemos en la linea de comando: 

/home/”NOMBRE_USUARIO”/bin/skype/SkypeLauncher.sh  

espero ke les sirva  

saludos. 

Fuente:
[http://www.taringa.net/posts/linux/2596835/Hacer-funcionar-camara-web-NogaNet-en-Skype---UBUNTU.html](http://www.taringa.net/posts/linux/2596835/Hacer-funcionar-camara-web-NogaNet-en-Skype---UBUNTU.html)

---

### Post by SLA_leandrin on 2009-09-11
Este problema se solucionó en Jaunty, supongo que mejoras en el kernell?

---

