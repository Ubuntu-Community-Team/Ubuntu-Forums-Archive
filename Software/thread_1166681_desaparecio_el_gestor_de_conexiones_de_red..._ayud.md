---
title: "desaparecio el gestor de conexiones de red... ayuda!!!!"
date: 2009-05-22
forum: Software
---

### Post by infernus92 on 2009-05-22
bueno... lo que paso es mas o menos asi...
desde synaptic quise bajar el entorno LXDE. lo busque, lo seleccione con todo lo que me recomienda y pongo aplicar e instalar... se baja e instala y automaticamente se cerro el gestor de conexiones de red (network-manager)
ahora estoy desde el live CD, que lo tiene instalado por defecto
queria saber si desde aca puedo instalarlo o si puedo generar un archivo deb para instalarlo a mano...

muchas gracias si alguien me ayuda... estoy desdesperado sin internet y no quiero tener que usar ventanas...

Saludos

---

### Post by guillermolisi on 2009-05-22
> **infernus92 said:**
> bueno... lo que paso es mas o menos asi...
desde synaptic quise bajar el entorno LXDE. lo busque, lo seleccione con todo lo que me recomienda y pongo aplicar e instalar... se baja e instala y automaticamente se cerro el gestor de conexiones de red (network-manager)
ahora estoy desde el live CD, que lo tiene instalado por defecto
queria saber si desde aca puedo instalarlo o si puedo generar un archivo deb para instalarlo a mano...

muchas gracias si alguien me ayuda... estoy desdesperado sin internet y no quiero tener que usar ventanas...

Saludos
Como sabes que esta desinstalado ?
Te fijaste en Synaptics para ver como figura ?

Luego, tenes por lo menos dos alternativas al NM:

[LIST]
[*]Configurar y usar las interfaces de red a mano (editando el archivo /etc/network/interfaces)
[*]Usar Wicd
[/LIST]
Este ultimo ha tenido muy buena recepcion entre la gente porque funciona donde el NM falla.

Personalmente uso la primera alternativa (o sea, soy mi propio NM :))

---

### Post by infernus92 on 2009-05-22
gracias por responder... si, me fije desde synaptic, y me desinstalo network-manager y network-manager-gnome
yo me conecto a internet a traves de un modem 3G, Wicd tiene compatibilidad? ya viene instalado en ubuntu por defecto? o sino como lo bajo?
sino... que tengo que escribir en ese archivo para hacer funcionar internet? como me conecto?

Saludos

---

### Post by atari130xe on 2009-05-22
Me pasó algo similar al instalar Jaunty hace poco a un amigo, tiene conexion ADSL y de repente al querer reconfigurar la conexion, (no se conectaba automáticamente) la placa de red (eth0) habia "desaparecido", me dijeron que se puede usar (como hasta Intrepid) pppoeconf, lo habia echo pero seguía sin conectarse de manera automática, la única solución "molesta" por el momento es que reinicie la PC (se conecta automáticamente) y luego antes de apagarla se desconecte destildando la conexión, para que al volver a encenderla no se trunque la conexión, me suena a bug, insisto, no me pasó a mi solo sinó que inclusive en distintos foros (acá mismo en el foro Network) hay varios casos similares...

---

### Post by staar on 2009-05-22
> **infernus92 said:**
> gracias por responder... si, me fije desde synaptic, y me desinstalo network-manager y network-manager-gnome
yo me conecto a internet a traves de un modem 3G, Wicd tiene compatibilidad? ya viene instalado en ubuntu por defecto? o sino como lo bajo?
sino... que tengo que escribir en ese archivo para hacer funcionar internet? como me conecto?

Saludos

para conectarte, sin el nm, podés usar wvdial, un marcador ppp (las conexiones 3g son similares al antiguo dial-up) bastante fácil, solo tenés que editar el archivo /etc/wvdial.conf con los datos correctos, que proveedor tenés?

saludos

---

### Post by guillermolisi on 2009-05-22
> **infernus92 said:**
> gracias por responder... si, me fije desde synaptic, y me desinstalo network-manager y network-manager-gnome
yo me conecto a internet a traves de un modem 3G, Wicd tiene compatibilidad? ya viene instalado en ubuntu por defecto? o sino como lo bajo?
sino... que tengo que escribir en ese archivo para hacer funcionar internet? como me conecto?

Saludos
No se si Wicd administra conexiones 3G. Se que en muchos casos fue una muy buena alternativa para los que usan WiFi y experimentaron/sufrieron con el NM.

Wicd esta en los repositorios (universe) y no viene instalado por defecto ya que es el NM el elegido para Ubuntu.

Que tipo de conexion estas usando para Internet ?

---

### Post by Apipote on 2009-05-22
Hace mucho que sufro (uno mas de muchos, según leo), NM. 
No hay caso, está repleto de bugs.

Wicd, es hasta hoy una salvación para mí.

Probalo, está en Synaptic y elimina automáticamente NM, para evitar conflictos.

Suerte

---

### Post by staar on 2009-05-22
Wicd NO gestiona conexiones ppp (las 3g incluidas), por lo menos la última vez que lo probé, no tenía esa funcionalidad...

sin nm, para una conexión 3g, los más fácil es usar wvdial, que viene instalado por defecto, asi que sólo hay que modificar el wvdial.conf con los datos correctos para el proveedor...

saludos

---

### Post by guillermolisi on 2009-05-22
Y si el modem ADSL esta como router y hace el discado, haria falta Wvdial ? (se nota que uso cablemodem ?) :)

---

### Post by infernus92 on 2009-05-22
es una conexion 3g... el proveedor es movistar y de casualidad tengo anotada la configuracion que tenia en el NM... y mientras tanto solo tengo internet desde el LiveCD

que tengo que poner en el wvdial.conf??

saludos

---

### Post by pablo.s on 2009-05-22
Si habilitás el repositorio
del CD-Rom en Synaptic,
podés reinstalar el Network
Manager otra vez.
No te compliqués con
wvdial.conf.

---

### Post by infernus92 on 2009-05-22
gracias pablo... pero ya intente eso... y no me funciono... cuando intento instalarlo me salta un cartel de error... no me acuerdo que dice... y la verdad no tengo muchas ganas de reiniciar la computadora para leerlo a menos que sea necesario...
si hace falta, avisenme que lo hago... pero preferiria no tener que hacerlo...

saludos

EDITO: ah... tambien trate de instalar wvdial porque tampoco lo tengo instalado y tampoco me funciono...

---

### Post by infernus92 on 2009-05-23
bueno... al final lo pude solucionar... baje el "network-manager" y el "network-manager-gnome" de internet y los instale manualmente
dejo las direcciones por si alguien tiene el mismo problema que yo

network-manager: [http://packages.ubuntu.com/es/jaunty/i386/network-manager/download](http://packages.ubuntu.com/es/jaunty/i386/network-manager/download)

betwork-manager-gnome: [http://ar.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.7.1~rc4.1-0ubuntu2_i386.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.7.1~rc4.1-0ubuntu2_i386.deb)

Saludos

---

