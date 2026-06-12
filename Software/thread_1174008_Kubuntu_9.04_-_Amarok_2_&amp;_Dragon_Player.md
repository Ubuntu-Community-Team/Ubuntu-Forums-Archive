---
title: "Kubuntu 9.04 - Amarok 2 &amp; Dragon Player"
date: 2009-05-30
forum: Software
---

### Post by NickCis on 2009-05-30
Hola, hace poco instale Kubuntu 9.04. En general, me parecio muy logrado, y muy lindo a la vista.
Los unicos problemas que encontre fueron con el Dragon Player y el Amarok 2.
Con el Amarok 2, no encontre la opcion para reproducir CD de musica (los tipicos Cd qe compras legalmente en cualquier casa de musica), al meterlo, no se reproduce automaticamente, y no encuentro ninguna opcion para reproducirlo desde el amarok. Como puedo hacerlo?.

Y despues con el dragon player, el problema es que no puedo ver los menues de los videos. Osea, si meto un Dvd con menu, veo el menu todo bien. Pero si quiero reproducir un dvd que tengo el BackUp en la maquina no veo el menu. Como podria solucionar esto?.

Saludos, y gracias :P

---

### Post by guillermolisi on 2009-05-30
> **NickCis said:**
> Hola, hace poco instale Kubuntu 9.04. En general, me parecio muy logrado, y muy lindo a la vista.
Los unicos problemas que encontre fueron con el Dragon Player y el Amarok 2.
Con el Amarok 2, no encontre la opcion para reproducir CD de musica (los tipicos Cd qe compras legalmente en cualquier casa de musica), al meterlo, no se reproduce automaticamente, y no encuentro ninguna opcion para reproducirlo desde el amarok. Como puedo hacerlo?.

Y despues con el dragon player, el problema es que no puedo ver los menues de los videos. Osea, si meto un Dvd con menu, veo el menu todo bien. Pero si quiero reproducir un dvd que tengo el BackUp en la maquina no veo el menu. Como podria solucionar esto?.

Saludos, y gracias :P
Amarok 2 aun no tiene implementada a funcionalidad de reproducir musica desde un CD de audio (CDA).

---

