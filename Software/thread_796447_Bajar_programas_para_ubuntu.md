---
title: "Bajar programas para ubuntu"
date: 2008-05-16
forum: Software
---

### Post by damian168 on 2008-05-16
Soy nuevo en esto, pero el problema q tengo es que la pc a la que le instale ubuntu no esta conectada a internet, alguien me puede decir como hacer para bajar los paquetes o los programas para instalarle, ya que nisiquiera tengo los codecs para escuchar musica.:(
[RIGHT]Muchas gracia![/RIGHT]

---

### Post by Hernán-Amaya on 2008-05-16
te recomiendo que entres en la guía de ubuntu que hay muchas cosas para los noveles como nosotros a mi me sirvió mucho

[http://www.guia-ubuntu.org](http://www.guia-ubuntu.org) 

y acá tenes algo que te puede servir 

[http://www.guia-ubuntu.org/index.php?title=A%C3%B1adir_aplicaciones#Instalar_paquetes_sin_internet](http://www.guia-ubuntu.org/index.php?title=A%C3%B1adir_aplicaciones#Instalar_paquetes_sin_internet)

---

### Post by damian168 on 2008-05-16
Grax hernan, me ayudo mucho, pero el problema q mew queda ahora es de donde sacar los archivos .dev. o sea, de donde descargarlos. no hay alguna pagina, por que generalmente yo me conecto de un ciber, y la maquinas tienen windows.

---

### Post by margori on 2008-05-16
> **damian168 said:**
> Grax hernan, me ayudo mucho, pero el problema q mew queda ahora es de donde sacar los archivos .dev. o sea, de donde descargarlos. no hay alguna pagina, por que generalmente yo me conecto de un ciber, y la maquinas tienen windows.

Aca tenes dos lugares donde podes descargar cosas interesantes, como para que vayas viendo como es el manejo de los paquetes:

[http://gnomefiles.org/index.php](http://gnomefiles.org/index.php)
[http://www.getdeb.net/](http://www.getdeb.net/)

Aunque lo mejor, mas facil de descargar y tener los programas actualizados, es utilizar los repositorios, oficiales de canonical o de terceros.

Aca tenes una documentacion clave sobre este tema:

[http://doc.ubuntu-es.org/Repositorios](http://doc.ubuntu-es.org/Repositorios)

---

### Post by sajnox on 2008-05-17
Hace un rato que venia viendo como era el tema de la descarga de paquetes sin internet y me parece que la mejor manera es la siguiente:

1) En la maquina sin internet elegir con el synaptic cuales son los paquetes a descargar (es importante que sea en la maquina sin internet por que de esta manera verifica las dependencias)

2) Una vez que elegiste todos los paquetes en synaptic elegis en archivo/generar script de descarga y guardas el archivo que genera

3) Si usas otra maquina con Linux ejecutas el script y te lo descarga a la carpete desde donde ejecutas el archivo. Si estas en un locutorio y la maquina tiene windows (que es lo mas probable) abris el script con el bloc de notas o cualquier editor de textos y vas a ver que el script es algo como lo siguiente:
```

#!/bin/sh
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xaw3d/xaw3dg_1.5+E-15_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/3/3dchess/3dchess_0.8.1-12_i386.deb
```

Lo que tenes que hacer es copiar por cada linea todo desde el http: en adelante (el http incluido) y pegarla en el navegador, esto va a hacer que descargue el archivo .deb a la maquina.

4) Una vez que tenes todos los .deb los llevas a la maquina donde los vas a instalar

5) Con la terminal (parado en la carpeta donde copiaste los .deb) ejecutas

```
sudo dpkg -i *.deb
```

Listo !!! Esto deberia instalar todo lo que seleccionaste con el synaptic y sin romperte la cabeza con las dependencias.

Contanos si te sirvio

Saludos

---

### Post by margori on 2008-05-17
> **sajnox said:**
> 1) En la maquina sin internet elegir con el synaptic cuales son los paquetes a descargar (es importante que sea en la maquina sin internet por que de esta manera verifica las dependencias)

