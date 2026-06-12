---
title: "[SOLVED] Aplicar un patch ¿Cómo?"
date: 2008-11-22
forum: Software
---

### Post by c4d0rn4 on 2008-11-22
Hola gente, estoy mudándome a [Openbox]("http://icculus.org/openbox/index.php/Main_Page"), pero estoy padeciendo un bug molesto con el AWN [SIZE="1"](aka: avant windows navigator)[/SIZE].

El hecho concreto es que está reportado el bug
[https://bugs.staging.launchpad.net/awn/+bug/239277](https://bugs.staging.launchpad.net/awn/+bug/239277)

y alguien dice haber hecho un patch que lo soluciona y que estaría agregándose en una próxima versión de Openbox

[https://bugs.staging.launchpad.net/awn/+bug/239277/comments/8](https://bugs.staging.launchpad.net/awn/+bug/239277/comments/8)

Alguien sabe como se aplica un patch?

La verdad entiendo tan poco el adjunto que no se por donde empezar a buscar. =P

---

### Post by guillermolisi on 2008-11-22
> **c4d0rn4 said:**
> Hola gente, estoy mudándome a [Openbox]("http://icculus.org/openbox/index.php/Main_Page"), pero estoy padeciendo un bug molesto con el AWN [SIZE=1](aka: avant windows navigator)[/SIZE].

El hecho concreto es que está reportado el bug
[https://bugs.staging.launchpad.net/awn/+bug/239277](https://bugs.staging.launchpad.net/awn/+bug/239277)

y alguien dice haber hecho un patch que lo soluciona y que estaría agregándose en una próxima versión de Openbox

[https://bugs.staging.launchpad.net/awn/+bug/239277/comments/8](https://bugs.staging.launchpad.net/awn/+bug/239277/comments/8)

Alguien sabe como se aplica un patch?

La verdad entiendo tan poco el adjunto que no se por donde empezar a buscar. =P
Por lo que dice el autor del patch, tendrias que compilarlo con el gcc, compilador para lenguaje C, y luego reemplazar el archivo objeto obtenido por el que funciona mal.

---

### Post by c4d0rn4 on 2008-11-22
> **guillermolisi said:**
> Por lo que dice el autor del patch, tendrias que compilarlo con el gcc, compilador para lenguaje C, y luego reemplazar el archivo objeto obtenido por el que funciona mal.

y hay alguna instrucción de como compilarlo? tipo make, make install?

---

### Post by guillermolisi on 2008-11-22
> **c4d0rn4 said:**
> y hay alguna instrucción de como compilarlo? tipo make, make install?
No vi algo especifico sobre eso en los links que enviaste, pero si queres ver todas las alternativas que el compilador de C tiene te sugiero leer su manual (man gcc en consola).
Puede que no necesite de alguna opcion en particular, puede que si.

El tema es que si te da un warinig o un error, sabrias que hacer, como seguir ?

---

### Post by sherwoodinc on 2008-11-22
Hola!

   Creo que lo más sencillo sería conseguir las fuentes para el openbox, lograr hacerlas compilar correctamente, poder generar un paquete .deb "custom" que contega la compilación manual, para poder instalarlo y ver que todo funcione como esperás.
   Una vez logrado eso, basta con aplicar el patch que postearon a los fuentes, eso se hace con el comando de consola "patch" que toma un patch  guardado en un archivo de texto y lo aplica a las carpetas/archivos correspondientes.

   En Ubuntu podés conseguir las fuentes con el apt, lo que te ahorra andar bajandote .tar.gz con los fuentes de la página de openbox, o andar buscando la versión correcta de los fuentes del paquete para tu sistema. Como nunca lo había hecho antes, miré un poco y encontré en

[http://ubuntuforums.org/showthread.php?t=101097]("http://ubuntuforums.org/showthread.php?t=101097") 

un howto de como recompilar "a la manera ubuntu" un paquete.

  Te recomiendo leer ese link porque explica muy bien el procedimiento; igual te transcribo la serie de pasos que seguí en mi propia pc para conseguir las fuentes del openbox, aplicar el patch (que se llama "openbox-shapedwin.patch"), y compilar y generar los paquetes .deb.

Te dejo la lista de comandos que tipeé en una Terminal, los cuales me generaron un paquete correcto en mi Ubuntu 8.10 (patch incluido):

```
mkdir build
cd build
sudo apt-get build-dep openbox
sudo apt-get source openbox
sudo -s

```
Antes de continuar, me bajé con firefox el patch del reporte de bug a la carpeta "build" que creé, y el archivo de patch se llamaba "openbox-shapedwin.patch".

Luego volví a la Terminal a seguir tipeando comandos:
```

cp openbox-shapedwin.patch openbox-3.4.7.2/
cd openbox-3.4.7.2/
man patch
patch -p0 < openbox-shapedwin.patch 
ls
./configure
dpkg-buildpackage -rfakeroot -uc -b
ls
cd ..
ls
dpkg -i openbox_3.4.7.2-2_amd64.deb 
dpkg -i libobparser21_3.4.7.2-2_amd64.deb 

```
NOTA: El nombre final de los paquetes puede variar en tu sistema, dependiendo de la versión del fuente, o de que que estés o no en 64 bits...

NOTA2: Con el comando "sudo -s" pasé a modo root, pero no estoy seguro de que sea necesario (al menos hasta el momento de instalar los .deb).

NOTA3: Mis comandos deberían empezarse en el "home", o al menos así lo hice yo. Aunque en realidad no importa mucho porque creás la carpeta "build" y hacés todo ahí adentro...

Si te surge algún problema con esto, avisame...

---

### Post by c4d0rn4 on 2008-11-22
aparecio un nuevo post en el tiempo que tarde en contestar :lolflag:; procesando post anterior


loading...

EDIT: Terminé de hacerlo, te amo! jajaj xD
Ya tengo openbox andando de 10!!


Lo único raro es que cuando puse dpkg-buildpackage -rfakeroot -uc -b ; me daba un error con -rfakeroot. Le saqué eso y anduvo.

---

### Post by sherwoodinc on 2008-11-23
Capaz que no tenías el paquete "fakeroot" instalado, yo lo debo haber instalado hace tiempo y no me acuerdo ya por qué :confused:
De todas maneras te funcionó sin eso, porque ya eras root al momento de hacer el dpkg-buildpackage.

Lo que me pasó a mí después de instalar el paquete, es que el ubuntu me avisa que ese paquete se puede actualizar (calculo que lo va a pisar con la versión del repositorio).

Capaz que te conviene bloquear el paquete en el Synaptic para que no te lo trate de actualizar...

Me alegro que te haya funcionado!

Saludos

---

