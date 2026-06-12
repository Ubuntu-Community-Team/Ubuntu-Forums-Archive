---
title: "Error al iniciar .dmrc"
date: 2009-07-09
forum: Software
---

### Post by zhelo on 2009-07-09
prueba:
[http://i32.tinypic.com/2hns55v.jpg](http://i32.tinypic.com/2hns55v.jpg)

situacion: 
prendo mi tarro, ingreso a ubuntu, cagar el la barra y luego parace "la prueba"

bases:
formatee con ubuntu amd64, (siendo que antes le tenia el intel de 32) respalde la carpeta home con todos su archivos ocultos, una vez intalado ubuntu amd64, proceido a pegar home  para volver a tener mis configuraciones,, reinici y aparecio "prueba", sin embargo mis configuraciones volvieron hacer lo que fueron antes d ela formateada

que paso?

---

### Post by pagondel on 2009-07-10
Zhelo, al copiar los archivos de tu $HOME se perdieron los permisos q requiere .dmrc para funcionar correctamente, puedes intentar ingresar como root desde el recovery mode, y escribir lo siguiente:

```
 cd /home/TuUsuario
```
(FIJATE BIEN, en q debes reemplazar TuUsuario con el nombre de tu usuario)
```
rm .dmrc
```
Reinicia, y cuentanos como te fue.

---

### Post by zhelo on 2009-07-10
> **pagondel said:**
> Zhelo, al copiar los archivos de tu $HOME se perdieron los permisos q requiere .dmrc para funcionar correctamente, puedes intentar ingresar como root desde el recovery mode, y escribir lo siguiente:

```
 cd /home/TuUsuario
```(FIJATE BIEN, en q debes reemplazar TuUsuario con el nombre de tu usuario)
```
rm .dmrc
```Reinicia, y cuentanos como te fue.

iniciar en modo recovery, luego terminarl, sudo su... me envio directamente a /home/TuUsuario (pero con un gato[#] al lado de tu usuario), luego rm .dmrc, reiniciar y aparece lo mismo 
[http://i32.tinypic.com/2hns55v.jpg](http://i32.tinypic.com/2hns55v.jpg)

trate de nuevo sin entrar a modo recovery pero el archivo ya habia sido borrado, reinicie y sigue lo mismo

---

