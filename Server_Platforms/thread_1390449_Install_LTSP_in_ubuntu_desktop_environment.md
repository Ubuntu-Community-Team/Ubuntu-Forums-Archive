---
title: "Install LTSP in ubuntu desktop environment"
date: 2010-01-25
forum: Server Platforms
---

### Post by tyoc213 on 2010-01-25
Hi there! I want to been able to connect remotely via RDP protocol with a client (for example from work to house) and I found that I can use

[http://wiki.ltsp.org/](http://wiki.ltsp.org/)

What packages I need to install, and how I configure it?

I connect my laptop via wireless throught eth2.

---

### Post by stlsaint on 2010-01-25
Do a quick search of ltsp in the synaptic package manager and you will see many options for it: ltsp-client, ltsp-server, ltsp-gui, etc etc, then use the website for further configs/setup.

---

### Post by tyoc213 on 2010-01-26
etc etc etc is not much about an explanation...

In my 9.10 I get some like

> $ sudo ltsp-build-client --mount-package-cache


...............
I: Configuring sgml-base...
I: Configuring tasksel...
I: Configuring gnupg...
I: Configuring ubuntu-keyring...
I: Configuring xml-core...
I: Configuring libparse-debianchangelog-perl...
I: Configuring libc-bin...
I: Configuring initramfs-tools...
W: Failure while configuring base packages.  This will be attempted 5 times.
W: Failure while configuring base packages.  This will be attempted 5 times.
W: Failure while configuring base packages.  This will be attempted 5 times.
W: Failure while configuring base packages.  This will be attempted 5 times.
W: Failure while configuring base packages.  This will be attempted 5 times.
I: Base system installed successfully.
Generating locales...
  es_MX.UTF-8... done
Generation complete.
Añadiendo `diversion of /sbin/start-stop-daemon to /sbin/start-stop-daemon.real by ltsp-client'
update-alternatives: using /usr/sbin/policy-rc.d.ltsp to provide /usr/sbin/policy-rc.d (policy-rc.d) in auto mode.
Añadiendo `diversion of /etc/mtab to /etc/mtab.real by ltsp-client'
«/opt/ltsp/i386/etc/apt/sources.list» -> «/opt/ltsp/i386/etc/apt/sources.list.old»
Des:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-es
Des:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg [189B]
Des:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-es [622kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-es
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-es
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-es
Des:4 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [44.1kB]
Des:5 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [54.9kB]
Des:6 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B]            
Des:7 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [21.9kB]                                                                                 
Des:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-es [4012B]                                                                                    
Des:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-es [1328kB]                                                                                     
Des:10 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [1666B]                                                                               
Des:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-es [106kB]                                                                                   
Des:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg [189B]                                                                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-es                                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-es                                                                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-es                                                                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-es                                                                                      
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                                                                                                
Des:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release [44.1kB]                                                                                            
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                                                                                                          
Des:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages [7971B]                                                                                         
Des:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages [5133kB]                                                                                          
Des:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages [190kB]                                                                                         
Des:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages [158kB]                                                                                       
Des:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages [14B]                                                                                   
Des:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages [93.0kB]                                                                                  
Des:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages [6942B]                                                                                 
Descargados 7816kB en 6min 9s (21.2kB/s)                                                                                                                    
Leyendo lista de paquetes... Hecho
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Tal vez quiera ejecutar `apt-get -f install' para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
  console-setup: Depende: xkb-data (>= 0.9) pero no va a instalarse
  dbus: Depende: libexpat1 (>= 1.95.8) pero no va a instalarse
  hal: Depende: libdbus-glib-1-2 (>= 0.78) pero no va a instalarse
       Depende: libexpat1 (>= 1.95.8) pero no va a instalarse
       Depende: libhal-storage1 (>= 0.5.11~rc2) pero no va a instalarse
       Depende: libhal1 (>= 0.5.10) pero no va a instalarse
       Depende: pciutils pero no va a instalarse
       Depende: usbutils pero no va a instalarse
       Depende: hal-info (>= 20070402) pero no va a instalarse
       Depende: consolekit (>= 0.3) pero no va a instalarse
  ldm: Depende: libatk1.0-0 (>= 1.20.0) pero no va a instalarse
       Depende: libcairo2 (>= 1.2.4) pero no va a instalarse
       Depende: libfontconfig1 (>= 2.4.0) pero no va a instalarse
       Depende: libfreetype6 (>= 2.2.1) pero no va a instalarse
       Depende: libgtk2.0-0 (>= 2.8.0) pero no va a instalarse
       Depende: libpango1.0-0 (>= 1.14.0) pero no va a instalarse
       Depende: openssh-client pero no va a instalarse o
                ssh pero no va a instalarse
       Depende: gtk2-engines-clearlooks
       Depende: ttf-dejavu-core pero no va a instalarse
       Depende: xserver-xorg pero no va a instalarse o
                xserver
       Depende: bsdmainutils pero no va a instalarse
       Depende: compiz-wrapper pero no va a instalarse
  ltsp-client: Depende: ltsp-client-core pero no va a instalarse
               Depende: pulseaudio-esound-compat pero no va a instalarse
               Depende: ltspfsd pero no va a instalarse
               Depende: libgl1-mesa-dri pero no va a instalarse
               Depende: xorg pero no va a instalarse
               Depende: inputattach pero no va a instalarse
               Depende: usplash pero no va a instalarse
               Depende: dmz-cursor-theme pero no va a instalarse
               Depende: usplash-theme-ubuntu pero no va a instalarse
               Depende: libasound2-plugins pero no va a instalarse
               Depende: pulseaudio pero no va a instalarse
               Depende: alsa-utils pero no va a instalarse
               Depende: alsa-base pero no va a instalarse
               Depende: sshfs pero no va a instalarse
               Depende: rdesktop pero no va a instalarse
               Depende: wget pero no va a instalarse
               Depende: sane-utils pero no va a instalarse
               Depende: cups-bsd pero no va a instalarse
  ubuntu-minimal: Depende: eject pero no va a instalarse
                  Depende: sudo
                  Depende: whiptail pero no va a instalarse
E: Dependencias incumplidas. Intente 'apt-get -f install' sin paquetes (o especifique una solución).
error: la instalación del cliente LTSP finalizó de forma anormal

---

### Post by tyoc213 on 2010-01-28
It was lot more easy to install and user freenx... I will go that way.

---

### Post by lykwydchykyn on 2010-01-29
FreeNX was the way to go; LTSP has nothing to do with what you wanted to accomplish, despite the name.  LTSP is for network-booting thin clients, not remote desktop connections.

FreeNX is the best (read: fastest) remote gui solution I've yet to see for Linux.

---

