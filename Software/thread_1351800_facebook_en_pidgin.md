---
title: "facebook en pidgin"
date: 2009-12-10
forum: Software
---

### Post by darkimedez on 2009-12-10
Hola a todos.

Ls cuento que este es mi primer post-tutorial y principalmente me he animado por lo que significa la comunidad del código libre que cada día avanza más y nos permite entre otras innumerables cosas personalizar a nuestro total gusto el aspecto del PC.

Uno de los grandes avances en mi Nb es añadir en ubuntu 9.10 (karmic koala) el cliente de mensajería instantánea Pidgin 2.6.4 con un plugin para poder administrar además el chat del facebook... sí, ver los contactos del chat de facebook en un entorno mucho más cómodo e interactuando además con los contactos de otros chat, como en mi caso, los del messenger y del gtalk.

Primer paso: Instalar Pidgin 

dos formas, directamente desde la terminal ejecutando 

```
sudo apt-get install pidgin
```

 o bien siguiendo la siguiente ruta: Aplicaciones> Centro de software de Ubuntu y en la parte superior derecha de la ventana escriben pidgin e instalan Mensajería de Internet Pidgin. Se verá más o menos así:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=140092&stc=1&d=1260935930[/IMG]

Pero bueno, para las versiones anteriores a Karmic Koala de ubuntu notarán que pidgin viene por defecto, así que para aquellos que tienen ubuntu 9.04 hacia abajo, omitan este paso.

Segundo paso: Instalar plugin.

Bueno, ahora sólo deben descargar desde la página [http://code.google.com/p/pidgin-face...downloads/list]("http://code.google.com/p/pidgin-facebookchat/downloads/list") el archivo de nombre [    pidgin-facebookchat-1.64.deb     ]("http://pidgin-facebookchat.googlecode.com/files/pidgin-facebookchat-1.64.deb")e instalarlo. Como se trata de un archivo .deb, instalarlo costará dos clicks.

Bueno, finalmente podrán ver desde pidgin en "gestionar cuentas" la opción de configurar el chat de facebook en el programa. Yo lo tengo así:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=140095&stc=1&d=1260937201[/IMG]


Si se fijan, junto a los avatares de mis amigos, aparecen además los soportes a los cuales pertenecen sus cuentas, conviviendo en el mismo entorno mis amigos del messenger con los del facebook y si notan más abajo, tambien hay una carpeta con mis amigos del google talk.

Eso es, espero os haya gustado. esta es la mejor forma de hacerlo ya que instalar el plugin-facebookchat desde la terminal ya no es operativo, contrario a lo que aparece en muchos foros googleados.

Saludos.

---

### Post by moreback on 2009-12-11
Prueba a conectarte con el Pidgin mientras tienes la página de Facebook **cerrada**. Por lo que dices se te desconecta el chat en la página así que creo que esto te está causando los conflictos.

Saludos.

---

### Post by darkimedez on 2009-12-11
eso ya lo he intentado y no pasa nada :(

lo raro es que esta es la tercera version de linux en que trato de usar el plugin ese y en ninguno me funcionaba, pero en google parece que a nadie le fallaba... seré yo nomás??

---

### Post by Carlos C on 2009-12-12
¿Cómo lo instalas?

---

### Post by darkimedez on 2009-12-12
en terminal

sudo apt-get install plugin-facebookchat

---

### Post by moreback on 2009-12-12
¿Revisaste después en el listado de plugins de pidgin para configurarlo?

---

### Post by darkimedez on 2009-12-12
no sale en la lista de plugins de pidgin pero si se puede configurar desde el listado de soportes del cliente de mensajeria instantanea.

alguno de ustedes tiene este plugin funcionando??

saludos, dario.

---

### Post by moreback on 2009-12-12
Instalé ese plugin y tampoco me funciona, me arroja el error "Could not retrieve buddy list" así que supongo que ya no es compatible.

PD: me acaba dar otro error de "Chat service currently unavailable" jua

---

### Post by frihed on 2009-12-12
Estimados, tuve el mismo problema con Pidgin que han comentado. Ahora lo vi y empecé a buscar sobre este problema y encontré el bug reportado: [https://bugs.launchpad.net/ubuntu/+source/pidgin-facebookchat/+bug/474872](https://bugs.launchpad.net/ubuntu/+source/pidgin-facebookchat/+bug/474872) . Ahí dan la solución, que es bajar el paquete correspondiente ya arreglado (está acá: [http://code.google.com/p/pidgin-facebookchat/downloads/list](http://code.google.com/p/pidgin-facebookchat/downloads/list)) . Por lo menos, a mí me funcionó el arreglo. ;)

Saludos

---

### Post by darkimedez on 2009-12-13
Gracias frihed por tu aporte, esto por fin es lo que me soluciono el problema, ahora estoy contentisimo con pidgin que me tiene disponible en los tres chat q utilizo: msn, gtalk y ahora fbook!!

gracias xD

---

### Post by _ZeTa on 2009-12-14
darkimedez, xq no haces un howto (tutorial) de como lo lograste?
sería interesante para todos los usuarios nuevos de la comunidad... 
¡te animo a que lo hagas!, asi nos sirve a todos ;)

---

### Post by darkimedez on 2009-12-15
_Zeta es muy facil, solo debes tener instalado pidgin (lo prefiero por montones a empathy) y luego descargar el plugin [http://code.google.com/p/pidgin-face...downloads/list]("http://code.google.com/p/pidgin-facebookchat/downloads/list") para poder ver el chat de facebook en el entorno de la paloma XD

---

### Post by _ZeTa on 2009-12-22
_[Post de la semana]("http://ubuntuforums.org/showthread.php?t=1176055")_: _[22 de Diciembre]("http://www.ubuntu-cl.org/grupos/foro/chat-de-facebook-en-pidgin")_ 2009

---

### Post by jasan212 on 2010-06-18
buen dia para todos 



 ami no me funciona, sale el siguiente error cuando trato de ejecutar  el .deb
 



No se pudo abrir /tmp/pidgin-facebookchat-1.64.deb porque la  aplicación auxiliar asociada no existe. Modifique la asociación en sus  preferencias.
 



tengo instalado el pidgin y funcionando sin problemas, me podrian  colaborar muchas gracias.


 jasan212

---

### Post by moreback on 2010-06-20
sudo apt-get install gdebi

---

### Post by jasan212 on 2010-06-21
nada..... muchas gracias por tu ayuda!!!

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
gdebi ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 10 no actualizados.


alguna otra alternativa???


jasan212

---

### Post by Carlos C on 2010-06-23
> **jasan212 said:**
> buen dia para todos 



 ami no me funciona, sale el siguiente error cuando trato de ejecutar  el .deb
 



No se pudo abrir /tmp/pidgin-facebookchat-1.64.deb porque la  aplicación auxiliar asociada no existe. Modifique la asociación en sus  preferencias.
 



tengo instalado el pidgin y funcionando sin problemas, me podrian  colaborar muchas gracias.


 jasan212
veo que el paquete está en la carpeta /tmp, lo estás tratando de abrir directamente, por eso no te funciona. Debes descargar el paquete (guardarlo, no abrirlo) en tu home y luego, desde ahí, haces doble click sobre el paquete.

---

