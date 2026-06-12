---
title: "No inicia el Centro de Software - Lucid Lynx"
date: 2010-09-30
forum: Software
---

### Post by Arabela on 2010-09-30
Algunas respuestas, ninguna solucion..... por suerte ya estabamos sobre la fecha en que se actualiza a maverick.... Hoy estreno version de ubuntu y gracias a eso se soluciono lo del centro de software.......... Gracias [sys.adm.og]("http://ubuntuforums.org/member.php?u=1160362") por las ganas de ayudar!!!


****************************

Hola foro, como estan?


 Hace varios dias (despues de alguna actualizacion) tengo problemas  para abrir el centro de software, al hacer click se queda en  "Iniciando.." y luego se cierra la ventana
 Busque y busque pero no encontre solucion :(
 Por algun lado lei que una posible seria


 1. sudo dpkg --configure -a
2. sudo apt-get autoremove
3. sudo apt-get update
 Pero no, no funciono tampoco




 Pego lo q me sale al poner en la terminal software-center :




 ```
WARNING:root:No styling hints for UbuntuStudio were found... using Human hints.
WARNING:root:'/usr/share/desktop-directories/Education.directory' has no name
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 157, in __init__
    self.icons, datadir)
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 79, in __init__
    self._build_ui()
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 85, in _build_ui
    self.icons)
  File "/usr/share/software-center/softwarecenter/view/catview.py", line 88, in __init__
    self.categories = self.parse_applications_menu(desktopdir)
  File "/usr/share/software-center/softwarecenter/view/catview.py", line 348, in parse_applications_menu
    category = self._parse_menu_tag(child)
  File "/usr/share/software-center/softwarecenter/view/catview.py", line 307, in _parse_menu_tag
    (untranslated_name, name, gettext_domain, icon) = self._parse_directory_tag(element)
TypeError: 'NoneType' object is not iterable
``` Y lo que sale al poner software-center --debug




 ```
DEBUG:root:get_distro: 'Ubuntu'
DEBUG:root:query for the update-database exception  'org.freedesktop.DBus.Error.ServiceUnknown: The name  com.ubuntu.Softwarecenter was not provided by any .service files'  (probably ok)
INFO:root:writing html output to '/tmp/tmpArwz4u/software-center-render.html'
WARNING:root:No styling hints for UbuntuStudio were found... using Human hints.
INFO:root:writing html output to '/tmp/tmpBEtJSw/software-center-render.html'
DEBUG:root:reading '/usr/share/desktop-directories/Utility.directory'
DEBUG:root:adding: Utility
DEBUG:root:adding: Accessibility
DEBUG:root:reading '/usr/share/desktop-directories/Utility-Accessibility.directory'
DEBUG:root:adding: Accessibility
DEBUG:root:adding: Settings
DEBUG:root:adding: Development
DEBUG:root:adding section: devel
DEBUG:root:adding section: restricted/devel
DEBUG:root:adding section: universe/devel
DEBUG:root:adding section: multiverse/devel
DEBUG:root:adding section: haskell
DEBUG:root:adding section: restricted/haskell
DEBUG:root:adding section: universe/haskell
DEBUG:root:adding section: multiverse/haskell
DEBUG:root:adding section: java
DEBUG:root:adding section: restricted/java
DEBUG:root:adding section: universe/java
DEBUG:root:adding section: multiverse/java
DEBUG:root:adding section: libdevel
DEBUG:root:adding section: restricted/libdevel
DEBUG:root:adding section: universe/libdevel
DEBUG:root:adding section: multiverse/libdevel
DEBUG:root:adding section: lisp
DEBUG:root:adding section: restricted/lisp
DEBUG:root:adding section: universe/lisp
DEBUG:root:adding section: multiverse/lisp
DEBUG:root:adding: Translation
DEBUG:root:adding section: cli-mono
DEBUG:root:adding section: restricted/cli-mono
DEBUG:root:adding section: universe/cli-mono
DEBUG:root:adding section: multiverse/cli-mono
DEBUG:root:adding section: ocaml
DEBUG:root:adding section: restricted/ocaml
DEBUG:root:adding section: universe/ocaml
DEBUG:root:adding section: multiverse/ocaml
DEBUG:root:adding section: perl
DEBUG:root:adding section: restricted/perl
DEBUG:root:adding section: universe/perl
DEBUG:root:adding section: multiverse/perl
DEBUG:root:adding section: python
DEBUG:root:adding section: restricted/python
DEBUG:root:adding section: universe/python
DEBUG:root:adding section: multiverse/python
DEBUG:root:adding section: ruby
DEBUG:root:adding section: restricted/ruby
DEBUG:root:adding section: universe/ruby
DEBUG:root:adding section: multiverse/ruby
DEBUG:root:adding section: vcs
DEBUG:root:adding section: restricted/vcs
DEBUG:root:adding section: universe/vcs
DEBUG:root:adding section: multiverse/vcs
DEBUG:root:adding: RevisionControl
DEBUG:root:adding: WebDevelopment
DEBUG:root:reading '/usr/share/desktop-directories/Education.directory'
WARNING:root:'/usr/share/desktop-directories/Education.directory' has no name
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 157, in __init__
    self.icons, datadir)
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 79, in __init__
    self._build_ui()
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 85, in _build_ui
    self.icons)
  File "/usr/share/software-center/softwarecenter/view/catview.py", line 88, in __init__
    self.categories = self.parse_applications_menu(desktopdir)
  File "/usr/share/software-center/softwarecenter/view/catview.py", line 348, in parse_applications_menu
    category = self._parse_menu_tag(child)
  File "/usr/share/software-center/softwarecenter/view/catview.py", line 307, in _parse_menu_tag
    (untranslated_name, name, gettext_domain, icon) = self._parse_directory_tag(element)
TypeError: 'NoneType' object is not iterable
``` Espero puedan ayudarme porque para mi esto es chino complejo!!!
 Gracias, abrazos!
 

P.d. Ya intente reinstalar software-center desde synaptic pero tampoco se soluciono

---

### Post by josecuervo86 on 2010-09-30
Hay un Bug reportado sobre este asunto aca [0]. Para arreglar el error tenes que crear un directorio de nombre **xapian** en /var/cache/software-center y darle los permisos correspondientes:

```
sudo mkdir -p -m755 /var/cache/software-center/xapian
```

[0][https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/620011]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/620011")

---

### Post by Arabela on 2010-09-30
Ya tengo esa carpeta dentro de software-center.... copie y pegue en la terminal los permisos que me pasaste pero naaaaaaaada sigue sin funcionar

---

### Post by josecuervo86 on 2010-09-30
Que versión de python estas usando? pone esto en la terminal:

```
python -V
``` y pegalo el resultado aca

---

### Post by Arabela on 2010-10-01
Python 2.6.5
 esa...

---

### Post by juancarlospaco on 2010-10-01
sudo apt-get purge software-center ; sudo apt-get install software center

Eso lo deberia desinstalar, y volver a instalar.
:)

