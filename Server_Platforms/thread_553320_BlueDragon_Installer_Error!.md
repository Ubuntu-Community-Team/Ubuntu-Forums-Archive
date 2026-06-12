---
title: "BlueDragon Installer Error!"
date: 2007-09-17
forum: Server Platforms
---

### Post by goransv on 2007-09-17
I got this errror when I tried to install BlueDragon 7 on Ubuntu Server 7.0.4:
sudo ./BlueDragon_Server_70_339-Linux2.sh -i console
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

exec: 2482: /tmp/install.dir.17901/Linux/resource/jre/bin/java: not found

Before runing the installer I had: chmod 744 BlueDragron_Installer.sh
I also tried to download it again, in case it was corrupted.

It looks as if it´s a problem with the installer.

I allso tried to to change the IATEMPDIR like this (for the eventuality that /tmp has noexec permissions) :
mkdir /home/tmp; export IATEMPDIR=/home/tmp; 
But no success.

I had no problem to do a console install on a Ubuntu 7.0.4 Desktop version and also managed to do a succesfull install on another Ubuntu Server. 
 I have no Idea what it is that are causing this installation problem, all I know is that if Java is not installed the installation will work. Before I start to uninstall everything untill the Installer works I attach a diff of the installed programs (diff error_server working_server).

---

### Post by tj71587 on 2008-01-12
I recently had this error as well, did you download it from a windows machine and transfer it to the server, you must download it from the ubuntu machine.

---

