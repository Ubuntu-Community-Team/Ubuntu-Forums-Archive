---
title: "VMWare server on Feisty Server"
date: 2007-10-13
forum: Server Platforms
---

### Post by jmoe74 on 2007-10-13
I have successfully installed VMWare server on Ubuntu Server 7.04. There is no window management installed so I am running this server from the command line. Does anyone know how to install VMs without a  gui? I want to access these VMs over the network with VMWare Player.

any clues?:confused:

---

### Post by gfowler on 2007-10-13
> **jmoe74 said:**
> I have successfully installed VMWare server on Ubuntu Server 7.04. There is no window management installed so I am running this server from the command line. Does anyone know how to install VMs without a  gui? I want to access these VMs over the network with VMWare Player.

any clues?:confused:

Go over to the VMWare site and d/l your flavor of VMServer Console (Linux/Win/etc) of choice to run on your workstation, problem solved.

---

### Post by Mike'sHardLinux on 2007-10-13
I did something similar a while ago, and it seems that I had to install some X related libs on the server to make this work. The only difference is I had installed VMware Server on the server and the client.

---

### Post by Macchi on 2007-10-14
You should try the VMware Server Console from a remote machine!
It is possible to run your virtual machines from a computer having a graphical interface in your network. There are also solutions for running the virtual machines through a web browser.

The VMware console provides a graphical environment for the virtual machines and for all settings and administration of the VMware server without having to install a GUI on the server. 

PS: Nowadays I see no virtue in the self-infliction of a command line if there are graphical tools that provide superior solutions for accomplishing the same task in a safer, better and faster way.

---

### Post by markymarknz on 2007-10-14
I had a similar situation mid last year when I setup an experimental vmware server with Ubuntu in a corporate environment.
I used Edgy and installed fluxbox for a good lightweight X Server, then if I needed to I can graphically control the VM guests from the console.
I also downloaded and installed the VMWare MUI from their website which is the web interface.
Like what others said you can also use the VMWare Console from your PC to connect to the server. All are good options but depending on how important the server is it's a good idea to have more than one way of accessing and installing the Guests.

Mark

---

