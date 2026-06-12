---
title: "Como instalo firefox 3.5?"
date: 2009-07-01
forum: Software
---

### Post by dcorrea on 2009-07-01
Hola a todos!!
Ya salio la version de Firefox 3.5 
Mi consulta es como lo hago para instalarlo.
Ya baje el programa desde la pagina oficial...
pero ni idea como instalarlo desde la consola.

Gracias a todos.!

---

### Post by RafaelG on 2009-07-01
> **dcorrea said:**
> Hola a todos!!
Ya salio la version de Firefox 3.5 
Mi consulta es como lo hago para instalarlo.
Ya baje el programa desde la pagina oficial...
pero ni idea como instalarlo desde la consola.

Gracias a todos.!


Synaptic Package Manager estan todos los Packages que descargues, Busca:Firefox-3.5 si no me equiboco

Saludos.

---

### Post by dcorrea on 2009-07-01
Hola, Segui tus recomendaciones pero de la siguiente manera;
Sistema->Administracion->Gestor de paquetes Synaptic luego busque Firefox-3.5 lo marque lo instale. Reinicie Firefox..pero aun me aparece la version 3.0.11

:(

---

### Post by RafaelG on 2009-07-01
> **dcorrea said:**
> Hola, Segui tus recomendaciones pero de la siguiente manera;
Sistema->Administracion->Gestor de paquetes Synaptic luego busque Firefox-3.5 lo marque lo instale. Reinicie Firefox..pero aun me aparece la version 3.0.11

:(


Revisa este link lo acabo de hacer y estoy utilizando  SHIRETOKO asi se llama esta nueva version beta de firefox 3.5

[http://www.tribulinux.com/tutoriales-como-instalar-firefox-35-ubuntu.html](http://www.tribulinux.com/tutoriales-como-instalar-firefox-35-ubuntu.html)

Saludos

---

### Post by radixs on 2009-07-01
> **RafaelG said:**
> Revisa este link lo acabo de hacer y estoy utilizando el nuevo SHIRETOKO asi se llama este nuevo firefox 3.5

[http://www.tribulinux.com/tutoriales-como-instalar-firefox-35-ubuntu.html](http://www.tribulinux.com/tutoriales-como-instalar-firefox-35-ubuntu.html)

Saludos


Ojo SHIRETOKO es la version de firefox 3.5 y para instalarla nececitas agregar un repositorio para instalarlo.

PS: Firefox Shiretoko segun lo leido por internet es la version en desarrollo de firefox asi que si te atrevez lo instales.

---

### Post by dcorrea on 2009-07-01
> **RafaelG said:**
> Revisa este link lo acabo de hacer y estoy utilizando el nuevo SHIRETOKO asi se llama este nuevo firefox 3.5

[http://www.tribulinux.com/tutoriales-como-instalar-firefox-35-ubuntu.html](http://www.tribulinux.com/tutoriales-como-instalar-firefox-35-ubuntu.html)

Saludos

ya, segui las instrucciones del link que diste...
finalmente me instalo una aplicacion Minefield 3.5 Web browser..
la abri y es la version 3.5.1 pre mozilla firox Shiretoko
la voy a probar...

sera mucho pedir como pasarla a español?
Oye y el icono es un planeta tierra azul !!!

---

### Post by RafaelG on 2009-07-01
Si es un Planeta Azul, lo bueno es que si te das cuenta mantienes Firefox que viene por defecto en Ubuntu. [B]Tambien es bueno aclarar que Shiretoko es para Proposito de Prueba solamente como lo dice es la Version Beta.
[/B]

Saludos

---

### Post by moreback on 2009-07-01
Esta información es bien importante, por favor leer los que quieran ff 3.5:

[http://www.asoftsite.org/s9y/archives/160-FAQ-Where-can-I-get-firefox-3.5-for-Ubuntu.html](http://www.asoftsite.org/s9y/archives/160-FAQ-Where-can-I-get-firefox-3.5-for-Ubuntu.html)

---

### Post by moFeta on 2009-07-01
Para instalarlo hay varios métodos, uno es el uso del repositorio ppa indicado, pero ese instala una version de desarrollo 3.5.1, y que no hay forma de ponerlo en español.
La otra es el uso de [ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/"), un script en python que te permite instalar la ultima version disponible de los productos mozilla.
Y una que acabo de ver es la que muestran en el blog [Ubuntulife]("http://ubuntulife.wordpress.com/2009/07/01/un-solo-comando-para-instalar-firefox-3-5-final/"), usando un solo comando en terminal> cp -r ~/.mozilla/firefox/ ~/firefox_backup | wget -O - [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/es-ES/firefox-3.5.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/es-ES/firefox-3.5.tar.bz2) | tar xj -C ~ Es cosa de copiar y pegar.

Suerte.

---

### Post by nopersona on 2009-07-01
Aguardando con tranquilidad la versión final :p

---

### Post by moFeta on 2009-07-02
> **nopersona said:**
> Aguardando con tranquilidad la versión final :p

Esta ES la versión final. Supongo que quieres decir a que aparezca en los repositorios de Ubuntu.

Suerte.

---

### Post by nopersona on 2009-07-03
> **moFeta said:**
> Esta ES la versión final. Supongo que quieres decir a que aparezca en los repositorios de Ubuntu.

Suerte.

Correcto, prefiero testear porgramas mucho más experimentales.

---

### Post by aledruetta on 2009-07-03
No es mi intensión discutir si está bien o no está bien instalar versiones de sortware que no están en los repositorios oficiales de Ubuntu, porque eso está "más allá del bien y del mal", como diría Federico.

Simplemente quería saber por qué Ubuntu va atrasado en cuanto a versiones de Firefox. La que me instaló Jaunty es la 3.0 o 1.0 "for Ubuntu".

¿Alguien sabe? ¿Son tan inestables las nuevas versiones? ¿Cuántas actualizaciones ya liberó Mozilla desdee la 3.0? ¿Por qué el Gestor de Actualizaciones no las habilita?

Gracias,
Alejandro.

---

### Post by nopersona on 2009-07-04
Acá el repositorio de Launchpad para Jaunty, fresquito de muylinux.

[http://www.muylinux.com/2009/07/03/firefox-3-5-a-la-ultima-en-jaunty/#more-3148](http://www.muylinux.com/2009/07/03/firefox-3-5-a-la-ultima-en-jaunty/#more-3148)

---

### Post by zhelo on 2009-07-04
pero en el home de mozilla hay versiones para linux

---

### Post by Patriciologico on 2009-07-06
> **aledruetta said:**
> No es mi intensión discutir si está bien o no está bien instalar versiones de sortware que no están en los repositorios oficiales de Ubuntu, porque eso está "más allá del bien y del mal", como diría Federico.

Simplemente quería saber por qué Ubuntu va atrasado en cuanto a versiones de Firefox. La que me instaló Jaunty es la 3.0 o 1.0 "for Ubuntu".

¿Alguien sabe? ¿Son tan inestables las nuevas versiones? ¿Cuántas actualizaciones ya liberó Mozilla desdee la 3.0? ¿Por qué el Gestor de Actualizaciones no las habilita?

Gracias,
Alejandro.

No se trata que sean o no inestables. Cuando se trabaja en una versión de Ubuntu, se selecciona cierta cantidad de paquetes y se trata que estén en su versión mas avanzada al momento de empaquetar y lanzar Ubuntu. Una vez hecho esto, se congela la inclusión de versiones superiores y las actualizaciones se dedican a corregir problemas y no agregar nuevas funcionalidades, por que sino seria muy inestable estar agregando constantemente nuevas características. Por eso tenemos versión cada 6 meses, si incluyeran todas las nuevas versiones, de todas las aplicaciones entonnces el modelo de desarrollo seria como el de Debian, bastaria que instalases la version inestable y no necesitarias actualizar el sistema cada 6 meses para agregar nuevas funcionalidades.

(Espero mi texto sea comprensible, ando como un script en Perl el dia de hoy)

Saludos!


Pd: Sobre Shiretoko, vi que agregan el repositorio Daily, eso significa que no es beta ni estable, sino el repositorio de pruebas diario, es decir siempre en cambio.

---

### Post by darolu on 2009-07-06
> **dcorrea said:**
> Hola a todos!!
Ya salio la version de Firefox 3.5 
Mi consulta es como lo hago para instalarlo.
Ya baje el programa desde la pagina oficial...
pero ni idea como instalarlo desde la consola.

Gracias a todos.!

Lo que descargamos desde la página oficial, es el programa ya compilado y listo para usar.

Lo más sencillo es abrir Nautilus (Lugares - Carpeta personal) e ir al directorio dónde descargamos el archivo firefox_xxx.tar.bz2 y darle click derecho y luego "extraer aquí".

Desde consola simplemente tenemos que hacer:
```
:~/tar -xf firefox_xxx.tar.bz2
```

Con esto creará un directorio llamado firefox; podemos mover este folder a algún otro directorio si así lo deseamos (yo lo puse en /opt/), aunque no es necesario.

Para correr el programa simplemente hacemos en la consola:
```
~/firefox/./firefox
```
Importante que hay que hacer **./firefox** si solo usamos firefox correrá la versión 3.0xx que tengamos instalada; de aquí yo recomiendo crear un lanzador (o editar el ya existente), en la línea que dice "comando" incluímos la ruta y el comando ./firefox, por ejemplo: "/opt/firefox/./firefox %u"

Nota: si se mueve el directorio firefox/ a un lugar fuera de /home/username es importante asegurarse que tenga permisos para ejecutarlo, por ejemplo:
```
sudo chmod -R 755 /opt/firefox
```

---

### Post by aledruetta on 2009-07-06
> **Patriciologico said:**
> No se trata que sean o no inestables. Cuando se trabaja en una versión de Ubuntu, se selecciona cierta cantidad de paquetes y se trata que estén en su versión mas avanzada al momento de empaquetar y lanzar Ubuntu. Una vez hecho esto, se congela la inclusión de versiones superiores y las actualizaciones se dedican a corregir problemas y no agregar nuevas funcionalidades, por que sino seria muy inestable estar agregando constantemente nuevas características. Por eso tenemos versión cada 6 meses, si incluyeran todas las nuevas versiones, de todas las aplicaciones entonnces el modelo de desarrollo seria como el de Debian, bastaria que instalases la version inestable y no necesitarias actualizar el sistema cada 6 meses para agregar nuevas funcionalidades.

(Espero mi texto sea comprensible, ando como un script en Perl el dia de hoy)

Saludos!


Pd: Sobre Shiretoko, vi que agregan el repositorio Daily, eso significa que no es beta ni estable, sino el repositorio de pruebas diario, es decir siempre en cambio.

Gracias Patriciologico. Se entendió perfectamente el script. Saludos.

---

### Post by zhelo on 2009-07-06
servira esta pagina?
[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

---

