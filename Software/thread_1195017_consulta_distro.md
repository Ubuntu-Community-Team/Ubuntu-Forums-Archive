---
title: "consulta distro"
date: 2009-06-23
forum: Software
---

### Post by lucasfava on 2009-06-23
Hola como están

Necesito consultar , sobre que distro usar para una pentium 3 con 233 de memoria. Cual es recomendable :confused:

---

### Post by guillermolisi on 2009-06-23
> **lucasfava said:**
> Hola como están

Necesito consultar , sobre que distro usar para una pentium 3 con 233 de memoria. Cual es recomendable :confused:
Instalar con Ubuntu Alternate, porque tenes menos de 256Mb RAM, y usar como escritorio grafico, si es que queres este tipo de entorno, XFCE (Xubuntu) o LXDE.

Si no queres escritorio grafico, podes usar algun Windows Manager (hay una muy buena cantidad, para elegir). Si pones "linux Window manager" en Google te trae cantidad de informacion.

Eso si, no es lo mismo configurar un escritorio grafico que un gestor de ventanas.

Edit: Lo mande a Software porque las distribuciones de Linux no se pueden patear. Solo insultarlas.

---

### Post by gmunioz on 2009-06-23
Hola Lucas:

Si tienes, tiempo y ganas, puedes intentar:

1) Descargar Ubuntu Server, grabar la imagen en un cd, iniciar el

ordenador con el, e instalar con particionamiento manual en:

Una partición primaria, sistema de archivos ext4, de entre 7 y 

14 gigas punto de montaje /

Una partición lógica, sistema de archivos intercambio, de 1 giga,

montaje por defecto, intercambio, swap.

Una partición lógica, sistema de archivos ext4, punto de montaje /home

Instalas solo el sistema base y el servidor de impresión

2) Iniciarás, obviamente en un server, en consola, solo texto.

Para instalar un entorno grafico capaz de correr en ese ordenador, 

tienes muchas opciones, mi sugerencia es lxde, un procedimiento sería:

3) ejecutar estos comandos:

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install x-window-system-core gdm gksu gnome-system-tools gnome-nettools synaptic lxde language-pack-es language-pack-es-base language-pack-gnome-es language-pack-gnome-es-base language-selector language-support-es

startx

Y ya tendrías un entorno gráfico ligero, para luego con tranquilidad y

desde synaptic, ir instalando los paquetes necesarios para tus tareas

eligiendo los mas livianos.

Ejemplos: Abiword - Gnumeric - Gpaint - Kazehakaze - Xchm - Xpdf - Mc

---

### Post by guillermolisi on 2009-06-23
> **gmunioz said:**
> Hola Lucas:

Si tienes, tiempo y ganas, puedes intentar:

1) Descargar Ubuntu Server, grabar la imagen en un cd, iniciar el

ordenador con el, e instalar con particionamiento manual en:

Una partición primaria, sistema de archivos ext4, de entre 7 y 

14 gigas punto de montaje /

Una partición lógica, sistema de archivos intercambio, de 1 giga,

montaje por defecto, intercambio, swap.

Una partición lógica, sistema de archivos ext4, punto de montaje /home

Instalas solo el sistema base y el servidor de impresión

2) Iniciarás, obviamente en un server, en consola, solo texto.

Para instalar un entorno grafico capaz de correr en ese ordenador, 

tienes muchas opciones, mi sugerencia es lxde, un procedimiento sería:

3) ejecutar estos comandos:

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install x-window-system-core gdm gksu gnome-system-tools gnome-nettools synaptic lxde language-pack-es language-pack-es-base language-pack-gnome-es language-pack-gnome-es-base language-selector language-support-es

startx

Y ya tendrías un entorno gráfico ligero, para luego con tranquilidad y

desde synaptic, ir instalando los paquetes necesarios para tus tareas

eligiendo los mas livianos.

Ejemplos: Abiword - Gnumeric - Gpaint - Kazehakaze - Xchm - Xpdf - Mc
Por que Ubuntu server ?

---

### Post by staar on 2009-06-23
me sumo a la pregunta de guillermo, no sería mejor desde la versión alternate de la desktop, instalando un sistema básico? digo, por el kernel...

saludos

---

### Post by gmunioz on 2009-06-24
Hola:

```
¿Por qué Ubuntu server? 
```

Pues porque:

1 - En mi experiencia siempre me ha dado mejor resultado

para instalar sistemas bases, instalar el server,

configurarlo y luego ir agregándole lo necesario,

siempre queda un sistema más liviano.

2- Versión server, porque desde hace algunas versiones

el alternate-cd ¡no lo trae más!, supongo que por cuestiones

de espacio u otras que ignoro. Asi que directamente descargo

el cd del server en lugar del alternate.

3- Esta es un importante diferencia de Ubuntu con Debian,

con Debian, generalmente aprendes algo y para siempre te sirve

con Ubuntu debes estar atento, pues de versión en versión las

