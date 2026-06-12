---
title: "Vnc"
date: 2009-10-04
forum: Software
---

### Post by capcabgue on 2009-10-04
Hola:

Les cuanto, traté de conectar Linux y guin2 mediante VNC, seguí un tutorial de conexión ([http://www.ajpdsoft.com/modules.php?name=News&file=print&sid=406](http://www.ajpdsoft.com/modules.php?name=News&file=print&sid=406)) entre ambos SO había que poner una password, etc no sé si la anoté mal o se me olvidó, pero la  cosa es que ahora no me puedo ni conectar.
Por eso, despues de tratar de deshacer todo lo que me decía y dado que no funcionó borré .vnc en root y en el home, como tampoco me funcionó desinstalé VNC. luego un aptitude y lo reinstalé, pero me sale nuevamente la ventanita pidiendome el password (el que no tengo idea cuál es).
Bueno mi pregunta después de explicar que me pasó es si alguien sabe de como borrar completamente todo lo que tenga que ver con VNC o donde estan las authentication, y luego reinstalar VNC y dejarlo como nuevo, es decir que haga el vncviewer IP y me pueda conectar.


Saludos

---

### Post by _ZeTa on 2009-12-30
en sistema, escritorio remoto aparece la autenticación de la que hablas... si le cambias la contraseña ahi, te va a pedir esa contraseña cuando ingresas desde realvnc en windows.

además aparece la opción de que la dejes sin contraseña, y sin confirmación... sin contraseña no lo recomiendo... 

Espero te sirva.

saludos!

---

### Post by CdK1 on 2009-12-31
El servidor vnc es el win?, si es así, ahí debes setear la passwd...

---

