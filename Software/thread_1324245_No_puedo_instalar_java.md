---
title: "No puedo instalar java"
date: 2009-11-12
forum: Software
---

### Post by matias_tati on 2009-11-12
Logro instalar sun-java6-bin y sun-java6-jre
Pero sun-java-plugins no logro me tira esto en Synaptic
Es para instalar Jdownloader.

[[img]http://h.imagehost.org/t/0842/Pantallazo.jpg[/img]](http://h.imagehost.org/view/0842/Pantallazo)

---

### Post by SLA_leandrin on 2009-11-12
Creo -creo- que no necesitás ningún plugin extra además de java para el Jdownloader...

Probaste instalando ubuntu-restricted-extras?

---

### Post by matias_tati on 2009-11-12
Me tira este cartel cuando intento abrirlo y supuse que era por eso.

[[img]http://h.imagehost.org/t/0686/Pantallazo.jpg[/img]](http://h.imagehost.org/view/0686/Pantallazo)

---

### Post by SLA_leandrin on 2009-11-12
```
sudo apt-cache search libgcj.so
[sudo] password for leandro: 
libgcj-bc - Biblioteca de enlace para usar con gcj

```

Mirá, haciendo un search me sale que necesitas esa biblioteca, probá haciendo un

```
sudo apt-get install libgcj-bc
```

---

### Post by matias_tati on 2009-11-12
No funca podria alguien guiarme paso a paso y voy contando que errores me tira y lo que hago?
A los mod: Abro un tema nuevo?

---

### Post by guillermolisi on 2009-11-12
> **matias_tati said:**
> No funca podria alguien guiarme paso a paso y voy contando que errores me tira y lo que hago?
A los mod: Abro un tema nuevo?
Seguilo aqui y en todo caso se adecua el Title del thread y listo.

---

### Post by matias_tati on 2009-11-12
Ok gracias.

---

### Post by matias_tati on 2009-11-13
Bueno para instalar Jdown loader sigo las intrucciones de este tutorial
[http://geek-side.net/como-instalar-jdownloader-en-ubuntu-9-10-karmic-koala/](http://geek-side.net/como-instalar-jdownloader-en-ubuntu-9-10-karmic-koala/)

Como rpimer paso me pide que ejecute 

sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugins

Y me tira 

matias@matias-desktop:~$ sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugins
[sudo] password for matias: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
sun-java6-jre ya está en su versión más reciente.
sun-java6-bin ya está en su versión más reciente.
E: No se pudo encontrar el paquete sun-java6-plugins
matias@matias-desktop:~$

---

### Post by josecuervo86 on 2009-11-13
Tenes los repos multiverse activados? Ese paquete esta ahi. 

[http://packages.ubuntu.com/karmic/sun-java6-plugin](http://packages.ubuntu.com/karmic/sun-java6-plugin)

---

### Post by santiagoward2000 on 2009-11-13
Hola!
Me parece que debe haber un error de ortografia en esa pagina (si, ya se, hablo de errores de ortografia y aca no me andan los acentos ;)). El paquete se llama **sun-java6-plugin** (sin la **s**).
Proba:
```
sudo apt-get install sun-java6-plugin
``` y fijate si con eso anda.
Saludos!

---

### Post by matias_tati on 2009-11-13
> **santiagoward2000 said:**
> Hola!
Me parece que debe haber un error de ortografia en esa pagina (si, ya se, hablo de errores de ortografia y aca no me andan los acentos ;)). El paquete se llama **sun-java6-plugin** (sin la **s**).
Proba:
```
sudo apt-get install sun-java6-plugin
``` y fijate si con eso anda.
Saludos!

matias@matias-desktop:~$ sudo apt-get install sun-java6-plugin
[sudo] password for matias: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  sun-java6-plugin: Depende: sun-java6-bin (= 6-15-1) pero 6-16-0ubuntu1.9.04 va a ser instalado
E: Paquetes rotos
matias@matias-desktop:~$

---

### Post by matias_tati on 2009-11-13
> **josecuervo86 said:**
> Tenes los repos multiverse activados? Ese paquete esta ahi. 

[http://packages.ubuntu.com/karmic/sun-java6-plugin](http://packages.ubuntu.com/karmic/sun-java6-plugin)

Me podrias especificar bien como hacerlo? no quiero hacer macana.

---

### Post by matias_tati on 2009-11-15
NO se olviden de mi por favor.

---

### Post by santiagoward2000 on 2009-11-15
> **matias_tati said:**
> matias@matias-desktop:~$ sudo apt-get install sun-java6-plugin
[sudo] password for matias: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  sun-java6-plugin: Depende: sun-java6-bin (= 6-15-1) pero **[COLOR="Red"]6-16-0ubuntu1.9.04[/COLOR]** va a ser instalado
E: Paquetes rotos
matias@matias-desktop:~$

Hola y perdón por la demora!
Me parece raro lo que marqué en rojo. En mis repositorios solo tengo la versión 6-15-1 (que es la que te pide). ¿Agregaste algún repositorio?
Igual, probemos algo. Abrí Synaptic y buscá el paquete **sun-java6-bin**. Seleccionálo y tocá en **Package > Force Version...** (o podés usar **Ctrl+E**). En la ventana que te abre, seleccioná la versión 6-15-1 y dale **Force Version**.
Si todo va bien, tratá de instalar de nuevo el **sun-java6-plugin**.
Cualquier cosa preguntá.
Saludos!

---

### Post by guillermolisi on 2009-11-15
> **santiagoward2000 said:**
> Hola y perdón por la demora!
Me parece raro lo que marqué en rojo. En mis repositorios solo tengo la versión 6-15-1 (que es la que te pide). ¿Agregaste algún repositorio?
Igual, probemos algo. Abrí Synaptic y buscá el paquete **sun-java6-bin**. Seleccionálo y tocá en **Package > Force Version...** (o podés usar **Ctrl+E**). En la ventana que te abre, seleccioná la versión 6-15-1 y dale **Force Version**.
Si todo va bien, tratá de instalar de nuevo el **sun-java6-plugin**.
Cualquier cosa preguntá.
Saludos!
Y si es peor el remedio que la enfermedad, cual es el plan para volver atras, el rollback plan para dejar las cosas como estaban originalmente y volver a empezar ?

Por que ese paquete y no el que corresponde a KK ? Estaran correctos los repositorios seleccionados ?

---

### Post by santiagoward2000 on 2009-11-15
Hola Guille!

> **guillermolisi said:**
> Por que ese paquete y no el que corresponde a KK ?

El 6-15-1 es el que corresponde a Karmic. La 6-16-0ubuntu1.9.04 está en **jaunty-updates**. [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=sun-java6-bin]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=sun-java6-bin")
Me parece que tenés razón, debe haber algo mal es sus repositorios (a no ser que siga usando Jaunty, yo imaginé que era Karmic por la guía que señaló).
Saludos!

---

### Post by matias_tati on 2009-11-15
Uso Karmic actualize hace poco y necesitaria ayuda porque no me guio con el link

---

### Post by santiagoward2000 on 2009-11-15
> **matias_tati said:**
> Uso Karmic actualize hace poco y necesitaria ayuda porque no me guio con el link

Entonces me parece que hay algo mal en tus respositorios (el link era solo para mostrar que la version de Karmic es la 6-15-1, mientras que la 6-16-0ubuntu1.9.04 fue una actualizacion de Jaunty). ¿Podés subir el contenido del archivo **/etc/apt/sources.list** y los que estén en **/etc/apt/sources.list.d**?

---

### Post by matias_tati on 2009-11-15
[[img]http://a.imagehost.org/t/0640/Pantallazo-Or_genes_del_software.jpg[/img]](http://a.imagehost.org/view/0640/Pantallazo-Or_genes_del_software)

[[img]http://i.imagehost.org/t/0109/Pantallazo-sources_list_d_Navegador_de_archivos.jpg[/img]](http://i.imagehost.org/view/0109/Pantallazo-sources_list_d_Navegador_de_archivos)

---

### Post by santiagoward2000 on 2009-11-15
¿Podrias en una terminal escribir:
```
gedit /etc/apt/sources.list
``` y copiar el texto aca?

---

### Post by matias_tati on 2009-11-15
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) intrepid main # (desactivado en la actualización a karmic)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports restricted main multiverse universe
deb [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./ # (desactivado en la actualización a karmic)
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./ # (desactivado en la actualización a karmic)

---

### Post by santiagoward2000 on 2009-11-15
> **matias_tati said:**
> # deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[COLOR="Red"]deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse[/COLOR]
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) intrepid main # (desactivado en la actualización a karmic)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports restricted main multiverse universe
deb [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./ # (desactivado en la actualización a karmic)
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./ # (desactivado en la actualización a karmic)

Me parece que el problema debe venir por la linea que marque en rojo. Me parece que ahi tendria que decir **karmic-backports**.
En la terminal escribi:
```
sudo gedit /etc/apt/sources.list
```
pone tu password, cambia jaunty por karmic en esa linea (no toques nada mas), guarda y cerra. Despues, en la terminal hace:
```
sudo apt-get update
sudo apt-get install sun-java6-plugin
```
y comenta si anduvo.
Suerte!

---

### Post by josecuervo86 on 2009-11-15
> **matias_tati said:**
> 
[COLOR="Red"]deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse[/COLOR]


Estara aca el problema?

Santiago no vi tu comentario :)

---

### Post by matias_tati on 2009-11-16
Lo cambie y me sigue pasando lo mismo....

---

### Post by guillermolisi on 2009-11-16
> **matias_tati said:**
> Lo cambie y me sigue pasando lo mismo....
Luego de cambiarlo, hiciste una actualizacion del cache de repositorios (apt-get update) ?

---

### Post by matias_tati on 2009-11-16
> **guillermolisi said:**
> Luego de cambiarlo, hiciste una actualizacion del cache de repositorios (apt-get update) ?

Si segui los pasos al pie de la letra..

---

### Post by guillermolisi on 2009-11-16
Desactivaste este otro repositorio de Intrepid ?
> 
deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) intrepid main # (desactivado en la actualización a karmic)

---

### Post by josecuervo86 on 2009-11-16
> **guillermolisi said:**
> Desactivaste este otro repositorio de Intrepid ?

Es verdad! Al ultimo del sources.list hay tres repos, uno de intrepid y dos de Jaunty que no están comentados. Comentalos y fijate que onda, y de paso mostranos el source.list como queda

---

### Post by matias_tati on 2009-11-17
Como los desactivo?

---

### Post by guillermolisi on 2009-11-17
En Origenes de Software (Software Sources) tenes una pestaña para marcar/desmarcar (habilitar/deshabilitar) repositorios.
Tenes que tener habilitados solamente repositorios para Karmic.

---

### Post by matias_tati on 2009-12-02
Este es el resultado de sudo apt-get update

```
matias@matias-desktop:~$ sudo apt-get update
[sudo] password for matias: 
Obj http://ar.archive.ubuntu.com karmic-backports Release.gpg                  
Ign http://ar.archive.ubuntu.com karmic-backports/main Translation-es          
Obj http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com stable/non-free Translation-es                        
Obj http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-es                 
Obj http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-es                      
Obj http://archive.ubuntu.com karmic Release.gpg                               
Des:1 http://archive.ubuntu.com karmic/main Translation-es [622kB]             
Ign http://ar.archive.ubuntu.com karmic-backports/restricted Translation-es    
Ign http://ar.archive.ubuntu.com karmic-backports/universe Translation-es      
Ign http://ar.archive.ubuntu.com karmic-backports/multiverse Translation-es    
Ign http://www.pvv.ntnu.no ./ Release.gpg                                      
Ign http://www.pvv.ntnu.no ./ Translation-es                                   
Obj http://ar.archive.ubuntu.com karmic-backports Release                      
Obj http://deb.opera.com stable Release                                        
Obj http://archive.canonical.com karmic Release                                
Des:2 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-es                        
Obj http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-es                        
Des:3 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-es                        
Des:4 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-es                        
Des:5 http://www.pvv.ntnu.no ./ Release [712B]                                 
Obj http://ppa.launchpad.net intrepid Release                                  
Des:6 http://ppa.launchpad.net karmic Release [66,0kB]                         
Obj http://ar.archive.ubuntu.com karmic-backports/main Packages                
Obj http://archive.canonical.com karmic/partner Packages                       
Obj http://www.pvv.ntnu.no ./ Packages                                         
Ign http://deb.opera.com stable/non-free Packages                              
Obj http://ar.archive.ubuntu.com karmic-backports/restricted Packages          
Obj http://ar.archive.ubuntu.com karmic-backports/universe Packages            
Obj http://ar.archive.ubuntu.com karmic-backports/multiverse Packages          
Obj http://archive.canonical.com karmic/partner Sources                        
Ign http://deb.opera.com stable/non-free Packages                              
Obj http://www.pvv.ntnu.no ./ Sources                                          
Obj http://deb.opera.com stable/non-free Packages                              
Obj http://ppa.launchpad.net karmic Release                                    
Des:7 http://ppa.launchpad.net karmic Release [66,0kB]             
Ign http://ppa.launchpad.net karmic Release                                    
Des:8 http://ppa.launchpad.net karmic Release [66,0kB]                         
Obj http://ppa.launchpad.net intrepid/main Packages                            
Ign http://ppa.launchpad.net karmic Release                                    
Des:9 http://ppa.launchpad.net karmic/main Packages [3.293B]                   
Obj http://ppa.launchpad.net karmic/main Packages                              
Des:10 http://ppa.launchpad.net karmic/main Packages [629B]                    
Obj http://ppa.launchpad.net karmic/main Packages                              
Obj http://ppa.launchpad.net karmic/main Sources                               
Des:11 http://archive.ubuntu.com karmic/restricted Translation-es [4.012B]     
Des:12 http://archive.ubuntu.com karmic/universe Translation-es [1.328kB]      
Des:13 http://archive.ubuntu.com karmic/multiverse Translation-es [106kB]      
Obj http://archive.ubuntu.com karmic-updates Release.gpg                       
Ign http://archive.ubuntu.com karmic-updates/main Translation-es               
Ign http://archive.ubuntu.com karmic-updates/restricted Translation-es         
Ign http://archive.ubuntu.com karmic-updates/universe Translation-es           
Ign http://archive.ubuntu.com karmic-updates/multiverse Translation-es         
Obj http://archive.ubuntu.com karmic-security Release.gpg                      
Ign http://archive.ubuntu.com karmic-security/main Translation-es              
Ign http://archive.ubuntu.com karmic-security/restricted Translation-es        
Ign http://archive.ubuntu.com karmic-security/universe Translation-es          
Ign http://archive.ubuntu.com karmic-security/multiverse Translation-es        
Obj http://archive.ubuntu.com karmic-backports Release.gpg                     
Ign http://archive.ubuntu.com karmic-backports/restricted Translation-es       
Ign http://archive.ubuntu.com karmic-backports/main Translation-es             
Ign http://archive.ubuntu.com karmic-backports/multiverse Translation-es       
Ign http://archive.ubuntu.com karmic-backports/universe Translation-es         
Obj http://archive.ubuntu.com karmic Release                                   
Obj http://archive.ubuntu.com karmic-updates Release                           
Obj http://archive.ubuntu.com karmic-security Release                          
Obj http://archive.ubuntu.com karmic-backports Release                         
Obj http://archive.ubuntu.com karmic/main Packages                             
Obj http://archive.ubuntu.com karmic/restricted Packages                       
Obj http://archive.ubuntu.com karmic/main Sources                              
Obj http://archive.ubuntu.com karmic/restricted Sources                        
Obj http://archive.ubuntu.com karmic/universe Packages                         
Obj http://archive.ubuntu.com karmic/universe Sources                          
Obj http://archive.ubuntu.com karmic/multiverse Packages                       
Obj http://archive.ubuntu.com karmic/multiverse Sources                        
Obj http://archive.ubuntu.com karmic-updates/main Packages                     
Obj http://archive.ubuntu.com karmic-updates/restricted Packages               
Obj http://archive.ubuntu.com karmic-updates/main Sources                      
Obj http://archive.ubuntu.com karmic-updates/restricted Sources                
Obj http://archive.ubuntu.com karmic-updates/universe Packages                 
Obj http://archive.ubuntu.com karmic-updates/universe Sources                  
Obj http://archive.ubuntu.com karmic-updates/multiverse Packages               
Obj http://archive.ubuntu.com karmic-updates/multiverse Sources                
Obj http://archive.ubuntu.com karmic-security/main Packages                    
Obj http://archive.ubuntu.com karmic-security/restricted Packages              
Obj http://archive.ubuntu.com karmic-security/main Sources                     
Obj http://archive.ubuntu.com karmic-security/restricted Sources               
Obj http://archive.ubuntu.com karmic-security/universe Packages                
Obj http://archive.ubuntu.com karmic-security/universe Sources                 
Obj http://archive.ubuntu.com karmic-security/multiverse Packages              
Obj http://archive.ubuntu.com karmic-security/multiverse Sources               
Obj http://archive.ubuntu.com karmic-backports/restricted Packages             
Obj http://archive.ubuntu.com karmic-backports/main Packages                   
Obj http://archive.ubuntu.com karmic-backports/multiverse Packages             
Obj http://archive.ubuntu.com karmic-backports/universe Packages               
Descargados 2.197kB en 31s (69,6kB/s)                                          
Leyendo lista de paquetes... Hecho
W: Error de GPG: http://ppa.launchpad.net karmic Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 5A9BF3BB4E5E17B5
W: Error de GPG: http://ppa.launchpad.net karmic Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 0A316B5D4827A579
matias@matias-desktop:~$
```

[[img]http://h.imagehost.org/t/0347/Pantallazo-Or_genes_del_software.jpg[/img]](http://h.imagehost.org/view/0347/Pantallazo-Or_genes_del_software)

---

### Post by guillermolisi on 2009-12-02
Ademas de que no verifica/le falta la clave de autenticacion correcta (porque me parece que lo que esta mal es el nombre del repositorio), tenes varias menciones a repositorios Intrepid y eso te traera problemas ya que estas usando Karmic.

---

### Post by matias_tati on 2009-12-02
Entonces que hago yo no entiendo ni jota de esto...

---

### Post by guillermolisi on 2009-12-02
> **matias_tati said:**
> Entonces que hago yo no entiendo ni jota de esto...
Con el utilitario Origenes de Software (Software Sources) tenes que deshabilitar/desmarcar las entradas de los repositorios que corresponden a Intrepid y que, por lo que vi, tambien tenes habilitados para Karmic.

Luego dale una leida a [este thread]("http://ubuntuforums.org/showthread.php?t=1174296") que habla sobre como agregar correctamente repositorios ppa y sus claves.

---

### Post by matias_tati on 2009-12-02
> **guillermolisi said:**
> Con el utilitario Origenes de Software (Software Sources) tenes que deshabilitar/desmarcar las entradas de los repositorios que corresponden a Intrepid y que, por lo que vi, tambien tenes habilitados para Karmic.

Luego dale una leida a [este thread]("http://ubuntuforums.org/showthread.php?t=1174296") que habla sobre como agregar correctamente repositorios ppa y sus claves.

Un pregunta: para que seria exactamente PPA porque es de Chromium esta pero la desactivo en todo caso, pq esta chromium no es la version final y solo la estoy probando.

Edito: lo agregue con el comando sudo add-apt-repository disponible en Karmic

ahora tiro el resultado nuevament a ver si ven algo raro:

```
matias@matias-desktop:~$ sudo apt-get update
Obj http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-es                        
Obj http://ppa.launchpad.net karmic Release.gpg                                
Obj http://ar.archive.ubuntu.com karmic-backports Release.gpg                  
Ign http://ar.archive.ubuntu.com karmic-backports/main Translation-es          
Ign http://ar.archive.ubuntu.com karmic-backports/restricted Translation-es    
Ign http://ppa.launchpad.net karmic/main Translation-es                        
Obj http://ppa.launchpad.net karmic Release                                    
Ign http://ar.archive.ubuntu.com karmic-backports/universe Translation-es      
Ign http://ar.archive.ubuntu.com karmic-backports/multiverse Translation-es    
Obj http://ar.archive.ubuntu.com karmic-backports Release                      
Obj http://ppa.launchpad.net karmic Release                                    
Obj http://ar.archive.ubuntu.com karmic-backports/main Packages                
Obj http://ppa.launchpad.net karmic/main Packages                              
Obj http://ar.archive.ubuntu.com karmic-backports/restricted Packages          
Obj http://ar.archive.ubuntu.com karmic-backports/universe Packages            
Obj http://ar.archive.ubuntu.com karmic-backports/multiverse Packages          
Obj http://ppa.launchpad.net karmic/main Packages                              
Obj http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com stable/non-free Translation-es                        
Obj http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-es                 
Obj http://deb.opera.com stable Release                                        
Obj http://archive.canonical.com karmic Release                                
Ign http://deb.opera.com stable/non-free Packages                              
Obj http://archive.canonical.com karmic/partner Packages                       
Ign http://deb.opera.com stable/non-free Packages                              
Obj http://archive.canonical.com karmic/partner Sources                        
Obj http://deb.opera.com stable/non-free Packages                             
Obj http://archive.ubuntu.com karmic Release.gpg       
Obj http://archive.ubuntu.com karmic/main Translation-es
Obj http://archive.ubuntu.com karmic/restricted Translation-es
Obj http://archive.ubuntu.com karmic/universe Translation-es
Obj http://archive.ubuntu.com karmic/multiverse Translation-es
Obj http://archive.ubuntu.com karmic-updates Release.gpg
Ign http://archive.ubuntu.com karmic-updates/main Translation-es
Ign http://archive.ubuntu.com karmic-updates/restricted Translation-es
Ign http://archive.ubuntu.com karmic-updates/universe Translation-es
Ign http://archive.ubuntu.com karmic-updates/multiverse Translation-es
Obj http://archive.ubuntu.com karmic-security Release.gpg
Ign http://archive.ubuntu.com karmic-security/main Translation-es
Ign http://archive.ubuntu.com karmic-security/restricted Translation-es
Ign http://archive.ubuntu.com karmic-security/universe Translation-es
Ign http://archive.ubuntu.com karmic-security/multiverse Translation-es
Obj http://archive.ubuntu.com karmic-backports Release.gpg
Ign http://archive.ubuntu.com karmic-backports/restricted Translation-es
Ign http://archive.ubuntu.com karmic-backports/main Translation-es
Ign http://archive.ubuntu.com karmic-backports/multiverse Translation-es
Ign http://archive.ubuntu.com karmic-backports/universe Translation-es
Obj http://archive.ubuntu.com karmic Release
Obj http://archive.ubuntu.com karmic-updates Release
Obj http://archive.ubuntu.com karmic-security Release
Obj http://archive.ubuntu.com karmic-backports Release
Obj http://archive.ubuntu.com karmic/main Packages
Obj http://archive.ubuntu.com karmic/restricted Packages
Obj http://archive.ubuntu.com karmic/main Sources
Obj http://archive.ubuntu.com karmic/restricted Sources
Obj http://archive.ubuntu.com karmic/universe Packages
Obj http://archive.ubuntu.com karmic/universe Sources
Obj http://archive.ubuntu.com karmic/multiverse Packages
Obj http://archive.ubuntu.com karmic/multiverse Sources
Obj http://archive.ubuntu.com karmic-updates/main Packages
Obj http://archive.ubuntu.com karmic-updates/restricted Packages
Obj http://archive.ubuntu.com karmic-updates/main Sources
Obj http://archive.ubuntu.com karmic-updates/restricted Sources
Obj http://archive.ubuntu.com karmic-updates/universe Packages
Obj http://archive.ubuntu.com karmic-updates/universe Sources
Obj http://archive.ubuntu.com karmic-updates/multiverse Packages
Obj http://archive.ubuntu.com karmic-updates/multiverse Sources
Obj http://archive.ubuntu.com karmic-security/main Packages
Obj http://archive.ubuntu.com karmic-security/restricted Packages
Obj http://archive.ubuntu.com karmic-security/main Sources
Obj http://archive.ubuntu.com karmic-security/restricted Sources
Obj http://archive.ubuntu.com karmic-security/universe Packages
Obj http://archive.ubuntu.com karmic-security/universe Sources
Obj http://archive.ubuntu.com karmic-security/multiverse Packages
Obj http://archive.ubuntu.com karmic-security/multiverse Sources
Obj http://archive.ubuntu.com karmic-backports/restricted Packages
Obj http://archive.ubuntu.com karmic-backports/main Packages
Obj http://archive.ubuntu.com karmic-backports/multiverse Packages
Obj http://archive.ubuntu.com karmic-backports/universe Packages
Leyendo lista de paquetes... Hecho
matias@matias-desktop:~$ 

```

---

### Post by guillermolisi on 2009-12-03
Ahora tenes todos los repos para Karmic, salvo el de Opera que no especifica, solo dice stable.
De hecho no te dio ningun error despues de actualizar el cache de repositorios.

No entiendo tu pregunta sobre los repositorios ppa.

---

### Post by matias_tati on 2009-12-03
No importa.
Ahora pruebo instalar java de nuevo?

---