---

### Post by Arabela on 2010-10-02
Desinstalo, volvio a instalar pero naaaaaada sigue sin funcionar..... :(

Copio y pego por si sirve como dato...

```
sudo apt-get purge software-center
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  libportaudio2 python-aptdaemon-gtk python-aptdaemon libindicate-gtk2
  libboost-thread1.40.0 aptdaemon glob2-data
Utilice «apt-get autoremove» para eliminarlos.
Los siguientes paquetes se ELIMINARÁN:
  software-center*
0 actualizados, 0 se instalarán, 1 para eliminar y 0 no actualizados.
Se liberarán 1.651kB después de esta operación.
¿Desea continuar [S/n]? s
(Leyendo la base de datos ...  00%
224071 ficheros y directorios instalados actualmente.)
Desinstalando software-center ...
Purgando ficheros de configuración de software-center ...
Procesando disparadores para man-db ...
Procesando disparadores para hicolor-icon-theme ...
Procesando disparadores para python-gmenu ...
Rebuilding /usr/share/applications/desktop.es_AR.utf8.cache...
Procesando disparadores para desktop-file-utils ...
Procesando disparadores para packagekit-backend-apt ...
Generating mime/codec maps...
Procesando disparadores para python-support ...
Procesando disparadores para python-central ...
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho

``````
sudo apt-get install software-center
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  libportaudio2 libindicate-gtk2 libboost-thread1.40.0 glob2-data
Utilice «apt-get autoremove» para eliminarlos.
Se instalarán los siguientes paquetes NUEVOS:
  software-center
0 actualizados, 1 se instalarán, 0 para eliminar y 0 no actualizados.
Se necesita descargar 0B/318kB de archivos.
Se utilizarán 1.724kB de espacio de disco adicional después de esta operación.
Seleccionando el paquete software-center previamente no seleccionado.
(Leyendo la base de datos ...  00%
223934 ficheros y directorios instalados actualmente.)
Desempaquetando software-center (de .../software-center_2.1.0~ppa1_all.deb) ...
Procesando disparadores para man-db ...
Procesando disparadores para packagekit-backend-apt ...
Generating mime/codec maps...
Procesando disparadores para python-gmenu ...
Rebuilding /usr/share/applications/desktop.es_AR.utf8.cache...
Procesando disparadores para desktop-file-utils ...
Procesando disparadores para hicolor-icon-theme ...
Procesando disparadores para python-central ...
Procesando disparadores para python-support ...
Configurando software-center (2.1.0~ppa1) ...

Procesando disparadores para python-central ...

```Alguna otra ocurrencia??

Gracias miles desde ya por querer ayudar! :)

---

### Post by Arabela on 2010-10-05
Nadie? Naaaaaaaaada? Me abandonaron con tremendo problema?

Por favor ayuuuuuuuuuuuda!!!

---

### Post by sys.adm.og on 2010-10-05
Prueba chequeando las dependencias del paquete.

