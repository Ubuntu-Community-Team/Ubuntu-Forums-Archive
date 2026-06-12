---
title: "The vboxdrv kernel module is not loaded"
date: 2009-06-02
forum: Virtualisation
---

### Post by pHuXx on 2009-06-02
I updated to Jaunty and am getting this:

q@q-desktop:~$ sudo VirtualBox
[sudo] password for q: 
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (2.6.28-11-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.

When i do sudo /etc/init.d/vboxdrv setup:

q@q-desktop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

So what should i do.
Please help.

---

### Post by bluefrog on 2009-06-03
* Look at /var/log/vbox-install.log to find out what went wrong
as said

---

### Post by Perryg on 2009-06-03
I would suggest that you do what the message is telling you to do.
Look at /var/log/vbox-install.log to find out what went wrong

Probably you need the kernel-headers for you Linux version, but this will be in the last few lines of the log.

---

### Post by pHuXx on 2009-06-03
"Look at /var/log/vbox-install.log to find out what went wrong"

This is var/log/vbox-install.log:

/etc/init.d/vboxdrv: 342: /usr/share/virtualbox/src/vboxdrv/build_in_tmp: not found


So what should i do.

---

### Post by squareff255 on 2010-02-11
I FOUND THE SOLUTION! You just need to use the following commands

```

cd /etc/init.d

```
and then...
```

sudo mv vboxdrv.dpkg-bak vboxdrv

```
and finally...
```

sudo /etc/init.d/vboxdrv setup

```
Then, if you have any virtualbox anything running, shut it off and turn it back on. Worked for me on Ubuntu 9.10 Karmic Koala with VirtualBox 3.1.2

---

### Post by ntitdost on 2010-05-16
> **squareff255 said:**
> I
```

sudo mv vboxdrv.dpkg-bak vboxdrv

```

My system don't have file vboxdrv.dpkg-bak, I use 10.04. Maybe have any mistake here?

---

### Post by jospehko on 2011-09-18
sudo /etc/init.d/vboxdrv setup 
solved my problem....


Thank you.
Joseph

---

### Post by ballgame on 2012-03-05
> **ntitdost said:**
> My system don't have file vboxdrv.dpkg-bak, I use 10.04. Maybe have any mistake here?

Same problem...

```
root@b0tlomo:/etc/init.d# sudo mv vboxdrv.dpkg-bak vboxdrv
mv: cannot stat `vboxdrv.dpkg-bak': No such file or directory
``````
root@b0tlomo:~# sudo /etc/init.d/vboxdrv setup
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
 * Stopping VirtualBox kernel modules                                         [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  
 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong
```I'm trying to get this installed on a Ubuntu 10.10 VPS with no luck so far. Can anyone give me any guidance please!!!

---

