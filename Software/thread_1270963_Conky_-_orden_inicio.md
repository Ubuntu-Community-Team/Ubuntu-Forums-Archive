---
title: "Conky - orden inicio"
date: 2009-09-20
forum: Software
---

### Post by sitiomatic on 2009-09-20
Hola a todos, hace mil que no escribo por aca ya que habia abandonado ubuntu. 
Los problemas de mi video intel en jaunty me agotaron, probe cuanto metodo lei por ahi y nada. 
El otro dia lei que esos problemas se arreglarian en karmic y ya que estaba dispuesto a formatear instale la beta del kernel nuevo y ........maravilla!! todo se arreglo :)
El tema es que entre tantas instalaciones y desinstalaciones algunas cosas no me quedaron bien.
Puse conky para que arranque al bootear, pero arranca en una ventana y me queda arriba de todo.
Lo mato, lo vuelvo a arrancar, mismo conky con la misma orden y queda integrado al desktop. Lo arranco solo con conky sin parametros
Eso me hizo suponer que si conky arrancara ultimo al bootear, arrancaria bien.
Donde puedo modificar el orden?
Gracias mil

---

### Post by gmunioz on 2009-09-20
Hola sit....:

1- karmic aun es alfa, alfa 6, para la beta falta.

2- Si quieres que conky te arranque en el inicio del sistema, 

pero en ultimo término debes crear un script (archivo de texto

ejecutable) en /etc/init.d llamado por ejemplo myconky

Esto lo haces ejecutando en consola (Aplicaciones - Accesorios - 

Terminal)

```
sudo gedit /etc/init.d/myconky
```

Le pones estas líneas

```
#!/bin/sh
/usr/bin/conky &
```

Guardas el archivo

Cierras el editor, gedit

Le das permisos de ejecución

```
sudo chmod +x /etc/init.d/myconky
```

Y lo pones en el arranque de tu sistema:

```
sudo ln -s /etc/init.d/myconky /etc/rc2.d/S99myconky
sudo ln -s /etc/init.d/myconky /etc/rc3.d/S99myconky
sudo ln -s /etc/init.d/myconky /etc/rc4.d/S99myconky
sudo ln -s /etc/init.d/myconky /etc/rc5.d/S99myconky
```

---

### Post by Fak89 on 2009-09-20
> **sitiomatic said:**
> Hola a todos, hace mil que no escribo por aca ya que habia abandonado ubuntu. 
Los problemas de mi video intel en jaunty me agotaron, probe cuanto metodo lei por ahi y nada. 
El otro dia lei que esos problemas se arreglarian en karmic y ya que estaba dispuesto a formatear instale la beta del kernel nuevo y ........maravilla!! todo se arreglo :)
El tema es que entre tantas instalaciones y desinstalaciones algunas cosas no me quedaron bien.
Puse conky para que arranque al bootear, pero arranca en una ventana y me queda arriba de todo.
Lo mato, lo vuelvo a arrancar, mismo conky con la misma orden y queda integrado al desktop. Lo arranco solo con conky sin parametros
Eso me hizo suponer que si conky arrancara ultimo al bootear, arrancaria bien.
Donde puedo modificar el orden?
Gracias mil

Que tal..
Mira, crea un archivo de texto ubicado en /usr/bin y llamalo inicio-conky. En el contenido de este archivo pone:
```
#!/bin/bash

sleep 10 && conky; 
```
Y ahora en Sistema, Preferencias, Aplicaciones al Inicio edita la linea Conky y pone en orden "inicio-conky"..
Con eso debería iniciar a la perfeccioné ;)

---

### Post by sitiomatic on 2009-09-20
Hola
El primer metodo no me anduvo, el segundo si, pero poniendo sleep 20 en lugar de sleep 10, con 10 seguia saliendo como antes.
Gracias a los dos!!

---

### Post by Fak89 on 2009-09-21
> **sitiomatic said:**
> Hola
El primer metodo no me anduvo, el segundo si, pero poniendo sleep 20 en lugar de sleep 10, con 10 seguia saliendo como antes.
Gracias a los dos!!

De nada, y claro, olvide aclararte.
La cantidad de tiempo se coloca dependiendo de lo que tarde en iniciar el desktop ubuntu.

Un saludo!

---

