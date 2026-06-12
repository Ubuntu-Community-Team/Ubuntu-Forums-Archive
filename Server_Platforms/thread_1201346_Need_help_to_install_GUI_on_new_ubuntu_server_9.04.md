---
title: "Need help to install GUI on new ubuntu server 9.04"
date: 2009-07-01
forum: Server Platforms
---

### Post by JohnyBoy123 on 2009-07-01
Hi Friends,      I need help in installing and get RDP of GUI of new ubuntu server 9.04.      The situation is I have a website that is using air application, and I have new ubuntu server. Now I need to get that site running on new ubuntu server.     problem is Ubuntu server dont have GUI and I need GUI to install air application.  I've installe d all other required software for site running but untill I get the GUI interface i cant install the air application.   I've installed the ubuntu-desktop on server and tried to run the GUI through different options like ssh tunnel, vncviewer, vpn, etc....  but all are having problems at some stage , may be I m missing some steps.    My purpose is to install GUI correctly on ubuntu server and get a ccess to that GUI.  I have ubuntu client version is installed in my local pc and also have windows xp installed in local pc.  But not sure which is the best way to install the GUI on server and get the RDP of server GUI.   I can roll back all the installation on server and can start from fresh installation on server , but need some guidance.   Please help me by guiding the best way to do this.   T hanks a lot  in advance.

---

### Post by Avinash.Rao on 2009-07-01
Do you want to install Ubuntu Desktop on the server or do you want to take remote control of the server desktop.??

---

### Post by netztier on 2009-07-01
> **JohnyBoy123 said:**
> Hi Friends,      I need help in installing and get RDP of GUI of new ubuntu server 9.04.  

RDP is Microsoft's *Remote Desktop Protocol* and there is no server-side support on Ubuntu for RDP, i.e. you cannot share a daesktop with RDP. However, there is an RDP client included with Ubuntu Desktop, that allows to access desktops of Windows machines over the network.

Desktop sharing on Ubuntu Desktop is generally done with the VNC protocol, for which different viewers/clients exist.

Ubuntu servers don't have GUIs: This has been and still is a wise design decision by Canonical (also see [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)).

If you really require a GUI, you might be better off by installing Ubuntu Desktop from CD (yes, Ubuntu Desktop!), adding your server apps to it (NFS, Samba, Apache, BIND etc, to suit your needs), and then replace the standard kernel with the server-optimized kernel.

Still, an application that requires a local GUI to install on a GUI-less server brings some questions: bad choice of application, or bad choice of server platform?

regards

Marc

---

### Post by Avinash.Rao on 2009-07-01
Marc,

Will the installation of Xubuntu-desktop on top of Ubuntu Server 8.04 change the kernel? I guess not? 


> **netztier said:**
> 

If you really require a GUI, you might be better off by installing Ubuntu Desktop from CD (yes, Ubuntu Desktop!), adding your server apps to it (NFS, Samba, Apache, BIND etc, to suit your needs), and then replace the standard kernel with the server-optimized kernel.

Still, an application that requires a local GUI to install on a GUI-less server brings some questions: bad choice of application, or bad choice of server platform?

regards

Marc

---

### Post by netztier on 2009-07-01
> **Avinash.Rao said:**
> Will the installation of Xubuntu-desktop

Of course not, but that's not what I suggested, either. 

If a desktop environment is an absolute need, I would suggest to install (one of) the desktop versions of Ubuntu, and then add a server kernel to it. The reason is: the set of packages that "makes" an Ubuntu Desktop installation is well-integrated and "everyting fits nicely together", better than it does when you add "ubuntu-desktop" (or kubuntu-desktop or xubuntu-desktop) server installation.

So by doing the "reverse approach" of adding a server kernel to a desktop installation results in a better-integrated server-with-desktop. Not that this would be something desirable, anyway... 

regards

Marc

---

### Post by Avinash.Rao on 2009-07-04
Thank you for your explanation. 
I have done the first one.. Installed Xubuntu Desktop on Ubuntu Server 8.04 bcoz LTSP was one of the main services requried.

;)

> **netztier said:**
> Of course not, but that's not what I suggested, either. 

If a desktop environment is an absolute need, I would suggest to install (one of) the desktop versions of Ubuntu, and then add a server kernel to it. The reason is: the set of packages that "makes" an Ubuntu Desktop installation is well-integrated and "everyting fits nicely together", better than it does when you add "ubuntu-desktop" (or kubuntu-desktop or xubuntu-desktop) server installation.

So by doing the "reverse approach" of adding a server kernel to a desktop installation results in a better-integrated server-with-desktop. Not that this would be something desirable, anyway... 

regards

Marc

---

### Post by windependence on 2009-07-04
What exactly does this air thing do? I have never heard of it. CLI is your best bet if you are going to run a production server.

-Tim

---

### Post by Avinash.Rao on 2009-07-05
Even I dont know about this AIR!!! and even CLI!! :)


> **windependence said:**
> What exactly does this air thing do? I have never heard of it. CLI is your best bet if you are going to run a production server.

-Tim

---

### Post by Avinash.Rao on 2009-07-19
Marc,

How do i do this? How do install a server kernel to an already installed XUbuntu Desktop? My intention is to make use of my new Sun Fire Server X4150 to the maximum in terms of hardware resources and performance.

Thanks
Avinash


> **netztier said:**
> Of course not, but that's not what I suggested, either. 

If a desktop environment is an absolute need, I would suggest to install (one of) the desktop versions of Ubuntu, and then add a server kernel to it. The reason is: the set of packages that "makes" an Ubuntu Desktop installation is well-integrated and "everyting fits nicely together", better than it does when you add "ubuntu-desktop" (or kubuntu-desktop or xubuntu-desktop) server installation.

So by doing the "reverse approach" of adding a server kernel to a desktop installation results in a better-integrated server-with-desktop. Not that this would be something desirable, anyway... 

regards

Marc

---

### Post by cariboo on 2009-07-19
To install a server kernel, open Synaptic and search for linux-image*server, then mark it for installation, then click apply. According to [this]("http://labs.adobe.com/wiki/index.php/AIR_for_Linux:Release_Notes"), you have to install Adobe AIR from the command line.

Edit: create a link to the package:

[apt://linux-image-server](apt://linux-image-server)

---

### Post by juancarlospaco on 2009-07-19
Don't use VNC on Server, or you get hacked/pwned, use SSH, it can handle X.

example:

ssh -X user@server-ip nautilus

---

### Post by windependence on 2009-07-19
A good, sound suggestion. Yeah, VNC has gotten really weak on security as of late.

-Tim

---

### Post by z3uSS on 2009-08-20
still if someone really wants GUI on ubuntu 9.04 how can u do it ? because xinit is not installed, instead x11-common apears as the main package, so startx doesn't work, 

anyone knows how can i install GUI (kde or gnome) on 9.04 server ?

help pls....

---

### Post by Avinash.Rao on 2009-08-20
What exactly do u want? Just an X-Display or the complete desktop on Server 

If you have a server install, you can do a apt-get install ubuntu-desktop to install the complete ubuntu desktop which is based on Gnome..
or apt-get install kubuntu-desktop for KDE


> **z3uSS said:**
> still if someone really wants GUI on ubuntu 9.04 how can u do it ? because xinit is not installed, instead x11-common apears as the main package, so startx doesn't work, 

anyone knows how can i install GUI (kde or gnome) on 9.04 server ?

help pls....

---

