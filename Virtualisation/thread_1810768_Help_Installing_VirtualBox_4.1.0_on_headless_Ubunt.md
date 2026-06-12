---
title: "Help Installing VirtualBox 4.1.0 on headless Ubuntu server 10.10"
date: 2011-07-23
forum: Virtualisation
---

### Post by benju on 2011-07-23
Hello Everyone

I was wondering if somebody could help me getting a VirtualBox 4.1.0 to run on an Ubuntu Server 10.10.
I've followed certain guides ( [http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.0-on-a-headless-ubuntu-10.10-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.0-on-a-headless-ubuntu-10.10-server) ) but unfortunately no matter what I do I keep getting errors about dependencies not being met, and I'm afraid some of them are X11 dependencies ( which would defeat the purpose of the headless server ) 
I would appreciate any help or suggestions.

---

### Post by Tea4all on 2011-07-23
Try adding ```
deb http://download.virtualbox.org/virtualbox/debian maverick contrib non-free
``` to /etc/apt/sources.list instead. Then ```
sudo apt-key add oracle_vbox.asc
```. Follow the instructions at [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) for installation. Then look at the help section at [http://www.virtualbox.org/manual/ch07.html#vboxheadless](http://www.virtualbox.org/manual/ch07.html#vboxheadless) and follow the instructions. The article your trying to follow is a little dated.

---

### Post by benju on 2011-07-23
ThankYou very much Tea4all, however I'm still being asked to install 172MB of packages ( in which among others are: ... x11-common x11-utils x11-xserver-utils xdg-utils ) Am I correct in interpreting this as installing an X ( graphical? ) system in my Server, and if so this is precisely what I don't want. I don't want X11 to be installed at all.

---

### Post by CharlesA on 2011-07-23
Those are just dependencies. It isn't installing a GUI on the server.

---

### Post by benju on 2011-07-23
ThakYou as well CharlesA. I suppose I was getting confused ( when I saw the X11 stuff ) appreciate everyone's help.

---

### Post by Tea4all on 2011-07-23
Try downloading the .deb package from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) directly and installing with ```
sudo gdebi virtualbox-4.1*.deb -- --nox11
```
Edit: was not done editing yet...

---

### Post by kkaland on 2012-01-02
The trick for this is to run

```
sudo apt-get install virtualbox-4.1 --no-install-recommends
```

This will prevent the X server and other graphical programs from being installed.

Be sure to run

```
sudo apt-get install dkms
```

as well afterward.

---

