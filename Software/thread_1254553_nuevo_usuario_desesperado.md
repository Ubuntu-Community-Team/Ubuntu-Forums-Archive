---
title: "nuevo usuario desesperado"
date: 2009-08-31
forum: Software
---

### Post by sebamista on 2009-08-31
hace mas de una semana que estoy intentando usar el synaptic, pero me salta el sig error:

             [COLOR=Red]Incapaz de obtener un bloqueo exclusivo[/COLOR]
[CENTER]
[COLOR=Red]        Esto normalmente significa que ya se está ejecutando otra aplicación de gestión de paquetes (como apt-get o aptitude). Por favor, cierre esa aplicación primero.[/COLOR]
[/CENTER]

inicio un terminal y cargo  

sudo dpkg --configure -a

y ahi empieza lo lindo esta todo el dia con lo mismo, se ve que esta buscando algo pero no lo encuentra:

[COLOR=Red]--13:55:45--  [ftp://ftp.3drealms.com/share/1rott13.zip](ftp://ftp.3drealms.com/share/1rott13.zip)
  (intento:13) => `/usr/share/games/rott/1rott13.zip'
Conectando a ftp.3drealms.com|74.208.171.241|:21... conectado.
Identificándose como anonymous ... ¡Conectado!
==> SYST ... hecho.    ==> PWD ... hecho.
==> TYPE I ... hecho.  ==> CWD /share ... hecho.
==> PASV ... no se pudo conectar a 74.208.171.241 puerto 49951: Expiró el tiempo de conexión
Reintentando.

--13:59:07--  [ftp://ftp.3drealms.com/share/1rott13.zip](ftp://ftp.3drealms.com/share/1rott13.zip)
  (intento:14) => `/usr/share/games/rott/1rott13.zip'
Conectando a ftp.3drealms.com|74.208.171.241|:21... conectado.
Identificándose como anonymous ... ¡Conectado!
==> SYST ... hecho.    ==> PWD ... hecho.
==> TYPE I ... hecho.  ==> CWD /share ... hecho.
==> PASV ... 
[/COLOR]
lo espere hasta el intento 40 y nunca pasa de PASV...
ya probe de toda clase de comandos, la apague, reinicie y ya no se que cosas mas le hice y no consigo finalizar este error....


[SIZE=6]help!!!!!!!![/SIZE]

---

### Post by Hei Ku on 2009-08-31
Que intentaste instalar?

Postea por favor tu archivo /etc/apt/sources.list

---

### Post by sebamista on 2009-08-31
primero quise instalar un juego que estaba en los paquetes originales del ubuntu, no recuerdo cual, pero despues me lo hace con cualqier cosa que quiera instalar por synaptic
explicame como leo ese archivo
:confused:

---

### Post by josecuervo86 on 2009-08-31
En una terminal escribi:

```
sudo gedit /etc/apt/sources.list
```

Lo que te aparezca agarra y pegalo aca asi lo vemos

---

### Post by sebamista on 2009-08-31
#deb cdrom:[Ubuntu 8.04.3 _Hardy Heron_ - Release i386 (20090713.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by Hei Ku on 2009-08-31
Recordás el comando que pusiste para instalar ese juego?

---

### Post by sebamista on 2009-08-31
> **Hei Ku said:**
> Recordás el comando que pusiste para instalar ese juego?

mire los paquetes que estaban en el synaptic, y en la parte de entretenimientos seleccione una casilla, luego salto una ventana diciendo que dicho programa tenia asociados, le do ok y empeso a busca y buscar, y no paro mas.

ahora hace otra cosa, a los 20 intentos corta, y me tira un error. pero me deja libre el synaptic. pero cualquier cosa que quiera instalar me sale lo mismo

---

### Post by Hei Ku on 2009-08-31
Recordás cuál fue el que seleccionaste para instalar? Podes entrar a Synaptic y seleccionar para removerlo?

---

### Post by sebamista on 2009-08-31
> **Hei Ku said:**
> Recordás cuál fue el que seleccionaste para instalar? Podes entrar a Synaptic y seleccionar para removerlo?

no no me deja entra me dice que hay otra aplicacion ejecutandose:

Ya hay otro synaptic en ejecución

Hay otro synaptic funcionando en modo no interactivo, espere hasta que termine.

---

### Post by Hei Ku on 2009-08-31
Pone en una terminal:

sudo pkill synaptic*

Y volve a probar.

---

### Post by sebamista on 2009-08-31
> **Hei Ku said:**
> Pone en una terminal:

sudo pkill synaptic*

Y volve a probar.

me cerro la ventana pero cuando abro el synaptic salta el siguiente error 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

y volvemos a lo mismo...

---

### Post by Hei Ku on 2009-08-31
Cual es el nombre del paquete que instalaste?

Pone:

sudo dpkg -r <nombre_del_paquete>

---

### Post by sebamista on 2009-08-31
no tengo ni idea cual sea el nobre del paquete. y no se como sacarlo, ya que no me da ninguna opcion al abrir el synaptic

---

### Post by josecuervo86 on 2009-08-31
Por casualidad intentaste instalar el rise of the triad de 3D realms? porque ese es el juego que aparece en el mensaje de error del primer post. Si es ese, el paquete se llama rott

---

### Post by sebamista on 2009-08-31
> **josecuervo86 said:**
> Por casualidad intentaste instalar el rise of the triad de 3D realms? porque ese es el juego que aparece en el mensaje de error del primer post. Si es ese, el paquete se llama rott

no recuerdo bien, pero creo que si...
igualmente sale el siguiente error:

usuario@usuario-desktop:~$ sudo dpkg -r rott
[sudo] password for usuario: 
dpkg: el área de la base de datos de estado está bloqueada por otro proceso
usuario@usuario-desktop:~$

---

### Post by Hei Ku on 2009-08-31
Cerra el synaptic antes de poner ese comando.

---

### Post by sebamista on 2009-09-01
[quote=Hei Ku;7878898]Cerra el synaptic antes de poner ese comando.[/quot

no me deja hacerlo

esta una y otra ves intentando instalar y no me deja cerrarlo

---

### Post by sebamista on 2009-09-01
solucionado:

en terminal use comando :

$ sudo pkill synaptic*

una vez cerrado la descarga, use en terminal:

$ sudo dpkg -r rott

salto lo sig:

usuario@usuario-desktop:~$ sudo pkill synaptic*
[sudo] password for usuario: 
usuario@usuario-desktop:~$ sudo dpkg -r rott
(Leyendo la base de datos ...  
102800 ficheros y directorios instalados actualmente.)
Desinstalando rott ...

y luego busque el paquete rott en el synaptic y lo elimine..... santo remedio


gracias

---

