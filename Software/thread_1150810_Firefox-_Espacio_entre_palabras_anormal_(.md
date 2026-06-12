---
title: "Firefox- Espacio entre palabras anormal :("
date: 2009-05-06
forum: Software
---

### Post by mario gavilan on 2009-05-06
Solamente Firefox me funciona mal en el sentido de que se separan demacioado las palabras de los texos, ya intente Editar-> Preferencias -> Contenido -> configurar las fuentes, pero no se soluciona D:

aca dejo un screenshot de mi problemas:


[http://img408.imageshack.us/my.php?image=pantallazoy.png](http://img408.imageshack.us/my.php?image=pantallazoy.png)


de antemano muchas gracias :D

---

### Post by clasificado on 2009-05-06
Increíble :D

Que versión de ubuntu estas usando? 9.10? 32 o 64 bits? (preguntas de rutina)

clasificado

---

### Post by dirty fingers on 2009-05-06
jajaja re loco. cargue la pagina a ver si lograba hacer el mismo efecto tocando los parámetros de estilo de página, tamaño y codificación de caracteres y nada.
[http://java.com/es/download/help/5000011400.xml](http://java.com/es/download/help/5000011400.xml)

que paso entre que se veía bien y se empezó a ver mal ?

---

### Post by ubuntu27 on 2009-05-06
No sera que no tiene los fonts de microsoft instalados?

Mario. Abre el Gestor de paquetes Synaptic (menu Sistema-->Administracion--->Synaptic)

y busca un paquete llamado  **ttf-mscorefonts-installer**

Yo supongo que tienes la version actual de Ubuntu que es 9.04 (o Jaunty Jackalope).

Si estas usando la versiones previas de Ubuntu, entonces lo que necesitas instalar es **msttcorefonts**


Tambien te recomiendo que instales **ttf-liberation**
```

sudo apt-get install ttf-liberation
```

---

### Post by mario gavilan on 2009-05-06
no me funcionó nada de lo que me recomendo dirty finger y ubuntu27, instale los font y el java jre pero sigue igual:


[http://img141.imageshack.us/my.php?image=pantallazo2s.png](http://img141.imageshack.us/my.php?image=pantallazo2s.png)

AAAAAAA!!! no se que podrá ser

PD: tengo ubuntu 9.04 64bits

---

### Post by pablo.s on 2009-05-06
Probaste cambiando en las
preferencias de Firefox el
tipo de fuente a una mas
común, como Vera Sans, o
Monospace?

---

### Post by mario gavilan on 2009-05-07
Si lo probé y tampoco me cambia los textos de la aplicacion firefox ya que como se ve en la screenshot tambien los textos de la aplicacion se ven anormales 

[http://img156.imageshack.us/my.php?image=pantallazo3.png](http://img156.imageshack.us/my.php?image=pantallazo3.png)

---

### Post by clasificado on 2009-05-08
¿Probaste con el live cd?

Como para seprarar si es un bug de la implementación del 9.04 64bits o es configuración de tu machine

clasificado

---

### Post by mario gavilan on 2009-05-08
voy a porbar live cd y les cuento

---

### Post by mario gavilan on 2009-05-11
con live CD se ve bien. 
cuando instale ubuntu firefox funcionaba bien, pero despues de un tiempo de uso sucedio este problema.

---

### Post by ubuntu27 on 2009-05-11
Abre Nautilus (el navegador de Archivos), y anda tu direcotrio home

Presiona Control H para que se muestre los archivo sescondidos. Talvez el atajo de tecla no sea lo mismo en castellano. Si no funciona control H, anda a menu **Ver**------>Mostrar Archivos Ocultos

Ahora, elimina el directorio (carpeta) llamado ".mozilla" (fijate que hay un PUNTo antes de mozilla)

Presiona Control H de nuevo para volver a ocultar los archivos ocultos.


Listo

Ahora, vuelve a abrir firefox.

---

### Post by Hei Ku on 2009-05-11
Advertencia: eso te va a borrar tu profile de Firefox, Thunderbird, etc. Lo recomendable es hacer un backup antes, por las dudas.

---

### Post by mario gavilan on 2009-05-12
muchas gracias, voy a probar eliminar el profile .mozilla y le cuento como me fue :)

---

### Post by milovan1971 on 2009-05-12
Se ha reportado este error por un problema con un paquete [pando-graphite] que se usa para ver las "smart fonts". Fijate si lo tenes instalado con el gestor de paquetes synaptic, y si es asi, proba eliminandolo a ver que pasa.

---

### Post by milovan1971 on 2009-05-12
upsss.... es pango-graphite (con g) :)

---

### Post by mario gavilan on 2009-05-13
interesante, voy a probar si sacando el paquete de pando se arregla y le pongo (SOLUCIONADO) :guitar:

---

### Post by mario gavilan on 2009-05-13
SOLUCIONADO , era el paquete pango-graphite.

muchas gracias a todos por ayudarme a solucionar el problema y espero que les sirva a los demas que tengan este problema \\:D/

---

### Post by mario gavilan on 2009-05-13
:)

---

### Post by cortsenc on 2009-10-08
Tengo el mismo problema i googleando he llegado a este foro que me dio la solución. Gracias!!

---

