---
title: "Howto: Alertas de aMSN en notificaciones (libnotify)"
date: 2009-09-12
forum: Software
---

### Post by VonlisT on 2009-09-12
Hace un par de días que me vienen molestando las alertas del aMSN, no me gusta su estética, a pesar de que se puede cambiar la apariencia. De pronto se me ha ocurrido la idea de poner las alertas del aMSN en las notificaciones, para que quede al estilo de pidgni, xchat, entre otros. Para lo cual buscando en internet me encontré con un plugin que lo permite realizar
El enlace del plugin es:

[http://www.amsn-project.net/getURL.php?id=215](http://www.amsn-project.net/getURL.php?id=215)

Los requerimientos mínimos para poder configurarlo son:
* libnotify1
* libnotify-bin

Para instalar ambos, basta copiar y pegar esto en consola:
```
sudo apt-get install libnotify1 libnotify-bin
```A pesar de que la descripción dice que es para aMSN 0.97, está configurado para aMSN 0.98b, no tengo idea del porqué, el punto es que con aMSN 0.97 funciona bien.
Para solucionar esto primeramente debemos descomprimir el archivo que descargamos y entramos a la carpeta. Buscamos el archivo "plugininfo.xml" y lo abrimos con un editor de texto.
Buscamos la línea 8, que tiene el siguiente tag:
```
<amsn_version>0.98b</amsn_version>
```Sólo modificamos el "0.98b" cambiándolo por:
```
<amsn_version>0.97</amsn_version>
```Con esto le decimos al aMSN que el plugin requiere por lo menos la versión 0.97 (No sé si funcionará en versiones anteriores).
  Ahora ya tenemos configurado el plugin, entonces copiamos la carpeta entera (notify) dentro de la carpeta **$HOME/.amsn/plugins**
Para ver la carpeta .amsn solo apretas Ctrl + H y se mostrarán todas las carpetas ocutas, para dejarlas como estaban; lo mismo.
Ahora abren el aMSN y van a: Cuenta - Selector de plug-ins y buscan Notify en el panel izquierdo. lo activan y listo.
Una vez que esté funcionando, les mostrará una alerta como esta:

[IMG]http://img34.imageshack.us/img34/889/amsnnotify.png[/IMG]

Saludos
[IMG]http://img34.imageshack.us/i/amsnnotify.png/[/IMG]

---

### Post by _ZeTa on 2009-12-30
[Post de la semana]("http://ubuntuforums.org/showthread.php?t=1176055"): [30 de Diciembre]("http://www.ubuntu-cl.org/grupos/foro/alertas-de-amsn-en-notificaciones-libnotify") 2009

---

### Post by CdK1 on 2009-12-31
Emesene lo tiene en sus complementos, además de ser más rápido y sin quedarse pegado como amsn...

---

### Post by x_jefesin_x on 2009-12-31
Buen post compañero ...:P
y un excelente dato =D>

Saludos...

---

### Post by x_jefesin_x on 2010-01-01
una pregunta:

Como lo hago con la versión 0.99b ??:confused:
Ya probé cambiando el numero come le haces 
con la versión 0.97


Gracias :)

---

