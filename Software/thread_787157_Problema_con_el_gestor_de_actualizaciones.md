---
title: "Problema con el gestor de actualizaciones"
date: 2008-05-08
forum: Software
---

### Post by silencio65 on 2008-05-08
Hola, gente.

Antes que nada pido disculpas de antemano si estoy preguntando una tontería, ya que mi experiencia en Linux es bastante limitada, y mi desconocimiento en lo que tiene que ver con repositorios y otras yerbas es casi absoluto. 
Lo cierto es que estuve intentando encontrar una solución a este problema en distintos foros, Howtos y demás y no encontré nada que me fuera de ayuda, así que me decidí a escribir.

El hecho es que después de actualizar a Hardy me aparece el siguiente mensaje de error en el gestor de actualizaciones:


```
W: Ha ocurrido un error durante la verificación de la firma. El repositorio no se ha actualizado y se usarán los archivos de índice anteriores. Error de GPG: http://security.ubuntu.com hardy-security Release Las siguientes firms fueron inválidas: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Ha ocurrido un error durante la verificación de la firma. El repositorio no se ha actualizado y se usarán los archivos de índice anteriores. Error de GPG: http://ar.archive.ubuntu.com hardy-updates Release Las siguientes firms fueron inválidas: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/hardy-security/Release  

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
```

Les adjunto mi archivo sources.list, por si les da alguna pista (de todos modos, no creo haberle hecho ninguna modificación):

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ar.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ar.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ar.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ar.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ar.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
```

La verdad es que estoy bastante desconcertado con esto, así que si alguien puede darme alguna pista, estaré profundamente agradecido.

---

### Post by clasificado on 2008-05-08
No tengo idea como llegaste a eso, pero vamos a tratar de sacarte de ahi.

**En una terminal, ejecutate esto**
```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
apt-key add ~/.gnupg/pubring.gpg
```

Bueno, el problema parece de firmas digitales. Con la primera linea te descargas la firma digital para los repositorios (de nuevo, supuestamente viene con ubuntu), con la segunda linea la agregás a las firmas de confianza.

osea: no tiene nada que ver con el sources.list. venias bien.

> **silencio65 said:**
> Antes que nada pido disculpas de antemano si estoy preguntando una tontería

Una tontería hubiera sido no preguntar :KS

Mucha suerte

clasificado

---

### Post by silencio65 on 2008-05-09
Muchísias gracias por la respuesta.

De todas maneras el problema persiste.

> **En una terminal, ejecutate esto**
```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
apt-key add ~/.gnupg/pubring.gpg
```

Esto es lo que me devolvieron los 2 comandos:

```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5

gpg: solicitando clave 437D05B5 de hkp servidor wwwkeys.eu.pgp.net
gpg: clave 437D05B5: clave pública "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" importada
gpg: no se encuentran claves totalmente fiables
gpg: Cantidad total procesada: 1
gpg:               importadas: 1
```

```
apt-key add ~/.gnupg/pubring.gpg

gpg: error escribiendo anillo `/etc/apt/trusted.gpg': error de escritura
gpg: no se puede abrir `/etc/apt/secring.gpg'
gpg: Error leyendo `/home/nando/.gnupg/pubring.gpg': error de escritura
gpg: import from `/home/nando/.gnupg/pubring.gpg' failed: error de escritura
```

Al aparecerme este mensaje, supuse que tal vez tenía que ingresarlo con *sudo* (¿Será así? ¿Me mandé una macana?) La cuestión es que tipeando "sudo apt-key add ~/.gnupg/pubring.gpg" la terminal me contestó "OK", así que supuse que había hecho bien. Pero cuando vuelvo al gestor de actualizaciones y le doy al botón "Comprobar" me sigue apareciendo el mismo mensaje que antes.

Intenté también tipear via terminal "sudo apt-get update" que, por lo que entiendo, hace lo mismo que el botón comprobar  y, si bien el resultado es el mismo mensaje, me da in poco más de información (que, para variar, no sé cómo decodificar). La adjunto:

```
Obj http://ar.archive.ubuntu.com hardy Release.gpg
Obj http://ar.archive.ubuntu.com hardy/main Translation-es                     
Obj http://ar.archive.ubuntu.com hardy/restricted Translation-es               
Obj http://ar.archive.ubuntu.com hardy/universe Translation-es                 
Obj http://ar.archive.ubuntu.com hardy/multiverse Translation-es               
Des:1 http://ar.archive.ubuntu.com hardy-updates Release.gpg [191B]            
Obj http://archive.ubuntu.com hardy Release.gpg                                
Des:2 http://security.ubuntu.com hardy-security Release.gpg [191B]             
Obj http://archive.ubuntu.com hardy Release                                    
Obj http://archive.ubuntu.com hardy/main Sources                               
Ign http://security.ubuntu.com hardy-security/main Translation-es              
Obj http://archive.ubuntu.com hardy/restricted Sources                         
Ign http://security.ubuntu.com hardy-security/restricted Translation-es        
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://security.ubuntu.com hardy-security/universe Translation-es
Ign http://ppa.launchpad.net hardy/main Translation-es 
Des:3 http://ppa.launchpad.net hardy Release [27,6kB]  
Ign http://security.ubuntu.com hardy-security/multiverse Translation-es
Des:4 http://security.ubuntu.com hardy-security Release [37,0kB]
Err http://security.ubuntu.com hardy-security Release                         
  
