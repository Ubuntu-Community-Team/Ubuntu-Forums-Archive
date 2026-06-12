---
title: "Error al actualizar"
date: 2012-10-18
forum: Software
---

### Post by octaviosk8 on 2012-10-18
[CENTER]Hola ,tengo Ubuntu 12.04.1 LTS , bueno en la ultima actualización me dio este error 
Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de esto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ar.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'

Soy nuevo en ubuntu y no se que signifique el error. 
[/CENTER]

---

### Post by guillermolisi on 2012-10-19
En este caso, en que utilizan mirrors de Argentina, el problema esta en que muchas veces no se actualizan bien, hay problemas de conectividad, paquetes corruptos, indices malformados, y una serie de etcs.

Cambia el origen de los repositorios, por ejemplo elegi los centrales, y volve a probar.

---

### Post by octaviosk8 on 2012-10-19
> **guillermolisi said:**
> En este caso, en que utilizan mirrors de Argentina, el problema esta en que muchas veces no se actualizan bien, hay problemas de conectividad, paquetes corruptos, indices malformados, y una serie de etcs.

Cambia el origen de los repositorios, por ejemplo elegi los centrales, y volve a probar.
Lo puse en Servidor Principal pero me sigue dando el mismo error
y otra cosa, cada vez que abro el software center este se cierra al instante y si lo reabro tambien ._.

---

### Post by octaviosk8 on 2012-10-19
[CENTER]Cuando abro elsoftware center se queda cargando y se cierra inesperadamente
en la consola dice esto: 
octavio@octavio-CDR-E11-S2:~$ software center
software: no se encontró la orden
octavio@octavio-CDR-E11-S2:~$ software-center
2012-10-19 12:54:11,428 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-10-19 12:54:11,445 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-10-19 12:54:12,906 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-10-19 12:54:13,375 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-10-19 12:54:13,593 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/update-software-center-agent", line 73, in <module>
    cache = apt.Cache(memonly=True)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 145, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.getdeb.net_ubuntu_dists_lucid-getdeb_games_binary-i386_Packages, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.
2012-10-19 12:54:35,159 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 1
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 145, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.getdeb.net_ubuntu_dists_lucid-getdeb_games_binary-i386_Packages, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.
2012-10-19 12:54:38,638 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1422, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1352, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 154, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 171, in init_view
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 238, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 511, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 271, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 450, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 439, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 124, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 317, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 212, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'

Y cuando intento instalar algo, sea lo que sea, por ejemplo el synatic que no lo tengo

octavio@octavio-CDR-E11-S2:~$ sudo apt-get install synaptic
Leyendo lista de paquetes... ¡Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.getdeb.net_ubuntu_dists_lucid-getdeb_games_binary-i386_Packages
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.
octavio@octavio-CDR-E11-S2:~$ 


o el gparted 

octavio@octavio-CDR-E11-S2:~$ sudo apt-get install gparted
Leyendo lista de paquetes... ¡Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.getdeb.net_ubuntu_dists_lucid-getdeb_games_binary-i386_Packages
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.
octavio@octavio-CDR-E11-S2:~$ 

y así con todo ._. ayuda xd 
[/CENTER]

---

### Post by guillermolisi on 2012-10-19
Los dos sintomas estan relacionados, es decir tiene la misma base problematica, asi que uni ambos hilos.

Para ubicarnos mejor en situacion:

Desde que medio instalaste, CD, pendrive ?
La imagen ISO fue verificada antes de la instalacion ?
Que conexion a Internet estas utilizando, en detalle ?

Luego, podrias mostrar el contenido del archivo /etc/apt/sources.list ?

---

### Post by octaviosk8 on 2012-10-19
> **guillermolisi said:**
> Los dos sintomas estan relacionados, es decir tiene la misma base problematica, asi que uni ambos hilos.

Para ubicarnos mejor en situacion:

Desde que medio instalaste, CD, pendrive ?
La imagen ISO fue verificada antes de la instalacion ?
Que conexion a Internet estas utilizando, en detalle ?

Luego, podrias mostrar el contenido del archivo /etc/apt/sources.list ?
USB, la imagen ISO la descargue desde la pag oficial y la instale con universal usb installer tal como dice la pag oficial
Estoy utilizando conexion wi fi a un router 3Com , el proveedor es Telecentro.

El contenido del source.list es el siguiente:

deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb games
deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
deb-src [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main

Muchas gacias desde ya

---

### Post by guillermolisi on 2012-10-19
Comenta/desactiva la siguiente lista de repositorios:
> deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb games
deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
deb-src [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
y volve a intentar la actualizacion.

Si falla, abri una consola/terminal e ingresa:
```
sudo dpkg --configure -a
```

Comentanos que resultado arrojo este ultimo proceso.

---

### Post by octaviosk8 on 2012-10-19
> **guillermolisi said:**
> Comenta/desactiva la siguiente lista de repositorios:

y volve a intentar la actualizacion.

Si falla, abri una consola/terminal e ingresa:
```
sudo dpkg --configure -a
```Comentanos que resultado arrojo este ultimo proceso.
Me funciono , MUCHISIMAS GRACIAS DE VERDAD!

---

### Post by guillermolisi on 2012-10-20
Buenisimo !

Ahora, seria muy interesante saber por que tenes esos repositorios que te sugeri desactivar.

Primero: Me llamo muchisimo la atencion que sean para una version de Ubuntu que no estas usando, Hardy en lugar de Precise que es la correcta.

Si alguno de ellos te permite mantener actualizado algun paquete de software de utilidad/interes, primero hay que ver si no hay empaquetados para Precise. Si los hay, actualizar la denomincacion del repositorio.

Hechos estos deberes, activar de a uno por vez e intentar la actualizacion. Si alguno reporta problemas, dejarlo desactivado.

Sigamos con esta parte para dar por resuelto el caso, que falta muy poco.

---

### Post by octaviosk8 on 2012-10-20
[CENTER]soy yo otra vez y con otro error ._. 
al comprobar las actualizaciones me dice lo siguiente: 

Falló al descargar la información del repositorio

Compruebe su conexión a Internet.

Detalles del error:

W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG 77589CABF0B5D826 Launchpad antigone, W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG ED08E6DC7A2DA9DB Launchpad PPA for David Rosca, W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG A6DCF7707EBC211F Launchpad PPA for Ubuntu Mozilla Security Team, W:Failed to fetch [http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Muchas gracias y espero no molestar con tantos errores en poco tiempo xD
[/CENTER]

---

### Post by madinc on 2012-10-20
you are not connected to the internet.
no está conectado a la internet.

---

### Post by octaviosk8 on 2012-10-20
> **madinc said:**
> you are not connected to the internet.
no está conectado a la internet.
¿ Y si no estoy conectado a internet como estoy respondiendo esto ?

---

### Post by madinc on 2012-10-20
> **octaviosk8 said:**
> ¿ Y si no estoy conectado a internet como estoy respondiendo esto ?

forgive me i thought  you had more than one PC, anyway i have looked those repos and they don't support Ubuntu Precise Pangolin, you should remove those repos and look for newer ones.

perdóname, pensé que tenía más de un PC, de todos modos he mirado los repos y no son compatibles con Ubuntu Precise Pangolin, debe quitar los repos y buscar nuevos.

---

### Post by octaviosk8 on 2012-10-20
> **madinc said:**
> forgive me i thought  you had more than one PC, anyway i have looked those repos and they don't support Ubuntu Precise Pangolin, you should remove those repos and look for newer ones.

perdóname, pensé que tenía más de un PC, de todos modos he mirado los repos y no son compatibles con Ubuntu Precise Pangolin, debe quitar los repos y buscar nuevos.
Que repositorios y como debo borrarlos ?

---

### Post by madinc on 2012-10-20
> **octaviosk8 said:**
> Que repositorios y como debo borrarlos ?

estos son los repos

> , W:Failed to fetch [http://ppa.launchpad.net/compiz/ppa/...-i386/Packages]("http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/binary-i386/Packages")  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/mozillateam...source/Sources]("http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/source/Sources")  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/mozillateam...-i386/Packages]("http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/binary-i386/Packages")  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/canonical-d...source/Sources]("http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/dists/precise/main/source/Sources")  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/compiz/ppa/...source/Sources]("http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/source/Sources")  404  Not Foundopen the update manager click settings then click other software and delete the repos that don't work.

abrir el gestor de actualizaciones de software haga clic en la configuración después haga clic en otro software y eliminar los repositorios que no funcionan.

ver imagen

---

### Post by octaviosk8 on 2012-10-21
> **madinc said:**
> estos son los repos

open the update manager click settings then click other software and delete the repos that don't work.

abrir el gestor de actualizaciones de software haga clic en la configuración después haga clic en otro software y eliminar los repositorios que no funcionan.

ver imagen
No me funciono D:

---

### Post by guillermolisi on 2012-10-21
De nuevo integre el otro hilo porque seguimos con problemas basados en lo mismo: Repositorios.

Si hay algun problema con la conexion a Internet, es algun comportamiento erratico en los DNS, pero descarto que este sea el problema porque no da errores en todos los repos.

Hasta donde vi, y excluyendo esos repos de Hardy que aun no se porque estaban activos, los demas repositorios son pertinentes de la version 12.04, asi que no veo razon para modificarlos/activar y/o desactivar alguno.

Por favor, no abrir mas hilos relacionados con este tema hasta que se presente otro claramente basado en otros origenes del problema. Gracias.

---

### Post by guillermolisi on 2012-10-21
Posiblemente lo que este sucediendo es que las URLs de los repos que estan dando error 404 hayan sido modificadas.

A efectos de lograr una base estable para las actualizaciones, para despues ir agregando repositorios PPA a discrecion, desactivar los que dan error 404, volver a actualizar y comentar que tal resulto.

Despues vemos como seguimos.

---

### Post by guillermolisi on 2012-10-21
El post de Nikkus fue movido a [http://ubuntuforums.org/showthread.php?t=2074367](http://ubuntuforums.org/showthread.php?t=2074367) generando un nuevo hilo ya que no era pertinente con este.

---

