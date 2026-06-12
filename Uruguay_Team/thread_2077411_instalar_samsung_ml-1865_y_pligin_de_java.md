---
title: "instalar samsung ml-1865 y pligin de java"
date: 2012-10-28
forum: Uruguay Team
---

### Post by rubencotelo on 2012-10-28
Hola amigos: gracias Layla por responder mis mensajes. Sabía que Pablo estaba complicado de salud, pero pensé que todo se había solucionado.
De igual forma tengo 2 problemas y en una de esas alguien puede ayudarme.
Principalmente el problema que tengo es como trabajar con un terminal e instalar archivos ejecutables como los pluggin de java y los drivers para instalar la impresora Samsung.
Lo de la impresora Samsung es una maquina que esta conectada en un pc que tiene instalado windows xp y tengo 3 maquinas que tienen instalado ubuntu 9.04 y que tengo que instalar los drivers para que impriman en la Samsung ml-1865.
Busque en internet y me dicen que tengo que abrir un terminal y escribir unos comandos, lo hago pero me da error. Lo mismo me pasa con los Pluggin de java. Seguramente no se como manejarme con eso.
En una pagina: [http://www.chilecomparte.cl/topic/1881631-instalacion-de-impresora-samsung-lm1685/](http://www.chilecomparte.cl/topic/1881631-instalacion-de-impresora-samsung-lm1685/)   encontré que me dicen: " Si no eres bueno con la terminal el archivo .tar.gz que acabas de descargar abrelo con el programa de Centro de Sofware y el mismo te lo instala". Trté de buscar el "programa de centro de software y no lo encontré.
Por favor les pido ayuda. Necesito alguien que me de una mano.

Muchisimas gracias desde ya por su ayuda

Saludos

---

### Post by danielmato on 2012-11-05
Veo muy difícil que el centro de software te instale un tar.gz.

Lo bajé para ver mas o menos que tiene.

Mi recomendación:

Bajar el archivo.

Descomprimirlo en el escritorio (o donde se te ocurra)

Entrar a la carpeta cdroot (clic doble)

Dentro hay un archivo y una carpeta.

Doble clic al autorun, salta un cuadro de díalogo, darle clic en ejecutar en terminal, y seguir los pasos que salgan.

Listo, deberías tener tus drivers instalados, y la impresora funcionando.

Saludos

---

### Post by fedeWCQ on 2012-11-27
Hola... todo bien!!! Soy nuevo en el foro y prácticamente nuevo el linux. Hace dos años probe Ubuntu y no hubo caso.

Pero luego de dos años aquí estoy, empece hace poco con Fedora y ahora con Ubuntu.

Mirá, una vez me dijeron que las impresoras son todo un tema en linux, yo diría que no solo las impresoras sino también las webcams.

Bueno, tenía el mismo problema con mi samsung ml1865(en fedora y unbuntu) y de pedo dí con un post en ingles que me dio la solución. Pero ahora no me la acuerdo, jajaja!

Igualmente, lo que hice fue instalar los repositorios de [http://www.bchemnet.com](http://www.bchemnet.com) e instalar unos paquetes, el tema es que no me acuerdo cuales. 
Luego me fijo en mi compu y te digo cuales son.

Igual te dejo el link con toda la info [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/), lo que tenes que hacer esta ahí.

---

### Post by fedeWCQ on 2012-11-27
Listo... ya encontré la solución!!!:guitar:

[HTML]avantgardaclue
September 20th, 2011, 05:58 AM

Just bought one of these nifty laser printers and struggled like mad to get it to work until I sussed how to do it and it was simplicity itself!

Process....

Add to repositories under update manager...

"deb http://www.bchemnet.com/suldr/ debian extra" without the quote marks!

Then get the apt-key

Refresh your repository listings

Go to synaptic and do search for... samsungmfp

Install samsungmfp-data & samsungmfp-driver

Plug in, turn on samsung laser, 'Add Printer' and presto should work!!

More info at http://www.bchemnet.com/suldr/[/HTML]

Fuente: [http://ubuntuforums.org/showthread.php?t=1899875](http://ubuntuforums.org/showthread.php?t=1899875)

---