Hay un problema en esta receta. La maquina que no tiene internet no puede descargar la lista de paquetes en los repositorios -> Synaptic estaría vacío y no puede armar las dependencias. :(

Esta buena la idea, pero te salteaste ese pequeño detalle.

Voy a dar mi opinion debido a mi experiencia en la migracion de win a linux y estoy seguro que me caeran mil objeciones. Varias veces instale Mandrake, SuSE, Ututo, Fedora, y demás pero siempre me volvia a win: no tenia internet -> no tenia ni documentacion ni forma de tener nuevos programas. Las dependencias eran un infierno y todo tenia que ser manual. Era un infierno. Uno no puede estar en linux si no tiene internet.

Se aceptan opiniones, sobre todo contructivas y que respondan a esta respuesta: ¿Cómo se hace para un novato sin internet pueda llegar a linux?

---

### Post by sajnox on 2008-05-17
Gracias Margori por la correccion

Evidentemente tuve mas buenas intenciones que conocimiento.

Me queda una pregunta, no seria posible pasarle a la maquina sin internet una lista de paquetes para que synaptic la tome y construya las dependencias ??

Si bien no le serviria para TODO, le serviria para lo que hay en los repositorios de Ubuntu que eso per se es bastante. Otra pregunta, si el repositorio se actualiza y la maquina sin internet no, al ir a buscar un paquete, via un script de descarga, no lo encontraria no?

---

### Post by narf y akim on 2008-05-18
Hola, hay una página que uso muy seguido para instalarle cosas a mi vieja pc. Buscá Nonetdebs: [http://nonetdebs.unixpod.com/](http://nonetdebs.unixpod.com/)
Ahora justo no la puedo abrir. Pero creo que tiene instrucciones fáciles.

---

### Post by sajnox on 2008-05-18
Excelente aporte, no lo conocia y me parece que es la mejor solucion de las que vi hasta ahora (aunque la verdad no fueron muchas).

A la noche lo miro con un poco mas de detenimiento a ver si lo puedo hacer andar.

---

### Post by sajnox on 2008-05-18
Esta MUY BUENO!!!! Recien lo probe y parece andar muy bien.

Tenemos que tenerlo en cuenta para recomendarlo a todos los que se manejan sin internet

---

### Post by Air23 on 2008-05-18
Alguien sabe si esto: [http://nonetdebs.unixpod.com/](http://nonetdebs.unixpod.com/) sirve tambien para Xubuntu? (estoy por instalarlo en mi vieja Pentium III que no tiene ni placa de red)

---

### Post by damian168 on 2008-09-17
Muchas gracias a los q me contestaron, me re colgue, y ni me acorde del post, y cuando volvi a seguir buscando me encontre con esto, ahora voy a probar, a ver q pasa...
Wish me LUCK!

---

### Post by damian168 on 2008-09-17
No se si sere yo q tengo mala suerte o q, pero entro a nonetdebs y me encuentro con este mensaje: "registration is no longer available after problems we've had with it in the past."
Por lo q yo entiendo de ingles, significa, Q NO M PUEDO REGISTRAR!!!
Alguien sabe como podria usarlo sin estar registrado o algo asi???????

---

### Post by EnriqueK on 2008-09-17
A ver, te dejo este enlace en donde en otro foro trato de detallar el proceso completo para instalar todo lo que se quiera sin tener internet, solo un poco de paciencia por que ese sitio está con algo de problemas .
[http://www.ubuntu-es.org/index.php?q=node/94529](http://www.ubuntu-es.org/index.php?q=node/94529)
Otra cosa, el sitio de nonetdebs hace ya tiempo que no funciona, mejor así por que al menos a mi no me convence eso de estar dependiendo de un servicio que en cualquier momento desaparece (tal como ocurrió)  una vez le tomes la mano al proceso, los codecs los puedes descargar con el nombre de w32codecs.
Después de leer todo te darás cuenta que la clave de todo radica en tener los índices de repositorios , el método explicado detalla para el caso de usar el Live CD de instalación, hay otras maneras, por ejemplo que alguien te pase esos archivos, yo podría hacerlo y subirlo a Rapidshare, pero el asunto es que uso Ubuntu 8.04  y realmente no se si los índices de repositorios de Ubuntu serán los mismos que Xubuntu, si querés averigualo y me das el OK para que te los suba a Rapidshare.

---

### Post by damian168 on 2008-09-19
EnriqueK tu link no funca.... :confused:
Te agradezco q me quieras subir los archivos a rapidshare, pero en realidad yo quiero apreder a bajarme algunos programas y no da pedirte cada cosa q me quiera bajar.... (by the way, yo uso el Ubuntu 8.04 de 64 bit)
Tambien te cuento q intente bajarme los paquetes de packages.ubuntu.com/ y me di cuenta q tengo q bajar las dependencias de cada cosa q bajo, y las dependencias de lo q quiero bajar a su vez tienen otras dependencias!!!!! es una locura... te juro q intente bajarlos pero, ya me estaba volviendo loco de tantas dependencias y lo deje ahi.

---

### Post by EnriqueK on 2008-09-19
Ese sitio anda como el tujes últimamente, pero paciencia que se compone.
El método se basa en **clonar** los índices de repositorios de otro equipo o usar el** Live CD **de instalación en otro equipo , cargarle un sources.list , luego hacés sudo apt-get update , esto hace que se carguen los índices en la carpeta **lists **situada en** /var/lib/apt** , lo que resta es llevar es carpeta** lists **y el** sources.list** a tu equipo y allí hacer nuevamente sudo apt-get update , lo que queda es usar Synaptic para generar un script de descargas de paquetes que podrás efectivizar en cualquier otro equipo. En el enlace que puse está todo detallado, paciencia.
Personalmente te recomiendo instalar un módem telefónico que cuestan entre  10 a 20U$  y tenerlo  solo para generar y actualizar los índices de repositorios usando servicios temporales a internet que solo cobran la llamada telefónica.

---

### Post by juanman on 2008-09-24
No mas inventos raros gente :P Acaba de salir un soft q, creo, es la solucion al problema. Se llama USPC (Ubuntu Simple Package Crawler), y da soporte para las versiones de ubuntu dapper, feisty, gutsy, hardy y la futura intrepid, en las arquitecturas i386 y amd64.
Es un programita desarrollado en pyqt en el q se puede buscar un paquete a instalar y el mismo te lista las dependencias necesarias (se puede desactivar la opcion para q ignore las dependencias q ya vienen por defecto en la distro), para despues descargarlas (por el mismo programa) desde archive.ubuntu.com...
Hay paquetes para ubuntu (intrepid, pero funciona en hardy) y windows. Si bien es la primer version, cumple con su funcion y es muy util para la gente q no tiene internet y baja el soft para instalar desde un ciber...

El finde, cuando tenga tiempo, voy a hacer un howto detallado...

El link a kde-apps: [http://www.kde-apps.org/content/show.php/uspc+-+Ubuntu+Simple+Package+Crawler+++?content=90015](http://www.kde-apps.org/content/show.php/uspc+-+Ubuntu+Simple+Package+Crawler+++?content=90015)
Y la pagina oficial: [http://code.google.com/p/uspc/](http://code.google.com/p/uspc/)

---

### Post by pablo atheist on 2008-09-24
fijate si te sirven estos links
[http://tuxpepino.wordpress.com/2007/08/29/tip-instalar-paquetes-sin-internet/](http://tuxpepino.wordpress.com/2007/08/29/tip-instalar-paquetes-sin-internet/)

[http://tuxpepino.wordpress.com/2007/10/02/%C2%BFconocias-aptoncd/](http://tuxpepino.wordpress.com/2007/10/02/%C2%BFconocias-aptoncd/)

saludos

---

### Post by vulkno on 2008-10-09
Si lo que desas es descargar los paquetes y actualizaciones que necesita ubuntu, xubuntu, kubuntu, etc. Yo hize un script para un amigo con tu mismo problema (acceso a internet). Este es el link [http://vulkno.blogspot.com/2008/10/netubu-descarga-y-actualiza-ubuntu-sin.html](http://vulkno.blogspot.com/2008/10/netubu-descarga-y-actualiza-ubuntu-sin.html) espero que te ayude. bye :guitar:

---

