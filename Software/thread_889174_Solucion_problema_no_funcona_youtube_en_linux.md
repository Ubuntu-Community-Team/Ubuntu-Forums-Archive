---
title: "Solucion problema no funcona youtube en linux"
date: 2008-08-13
forum: Software
---

### Post by Eduardo Natali on 2008-08-13
Hola, 

Les dejo a continuacion como solucione los problemas para ver los videos de youtube.

Distribucion: Ubuntu 8.04 - Hardy Heron
Tener instalado Flash player, lo pueden bajar desde [www.adobe.com](www.adobe.com)
Tener cerrado el firefox

Pasos
1) En Gnome ir a: Sistema > Administracion > Gestor de paquetes Synaptic
2) Buscar: Gnash
3) Con el boton derecho del mouse, marcar para re-instalar los siguientes paquetes:

gnash
gnash-common
gnash-cygal
gnash-tools
klash
konqueror-plugins-gnash
mozilla-plugin-gnash

4) Una vez seleccionados para reinstalar, darle al boton aplicar
5) Abrir mozilla firefox ir a youtube y cuando eligen un video hacen 1 click izquierdo y ya lo tienen andando.

Espero que les sirva,
Saludos Edu..

---

### Post by pol666 on 2008-08-13
Estas usando GNASH? como anda? algun problema hasta el momento?

---

### Post by Eduardo Natali on 2008-08-14
Hola,

Si estoy usando Gnash ningun problema todo funciona muy bien!

Saludos Edu

---

### Post by pol666 on 2008-08-14
mmm pero hay algo que noi me cierra por que decis que tenemos que tener el Adobe Flash player instalado si despues usas Gnash?, me gustaria saber cual plugin es el que se esta ejecutando por que hasta donde se, el Gnash andaba muy mal (como si el adobe no ¬¬)

---

### Post by faktorqm on 2008-08-15
a mi el flash de adobe me anda perfecto con opera 9.51 y tambien con firefox 3. lo unico que si abro los dos al mismo tiempo y abro paginas en flash, se nota la disminucion de rendimiento muy rapido... pero bueno. gnash la verdad andaba feo feo la ultima vez que lo postearon (y no fue hace mucho...) salu2!

---

### Post by pol666 on 2008-08-15
la verdad es que no entiendo flash, su comportamiento es muy distinto aca en Debian o el Ubuntu 7.10 que en Ubuntu 8.04, tengo la misma version y todo. 

por ejemplo en 7.10 y ahra en Debian. 
flash anda bien solo que cuando hay muchas animaciones en una pagina se tilda hasta el infinito. tambien tengo el problema solo den Debian que no puedo subir ni bajar el volumen de los videos de youtube

en 8.04, por pulseaudio esta el bug que se cierra Mozilla, es muy molesto, igual no veo disminucion de rendimiento.



............

con lo que explicas vos  Eduardo Natali me parece que estas usando el plugin de Adobe y si bien instalaste Gnash no esta funcionando este sino el primero

---

### Post by sebasthian777 on 2008-09-01
> **pol666 said:**
> la verdad es que no entiendo flash, su comportamiento es muy distinto aca en Debian o el Ubuntu 7.10 que en Ubuntu 8.04, tengo la misma version y todo. 

por ejemplo en 7.10 y ahra en Debian. 
flash anda bien solo que cuando hay muchas animaciones en una pagina se tilda hasta el infinito. tambien tengo el problema solo den Debian que no puedo subir ni bajar el volumen de los videos de youtube

en 8.04, por pulseaudio esta el bug que se cierra Mozilla, es muy molesto, igual no veo disminucion de rendimiento.



............

con lo que explicas vos  Eduardo Natali me parece que estas usando el plugin de Adobe y si bien instalaste Gnash no esta funcionando este sino el primero


up al bug ese... muy molesto la verdad...

tenes idea si se encontro solucion?

(perdon por re-abrir este post viejo pero encontre que te pasa lo mismo que a mi y queria saber si se puede solucionar)

---

