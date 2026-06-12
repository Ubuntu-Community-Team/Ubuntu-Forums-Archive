---
title: "[SOLVED] KDM muerto, arrancando con GDM"
date: 2009-07-25
forum: Software
---

### Post by SLA_leandrin on 2009-07-25
Hola muchachos,

Hoy me levanto, y prendo la notebook y para mi sorpresa comienza sin las X en una TTY, entonces pienso "Caramba, mis X están rotas!", luego de lo cual me fijo en el log de xorg, pero no parece haber nada raro. Sin embargo, por si las moscas, ejecuto el afamado comando ```
sudo dpkg-reconfigure -phigh xserver.xorg
```, procediendo luego al no menos famoso ```
startx
```pero nada, de vuelta a la consola.

Es entonces cuando decido hacer un ```
sudo kdm
```, y al largar la pantalla de logueo del kdm aparece una con todos los usuarios (quiero decir, todos todos) y con un look "a la antigua". Decido que esto sería eventualmente lo de menos, y me logueo de todos modos. Sin embargo no pude, ya que me largaba un error que ahora no recuerdo.

La "solución" por el momento fué un ```
sudo gdm
``` y así pude loguearme por ahora. 

El archivo kdm.log me larga unos errores pero no los se interpretar, 

```
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
 ddxSigGiveUp: Closing log

```

Por las dudas adjunto el log completo, por si alguien tiene una pista.

Ah, dato importante ayer actualicé a KDE 4.3 RC3...

Gracias!!

---

### Post by guillermolisi on 2009-07-25
Que version de KDE estabas usando antes ?

Monitoreaste la actualizacion a KDE 4.3 RC3 ?

Acabo de terminar esa actualizacion desde el repositorio ppa de esa version y solo tuve que forzar la instalacion del wizard porque el mismo paquete estaba incluido para upgrade (referencia circular o autoreferencia).

Me habia pasado algo similar cuando pase de 4.1 a 4.2 y lo resolvi leyendo hasta que conclui en lo de forzar el reemplazo.

Hasta aqui y con 4.3 RC3 sin problemas (y mucho mas rapido y estable que la 4.2.3)

---

### Post by SLA_leandrin on 2009-07-25
> **guillermolisi said:**
> Que version de KDE estabas usando antes ?

Monitoreaste la actualizacion a KDE 4.3 RC3 ?

Estaba con KDE 4.3 RC2 y no... creo que le di un apt-get upgrade y actualizó a RC3... la verdad no le presté atención. Pero al reiniciar salió el mencionado problema y además el plasma-widget-network-manager sale eth=unavailable, a pesar de que está conectado perfectamente al Wi-Fi pero bue... esperaré a que en KDE 4.3 esto se solucione, no me preocupa mucho.

Viendo el log en /var/log/apt/term.log no encontré ningún error en la actualización...

---

### Post by guillermolisi on 2009-07-25
La verdad que no se pero tratare de averiguar donde esta ese log.

Por otra parte, si abris Aptitude te marca algun paquete roto ?

---

### Post by guillermolisi on 2009-07-25
Acabo de ver el log /var/log/kdm.log generado con la actualizacion y posterior reinicio de la maquina y me encontre con esto:

```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux guillermo 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd)
        Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 25 11:40:17 2009
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[B]The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
[/B]Errors from xkbcomp are not fatal to the X server
```

Las lineas referidas a nVidia aparecen porque estoy sin el driver por causa de tener que iniciar con acpi=off por incompatibilidad entre la implementacion de la mother y el kernel 2.6.28-13 (X-server no puede "mapear" la placa de video).

---

### Post by SLA_leandrin on 2009-07-25
> **guillermolisi said:**
> La verdad que no se pero tratare de averiguar donde esta ese log.

Ahí agregué el log, está en

```
/var/log/apt/term.log
```


> **guillermolisi said:**
> Por otra parte, si abris Aptitude te marca algun paquete roto ?

No, ningún paquete roto...cosa'e mandinga :confused:

---

### Post by guillermolisi on 2009-07-25
Fijate en ```
$ sudo less /var/log/apt/term.log
```

EDIT: Lo envie sin haber leido el tuyo, sorry !

---

### Post by SLA_leandrin on 2009-07-25
```
Configurando kdm (4:4.2.96-0ubuntu2~jaunty1~ppa2) ...

Fichero de configuración `/etc/kde4/kdm/kdmrc'
 ==> Modificado (por usted o por un script) desde la instalación.
 ==> El distribuidor del paquete ha publicado una versión actualizada.
   ¿Qué quisiera hacer al respecto?  Sus opciones son:
    Y o I  : instalar la versión del paquete
    N o O  : conservar la versión actualmente instalada
      D    : mostrar las diferencias entre versiones
      Z    : ir a un shell para examinar la situación
 La acción por omisión es conservar la versión actual.
