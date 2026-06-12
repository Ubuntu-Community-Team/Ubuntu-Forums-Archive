---
title: "No funciona el Centro de Software."
date: 2010-08-24
forum: Software
---

### Post by Cacique1 on 2010-08-24
Hola. Hace poco instalé Ubuntu 10.04 desde el CD enviado por correo. Como no poseo conexión a Internet, tuve que bajar los paquetes .deb desde el repositorio oficial a mi pendrive, y luego instalarlos en mi PC. 
  Instalé varias aplicaciones: gstreamer-plugins-??; language-support-??; openoffice.org-??-es; myspell-es; aspell-es; non-free-codecs; w32codecs; ubuntu-restricted-extras; ttf-??-??; gnome-exe-thumbnailer; mjpegtools; dpkg-dev; wine.
  También instalé un par de programas: Hard Info; Apton CD.
  Todos los paquetes funcionan bien pero desde hace unos días dejó de funcionar la pestaña del “Centro de Software”. Al hacer doble clic en ella, empieza a cargar pero no se abre. Si bien no poseo conexión a Internet, me sirve para encontrar nombres de aplicaciones o programas para instalar y los ya instalados.
  Lo que quisiera saber es si alguien sabe cual puede ser el problema. También me seria útil saber el comando para tratar de abrirlo desde la Terminal.
  Desde ya, agradezco cualquier respuesta.

---

### Post by alfplayer on 2010-08-24
El comando es software-center.

---

### Post by Cacique1 on 2010-08-25
Muchas gracias por tu respuesta. Hasta pronto.

---

### Post by Cacique1 on 2010-08-26
Hola. Hace unos días pregunté en este foro como abrir el Centro de Software desde la Terminal en Ubuntu 10.04, porque el acceso de la pestaña no funciona. Averigue que se debe escribir software.center, pero al hacerlo me sale el siguiente mensaje:

 Traceback (most recent call last):
      File "/usr/bin/software-center", line 80, in <module>
        app = SoftwareCenterApp(datadir, xapian_base_path)
      File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
        self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
      File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
        store = ViewSwitcherList(datadir, db, icons)
      File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 203, in __init__
        self._update_channel_list()
      File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 277, in _update_channel_list
        self.append(self.available_iter, [channel.get_channel_icon(),
    AttributeError: 'list' object has no attribute 'get_channel_icon'
    
Como soy nuevo en Linux, no sé que significa. ¿Hay alguna forma de arreglar el problema?.
Desde ya, agradezco cualquier respuesta.

---

### Post by viralmeme on 2010-08-26
> **Cacique1 said:**
> Hola. Hace unos días pregunté en este foro como abrir el Centro de Software desde la Terminal ..

$sudo /usr/bin/software-center

---

### Post by Cacique1 on 2010-08-30
Hola. El problema es que yo no tengo conexión a Internet. Todos los paquetes que baje lo hice desde un Ciber. ¿Hay alguna forma de arreglar el problema sin conexión?.

---

### Post by guillermolisi on 2010-08-30
Software Center esta pensado para ser usado con conexion a Internet.

Si no contas con esa conexion, solo te queda prescindir de SC y continuar bajandote e instalando paquetes como venis haciendo hasta ahora.

---

### Post by Cacique1 on 2010-09-01
Hola. Lamento la noticia. Gracias de todos modos. Hasta pronto.

---

### Post by asterix77 on 2010-09-01
Cacique 1
 
 
Paseate por este post donde se detalla como instalar aplicaciones offline con unvi.
 
 
[http://ubuntuforums.org/showthread.php?t=1342971](http://ubuntuforums.org/showthread.php?t=1342971) , a lo mejor te resulta más práctico.
 
 
Saludos

---

### Post by gabak on 2011-06-26
proba de esto va de 10


[http://ubuntuforums.org/showthread.php?t=1791038&highlight=software+center](http://ubuntuforums.org/showthread.php?t=1791038&highlight=software+center)

try this series:

Clean up your package installation

If you have installed and uninstalled a lot of applications, chances are your system is infected with a lot of dependencies files that you have absolutely no use for. Here are some useful commands to get rid of any partial package and remove any unused dependencies:
Cleaning up of partial package:
sudo apt-get autoclean

Cleaning up of the apt cache:
sudo apt-get clean

Cleaning up of any unused dependencies:
sudo apt-get autoremove

A good practice to avoid any left behind is to use the autoremove command whenever you want to uninstall an application.
sudo apt-get autoremove application-name

---

### Post by evroce on 2011-08-12
Tengo este mismo problema. Mi centro de software no funciona. Tengo el sistema 11.4, el ultimo que salio. Reamente soy nueva en esto tambien. Agradeceria que me ayudaran. Ya le di a la terminal y puse ~$ sudo apt-get autoclean, lo que aparece es lo siguiente:

Leyendo lista de paquetes... ¡Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.

Me gustaria saber como resolver este problema. Gracias desde ya. :)

---

### Post by guillermolisi on 2011-08-13
> **evroce said:**
> Tengo este mismo problema. Mi centro de software no funciona. Tengo el sistema 11.4, el ultimo que salio. Reamente soy nueva en esto tambien. Agradeceria que me ayudaran. Ya le di a la terminal y puse ~$ sudo apt-get autoclean, lo que aparece es lo siguiente:

Leyendo lista de paquetes... ¡Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.

Me gustaria saber como resolver este problema. Gracias desde ya. :)
Mostranos que sale cuando ingresas en una terminal/consola ```
sudo apt-get update
```por favor.

---

