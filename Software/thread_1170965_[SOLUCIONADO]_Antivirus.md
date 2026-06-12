---
title: "[SOLUCIONADO] Antivirus"
date: 2009-05-26
forum: Software
---

### Post by lorenilla on 2009-05-26
Hola!

Acabo de actualizar a Ubuntu 8.04 e instalé el av clamtk V. 3.05-1,y  cuando quiero actualizar la firma de virus me arroja lo siguiente:
"Debes ejecutar este programa como administrador (root) para instalar actualizaciones"
La verdad no entiendo a qué se refiere, menos qué debo hacer, ojala me puedan ayudar, 

saludos;)

---

### Post by AlexDDR on 2009-05-26
ejecutar como root se refiere a ejecutar el sistema como administrador, el que tiene total acceso a este, ya que uno normalmente ocupa una cuenta de usuario, que carece de privilegios para varias funciones vitales del sistema. Esto se hace como medida de seguridad 

para poder ejecutar en modo de super  usuario o root o administrador debes en una consola (aplicaciones ---> accesorios >> Terminal) debes anteponer  sudo al nombre del programa

ejemplo:  "sudo gedit"


Tambien puedes hacer lo mismo con entorno grafico, para ello debes apretar ALT+F2 y en el cuadro de dialogo escribir

ejemplo:  "gksu gedit"

la difererencia es que el gksu hace todo en modo gráfico

Te recomiendo que desde el menu crees un aceso directo hacia el escritorio o el panel y agregues gksu al nombre del ejecutable del antivirus


saludos

---

### Post by flucoe on 2009-05-27
Un detalle: En Ubuntu hay un problema que impide actualizar de manera sencilla. De acuerdo a la página de [Clamtk]("http://clamtk.sourceforge.net/") antes de entrar en modo root debes hacer lo siguiente:

1) sudo /etc/init.d/apparmor stop

2) Entrar en modo root: sudo clamtk

3) Actualizar

4) sudo /etc/init.d/apparmor start

y listo

Saludos!

---

### Post by lorenilla on 2009-05-27
Gracias!!!!!!!!!!!!!
Alex y Flucoe, muy amables
funcionó según las instrucciones de Alex, pues al seguir los pasos que me indicas flucoe, dice que desconoce el fichero o directorio
todo era cosa de entrar en modo root y listo antivirus actualizado.
Gracias otra vez, ah y me encant{o eso de win free since, jajja, espero poder tener mi propia fecha, 
saludos:p

---

