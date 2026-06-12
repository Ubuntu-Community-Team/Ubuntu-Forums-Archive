---
title: "No me aparece el menú de SALIR + Password de Root"
date: 2010-03-17
forum: Software
---

### Post by sol03 on 2010-03-17
ola,

Es la primera vez que installo Ubuntu en cualquiera de sus versiones y  soy un usuario principiante. Yo trabajo en la oficina con otra  distribución (como usuario final) y decidí instalar Linux en casa para  conocer mejor el entorno. En el Menú de Inicio en Sistema no me aparece  el Menú de Salir, ni botones u opciones para apagar, cerrar sesión,  reiniciar, etc. ¿cómo puedo llevar a cabo estas tareas que no sea con  los botones de apagado o comandos de cónsola?.

Adicionalmente me gustaría saber el password por defecto de root cuando  se instala desde el CD porque aunque tengo un usuario administrativo no  es el root.

Perdonen mi ignorancia pero es mi primera vez.

Gracias de antemano por la ayuda,

SA
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8984284") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[]("http://ubuntuforums.org/editpost.php?do=editpost&p=8984284")[IMG]http://twitter.com/favicon.ico[/IMG][IMG]http://www.google.com/favicon.ico[/IMG][IMG]http://static.smarterfox.com/media/wiki-favicon-sharpened.png[/IMG][IMG]http://static.smarterfox.com/media/popup_bubble/oneriot-favicon.ico[/IMG]

---

### Post by leonardomdq on 2010-03-18
Hola sol, el indicador si no lo quitaste lo tenes en el panel superior sobre la derecha.
Si por algun motivo no lo tenes podes agregarlo posandote en el panel superior, boton derecho del mouse y vas a "añadir al panel" y buscas "miniaplicación de indicador de sessión" y lo podes añadir de ahi.

El password de root tenes que crearlo, de la siguiente manera:

Abris una terminal (aplicaciones -> accesorios -> Terminal) y pones lo siguiente:

```
sudo passwd root
``` y luego digitas tu clave para root. Con eso la activas.

Para entrar como root en la terminal pones:

```
su
```  presionas "enter" y escribis la clave root.


Saludos ;)

---

### Post by sol03 on 2010-03-18
> **leonardomdq said:**
> Hola sol, el indicador si no lo quitaste lo tenes en el panel superior sobre la derecha.
Si por algun motivo no lo tenes podes agregarlo posandote en el panel superior, boton derecho del mouse y vas a "añadir al panel" y buscas "miniaplicación de indicador de sessión" y lo podes añadir de ahi.

El password de root tenes que crearlo, de la siguiente manera:

Abris una terminal (aplicaciones -> accesorios -> Terminal) y pones lo siguiente:

```
sudo password
``` y luego digitas tu clave para root. Con eso la activas.

Para entrar como root en la terminal pones:

```
su
```  presionas "enter" y escribis la clave root.


Saludos ;)

Gracias por tu ayuda

---

### Post by sol03 on 2010-03-18
Gracias. Resuelto

---

