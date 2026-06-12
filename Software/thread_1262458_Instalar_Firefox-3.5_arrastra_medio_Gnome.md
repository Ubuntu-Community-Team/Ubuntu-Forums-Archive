---
title: "Instalar Firefox-3.5 arrastra medio Gnome"
date: 2009-09-09
forum: Software
---

### Post by sergiom99 on 2009-09-09
Buscando entre los paquetes disponibles, vi que ya estaba Firefox 3.5 para ser instalado.
Al tratar de instalarlo, me sale este resultado:

> $ sudo apt-get install firefox-3.5
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
  apturl firefox-3.5-branding gnome-app-install libcairo-perl libglib-perl libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl libgtk2-perl
  liblaunchpad-integration1 libvte-common libvte9 python-gconf python-gst0.10 python-gtkhtml2 python-launchpad-integration python-pyorbit python-sexy
  python-vte software-properties-gtk synaptic ubufox xulrunner-1.9.1
Paquetes sugeridos:
  firefox-3.5-gnome-support latex-xft-fonts libgtk2-perl-doc python-gconf-dbg python-gst0.10-dbg python-gnome2-extras-doc
  python-launchpad-integration-dbg python-pyorbit-dbg dwww deborphan
Se instalarán los siguientes paquetes NUEVOS:
  apturl firefox-3.5 firefox-3.5-branding gnome-app-install libcairo-perl libglib-perl libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl
  libgtk2-perl liblaunchpad-integration1 libvte-common libvte9 python-gconf python-gst0.10 python-gtkhtml2 python-launchpad-integration python-pyorbit
  python-sexy python-vte software-properties-gtk synaptic ubufox xulrunner-1.9.1
0 actualizados, 24 se instalarán, 0 para eliminar y 1 no actualizados.
Necesito descargar 15,8MB de archivos.
Se utilizarán 51,8MB de espacio de disco adicional después de esta operación.

Cómo es que para instalarlo necesito instalar la mitad de los paquetes de Gnome?? (Synaptic incluido, WTF!)
Tan mal está Ubuntu? 

Pensando en lo que el otro día estaba comentando Hei Ku de las traducciones, hasta cuando vamos a ser "kelpers" los que usamos Kubuntu?

---

### Post by pablo.s on 2009-09-09
A ver, voy a defender un
poquitito a Firefox y un
poquitito a GNOME y mucho
a KDE:

Las dependencias que te pide
son lógicas si pensamos en que
la versión compilada para Ubuntu
tiene mucha integración tanto con
Python (tipicamente Ubuntiano) y
la integración lógica con GTK.
Luego, supongo que debe haber
algún paquete de Firefox compilado
con los mínimos requerimientos
(en este momento se me ocurre que
IceCat está muy austeramente compilado).
Por otro lado, no creo que los usuarios
de KDE sean "kelpers". Hay dependencias
que los programas tienen, digamos que
sucede si yo quiero instalar Konqueror:
me voy a quejar de las dependencias
que practicamente exigen que instale
KDE. Como caso puntual yo utilizo a veces
K3B y practicamente me instala KDE
(nuevamente, lo básico, no completo).

---

### Post by guisheca on 2009-09-09
Una alternativa es descargarte el binario desde la página de firefox, con eso te librás de todas las dependencias de la versión compilada exclusivamente para ubuntu.

---

### Post by pablo.s on 2009-09-09
Mirá lo que sucede del otro
lado (si querés instalar Konqueror
desde GNOME)