```
osmar@osmarpc28:~$ dpkg --status software-center 
Package: software-center
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 1680
Maintainer: Michael Vogt <mvo@ubuntu.com>
Architecture: all
Version: 2.0.7
Replaces: software-store
Provides: software-store
Depends: python, python-central (>= 0.6.11), app-install-data (>= 0.4.0), gnome-icon-theme, gnome-menus, python-xapian, python-apt (>= 0.7.13.4ubuntu3), python-aptdaemon (>= 0.11+bzr342), python-aptdaemon-gtk, python-dbus, policykit-1, policykit-1-gnome | policykit-1-kde, python-gtk2, python-webkit, python-gconf, aptdaemon (>= 0.11+bzr322)
Recommends: lsb-release, python-launchpad-integration, apt-xapian-index, update-notifier
Conflicts: software-store
Conffiles:
 /etc/dbus-1/system.d/com.ubuntu.SoftwareCenter.conf d5c450e6bccfcb8177943516e8beb673
Description: Utility for browsing, installing, and removing applications
 The Ubuntu Software Center lets you browse and install thousands of
 free applications available for Ubuntu. You can view available
 applications by category, or search quickly by name or description.
 You can also examine the applications already installed, and remove
 those you no longer need.
 .
 To install or remove software using the Center, you need administrator
 access on the computer.
Python-Version: current

```

A mi me funciona asi, trata de cumplir esas dependencias que aparece en el resultado que me lanza, donde dice **Depends**, los que dicen **Recommends** son ultilidades pero no son indispensables para el buen funcionamiento.

Prueba y dinos que resultado da!
Muestranos tambien lo que lanza como resultado.

---

### Post by Arabela on 2010-10-05
Copio y pego, pero no veo que es lo que vaya mal (aunque no entiendo mucho)
> 
Package: software-center
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 1684
Maintainer: Michael Vogt <mvo@ubuntu.com>
Architecture: all
Version: 2.1.0~ppa1
Replaces: gnome-app-install, software-store
Provides: gnome-app-install, software-store
Depends: python, python-central (>= 0.6.11), app-install-data (>= 0.4.0), gnome-icon-theme, gnome-menus, python-xapian, python-apt (>= 0.7.93.1), python-aptdaemon (>= 0.11+bzr342), python-aptdaemon-gtk, python-dbus, policykit-1, policykit-1-gnome | policykit-1-kde, python-gtk2, python-webkit, python-xdg, python-gconf, aptdaemon (>= 0.11+bzr322)
Recommends: lsb-release, python-launchpad-integration, apt-xapian-index, update-notifier, software-properties-gtk
Conflicts: gnome-app-install, software-store
Conffiles:
 /etc/dbus-1/system.d/com.ubuntu.SoftwareCenter.conf d5c450e6bccfcb8177943516e8beb673
Description: Utility for browsing, installing, and removing applications
 The Ubuntu Software Center lets you browse and install thousands of
 free applications available for Ubuntu. You can view available
 applications by category, or search quickly by name or description.
 You can also examine the applications already installed, and remove
 those you no longer need.
 .
 To install or remove software using the Center, you need administrator
 access on the computer.
Python-Version: current

---

### Post by sys.adm.og on 2010-10-07
Lo que veo es una diferencia en la version
Version: 2.1.0~ppa1 esta es la tuya 

Version: 2.0.7 esta es la mia

No manejo como launchpad maneja sus versiones. A mi parecer esa version aun esta de prueba. Pues visite su pagina y la que tengo yo es la ultima version estable y actualizada.

Visita su página: [http://www.ubuntuupdates.org/packages/show/201769]("http://www.ubuntuupdates.org/packages/show/201769")

**En la pagina veras en la cabecera esto:**

-------------------------------------------------------------------------
Package gnome-app-installName:	gnome-app-install 

Description:	
dummy upgrade package for gnome-app-install -> software-center 
This is a transitional package so that gnome-app-install        users       get software-center on upgrades. It can be safely removed.

Latest version:	2.0.7

Ubuntu release:	lucid (10.04)

Level:	updates

Repository:	universe

Head package:	software-center


Show Raw Package Information

--------------------------------------------------------------------------


Da un clic donde Dice: "Show Raw Package Information"

Ahi veras una linea con lo siguiente:
**Filename: pool/universe/s/software-center/gnome-app-install_2.0.7_all.deb**
Esa es la ubicacion del paquete es el repositorio de ubuntu.

Entoces hagamos esto.

abre una terminal y abre el archivo sources.list que esta en el directorio /etc/apt/
```
vi /etc/apt/sources.list
```

En las primeras lineas veras de esta forma la url del repositorio que estas utilizando:

deb [http://**py**.archive.ubuntu.com/ubuntu/](http://**py**.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://py.archive.ubuntu.com/ubuntu/](http://py.archive.ubuntu.com/ubuntu/) lucid main restricte

En mi caso es **py** porque soy de Paraguay en el tuyo seria **ar** que es de Argentina.

Entonces copias la url y le añades la ubicacion que obtuvimos en la pagina de launchpad.
Quedaria así:

"http://py.archive.ubuntu.com/ubuntu/pool/universe/s/software-center/gnome-app-install_2.0.7_all.deb"

Copia este link en tu navegador ahi vas a descargar la version 2.0.7 que es la que tengo yo, la instalas y listo.

Avisa cualquier cosa!!

---

