---
title: "Ubuntu Server 12.04 LTS if graphical environment"
date: 2012-09-17
forum: Server Platforms
---

### Post by rawa on 2012-09-17
Hi

 One question, I installed Ubuntu 12.04 LTS server, then installed a graphical environment, but the operating system will continue behaving like Ubuntu Server or longer behave like a Desktop Ubuntu?

 thanks

 Ruben Arno
[U]
Ubuntu Server 12.04 LTS si entorno Grafico [/U]

Hola

Una duda, yo instalado Ubuntu server 12.04 LTS, luego instalado un entorno grafico, pero el sistema operativo se seguira comportando como Ubuntu Server o ya se comportara como un Ubuntu Desktop ?

Gracias

Ruben Arno

---

### Post by Bucky Ball on 2012-09-17
All depends what you installed. Do you mean a Desktop Environment? If you installed, say, xfce4, that won't install much else. If you installed ubuntu-desktop on the other hand, you have installed ALL the apps that come default with Ubuntu desktop edition so the server install is a bit pointless (may as well have installed Ubuntu then the server packages).

In short, you will have the server install PLUS the apps, packages, dependencies that come with any desktop environment you install. lxde, xfce4, this is extremely minimal. Anything *ubuntu-desktop, though, is installing all the default apps that come with that flavour (like an install). They all have the same base install, including server, then things are added to that for each flavour.

PS: xfce4 is common if a DE is required for a server environment.

---

### Post by snowpine on 2012-09-17
Hi rawa, most server professionals do not use a GUI on their servers for a variety of reasons (stability, security, performance, etc.). Learning to administer your server using the CLI is very easy with this excellent guide: [https://help.ubuntu.com/12.04/serverguide/](https://help.ubuntu.com/12.04/serverguide/)

---

### Post by jerrrys on 2012-09-17
You installed a desktop (which one?), but did you install a display manager?

sudo apt-get install lightdm

Or you can try the **startx** command in terminal.

---

### Post by rawa on 2012-09-17
Thanks for responding,

 I install Gnome Basic ...

 sudo apt-get install x-window-system-core gnome-core
 sudo apt-get install gksu
 sudo apt-get install gnome-system-tools gnome-nettool
 sudo apt-get install firefox

 However it has lost some attributes as the desktop version: as admministrador automated installers, for example the software center.

 A server that does not have a visual environment prepared for Administrators, delayed 20 years, and you can work in command line but time is wasted and not used the achievements of modern technology. Not if there is a graphical environment that already comes with visual tools to manage a server, anyone know anything?

 Note: probe with Zentyal but for my taste not stop we can add services and enhance our server, but not bad.

 Well, basically what I understood if I apply an installation of Ubuntu Server 12.04 LTS and then install a graphical environment such as Gnome, I lose the function of Server but most graphical environment programs, right?

 Thanks and a hug.

 Ruben Arno

Gracias por responder,

Yo instale Gnome basico ...

sudo apt-get install x-window-system-core gnome-core
sudo apt-get install gksu 
sudo apt-get install gnome-system-tools gnome-nettool
sudo apt-get install firefox

Sin embargo pierdo algunos atributos que tiene la version desktop como: como admministrador de instaladores automaticos, por ejemplo el centro de software.

Que un servidor no tenga un entorno visual preparado para Administradores, retrasa 20 años, ya que se puede trabajar en linea de comando pero se pierde tiempo y no se usa los logros de la tecnologia moderna. No se si hay algun entorno grafico que ya venga con las herramientas visuales para administrar un servidor, alguno conoce algo ?

Nota: probe con Zentyal pero para mi gusto no deja que podamos sumar servicios y potenciar nuestro servidor, pero no es malo.

Bueno, basicamente por lo que entendi si aplico una instalacion de Ubuntu Server 12.04 LTS y luego le instalo un entorno grafico como Gnome, no pierdo la funcion de Server sino que sumo los programas del entorno grafico, cierto ?

Gracias y un abrazo.

Ruben Arno


> **Bucky Ball said:**
> All depends what you installed. Do you mean a Desktop Environment? If you installed, say, xfce4, that won't install much else. If you installed ubuntu-desktop on the other hand, you have installed ALL the apps that come default with Ubuntu desktop edition so the server install is a bit pointless (may as well have installed Ubuntu then the server packages).

In short, you will have the server install PLUS the apps, packages, dependencies that come with any desktop environment you install. lxde, xfce4, this is extremely minimal. Anything *ubuntu-desktop, though, is installing all the default apps that come with that flavour (like an install). They all have the same base install, including server, then things are added to that for each flavour.

PS: xfce4 is common if a DE is required for a server environment.

---

### Post by rawa on 2012-09-17
Thanks, and I start reading and see if I can find the tools to quickly give power to Ubuntu Server 12.04 LTS server I'm testing.

Gracias, ya me pongo a leer y ver si encuentro rapidamente las herramientas para darle potencia al servidor Ubuntu Server 12.04 LTS que estoy probando.

Ruben Arno

---

### Post by rawa on 2012-09-17
Thanks Jerry, I do not know, I'll see how it works.

 a hug

Ruben Arno

Gracias Jerry, no lo conozco, voy a ver que tal funciona.

Un abrazo 

Ruben Arno

---

### Post by snowpine on 2012-09-17
Hi Ruben, there is no right or wrong answer. It depends on what the server is being used for. Maybe you are looking for something like Webmin?

[http://www.webmin.com/demo.html](http://www.webmin.com/demo.html)

More info about server GUI here:

[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

---

### Post by drdos2006 on 2012-09-17
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings on your network.


> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.590_all.deb

Install with :
sudo dpkg -i webmin_1.580_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to your server to edit files, create shares, startup daemons etc..

regards

---

