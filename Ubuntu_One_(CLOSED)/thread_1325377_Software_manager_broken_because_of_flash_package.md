---
title: "Software manager broken because of flash package"
date: 2009-11-13
forum: Ubuntu One (CLOSED)
---

### Post by 15176568 on 2009-11-13
I've tried to install flash player 10 from a debian package that I downloaded from the flash website.

There was a error during the installation and after the installation, all my package managers didn't work.
For example, if I start Synaptic, I get a message saying:

An error occurred
The following details are provided:

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I've tried a couple of basic stuff to sort it out, but to no avail.
I've tried the following:
Sudo dpkg --configure -a
Sudo apt-get update
Sudo apt-get upgrade
As I said, none of these worked.

Just for in case, I'm using Ubuntu 9.10.

Thanks.

---

### Post by mac9416 on 2009-11-13
Howdy!

These commands have fixed that problem for everyone I have suggested them to...

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

Good luck!

---

### Post by XavierArmstrong on 2009-11-15
Thank you very much for these comands! I have been trying to do this for the past hour or so.

---

### Post by etienne@Rofti on 2009-11-15
Thanks, mac9416! I had the same problem... All fixed now!

---

### Post by madhavsrao on 2009-11-15
> **mac9416 said:**
> Howdy!

These commands have fixed that problem for everyone I have suggested them to...

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

Good luck!
Thanks brb... :popcorn:

---

### Post by Arindam Saha on 2009-11-20
> **Re: Software manager broken because of flash package**
         Howdy!

These commands have fixed that problem for everyone I have suggested them to...

     Code:
     $ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way 
Good luck!     Thank you for the solution it worked like a charm, i was going nuts trying to uninstall the falshplugin.You are a lifesaver.:) Also explaning what each command does was just awesome for a linux newbie like me.

---

