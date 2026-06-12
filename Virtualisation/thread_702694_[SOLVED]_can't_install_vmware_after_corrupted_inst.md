---
title: "[SOLVED] can't install vmware after corrupted install"
date: 2008-02-20
forum: Virtualisation
---

### Post by TheLions on 2008-02-20
I started instalation from Automatix and since it asked me for serial key. Since I had'n have serial at that time i pressed cancel and Automatix has got frozen. 
I obtained a serial but i can't run installation anymore. When installing from Automatix i get this:

```

....
Po&#269;etna konfiguracija paketa ...
(Reading database ... 166818 files and directories currently installed.)
Unpacking vmware-server (from .../vmware-server_1.0.4-1gutsy2_amd64.deb) ...
[COLOR="Red"]dpkg: error processing /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1[/COLOR]
[COLOR="Red"]Errors were encountered while processing:
 /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
```

And installing vmware from official vmware webpage this:
```

The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

[COLOR="Red"]vmnet
vmmon[/COLOR]

Execution aborted.
```

Please help!!! [IMG]http://www.fer2.net/images/smilies/help.gif[/IMG][IMG]http://www.fer2.net/images/smilies/help.gif[/IMG][IMG]http://www.fer2.net/images/smilies/help.gif[/IMG]

---

### Post by fjgaude on 2008-02-20
You simply have to completely uninstall vmware. You can do it from Synaptic by using the Mark for Complete Removal function. And making sure you remove all the config files that you can see in the Status menu.

Do a Search for vmware and you will see what's there. Right click for complete removing.

Let us know how you are doing.

---

### Post by TheLions on 2008-02-20
First of all thx for reply 

after removing vmvare kernel modules i was able to install official version

---

### Post by fjgaude on 2008-02-20
Very good... we learn new things every day, eh?

---

### Post by TheLions on 2008-02-20
thank you for the help i'll mark this thread as solved an start new one about running existing vista in vmware!:)

---

