---
title: "pasar k3b al Español"
date: 2010-11-05
forum: Software
---

### Post by drazhe on 2010-11-05
Buenas, acabo de instalar **k3b** en mi **Ubuntu 10.10** desde el **centro de Software** y me lo instaló en *ingles*, antes habia podido pasarlo al castellano, instalando un paquete llamado **kde-i18n-es** desde **synaptick** pero cuando lo busco dicho paquete no aparece ahora, hay alguna manera de pasarlo al castellano?


saludos y gracias por su atención!

---

### Post by drazhe on 2010-11-07
Bueno gente, conseguí el dichoso paquete **kde-i18n-es** en está dirección

[B][URL="http://ftp.es.debian.org/debian/pool/main/k/kde-l10n/kde-i18n-es_4.4.5-1_all.deb"]http://ftp.es.debian.org/debian/pool/main/k/kde-l10n/kde-i18n-es_4.4.5-1_all.deb
[/URL][/B]
y para los demás idiomas por si alguno quiere, están todos aquí

**[http://packages.debian.org/sid/all/kde-i18n-es/download]("http://packages.debian.org/sid/all/kde-i18n-es/download")**


Como ven, es un .deb y con solo ejecutarlo, el k3b queda en castellano. Saludos y nuevamente Grcias por su atención!

---

### Post by biale on 2010-11-09
Para K3b, resuelve bien (en todo lugar) las vocales acentuadas? 

Por ejemplo en mi caso aparece "NingÃºn medio presente". Y solo en k3b, en k9copy todo sale de 10!

---

### Post by drazhe on 2010-11-19
> **biale said:**
> Para K3b, resuelve bien (en todo lugar) las vocales acentuadas? 

Por ejemplo en mi caso aparece "NingÃºn medio presente". Y solo en k3b, en k9copy todo sale de 10!

Hola, disculpá la demora, estuve muy ocupado y casi no entraba al foro, encontré este hilo en un blog


*Cito del blog: Ubunteate:*


Muchos de los que usamos GNOME como interfaz gráfica para nuestro maravilloso Sistema Operativo Ubuntu, a veces instalamos aplicaciones de KDE pero al intentar escribir los acentos está dando problemas.

**Solución:**
Vamos a **Sistema/Administración/Soporte de Idiomas**
En “**Sistema de método de entrada de teclado**” cambiamos el valor: **ibus por none**

[CENTER][IMG]http://www.ubunteate.es/wp-content/uploads/2010/11/acentos-300x252.gif[/IMG][/CENTER]

Y listo.




[SIZE="4"]**[Fuente]("http://www.ubunteate.es/solucionar-problemas-con-los-acentos-en-ubuntu")**[/SIZE]




Espero que te ayude, en mi caso personal, no tegno ese problema que mencionas, pero lo tuve en la version 9.10 o 10.04 no recuerdo....

---

### Post by biale on 2010-11-20
Acabo de probar la modificación de ibus por none, pero en mi caso no funcionó.

Lo curioso es que en una misma pantalla aparecen unas cuantas cosas con los locales OK y algunas otras mal. Como si tomara de dos lugares distintos. 

Incluso, algunas pantallas en las "sugerencias al inicio" aparecen bien y otras no (!?)

De todas maneras, muchas gracias por responder.

---

### Post by jhonsr on 2010-11-26
me funciono asi para ubuntu 10.10 :
intente esto
$ sudo apt-get install kde-i18n-es
y me salio el sgte. mensaje:

"El paquete kde-i18n-es no está disponible, pero algún otro paquete hace referencia
a él. Esto puede significar que el paquete falta, está obsoleto o sólo se
encuentra disponible desde alguna otra fuente
Sin embargo, los siguientes paquetes lo reemplazan:
  kde-l10n-es"

asi que le hice caso y me funciono :D
$sudo apt-get install kde-l10n-es

---

### Post by claracc on 2010-12-29
Tengo el mismo problema con k3b y lo he reportado en el ubuntu forums, en desktop environments: [http://ubuntuforums.org/showthread.php?p=10290879#post10290879](http://ubuntuforums.org/showthread.php?p=10290879#post10290879)

He intentado las soluciones que se dan aquí:

En el soporte de idiomas tengo none en vez de ibus (no funciona, los caracteres acentuados siguen saliendo mal).

Tengo instalado el paquete kde-l10n-es, pero tampoco me funciona.

¿Hay alguna otra solución?. Gracias por adelantado.

---

### Post by claracc on 2010-12-29
He solucionado el problema bajándome el paquete k3b-i18n_2.0.0-1_all.deb e instalándolo con gdebi tal y como indica en este link: [http://ubuntu-cosillas.blogspot.com/2010/08/solucionar-problemas-idioma-espanol-en.html](http://ubuntu-cosillas.blogspot.com/2010/08/solucionar-problemas-idioma-espanol-en.html).

Creo que es la misma solución que proponía drazhe: "Bueno gente, conseguí el dichoso paquete kde-i18n-es en está dirección

[http://ftp.es.debian.org/debian/pool/main/k/kde-l10n/kde-i18n-es_4.4.5-1_all.deb](http://ftp.es.debian.org/debian/pool/main/k/kde-l10n/kde-i18n-es_4.4.5-1_all.deb)

y para los demás idiomas por si alguno quiere, están todos aquí

http://packages.debian.org/sid/all/kde-i18n-es/download".

Gracias y saludos

---