cosas cambian radicalmente (hda x sda) (sda1 x uuid) etc. etc.

---

### Post by guillermolisi on 2009-06-24
> **gmunioz said:**
> Hola:

```
¿Por qué Ubuntu server? 
```Pues porque:

1 - En mi experiencia siempre me ha dado mejor resultado

para instalar sistemas bases, instalar el server,

configurarlo y luego ir agregándole lo necesario,

siempre queda un sistema más liviano.

2- Versión server, porque desde hace algunas versiones

el alternate-cd ¡no lo trae más!, supongo que por cuestiones

de espacio u otras que ignoro. Asi que directamente descargo

el cd del server en lugar del alternate.

3- Esta es un importante diferencia de Ubuntu con Debian,

con Debian, generalmente aprendes algo y para siempre te sirve

con Ubuntu debes estar atento, pues de versión en versión las

cosas cambian radicalmente (hda x sda) (sda1 x uuid) etc. etc.
Tengo una imagen ISO de JJ alternate desktop 32bits i386 en mi maquina que baje hace un par de semana.

Si bien la diferencia fundamental entre desktop y server esta en la latencia del kernel que usan, para ciertas cosas no se aconseja el kernel server.

Ahora, si lo que se busca es poner en marcha un desktop en una maquina modesta en recursos, no serian mejor alternativas como UbuntuLite, por ejemplo, que se instala en forma muy parecida al netinst de Debian, que un server ?

Si bien para algunos instalar un server puede parecer algo trivial, no lo es para un usuario generico que solo pretende poner en marcha un desktop para uso de oficina/domestico.

---

### Post by gmunioz on 2009-06-24
Hola:

Lo mio es simplemente una sugerencia, basada

en mi experiencia, siempre instalé mediante el 

alternate, ¿por qué? simplemente porque soy

antiguo y estoy acostumbrado a instalar controlando

lo que instalo, no porque me disguste el live-cd

de hecho baje el de Jaunty, con el fin de tener un

rescate ante una eventual falla de sistema y poder

acceder al sistema ext4, y cuando lo probé descubrí

que ahora los live-cd permiten instalar sin necesidad

de iniciar una sesión y tienen practicamente las mismas

opciones que el alternate y es más, la instalación es

más rápida.

Respecto del server, en general solia instalar desde el

alternate, primero el server, simple, con solo el servidor

de impresión, eso no demanda gran conocimiento y es muy rápido

y luego configuraba, tal como en Debian, las gráficas a mi gusto.

A partir de que el alternate no trajo mas el server, comencé a

usar la versión servidor y realmente no note diferencias importantes.

Además, en cualquier momento se puede optar por cambiar su kernel por

el genérico, es mas si se instala Virtualbox, se cambia automática

mente, la idea no es configurar un servidor, sino instalar el sistema

basico y a partir de el unas gráficas livianas y un equipo a medida.

Pero, te reitero, lo mio es solo práctica y experiencia, y sugiero

lo que no me ocasionó problemas. No se me ocurre aconsejar usar

karmic, gnome-shell ni grub2, aunque los uso, y he escrito acerca 

y sobre ellos. Lamentablemente nunca probé Ubuntulite así que no

puedo hablar respecto de esa distribución.

---

### Post by lucasfava on 2009-06-26
Hola y gracias por la ayuda :D

Al final buscando encontré una distro para pc's  de 486 a pIII y que usa poca memoria apenas 64mb,y ocupa 750 Mb de espacio en disco [COLOR="Red"]**DeliLinux**[/COLOR]. Alguno la vio en funcionamiento  :)

Dejo la pagina de [DeliLinux]("http://www.delilinux.de/index-es.html")

Una cosa mas Deli en turco quiere decir Loco:D

---

### Post by gmunioz on 2009-06-26
Hola Lucas:

Si lo que buscas es algo ligero distinto de Ubuntu

te sugiero slitaz

[http://www.talishte.com/download/isos/slitaz-1.0.iso](http://www.talishte.com/download/isos/slitaz-1.0.iso)

Es una distribución moderna, rápida y ligera, muy ligera.

---

### Post by lucasfava on 2009-06-27
> **gmunioz said:**
> Hola Lucas:

Si lo que buscas es algo ligero distinto de Ubuntu

te sugiero slitaz

[http://www.talishte.com/download/isos/slitaz-1.0.iso](http://www.talishte.com/download/isos/slitaz-1.0.iso)

Es una distribución moderna, rápida y ligera, muy ligera.

gmunioz que tal es la probaste :D

---

### Post by gmunioz on 2009-06-27
Hola Lucas:

Si la estoy corriendo en virtualbox.

Me gusta hasta para operativo por defecto

Lástima que quemé las naves, y hace tiempo

que opte por Ubuntu.

Tiene casi 1,5 gigas de aplicaciones de todo

tipo, para el que necesite ampliar el sistema.

Según mi experiencia, superó lejos a Dsl y Puppy.

---

