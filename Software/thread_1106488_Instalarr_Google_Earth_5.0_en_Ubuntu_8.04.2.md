---
title: "Instalarr Google Earth 5.0 en Ubuntu 8.04.2"
date: 2009-03-25
forum: Software
---

### Post by drazhe on 2009-03-25
Hola quiero instalar el Google earth 5.0 en mi ubuntu 8.04.2, encontre una pagina que me dice mas o menos como hacerlo, el problema es que una vez instalado, y despues de decirme "instalacion completa... blablala" cuando abro el programa este se cierra al instante... como se soluciona o que hice mal?

Admito que son un extremo novato en esto de linux y ubuntu, asi que lo mas seguro es que haya hecho alguna macana...

---

### Post by pablo.s on 2009-03-25
Tenés tarjeta de video 3D? Digamos con procesador de Nvidia o ATI? Puede ser 
una de las causas. Saludos.

---

### Post by drazhe on 2009-03-25
tengo una MSI GeForce 6200TC (TurboCache)

En esta misma maquina tengo el XP y ahi funciona el Google Earth...

no si sirve de dato, pero para instalarlo hice lo que decia este sitio

[http://virtualizado.net/instalar-google-earth-en-ubuntu-804/](http://virtualizado.net/instalar-google-earth-en-ubuntu-804/)

---

### Post by pablo.s on 2009-03-25
> **drazhe said:**
> tengo una MSI GeForce 6200TC (TurboCache)

Te propongo algo: ejecutá Google Earth desde una terminal y si sale un error 
(o el mensaje que sea) postealo acá. Eso va a orientar bastante.
Si tenés Compiz ejecutandose paralo antes de ejecutar GoogleEarth.

---

### Post by drazhe on 2009-03-25
> **pablo.s said:**
> Te propongo algo: ejecutá Google Earth desde una terminal y si sale un error 
(o el mensaje que sea) postealo acá. Eso va a orientar bastante.
Si tenés Compiz ejecutandose paralo antes de ejecutar GoogleEarth.

y como se si tengo compiz ejecutandose? te repito, soy un extremo novato en ubuntu y linux en general...

---

### Post by drazhe on 2009-03-25
cuando ejecuto el google earth desde el terminal, me tira este mensaje

Warning: Unable to create prefs directory '/home/nicolas/.googleearth'. El fichero ya existe.

pero cuando ejecuto el programa que supuestamente esta instalado, antes de abrir el programa me tira estos mensajes de error

al intentar ejecutar el programa, simplemente se cierra, dando el siguiente error:
&#8220;Could not create directory:
/root/.googleearth/Cache&#8221;

Y luego:
&#8220;Google Earth could not write to the current cache or myplaces file location. The values will be set as follows:
My Places Path: &#8216;/home/alexc2/.googleearth&#8217;
Cache Path: &#8216;/home/alexc2/.googleearth/Cache&#8217;&#8221;

al dar click en el boton de aceptar, se cierra.

---

### Post by drazhe on 2009-03-25
Acabo de bajar y reinstalar el programa, y una vez mas lo mismo... pero esta vez salto este mensaje:

nicolas@nicolas-desktop:~$ cd /home/nicolas/Escritorio
nicolas@nicolas-desktop:~/Escritorio$ chmod 770 GoogleEarthLinux.bin
nicolas@nicolas-desktop:~/Escritorio$ sudo ./GoogleEarthLinux.bin
[sudo] password for nicolas: 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.0.11337.1968..............................................................
loki_setup: Valor del tamaño sospechoso para la opción option

loki_setup: Valor del tamaño sospechoso para la opción option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...
Warning: Unable to create prefs directory '/root/.googleearth'. El fichero ya existe.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
nicolas@nicolas-desktop:~/Escritorio$

---

### Post by pablo.s on 2009-03-25
> **drazhe said:**
> Acabo de bajar y reinstalar el programa, y una vez mas lo mismo... pero esta vez salto este mensaje:

nicolas@nicolas-desktop:~$ cd /home/nicolas/Escritorio
nicolas@nicolas-desktop:~/Escritorio$ chmod 770 GoogleEarthLinux.bin
nicolas@nicolas-desktop:~/Escritorio$ sudo ./GoogleEarthLinux.bin

El problema está que no tenés que ejecutar la instalación con sudo. Está mal 
el tutorial que seguiste. Repetí la instalación y probá otra vez.

---

### Post by Air23 on 2009-03-25
> **drazhe said:**
> Hola quiero instalar el Google earth 5.0 en mi ubuntu 8.04.2, encontre una pagina que me dice mas o menos como hacerlo, el problema es que una vez instalado, y despues de decirme "instalacion completa... blablala" cuando abro el programa este se cierra al instante... como se soluciona o que hice mal?

Admito que son un extremo novato en esto de linux y ubuntu, asi que lo mas seguro es que haya hecho alguna macana...
Creo que tu problema es este:

[http://monespaceperso.org/blog-en/2009/03/10/how-to-install-google-earth-50-on-ubuntu-810/](http://monespaceperso.org/blog-en/2009/03/10/how-to-install-google-earth-50-on-ubuntu-810/)
[http://www.google.com/support/forum/p/earth/thread?tid=2adca7f2f27a7702&hl=en](http://www.google.com/support/forum/p/earth/thread?tid=2adca7f2f27a7702&hl=en)

Para solucionarlo tenes  que ir a la carpeta en que instalaste google earth (en mi caso es /home/usuario/googleearth o /home/usuario/.googleearth) y eliminar el archivo llamado libcrypto.so.0.9.8

---

### Post by c4d0rn4 on 2009-03-25
buscá bien libssl.so.0.9.8 yo tenía el mismo problema, había que borrarlo y crear un link al del sistema. Pero parece que con solo renombrarlo funca

[http://monespaceperso.org/blog-en/2009/03/10/how-to-install-google-earth-50-on-ubuntu-810/](http://monespaceperso.org/blog-en/2009/03/10/how-to-install-google-earth-50-on-ubuntu-810/)

fijate al final.


Edit: me ganaron... jaja xD
Digamos que es algo "normal" lo que te pasa, es un bug.

---

### Post by drazhe on 2009-03-25
estoy tratando de borrar o renombrar dicho archivo, pero no me permite.... ni siquiera me da la opcion de hacer algo..... como se lo hace? 

o mejor diganme como desinstalar el programa y asi puedo comenzar de nuevo...

---

### Post by pablo.s on 2009-03-25
> **drazhe said:**
> estoy tratando de borrar o renombrar dicho archivo, pero no me permite.... ni siquiera me da la opcion de hacer algo..... como se lo hace? 

o mejor diganme como desinstalar el programa y asi puedo comenzar de nuevo...

Y seguramente estás tratando de borrar el archivo que se instaló en la /home de
root. Fijate el post que te escribi antes. Instalalo de vuelta, pero sin usar sudo.
Ahi se va a instalar en /home/tu usuario/googleearth y ahi si tenes permisos.

Ojo, lo de /home/tu usuario sigifica que /tu usuario es el nombre de tu usuario, eh.
Redundante pero es asi.

Una vez que esté instalado probá los metodos que te explicaron acá c4d0rn4 y
Air23.

---

### Post by drazhe on 2009-03-25
Claro ya intente eso, pero ahora es peor, no solo me saltan los 2 carteles de error, sino que pega un pantallazo y vuelve a cargar el SO y me pide mi usuario y contraseña..... lo peor es que cuando apago el sistema, despues de unos minutos la PC vuelve a encenderse.... asi que vaya a saber que hice.....

---

### Post by pablo.s on 2009-03-26
> **drazhe said:**
> Claro ya intente eso, pero ahora es peor, no solo me saltan los 2 carteles de error, sino que pega un pantallazo y vuelve a cargar el SO y me pide mi usuario y contraseña..... lo peor es que cuando apago el sistema, despues de unos minutos la PC vuelve a encenderse.... asi que vaya a saber que hice.....

Caramba... yo te iba a sugerir que instalaras la versión mas antigua que
está en el repositorio Medibuntu... que mala pata muchacho. Si te sigue
interesando la aplicación, escribi lo siguiente en una terminal:

[FONT=Arial]sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

y después esto:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Espero realmente que no te quede una mala impresión de Ubuntu.
Saludos
[/FONT]

---

### Post by totolinux on 2009-03-26
Aquí esta la solución a este problema tardé  1 hora en encontrarla y probar cuanta solución veía pero nada funcionaba ojalá les sirva [http://planet.linux.org.sv/](http://planet.linux.org.sv/)
en el terminal antes poner "sudo -i" sin comillas luego seguir los pasos del tutorial.
saludos

---

### Post by drazhe on 2009-03-26
> **pablo.s said:**
> Caramba... yo te iba a sugerir que instalaras la versión mas antigua que
está en el repositorio Medibuntu... que mala pata muchacho. Si te sigue
interesando la aplicación, escribi lo siguiente en una terminal:

[FONT=Arial]sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

y después esto:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Espero realmente que no te quede una mala impresión de Ubuntu.
Saludos
[/FONT]


Pero que mala impresion me peudo llevar? en el 1er mensaje que puse dije que era un extremo novato en el asunto de linux y ubuntu, asi que seguro que las macanas me las mande yo.. jejejeje..... de cualquier manera salvo el kilombo del google earth, actualizar el openoffice a la version 3, instalar el opera, hacer que funcionara el ajedrez en 3D, la internet inlamabrica y los efectos visuales y no se que otra cosa mas estuve haciendo, fue barbaro... 

Voy a formatear e instalar d enuevo, asi queda el SO limpito y sin los errores que me mande con el google earth....

---

### Post by pablo.s on 2009-03-26
> **drazhe said:**
> Voy a formatear e instalar d enuevo, asi queda el SO limpito y sin los errores que me mande con el google earth....

Todo O.K. pero instalale Ubuntu loco  :)

---

### Post by drazhe on 2009-03-27
> **totolinux said:**
> Aquí esta la solución a este problema tardé  1 hora en encontrarla y probar cuanta solución veía pero nada funcionaba ojalá les sirva [http://planet.linux.org.sv/](http://planet.linux.org.sv/)
en el terminal antes poner "sudo -i" sin comillas luego seguir los pasos del tutorial.
saludos

Hola, intente hacer lo que dice el link que dejaste y pude instalarlo y hacerlo andar! 

Muchas gracias por la ayuda a todos!

---

