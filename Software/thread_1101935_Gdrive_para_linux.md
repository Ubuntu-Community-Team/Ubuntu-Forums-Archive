---
title: "Gdrive para linux"
date: 2009-03-20
forum: Software
---

### Post by erdosain9 on 2009-03-20
Podrían enseñarme a instalar el gmail drive para linux... la página del autro está en inglés... y tampoco sé mucho de linux... muchas gracias

---

### Post by NickCis on 2009-03-21
Podrias pasarnos la pagina de la qe estas hablando?.

Por lo que busque google, no hay ninguno para linux, podrias intentar usar alguno via wine, no se como andara.

La otra es usar el addon para el firefox: [https://addons.mozilla.org/es-ES/firefox/addon/1593](https://addons.mozilla.org/es-ES/firefox/addon/1593)

Saludos.

Edit: entontre mas info
La pagina official del plugin es: [http://www.getgspace.com/es/](http://www.getgspace.com/es/)
Nos lo podemos bajar de ak:[http://www.getgspace.com/es/download.html](http://www.getgspace.com/es/download.html)

Cuidado! "* DISCLOSURE: Gspace uses statcounter.com service to track the usage of the extension" esto significa que Gspace usa el servicio de statcounter.com para llevar un seguimiento del uso de la extencion!!

---

### Post by erdosain9 on 2009-03-21
Muchas gracias... la pagina de la que hablo es esta>

[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html)

saludos...

P.d. como hago???

---

### Post by erdosain9 on 2009-03-21
y por cierto... qué relevancia tiene esto:
"Cuidado! "* DISCLOSURE: Gspace uses statcounter.com service to track the usage of the extension" esto significa que Gspace usa el servicio de statcounter.com para llevar un seguimiento del uso de la extencion!!"

---

### Post by erdosain9 on 2009-03-26
entonces alguien podría enseñarme a instalarlo???

---

### Post by erdosain9 on 2009-03-27
ejem...  nadie sabe???????????

---

### Post by Hei Ku on 2009-03-27
Por threads anteriores sobre el mismo tema, me parece que nadie lo pudo hacer andar en linux.

---

### Post by guillermolisi on 2009-03-27
> **erdosain9 said:**
> ejem...  nadie sabe???????????
El tema no es saber como instalar sino saber traducir (y entender) o saber encontrar la informacion requerida en el idioma que domines.

En la misma pagina que mencionas dice todo lo necesario para instalar, usar y te da una revision de la implementacion de Gmail Filesystem.

En realidad este tema es OT ya que puede funcionar en cualquier plataforma y dentro de las Linux, en Ubuntu. Para todos los casos es similar con las diferencias de cada entorno operativo.

Para instalar, el autor de esa nota dice:
[INDENT]Asegurese de contar con Python 2.3 (o superior) instalado. La mayoria de las distribuciones Linux tendran su propio paquete para esto (tambien necesitaras los paquetes de desarrollo de python 2.3
>     * Make sure you have Python 2.3 (or later) installed. Most Linux distributions will have their own package for this (you'll also need the appropriate python2.3-dev packages).

Los kernels recientes (no se de que fecha es esta nota) incluyes FUSE por defecto. Si corre un kernel antiguo necesitara instalar la version 2.x de FUSE. Algunas distribuciones Linux (como Debian) vienen con un paquete. Si tu distribucion no lo trae. podes encontrar el (codigo) fuente en la pagina de descarga de FUSE en SourceForge. Dependiendo de tu plataforma podrias tener que copiar fusermount a /usr/bin para una correcta operacion.
>     * Recent kernels include FUSE by default. If you run an older kernel you will need to install version 2.x of FUSE. Some Linux distributions (such as Debian) come with a package. If your distro doesn't, you can find the source at FUSE's SourceForge download page. Depending on your platform you may have to copy fusermount to /usr/bin for correct operation.

Descargar las "ligaduras" de FUSE para Python desde el repositorio CVS (Control Version System) de FUSE. Revisa el modulo Python usando:
cvs -d:pserver:anonymous@fuse.cvs.sourceforge.net:/cvsroot/fuse co -P python
Luego segui las instrucciones (logicamente en Ingles) de Python/INSTALL.
>     * Download the Python FUSE bindings from FUSE's CVS repository. Checkout the python module using:
      cvs -d:pserver:anonymous@fuse.cvs.sourceforge.net:/cvsroot/fuse co -P python
      Then follow the instructions in python/INSTALL.

Bajate una copia de libgmail. versiones recientes funcionan por lo tanto si experimentas problemas deberias tomar la version CVS de libgmail siguiendo las instrucciones aqui. Despues de descargar (o revisar) al archivo, copiar libgmail.py y 1gconstants.py a algun lugar donde Python pueda encontrarlos (/usr/local/lib/python2.3/site-packages/ funciona para Debian, otras distros pueden variar)
>     * Download a copy of libgmail. Recent releases currently work however if you experience problems you may wish to grab the CVS version of libgmail by f ollowing the instructions here. After downloading (or checking out) the file, copy libgmail.py and lgconstants.py to somewhere Python can find them (/usr/local/lib/python2.3/site-packages/ works for Debian, others may vary).

Descargar gmailfs-0.8.0.tar.gz. Despues de descomprimir, copiar gmailfs.py a algun lugar facilmente accesible (por ejemplo, /usr/local/bin/gmailfs.py). Copia mount.gmailfs al directorio /sbin.
>     * Download gmailfs-0.8.0.tar.gz. After untarring, copy gmailfs.py to somewhere easily accessible (for example, /usr/local/bin/gmailfs.py). Copy mount.gmailfs to the /sbin directory.

[/INDENT]

Espero te sirva porque hasta donde se, esta funcionalidad fue discontinuada por Google hace un buen tiempo.

---

### Post by erdosain9 on 2009-03-27
Bueno, te agradezco mucho.  Sí, noté que estaba la explicación en la página.  Pero no sé mucho inglés y menos sé de linux... por lo que mi forma de atender la situación era muy pobre.
Saludos y gracias

---

