---
title: "disculpen la ignorancia.. pero no me quedo otra que preguntar..."
date: 2009-05-01
forum: Software
---

### Post by infernus92 on 2009-05-01
bueno... vengo usando ubuntu desde diciembre y la verdad me gusto mucho... pero queria probar otro entorno de escritorio ademas del GNOME que viene por defecto sin tener que instalar kubuntu, xubuntu, etc.
quiro mantener mi entorno GNOME pero que desde el inicio de sesion me deje elegir con cual quiero iniciar (se que se puede pero no se como)
pense en probar KDE y xfce y quizas fluxbox
si alguno me puede ayudar muchas gracias

Saludos

---

### Post by clasificado on 2009-05-01
son todos paquetes :)

```

sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get install mithbuntu-desktop

```

otros, como entlightment, están como paquetes sueltos y no desktop, ya que no son una distro oficial

PD: puden ensuciarte un poco la instalación, pero también se pueden remover

clasificado

---

### Post by infernus92 on 2009-05-01
gracias... ya estoy descargando KDE

Saludos

---

### Post by guillermolisi on 2009-05-01
> **infernus92 said:**
> gracias... ya estoy descargando KDE

Saludos
En realidad lo que se ensucia no es la instalacion sino los menues que medio se entremezclan y repiten.

Ojo que escritorios graficos no es lo mismo que windows managers. No ofrecen la misma funcionalidad y facilidad de uso. Gnome, KDE, LXDE, XFCE (y algun otro que me estare olvidando) son escritorios graficos. Flux y similares son windows managers (mucho mas livianos, por cierto, pero mas "duros" para el usuario).

---

### Post by z37a on 2009-05-01
> **guillermolisi said:**
> En realidad lo que se ensucia no es la instalacion sino los menues que medio se entremezclan y repiten.
...


Igualmente eso es configurable, podes hacer que el usplash(Pantalla de booteo del kernel) diga ubuntu, kubuntu, edubuntu o lo que quieras teniendo instalado el paquete que quieras también, al igual que la pantalla de entrada también se pueden configurar fácilmente. Si bien no recuerdo donde era esactamente se que estaban dentro del menú de configuraciones(asi que no necesitas tampoco usar bash para ello).

---

### Post by infernus92 on 2009-05-01
> **z37a said:**
> Igualmente eso es configurable, podes hacer que el usplash(Pantalla de booteo del kernel) diga ubuntu, kubuntu, edubuntu o lo que quieras teniendo instalado el paquete que quieras también

a que paquete te referis??
cuando baje el entorno KDE ayer se cambio el usplash y dice Kubuntu... y la verdad preferiria que diga ubuntu... si me podes decir muchas gracias...

Saludos

---

### Post by staar on 2009-05-01
creo que el (los) nombre era (k,x,myth)ubuntu-usplash-theme, con el startup-manager podés seleccionar el theme del usplash, o sino desinstala el de kubuntu...

saludos

---

### Post by infernus92 on 2009-05-01
> **staar said:**
> creo que el (los) nombre era (k,x,myth)ubuntu-usplash-theme, con el startup-manager podés seleccionar el theme del usplash, o sino desinstala el de kubuntu...

saludos

desinstale el de kubuntu antes de que postees esto...
sigo diciendo perdon por la ignorancia pero que es sartup-manager? no encontre nada asi ni en ingles ni en castellano...

Saludos


EDITO: ya encontre a que te referias... y lo baje y probe... muy facil de usar y bastante util... gracias

---

### Post by z37a on 2009-05-01
> **infernus92 said:**
> desinstale el de kubuntu antes de que postees esto...
sigo diciendo perdon por la ignorancia pero que es sartup-manager? no encontre nada asi ni en ingles ni en castellano...

Saludos


EDITO: ya encontre a que te referias... y lo baje y probe... muy facil de usar y bastante util... gracias

1º En un terminal, "sudo apt-get install startupmanager" para instalar el programa o desde synaptic

2º Vas a Sistema -> Administracion -> Administrador de arranque (Esto en Gnome, KDE ni idea!!!)

---