### Post by NickCis on 2009-05-30
=(, que mala onda lo del Amarok, que programa sugieren para que reprodusca Cds?.

Y por lo de los Menues de los Dvd?, ya tengo los codecs instalados (creo, instale eso de w32codecs o algo asi). Lo raro es que me pasa solo cuando los videos que reprodusco los mando a reproducir desde una carpeta especifica. Por ej, si meto un Dvd, y me lo autoreproduce, el menu esta. Pero si agarro el Dragon Player y le digo reproducime tal archivo (llendo manualmente al Dvd, y dandole al archivo qeu supongo es el primero), no anda el menu. Tambien me pasa con archivos de pelicual (en formato dvd) que tengo en mi pc. Alguna idea?.

Saludos.

---

### Post by Hei Ku on 2009-05-30
Usar el VLC. El dragon player esta en pañales todavia. O esperar a la version beta de Kaffeine.

---

### Post by guillermolisi on 2009-05-30
Lo de Amarok pareceria una regresion funcional (muy vieja) pero en realidad estan laburando a full para ponerlo a la altura (y un poco mas) de su anterior version.

---

### Post by NickCis on 2009-05-30
Ok, tonces tendre qe esperar hasta que se desarrollen, seguire usando amarok, para musica de la pc, me gusta la manera que ordena y todo eso :P.

El Vlc es nativo QT, o me recomiendan una alternativa en qt?.

Saludos.

---

### Post by pablo.s on 2009-05-30
VLC viene con dos o tres
front-ends, de los cuales
por defecto utiliza el de QT.

---

### Post by SLA_leandrin on 2009-05-30
un poco OT:

Me acuerdo q en el ubuntu 8.04 q tenía instalado antes, el VLC a modo pantalla completa, cuando movías el mouse te salían los comandos tipo play, adelante, atrás y una barra de progreso. En el Kubuntu 9.04 eso no existe, y en OpenSuse con KDE 4.2 tampoco... es algún plugin o algo así? Alguien sabe?

Gracias...!

---

### Post by pablo.s on 2009-05-30
Es porque la versión
que compilaron para
Jaunty oficial no tenía
esa caracteristica activada.
Hay una versión 1.0.0-rc2
en un [PPA]("https://launchpad.net/%7Ekow/+archive/ppa") que posee
esta función.

---

### Post by SLA_leandrin on 2009-05-30
Mmmm q lástima, probé pero:

```
Sorry, the package "vlc 1.0.0~rc2+20090529-0ubuntu1+kow1" failed to install or upgrade"
```

Mandé el reporte de error. Veremos.

---

### Post by pablo.s on 2009-05-30
> **SLA_leandrin said:**
> 
```
Sorry, the package "vlc 1.0.0~rc2+20090529-0ubuntu1+kow1" failed to install or upgrade"
```Mandé el reporte de error. Veremos.

Te falta la clave del PPA.
Nada más que eso.
Fijate en un [URL="http://ubuntuforums.org/showthread.php?t=1173614"]thread de
ayer[/URL] que escribi un paso
a paso como obtener la
clave de un PPA.
Reemplaza los datos y
te va a dejar bajar los
paquetes.

---

### Post by SLA_leandrin on 2009-05-30
Nada che, agregué la key pero parece q no es eso el problema,

```
Se encontraron errores al procesar:                                           
 /var/cache/apt/archives/vlc_1.0.0~rc2+20090529-0ubuntu1~kow1_i386.deb        
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

No se cual es el error code (1)...

---

### Post by guillermolisi on 2009-05-30
> **SLA_leandrin said:**
> Mmmm q lástima, probé pero:

```
Sorry, the package "vlc 1.0.0~rc2+20090529-0ubuntu1+kow1" failed to install or upgrade"
```Mandé el reporte de error. Veremos.
Si, logico, si no esta en los repositorios de la distribucion no hay soporte.

De paso, chivo para avisar que hay un sticky nuevo sobre como reportar bugs en Español, gentileza e iniciativa de Sajnox.

---

### Post by pablo.s on 2009-05-30
Debe haber bajado el 
paquete, pero por el
error que te da, es
probable que al tratar
de instalarlo se haya
roto el paquete.
Fijate en Synaptic si
figuran paquetes rotos
y desinstalá el que
aparezca.
Luego intentá instalar
la versión nueva.

PD: NO hay que reportar
bug, porque funciona.
El tema es que para los
PPA hay que incorporar
la clave, por un tema de
seguridad están firmados
los paquetes.

---

### Post by dirty fingers on 2009-05-30
me parece que lo mejorcito para kubuntu es el smplayer :idea:

---

### Post by NickCis on 2009-05-31
Como es eso de los distintos fronts para el vlcplayer?, me dan algunos ejemplos?.
Como los tengo que instalar?, primero el vlc normal y dsp eso?.

Saludos.

---

### Post by pablo.s on 2009-05-31
> **NickCis said:**
> Como es eso de los distintos fronts para el vlcplayer?, me dan algunos ejemplos?.
Como los tengo que instalar?, primero el vlc normal y dsp eso?.

No, para nada, eso depende
del que compila el código
fuente. VLC tiene varios
front-end, pero según el
gusto del que la compile,
vienen o no. En el sistema
Git (que es una especie de
repositorio de código) 
de VLC está cada versión. 
Supongamos que vos tenés
la versión 1.0RC que bajaste
de GetDeb. El empaquetador
por lo general es Christoph
Korn. Bueno, él decide que
quiere compilar con el front-end
de QT, pero no con el de wxWidgets.
Cuando le da las opciones para
que se compile le dice: hacelo
para QT4. Eso se llama usar
flags. Igualmente el front-end
mas logrado es el de QT4.

---

### Post by NickCis on 2009-05-31
> **pablo.s said:**
> No, para nada, eso depende
del que compila el código
fuente. VLC tiene varios
front-end, pero según el
gusto del que la compile,
vienen o no. En el sistema
Git (que es una especie de
repositorio de código) 
de VLC está cada versión. 
Supongamos que vos tenés
la versión 1.0RC que bajaste
de GetDeb. El empaquetador
por lo general es Christoph
Korn. Bueno, él decide que
quiere compilar con el front-end
de QT, pero no con el de wxWidgets.
Cuando le da las opciones para
que se compile le dice: hacelo
para QT4. Eso se llama usar
flags. Igualmente el front-end
mas logrado es el de QT4.

Ahh,,, y para usar en Kubuntu 9.04 (me parece qe usa Kde 4.2, no?), que sugieren, que lo instale del repositorio normal, y listo?. O usa vercion no esta compilada con QT?. O de get deb?.

Saludos.

---

### Post by pablo.s on 2009-05-31
> **NickCis said:**
> que sugieren, que lo instale del repositorio normal, y listo?.

Yo te recomiendo la
versión que está en
el PPA que comenté
en este mismo thread.

---

