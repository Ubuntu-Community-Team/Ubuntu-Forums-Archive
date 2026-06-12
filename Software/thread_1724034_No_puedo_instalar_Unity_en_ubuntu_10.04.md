---
title: "No puedo instalar Unity en ubuntu 10.04"
date: 2011-04-07
forum: Software
---

### Post by guillermon on 2011-04-07
Hola, he intentado mucho instalar la configuración Unity en Ubuntu 10.04. Me ha parecido muy interesante el ahorro de espacio que significaría en mi notebook. Pero bue, sigo lo que dicen todos los foros habidos y por haber, y nada... por ejemplo pongo```
guille@guille-laptop:~$ sudo add-apt-repository ppa:canonical-dx-team/une
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv B830F373C1A4AB09059A12F8AA2BB78B7AE26941
gpg: solicitando clave 7AE26941 de hkp servidor keyserver.ubuntu.com
gpg: clave 7AE26941: «Launchpad Private PPA for Canonical Desktop Experience Team» sin cambios
gpg: Cantidad total procesada: 1
gpg:              sin cambios: 1

``` Luego: sudo apt-get update
luego```
guille@guille-laptop:~$ sudo aptitude install unity
[sudo] password for guille: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho
No se pudo encontrar el paquete «unity». Sin embargo,
«unity» aparece en el nombre de los siguientes paquetes:
  edgy-community-wallpapers community-themes banshee-community-extensions 
No se pudo encontrar el paquete «unity». Sin embargo,
«unity» aparece en el nombre de los siguientes paquetes:
  edgy-community-wallpapers community-themes banshee-community-extensions 
No se instalará, actualizará o eliminará ningún paquete.
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B de archivos. Después de desempaquetar se usarán 0B.
Escribiendo información de estado extendido... Hecho
Leyendo lista de paquetes... Hecho                   
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho

``` No importa que ponga aptitude, apt-get, que lo intente en synaptic, etc... ¿alguien me ayuda?
Por otra parte, lo que sí he hecho es instalar finalmente la versión Remix, que creo es un paso intermedio. La estoy probando y me gusta... pero prefiero probar unity. Espero ayuda. Saludos
Guillermo

---

### Post by juancarlospaco on 2011-04-07
[B]sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily && sudo apt-get update
sudo apt-get install unity-qt-default-settings[/B]

---

### Post by pabloatilio on 2011-04-07
sudo add-apt-repository ppa:canonical-dx-team/une
sudo apt-get update --> FALTA el update
sudo apt-get install unity

Copiados tal cual del terminal de mi equipo y funcionó todo perfecto.
Parece que hiciste lo mismo pero yo lo hice en U10.10 y vos en U10.04.
Probablemente no te sirva entonces ese repositorio o no hiciste el update.
Casi seguro es la falta de update si no lo hiciste.
Saludos 

Pablo

---

### Post by guillermon on 2011-04-07
> **juancarlospaco said:**
> [B]sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily && sudo apt-get update
sudo apt-get install unity-qt-default-settings[/B]
Juan Carlos, he hecho lo que dices, y cuando hago el update, por ahí he leido esto:```
W: Imposible obtener http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found
``` Luego me dice que no ha encontrado ese paquete...
¿qué será?

---

### Post by guillermon on 2011-04-07
> **pabloatilio said:**
> sudo add-apt-repository ppa:canonical-dx-team/une
sudo apt-get update --> FALTA el update
sudo aptitude install unity
 Hola Pablo, he hecho el update, seguro... Gracias igual!

---

### Post by pabloatilio on 2011-04-07
> **guillermon said:**
> Juan Carlos, he hecho lo que dices, y cuando hago el update, por ahí he leido esto:```
W: Imposible obtener http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found
``` Luego me dice que no ha encontrado ese paquete...
¿qué será?


proba de instalar el primero si hiciste el update, no el unity-2d
osea solamente

sudo apt-get update
sudo apt-get install unity

Si lo que queres es instalar el unity2-d, el repositorio es distinto

sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily  (lo que te dijo juan carlos)

y si no te está leyendo ese repositorio no vas a poder instalar esa versión, sin embargo
hoy mismo yo lo usé sin problemas, raro.

---

### Post by pabloatilio on 2011-04-07
> **guillermon said:**
> Hola Pablo, he hecho el update, seguro... Gracias igual!


Perdón !! no lo había visto, saludos

---

### Post by juancarlospaco on 2011-04-07
Es para **Maverick+**

---

### Post by guillermon on 2011-04-07
> **juancarlospaco said:**
> Es para **Maverick+**
Ouuch! Me confié de enlaces equivocados! Pido disculpas... Gracias!
(y que pena)

---

