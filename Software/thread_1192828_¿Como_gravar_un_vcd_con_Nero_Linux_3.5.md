---
title: "¿Como gravar un vcd con Nero Linux 3.5?"
date: 2009-06-20
forum: Software
---

### Post by andy_91 on 2009-06-20
Bueno el titulo lo dice todo, ¿alguno tiene una idea?

---

### Post by rodolfojavier1982 on 2009-06-20
Es indispensable que utilices el Nero?
Yo utilizo K3b para grabaciones de Cds/Dvds, lo podes bajar via Aplicaciones->Añadir y quitar... (Deberia ser o quitar...)
Espero que te sirva.

---

### Post by gmunioz on 2009-06-20
Hola and...:

1- Primero debes crear la imagen iso, para eso entr otros esta devede.

2- Luego grabas la iso con lo que mas te agrade, brasero, k3d, nero.

---

### Post by NickCis on 2009-06-20
Yo estoy nececitando hacer un Dvd (con menu y todo eso), toy usando el Devede, es normal que tarde tanto?, me acuerdo qeu en win tardaba mucho pero este va como 3hs y ni va por la mitad :S...

Saludos.

---

### Post by andy_91 on 2009-06-20
es qque el brasero ni el devede me funcionan, no hay otro programa escrito en gtk que no utlice mencode :confused:

---

### Post by juancarlospaco on 2009-06-20
Grabar, es click derecho grabar.
Ahora Codificar el video en un formato es otra cosa que no es grabar.

---

### Post by luks911 on 2009-06-20
> **andy_91 said:**
> es qque el brasero ni el devede me funcionan, no hay otro programa escrito en gtk que no utlice mencode :confused:

¿Qué es lo que no funciona? ¿Qué es exactamente lo que querés hacer? ¿Qué pasos seguís para hacerlo? Contá un poco más así tratamos de buscarle la vuelta.

---

### Post by pablo.s on 2009-06-21
Acá está el [manual]("http://ftp6.nero.com/user_guides/nero9/burningrom/NeroBurningRom_Esp.pdf") de
Nero Burning Rom para
Windows. El de Linux
es muy similar.

---

### Post by andy_91 on 2009-06-21
lo que trate es de gravar videos con la extencion .mpg en un vcd para mi reproductor de DVD casero (el que se conecta al tele)

la cosa es que no puedo instalar devede por que me da un error con el paquete mencoder, y el brasero me dice que no puede gravar con los drivers existentes

> **pablo.s said:**
> Acá está el [manual]("http://ftp6.nero.com/user_guides/nero9/burningrom/NeroBurningRom_Esp.pdf") de
Nero Burning Rom para
Windows. El de Linux
es muy similar.

gracias por el manual lo voy a leer a ver si saco algo

---

### Post by andy_91 on 2009-06-21
leí el manual, es evidente que la opción vcd/svcd no esta en mi nero.
si esta la opción miniDV

---

### Post by luks911 on 2009-06-21
> **andy_91 said:**
> lo que trate es de gravar videos con la extencion .mpg en un vcd para mi reproductor de DVD casero (el que se conecta al tele)

la cosa es que no puedo instalar devede por que me da un error con el paquete mencoder, y el brasero me dice que no puede gravar con los drivers existentes



gracias por el manual lo voy a leer a ver si saco algo

Más preguntas :-P ¿Qué error te da al tratar de instalar devede? ¿Tenés los repositorios de Medibuntu?

---

### Post by KaKuS on 2009-06-22
Te recomendaría que desde la consola intentes instalar los paquetes que te dan error y que copies lo que te dice así te ayudamos. Quizás el problema está antes del paquete que graBa lo que quiere decir que instales el paquete que instales ninguno va a graBar.


Saludos

---

### Post by mama21mama on 2009-06-22
Usen el programa devede, ademas de hacer dvd de video tambien hace vcd.

Luego con nero... ptm nero no tiene para vcd. ¬¬

Bueno en este caso seria crear con devede una iso del VCD y luego la quemas con nero :D

Saludos

---

