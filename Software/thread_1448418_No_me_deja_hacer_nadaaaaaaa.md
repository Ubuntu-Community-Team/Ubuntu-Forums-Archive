---
title: "No me deja hacer nadaaaaaaa"
date: 2010-04-06
forum: Software
---

### Post by Patologico22 on 2010-04-06
Hola, he instalado ubuntu, no es la primera vez... pero no me considero mas que un simple usuario y no tengo interes en mucho mas, ya que soy profesional de la construcción y no de la informatica... 
En esta instalación que he hecho, no puedo actualizar, detectar sofware ni nada por el estilo, al parecer solo conectarme a internet....
Por ejemplo, cuando voy a Sistema / Administración / Pruebas del hardware... me pide mi clave y luego me da el siguiente mensaje:

No se pudo ejecutar /usr/bin/hwtest-gtk como usuario root.

 El mecanismo de autorización subyacente (sudo) no le permite ejecutar este programa. Contacte con su administrador de sistemas.

Espero que me puedan ayudar... Gracias

---

### Post by guillermolisi on 2010-04-06
Que usuario estas utilizando cuando queres llevar a cabo la prueba de hardware ? Uno creado durante la instalacion o directamente el usuario root ?

> No se pudo ejecutar /usr/bin/hwtest-gtk [COLOR=Blue]como usuario root[/COLOR].Este mensaje dice claramente que estas usando root como usuario cuando deberias utilizar uno creado en tiempo de instalacion o posterior a ese proceso distinto de root.

---

### Post by chulelinux on 2010-04-07
Patológico22, creo también que el problema ha sido que no creaste un usuario en la instalación... No me ha pasado nunca y calculo que instalaste Karmic (9.10) y que puede probarse si es esto:  creando un usuario desde Sistema/Administración/Usuarios y grupos (poniendo como contraseña de usuario la misma que estas usando para no hacerte lío)

slds

---

