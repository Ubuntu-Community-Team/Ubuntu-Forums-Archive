---
title: "No puedo instalar mediubuntu"
date: 2009-03-14
forum: Software
---

### Post by guillermon on 2009-03-14
Hola, he reinstalado, pasando a II, 8.10. Pero cuando instalo mediubuntu, me figura lo siguiente:
guille@guille-desktop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
--2009-03-14 22:01:37--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolviendo [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Conectando a [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 230 [text/plain]
Guardando: «/etc/apt/sources.list.d/medibuntu.list»

100%[======================================>] 230         --.-K/s   en 0s      

2009-03-14 22:01:37 (16,4 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' guardado [230/230]

E: Línea 53 mal formada en lista de fuentes /etc/apt/sources.list (análisis de dist)
guille@guille-desktop:~$
No sé bien cómo hacer... ayuda.... Desde ya gracias!!

---

### Post by staar on 2009-03-14
agregalo manualmente, editá el sources.list ```
sudo gedit /etc/apt/sources.list
``` agregale la linea ```
deb http://packages.medibuntu.org/ intrepid free non-free
``` recargá ```
sudo aptitude update
``` y despues instalá estos paquetes ```
sudo aptitude install medibuntu-keyring app-install-data-medibuntu.
```

saludos

---

### Post by guillermon on 2009-03-15
> **staar said:**
> agregalo manualmente, editá el sources.list ```
sudo gedit /etc/apt/sources.list
``` agregale la linea ```
deb http://packages.medibuntu.org/ intrepid free non-free
``` recargá ```
sudo aptitude update
``` y despues instalá estos paquetes ```
sudo aptitude install medibuntu-keyring app-install-data-medibuntu.
```

saludos

Hola, he seguido tus pasos. Luego de editar el sources.list, cuando quiero recargar vuelve a aparecer ese error. También ahora lo hace cuendo quiere actualizar el sistema, y dice así
```
No se ha podido inicializar la información de los paquetes

Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Línea 53 mal formada en lista de fuentes /etc/apt/sources.list (análisis de dist), E:No se pudieron leer las listas de fuentes.'
```
        Soy conciente que tengo un error, y no sé cómo solucionarlo. Agradezco tu ayuda, y espero que me ayudes de nuevo. Un grato saludo
Guillermo

---

### Post by Hei Ku on 2009-03-15
Postea tu archivos /etc/apt/sources.list, porque algo mal tenes ahi.

---

### Post by guillermon on 2009-03-22
> **Hei Ku said:**
> Postea tu archivos /etc/apt/sources.list, porque algo mal tenes ahi.

   Hola Hei Ku, me he demorado en responder, perdón (sigo muy interesado en resolver esto que tengo mal ahí). Cuando ejecuto ese archivo que me indicas, me abre el menú de Orígenes de Software... es por ello que te adjunto una captura. Ejecutanndo /etc/apt/sources.list.save, se puede ver sus detalles, que los copio a continuación. Espero vuestra ayuda, desde ya mil gracias!
```
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ar.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ar.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://ar.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://ar.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://ar.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ar.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://ar.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb-src http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb https://dl-ssl.google.com/linux/linux_signing_key.pub intrepid
```

---

### Post by Hei Ku on 2009-03-22
La ultima linea de tu sources.list no es un repositorio, si no la clave publica de google. Saca esa linea y volve a probar. Deberia funcionar bien ahora.

---

### Post by guillermon on 2009-03-25
> **Hei Ku said:**
> La ultima linea de tu sources.list no es un repositorio, si no la clave publica de google. Saca esa linea y volve a probar. Deberia funcionar bien ahora.

   Hola Hei Ku, he borrado como lo sugieres, y continúa el error, igual... He reiniciado, por supuesto. Continúa dando el cartel apenas se inicia el sistema; cuando le doy click, me dice que la línea 53 está mal formada, etc....
   Gracias igual, espero alguna otra sugerencia... Saludos!

---

### Post by pablo.s on 2009-03-25
Hola: la solución para el problema que te aqueja es la mas simple. 

Guardá una copia de sources.list con el nombre sources.list.old en la misma carpeta. 
Siendo superusuario en un editor de texto pegá y copia esto:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports restricted main multiverse universe





Y al archivo lo guardás como sources.list en /etc/apt/   y a continuación en una terminal escribís 
sudo apt-get update. 

Después que se realice este pequeño proceso agregás la llave gpg de medibuntu:
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -


y le agregás esta linea a /etc/apt/sources.list


deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
 
 

Una vez que tengas esto, muy cautelosamente vas agregando los repositorios 
externos que necesites.

Saludos.

---

### Post by guillermon on 2009-03-30
> **pablo.s said:**
> Hola: la solución para el problema que te aqueja es la mas simple. 

Una vez que tengas esto, muy cautelosamente vas agregando los repositorios 
externos que necesites.

Saludos.

Pablo, he seguido tu consejo y listo! solucionado. Muchas gracias. Se actualizó el sistema, no da error. Gracias de nuevo.
Guillermo

---