*** kdmrc (Y/I/N/O/D/Z) [por omisión=N] ? y
Instalando una nueva versión del fichero de configuración /etc/kde4/kdm/kdmrc ...
Instalando una nueva versión del fichero de configuración /etc/init.d/kdm ...
Instalando una nueva versión del fichero de configuración /etc/logrotate.d/kdm ...


```

Será que el problema viene por ahí?

---

### Post by guillermolisi on 2009-07-25
Cuando hice la actualizacion y aparecio el mensaje en la consola le dije N a esa accion para que me conserve todo lo que tenia configurado en kdmrc. Por eso te pregunte si habias monitoreado el proceso.

Algo me dice que estas en el camino correcto.

---

### Post by SLA_leandrin on 2009-07-25
Claro el problema es que cuando pongo 

```
sudo dpkg-reconfigure kdm
``` no me manda a esa opción, sinó directamente la pantallita celeste donde me dice si quiero gdm o kdm...

Voy a probar reinstalando kdm y aviso...

---

### Post by staar on 2009-07-25
por lo que sabía, kdm fue (o está siendo) modificado en kde 4.3, porque ya estaba un poco viejito el pobre, puede que alguna opción en tu kdmrc sea incompatible con la nueva versión, te recomendaría no que lo reinstales, sino que primero lo desinstales con --purge (aunque no sé como será con el tema de las dependencias, fijate si no te pide desinstalar algo más, y tené cuidado) y después lo vuelvas a instalar...

saludos

---

### Post by SLA_leandrin on 2009-07-25
> **staar said:**
> por lo que sabía, kdm fue (o está siendo) modificado en kde 4.3, porque ya estaba un poco viejito el pobre, puede que alguna opción en tu kdmrc sea incompatible con la nueva versión, te recomendaría no que lo reinstales, sino que primero lo desinstales con --purge (aunque no sé como será con el tema de las dependencias, fijate si no te pide desinstalar algo más, y tené cuidado) y después lo vuelvas a instalar...

saludos

Casualmente, mirá lo que arroja el siguiente comando:

```
sudo aptitude remove kdm && sudo aptitude install kdm
Leyendo lista de paquetes... Hecho                                                       
Creando árbol de dependencias                                                            
Leyendo la información de estado... Hecho                                                
Leyendo la información de estado extendido                                               
Inicializando el estado de los paquetes... Hecho                                         
Escribiendo información de estado extendido... Hecho                                     
Los siguientes paquetes están ROTOS:                                                     
  kubuntu-desktop                                                                        
Se ELIMINARÁN los siguientes paquetes:                                                   
  kdm                                                                                    
0 paquetes actualizados, 0 nuevos instalados, 1 para eliminar y 0 sin actualizar.        
Necesito descargar 0B de ficheros. Después de desempaquetar se liberarán 3727kB.         
No se satisfacen las dependencias de los siguientes paquetes:                            
  kubuntu-desktop: Depende: kdm pero no es instalable                                    
Las acciones siguientes resolverán estas dependencias                                    

Eliminar los paquetes siguientes:
kubuntu-desktop                  

La puntuación es 119

¿Acepta esta solución? [Y/n/q/?] q

```

Me asusté un poco la verdad... por ahora dejo todo así :shock:
Esperaré a que salga KDE 4.3 (la versión de a de veras) y ahí veo, que aconsejan??

---

### Post by oktubrer on 2009-07-26
No te asustes, kubuntu-desktop es un "meta-paquete".  
Está para que al instalarlo automágicamente instale todos los paquetes que componen el entorno kde.  (Lo mismo con ubuntu-desktop y gnome, o xubuntu-desktop y xfce)
Kdm es parte de estos paquetes de los que "depende" kubuntu-desktop, por eso al querer eliminarlo te dice que kubuntu-desktop está roto.
Yo particularmente en ocasiones he eliminado algunos paquetes que no quería, y terminé eliminando también el metapaquete (en ese entonces usaba gnome, asi que era ubuntu-desktop) y no se generó ningún daño colateral.
No se si fui claro, pero por las dudas estaría bueno si alguien puede acotar algo más para que no hagas macanas por mi culpa.  =D

EDITO:
¿ probaste directamente "sudo aptitude **reinstall** kdm" ?

---

### Post by guillermolisi on 2009-07-26
Y si instalas KDM en forma forzada ?

---

### Post by SLA_leandrin on 2009-07-27
Hola muchachos, perdón por la demora en responder, estaba de viaje.

Problema resuelto, de la siguiente manera;

```
sudo aptitude reinstall kdm
sudo dpkg-reconfigure kdm
```

Gracias oktuber por el "reinstall" no me había avivado!

Guille o alguno de los moderadores, podemos marcar como Solved?

Saludos.

---

### Post by staar on 2009-07-27
me alegro que se haya solucionado, para marcar como solved, editá el primer mensaje y cambiale el título...

saludos

---

