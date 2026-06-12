---
title: "Problema de refresco en VNC desde el cliente."
date: 2007-09-04
forum: Software
---

### Post by verahert on 2007-09-04
Hola, estoy intentando acceder a mi escritorio gnome desde vnc de windows cuando me conecto, el ratón se mueve y mi ubuntu reacciona a las acciones del ratón pero desde el pc donde estoy haciendo el vnc, no se me refresca la pantalla. Saben como se puede solucionar?

Saludos.

---

### Post by jpmorelli on 2007-09-04
Estoy justamente con las mismas pruebas, a mi me pasa lo mismo pero ya detecté que es el compiz habilitado. Si el mismo no está funcionando anda bárbaro. Estamos hablando de lo mismo ???
El KDE en cambio funciona aunque Compiz esté funcionando.
Alguien con más data ?

---

### Post by verahert on 2007-09-04
Tal cual desactive los efectos de escritorio y anda pero lo que noto que es MUY lento y lo estoy usando en lan ni me imagino en inet lo que debe ser, y como el nxserver no me sirve me tendre acostumbrar a la lentitud del VNC.

Saludos.

---

### Post by jpmorelli on 2007-09-04
verahert, probá el paquete xvnc4viewer, anda un poquito mejor

sudo apt-get install xvnc4viewer

desde la consola tirás el comando y si no me equivoco te abre la pantalla gráfica, etc

---

### Post by verahert on 2007-09-04
Ya lo instale en linux gracias!, y alguno mejor que el RealVNC en windows ?

Saludos.

---

### Post by rl_ar on 2010-09-26
si estas usando Cmpiz Fusion seleciona en la opción "Select Window Manager" la opción Metacity

---