### Post by andy_91 on 2009-06-23
```
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.

Como sólo solicito una única operación, es extremadamente posible que el
paquete simplemente no sea instalable y debería de rellenar un informe de
error contra ese paquete.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  mencoder: Depende: liblame0 (>= 3.97) pero no va a instalarse
E: Paquetes rotos

```
eso me dice la terminal

---

### Post by gmunioz on 2009-06-23
Hola Andy:

Por favor: copia y pega el contenido de tu archivo:

```
/etc/apt/sources.list
```

---

### Post by andy_91 on 2009-06-23
```
## -----------------------
## LINUX MINT REPOSITORIES
## -----------------------

## +++ Linux Mint 5 Elyssa (stable) +++
deb http://packages.linuxmint.com/ elyssa main upstream import 

## +++ Backports (not as stable) +++
## deb http://packages.linuxmint.com elyssa backport

## +++ Community (not as stable) +++
## deb http://packages.linuxmint.com elyssa community

## +++ Romeo (unstable) +++
## deb http://packages.linuxmint.com elyssa romeo

## +++ Source Repositories +++
## deb-src http://packages.linuxmint.com elyssa main upstream import
## deb-src http://packages.linuxmint.com elyssa community
## deb-src http://packages.linuxmint.com elyssa backport
## deb-src http://packages.linuxmint.com elyssa romeo

## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Ubuntu 8.04 Hardy (stable) +++
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse 
deb http://security.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse 

## +++ Backports & Proposed (not as stable) +++
## deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
## deb http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse

## +++ Source Repositories +++
## deb-src http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
## deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse

## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical (stable) +++
deb http://archive.canonical.com/ubuntu/ hardy partner 

## +++ Medibuntu (stable) +++
deb http://packages.medibuntu.org/ hardy free non-free  
deb http://ppa.launchpad.net/jerome-guelfucci/ppa/ubuntu/ hardy main  

deb http://ppa.launchpad.net/exaile-devel/ubuntu/ hardy main
```

es ubuntu con los repos de mint

---

### Post by gmunioz on 2009-06-24
Hola:

¿Qué es lo que estas usando?

Según tus datos usas Xubuntu Intrepid y en tus repositorios

Intrepid no existe.

Dado que mencionas a Linux Mint Elysa y como este, esta basado

en Hardy y a la vez, tienes repositorios de Hardy, parecería

que en definitiva estas usando Hardy.

Si esto fuera cierto, deja los repositorios asi:

```
## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Ubuntu 8.04 Hardy (stable) +++
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse 
deb http://security.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse 

## +++ Backports & Proposed (not as stable) +++
deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse

## +++ Source Repositories +++
deb-src http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse

## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical (stable) +++
deb http://archive.canonical.com/ubuntu/ hardy partner 

## +++ Medibuntu (stable) +++
deb http://packages.medibuntu.org/ hardy free non-free  
deb-src http://packages.medibuntu.org/ hardy free non-free

deb http://ppa.launchpad.net/jerome-guelfucci/ppa/ubuntu/ hardy main  
deb http://ppa.launchpad.net/exaile-devel/ubuntu/ hardy main
```
Luego ejecuta en consola:

sudo apt-get update
sudo apt-get install devede

Una vez instalado devede, desactiva lo backports y proposed.

---

### Post by andy_91 on 2009-06-24
es Xubuntu intrepid con los repositorios de mint

---

### Post by gmunioz on 2009-06-24
Hola Andy....:

Pues tienes un verdadero pandemoniun de repositorios y es  

verdaderamente extraño que tu sistema instale algo correctamente

con ese listado en tu sources.list.

Cambia tus repositorios a solo:


```
deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse 
deb http://security.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu intrepid-updates main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ intrepid partner 
deb http://packages.medibuntu.org/ intrepid free non-free  
deb-src http://packages.medibuntu.org/ intrepid free non-free


```

Y si piensas agregar los de mint, son los de felicia, no los de elyssa

---

### Post by andy_91 on 2009-06-25
valla ahora si se instalo el devede, la razon de usar elyssa es el nucleo linux ya que la vercion que trae xubuntu por defecto me dan problemas algunos dispositivos usb

---

### Post by andy_91 on 2009-06-25
Gracias por todo =D>

---

