---
title: "OpenOffice.org | viñetas | salto inesperado ?"
date: 2009-09-16
forum: Software
---

### Post by ppellet on 2009-09-16
Estimados

Cada vez que hago clic en alguna viñeta, dentro de un documento de texto de OOo, me cambia la pantalla a cualquier otra aplicación que tenga abierta. Si no tengo otras aplicaciones me muestra en primer plano los gadgets que tengo activados en mi escritorio (un reloj, calendario y otras cosas así).

Se ha transformado en un asunto muy molesto, ya que necesito trabajar con rapidez y, bueno, esto no debería pasar.

Uso Ubuntu 9.04, con OpenOffice.org 3.0, configurado para trabajar por defecto con .odt.

¿Alguien sabe porqué ocurre esto o cómo puedo solucionarlo?...

Saludos,

---

### Post by AlexDDR on 2009-09-16
Puedes actualizar a la version 3.1 en Jaunty si agregas

los repositorios:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) jaunty main

deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) jaunty main

y despues actualizando el sistema


talvez el bug ya se haya solucionado

saludos

---

### Post by ppellet on 2009-09-17
AlexDDR muchas gracias por tu ayuda. Acabo de realizar las operaciones que me indicas y comenzaré a probar como funciona todo.

Sin embargo, al actualizar me indica que me falta la "llave pública": [I]W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 60D11217247D1CFF
[/I]
¿puedes ayudarme con eso?...

Saludos cordiales,

---

### Post by AlexDDR on 2009-09-17
tienes que abrir una consola y anotar estos dos codigos que corresponden a importar la clave del repositorio de openoffice

gpg --keyserver subkeys.pgp.net --recv 60D11217247D1CFF
gpg --export --armor 60D11217247D1CFF | sudo apt-key add -

y como te darás cuenta el codigo que aparece corresponde al codigo que te arroja el error, por lo que si te pasa de nuevo solo tiene que cambiar el codigo de letras y numeros. Hay un scrpt que realiza eso de manera automatica para los repositorios pero yo no he querido instalarlo

saludos

---

### Post by ppellet on 2009-09-17
AlexDDR
¡Muchas Gracias! :)
Un 7 compadre

Acabo de realizar todos los pasos que me indicas y ha resultado todo bien. He probado el nuevo OOo y funciona bien respecto del problema que inicio este hilo.

Las claves funcionaron sin problemas y puedo actualizar normalmente desde consola.

Felices Fiestas para ti y todos los ubunteros de Chile, tiqui tiqui ti...!!!

---

### Post by AlexDDR on 2009-09-17
que bueno, yo tambien actualicé hace poo el openoffice y ahora me funciona mucho mejor


feliz 18 tb a todos 

saludos

---