Ign http://ppa.launchpad.net hardy/main Packages                              
Ign http://ppa.launchpad.net hardy/main Sources        
Obj http://ppa.launchpad.net hardy/main Packages
Obj http://ppa.launchpad.net hardy/main Sources
Ign http://ar.archive.ubuntu.com hardy-updates/main Translation-es             
Ign http://ar.archive.ubuntu.com hardy-updates/restricted Translation-es       
Ign http://ar.archive.ubuntu.com hardy-updates/universe Translation-es         
Ign http://ar.archive.ubuntu.com hardy-updates/multiverse Translation-es       
Obj http://ar.archive.ubuntu.com hardy Release                                 
Des:5 http://ar.archive.ubuntu.com hardy-updates Release [51,2kB]              
Err http://ar.archive.ubuntu.com hardy-updates Release                         
  
Obj http://ar.archive.ubuntu.com hardy/main Packages                           
Obj http://ar.archive.ubuntu.com hardy/restricted Packages                     
Obj http://ar.archive.ubuntu.com hardy/restricted Sources                      
Obj http://ar.archive.ubuntu.com hardy/main Sources                            
Obj http://ar.archive.ubuntu.com hardy/multiverse Sources                      
Obj http://ar.archive.ubuntu.com hardy/universe Sources                        
Obj http://ar.archive.ubuntu.com hardy/universe Packages                       
Obj http://ar.archive.ubuntu.com hardy/multiverse Packages                     
Descargados 385B en 8s (44B/s)                                                 
Leyendo lista de paquetes... Hecho
W: Ha ocurrido un error durante la verificación de la firma. El repositorio no se ha actualizado y se usarán los archivos de índice anteriores. Error de GPG: http://security.ubuntu.com hardy-security Release Las siguientes firms fueron inválidas: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Ha ocurrido un error durante la verificación de la firma. El repositorio no se ha actualizado y se usarán los archivos de índice anteriores. Error de GPG: http://ar.archive.ubuntu.com hardy-updates Release Las siguientes firms fueron inválidas: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/hardy-security/Release  

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas
```

Saludos, y gracias de nuevo

---

### Post by silencio65 on 2008-05-09
Hola. Yo de nuevo.

La cuestión evolucionó de una manera de lo más rara a lo largo del día.
A la mañana, el mensaje de error era el mismo de ayer. 
A la tarde, aparentemente había desaparecido una parte del problema; el mensaje ahora era el siguiente:

```
W: Ha ocurrido un error durante la verificación de la firma. El repositorio no se ha actualizado y se usarán los archivos de índice anteriores. Error de GPG: http://ar.archive.ubuntu.com hardy-updates Release Las siguientes firms fueron inválidas: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
```

Como verán, desapareció toda la parte referida a [http://security.ubuntu.com](http://security.ubuntu.com).

Siendo las 20:50 volví a probar y ya no aparecía ningún mensaje, y ahora funciona todo perfecto.

Es decir que, aparentemente, la solución dada por clasificado funcionó, pero se tomó casi un día para hacerlo.

Lo que me queda ahora es la curiosidad: ¿por qué habrá pasado esto? ¿Alguien tiene idea?

Saludos
silencio65

---

### Post by Hei Ku on 2008-05-10
Lo que paso es que se mezclaron dos cosas distintas. El primero no fue un error, sino que cambiaron la firma digital que usan para firmar los paquetes del repositorio. En ese caso, al menos con Kubuntu, la solucion mas simple es actualizar el indice de los repositorios desde Adept (o Synaptic, supongo) que actualizan automaticamente la firma y ya esta.
El segundo error es solo un problema de conexion.

---

### Post by devilsoulblack on 2008-05-10
Yo estoy obteniendo el mismo error, 

```
Fetched 3463B in 18s (187B/s)                                                                                                              
Reading package lists... Done
W: GPG error: http://us.archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
```


source.lst:

```
#deb http://download.skype.com/linux/repos/debian/ stable non-free
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
#deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
#deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe

deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main



## Repositorio Medibuntu - Ubuntu 8.04 LTS "Hardy Heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
#deb http://packages.medibuntu.org/ hardy free non-free
#deb-src http://packages.medibuntu.org/ hardy free non-free
```


alguna idea de como solucionarlo ?

---

### Post by Hei Ku on 2008-05-10
la mas facil es abrir adept o synaptic y actualizar. eso te actualiza tambien la llave gpg.

podes probar:

sudo apt-key update

sino, bajar la key y sudo apt-key add <nombre de archivo> pero no recuerdo de donde se bajan esas claves.

para clarificar, todos los repos oficiales se firman con una clave publica GPG. Periodicamente la actualizan y surgen estos errores. Nada grave, y es por nuestra seguridad. La firma garantiza que realmente son los paquetes que tienen que ser.

---

### Post by devilsoulblack on 2008-05-10
Hei Ku, tambien habia hecho eso y sigue el mismo GPG error error :(

---

### Post by Hei Ku on 2008-05-11
proba este comando 

```

wget -q http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg -O- | sudo apt-key add - && sudo apt-get update

```

---

### Post by lushnok on 2008-05-11
Buenas y santas estimados todos.
Ayer instalé e Hardy Heron, mi primer acercamiento a Ubuntu, Linux y demás... 
ando metiendo garfios y mirando todo hace algunas semanas.
Ahora, mientrs quería instalar unos codecs para escuchar musiquinha me aparece el siguiente error (va en "pantallazo")

Si alguien pudiera darme una mano... espero no haber **** nada.

---

### Post by WanderingKnight on 2008-05-11
Como dice el mensaje, tenes que correr el siguiente comando en la consola:

```
sudo dpkg --configure -a
```

Eso pasa cuando interrumpis al administrador de paquetes.

Habria que pedir que incluyan una traduccion de ese mensaje, veo mucha gente nueva con este mismo problema.

---

### Post by lushnok on 2008-05-11
Excelente! muchas gracias!
Sigo con algunos problemas de codecs, pero busco el thread para pregunar bien :P

Salud!

---

### Post by WanderingKnight on 2008-05-12
Teoricamente, si instalas ubuntu-restricted-extras deberias tener casi todo. Tambien esta el paquete win32codecs en [medibuntu](www.medibuntu.org) para decoding de video y algunos de audio mas raros.

---

### Post by faktorqm on 2008-05-12
Completo acá la información de WK, en esta pagina [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) hay varios metodos para instalar los paquetes, yo soy mas desconfiado y no soy amigo de los repositorios externos, asi que te adjunto aca el metodo "a mano".

```
wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb
```

```
sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb
```

Salu2!!

---

### Post by gera799 on 2008-06-07
Probá esto:

apt-get update -o Acquire::http::No-Cache=True

A mí me funcionó. Saludos

---

### Post by lezich on 2008-06-17
gracias, es la solucion al problema

***[SIZE="5"]sudo apt-get update -o Acquire::http::No-Cache=True[/SIZE]***

---

### Post by infoholico on 2012-08-28
Ninguna de las soluciones publicadas aquí me funcionó, pero en Launchpad conseguí el error y una solución que sí me funcionó.


```
$ cd /var/lib/apt
$ sudo mv lists lists.old
$ sudo mkdir -p lists/partial
$ sudo apt-get update
```

---

### Post by DioscuroDeviant on 2012-08-30
> **infoholico said:**
> Ninguna de las soluciones publicadas aquí me funcionó, pero en Launchpad conseguí el error y una solución que sí me funcionó.


```
$ cd /var/lib/apt
$ sudo mv lists lists.old
$ sudo mkdir -p lists/partial
$ sudo apt-get update
```



ESTA!!!!!!!!! Es la solución...!!!!!!! Muchas gracias....:KS:popcorn:

---

