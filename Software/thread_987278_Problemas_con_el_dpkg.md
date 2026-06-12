---
title: "Problemas con el dpkg"
date: 2008-11-19
forum: Software
---

### Post by DrKenobi on 2008-11-19
Se que esto lo deben haber posteado mil veces, pero todas las "soluciones" que encontre no me sirvieron!

La cosa es que se me colgo la PC y despues de eso no puedo instalar nada. El error que me tira es:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

Como dice el cartelito fui a un terminal y puse:

> sudo dpkg --configure -a

No me soluciono nada. Despues en un foro encontre que ademas de escribir eso en el terminal tenia que poner: 

> sudo apt-get update

Tampoco me soluciono nada. En fin.....como lo instale con el Wubi hace solo tres dias tengo pensado borrar todo y arrancar de nuevo. Pero me gustaria no hacerlo je

Gracias

---

### Post by sajnox on 2008-11-19
Despues de correr el sudo dpkg --configure -a te respondio algo, que error te tira cuando corres el sudo apt-get update, por que queres hacer un update?? Agregaste algun repositorio?? Queres instalar algo??

---

### Post by DrKenobi on 2008-11-19
Lo que quiero hacer es instalar el kPresenter, y ademas instalar unos updates que me aparecieron.

Despues de poner "sudo dpkg --configure -a" en un Terminal, me aparece lo siguiente:

> dpkg: parse error, in file `/var/lib/dpkg/updates/0078' near line 1:
 newline in field name `#padding'

Esto no me soluciona nada. Entonces, hice lo que encontre en un post del foro, de poner en un Terminal "sudo apt-get update". Esto me tiro el siguiente resultado:

> Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release [65.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages [1256kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages [8408B]        
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources [505kB]               
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources [3113B]         
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages [4542kB]         
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources [1981kB]                                         
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages [199kB]                                       
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources [95.8kB]                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources                                          
Fetched 8657kB in 1min31s (94.7kB/s)                                                                          
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Esto tampoco me soluciono nada. Cuando intento usar "System --> Add/Remove..." o "System ---> Synaptic Packager Manager" o el "System --> Update Manager" me tira siempre el mismo error:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report. 

Gracias

---

### Post by Hei Ku on 2008-11-19
Postea el contenido del archivo /etc/apt/sources.list

Probablemente sea un error que tuvo en la actualizacion por conexion lenta o algo asi.

Lo mas facil es hacer un update con un sources.list vacio y despues volver a poner el que tenias. Pero primero postea el contenido del archivo, a ver que tiene.

---

### Post by DrKenobi on 2008-11-19
Aca posteo el contenido del archivo /etc/apt/sources.list

> #deb cdrom:[Xubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030.3)]/ intrepid main multiverse restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse


Gracias

---

### Post by Hei Ku on 2008-11-19
Parece estar bien.

Hace lo siguiente:

```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
touch /etc/apt/sources.list
sudo apt-get update
sudo mv /etc/apt/sources.list.bak /etc/apt/sources.list
sudo apt-get update

```

Con eso debería salir andando. Postea si te sale algun error.

---

### Post by DrKenobi on 2008-11-20
Hola, Hei Ku:

Hice lo que me dijiste y cada vez que ponia "sudo apt-get update" me tiro el error de siempre:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report. 

No te hagas problema, voy a borrar todo y volver a instalarlo con el Wubi, es muy poco el tiempo que se pierde, y hace solo 4 dias que tengo el Xubuntu instalado. La proxima voy a tratar de tener mas cuidado para que no se me vuelva a dañar el archivo.

Gracias.

---

### Post by aymAtha on 2008-11-20
No eres el unico con ese problema estoy volviendo a instalar nuevamente pero queria ver si instalando con el CD pasa lo mismo??

---

### Post by fmsismo on 2008-11-22
Hola como va?

Te acordas que fue lo ultimo que instalaste antes de que te tire este problema?

podas pasarnos que te devuelve 

cat /var/lib/dpkg/updates/0078

Saludos

---

### Post by DrKenobi on 2008-11-22
aymAtha: yo lo instale siempre desde el cd, y el problema aparecio

fmsismo: ya lo desinstale..... cuando estaba intentando instalar el kPresenter se colgo la PC y ahi se daño el archivo

---

### Post by fmsismo on 2008-11-22
No estoy seguro, pero provaría moviendo el archivo 0078 a otro lado.

hace

sudo mv /var/lib/dpkg/updates/0078 /var/tmp/

sudo dpkg --configure -a 

sudo apt-get update
sudo apt-get upgrade



Si anda joya, sino volve para atrás todo.

sudo mv /var/tmp/0078 /var/lib/dpkg/updates/0078

Saludos

---