```
pablo@raanana:~$ sudo apt-get install konqueror
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dolphin exiv2 kde-icons-oxygen kdebase-bin kdebase-data kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
  kdelibs-bin kdelibs5 kdelibs5-data kfind khelpcenter4 konqueror-nsplugins
  libclucene0ldbl libexiv2-5 libkonq5 libkonq5-templates libqimageblitz4
  librasqal1 librdf0 libsoprano4 libstreamanalyzer0 libstreams0 redland-utils
  soprano-daemon
Suggested packages:
  kdebase konq-plugins
The following NEW packages will be installed:
  dolphin exiv2 kde-icons-oxygen kdebase-bin kdebase-data kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
  kdelibs-bin kdelibs5 kdelibs5-data kfind khelpcenter4 konqueror
  konqueror-nsplugins libclucene0ldbl libexiv2-5 libkonq5 libkonq5-templates
  libqimageblitz4 librasqal1 librdf0 libsoprano4 libstreamanalyzer0
  libstreams0 redland-utils soprano-daemon
0 upgraded, 28 newly installed, 0 to remove and 6 not upgraded.
Need to get 39.0MB of archives.
After this operation, 117MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

### Post by Hei Ku on 2009-09-09
Eh, el navegador de Gnome no es Firefox, asi que la comparacion no es justa.

Firefox promete ser multiplataforma, y no lo es. De hecho, es bastante malo en Linux comparado a la version de Windows.

---

### Post by santiagoward2000 on 2009-09-09
Digamos que un gran número de esas dependencias (incluyendo Synaptic) son arrastradas por el plugin **ubufox**, que es algo que agregaron en Ubuntu (y no entiendo cómo no es opcional). Como dijo guisheca, estas dependencias las podés saltear si lo bajás de la página del Firefox.
Saludos!

---

### Post by pablo.s on 2009-09-09
No es el navegador de GNOME,
es muy cierto. Pero el punto de
las dependencias creo que ilustra
el asunto, asi que utilicé a Konqueror
como antípoda de Firefox, cómo para
que no se sientan "kelpers" o "usuarios
de segunda". Hay una realidad que
son las dependencias y no se me ocurrió
mejor ejemplo para defender a ambos
escritorios. Porque yo no siento que
Kubuntu sea inferior: es distinto.
Hay que aceptar las diferencias y
convivir. Digo yo...

---

### Post by guidito73 on 2009-09-09
> **Hei Ku said:**
> Eh, el navegador de Gnome no es Firefox, asi que la comparacion no es justa.

Firefox promete ser multiplataforma, y no lo es. De hecho, es bastante malo en Linux comparado a la version de Windows.

Te parece? En la misma máquina, a mí me anda a las chapas en Ubuntu. Y mis viejos ni lo quieren usar en Windows por lo lento que se pone. Pero es cierto que tienen algunas cosas pendientes para ser totalmente "multiplataforma" (lanzarlo en java? =P=P=P=P=P)

---

### Post by Hei Ku on 2009-09-10
Creo que Santiago fue claro. Firefox puede andar sin todas esas dependencias. 

Es solo que a nadie se le paso por la cabeza que tenian que sacarlas para Kubuntu. Estan puestas para Ubuntu, no porque sean realmente necesarias, sino porque les resulta mas facil. Y ese es el punto que nos molesta a los usuarios de Kubuntu.

Vengo desde el domingo peleando con los pibes de traducciones porque otra vez rompieron las traducciones de Kubuntu. Y la unica respuesta con un poco de sentido que recibi fue: "el proceso esta roto" FOOBAR, como dirían algunos. Asi que a veces a los usuarios de Kubuntu es como que nos falta ese poquito de amor extra como para aguantar. :D

---

### Post by santiagoward2000 on 2009-09-10
A partir de este thread se me dio por probar el Firefox 3.5, ¿y saben qué vi? A los usuarios de KDE no solo les estaría instalando algo innecesario como ubufox (con todas sus dependencias), sino que además la versión de dicho plugin que está en los repositorios de Jaunty ni siquiera es compatible con Firefox-3.5.
Estuve leyendo [este otro thread]("http://ubuntuforums.org/showthread.php?p=7552580") y me enteré que existe una opción de apt-get (sí, lo admito, tengo que leer los man más seguido) que te deja instalar un programa sin los paquetes recomendados: **--no-install-recommends**
Entonces, haciendo un:
```
sudo apt-get --no-install-recommends install firefox-3.5
```
podrían instalarlo sin muchas de esas dependencias de GNOME.
Espero que les sirva!
Saludos!

---

### Post by oktubrer on 2009-09-10
Por si alguno desconfía, va la prueba desde KDE 4.3
```
rodrigo@Finisterre:~$ sudo apt-get --no-install-recommends install firefox-3.5
[sudo] password for rodrigo:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
  firefox-3.5-branding xulrunner-1.9.1
Paquetes sugeridos:
  firefox-3.5-gnome-support latex-xft-fonts
Paquetes recomendados
  ubufox libcanberra0
Se instalarán los siguientes paquetes NUEVOS:
  firefox-3.5 firefox-3.5-branding xulrunner-1.9.1
0 actualizados, 3 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 11,3MB de archivos.
Se utilizarán 34,8MB de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]?

```

Santiago, un groso.

---

### Post by sergiom99 on 2009-09-10
> **santiagoward2000 said:**
> 
Entonces, haciendo un:
```
sudo apt-get --no-install-recommends install firefox-3.5
```
podrían instalarlo sin muchas de esas dependencias de GNOME.


Es un buen dato. Ahora viene mas liviano. 
De cualquier manera, estoy 100% de acuerdo con Hei Ku, Kubuntu queda como medio de lado y que salga como salga. Otra prueba es que sacaron el Kcontrol, y trataron de unificarlo con el System Preferences que trae Ubuntu.

Todo el mundo dice que para probar KDE, no te quedes con Kubuntu. Me gustaría que esto se revierta en algún futuro no muy lejano y que Kubuntu no sea solo una segunda selección de Ubuntu. Estaría bueno que sea una de las distros de elección para disfrutar y aprovechar de KDE en todo su esplendor. (Cualquier duda, buscar en este mismo foro las discusiones de hace unos cuantos meses sobre que distro tiene el mejor KDE)

"Por lo menos, asi lo veo yo"... decia un viejo crápula :lolflag:

---

