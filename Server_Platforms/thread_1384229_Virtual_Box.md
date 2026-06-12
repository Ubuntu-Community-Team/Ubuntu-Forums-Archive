---
title: "Virtual Box"
date: 2010-01-18
forum: Server Platforms
---

### Post by Hozza on 2010-01-18
Right, i have installed ubuntu server with xfce GUI.

I have installed Virtual Box (not OSE).

after trying to run a virtual computer i got 
```
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

```

so i went and installed DKMS.

and then i ran '/etc/init.d/vboxdrv setup'

i then got
```
media@media-server:~$ /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                          *  done.
 * Recompiling VirtualBox kernel module                                      /etc/init.d/vboxdrv: 377: cannot create /var/log/vbox-install.log: Permission denied

 * Look at /var/log/vbox-install.log to find out what went wrong
```

This is the content of the vbox install log
```
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxdrv/3.1.2/source ->
                 /usr/src/vboxdrv-3.1.2

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.31-17-server cannot be found at
/lib/modules/2.6.31-17-server/build or /lib/modules/2.6.31-17-server/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:152: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.

```

Whats wrong and what do i do now??? :S

---

### Post by chuina on 2010-01-18
> "media@media-server:~$ /etc/init.d/vboxdrv setup"

your post shows u might forget to add sudo before the command
try adding sudo like

```
sudo /etc/init.d/vboxdrv setup
```

thnx

---

### Post by Hozza on 2010-01-18
thank you however.

```
media@media-server:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for media: 
 * Stopping VirtualBox kernel module                                          *  done.
 * Recompiling VirtualBox kernel module                                      
 * Look at /var/log/vbox-install.log to find out what went wrong

```

it still didn't work :S

---

### Post by arubislander on 2010-01-18
The log is informing you that it cannot find the sources for the kernel you are running. To grab those do:
```
$ sudo apt-get install build-essential
```

That should install everything you need.

---

### Post by Hozza on 2010-01-18
Thank you but it didnt work, i installed

```
sudo apt-get install build-essential
```

rebooted and ran the vbox, again i got an error message saying i needed to run.
```
sudo /etc/init.d/vboxdrv setup
```
after installing dkms, dkms was already installed from before however i marked it for reinstallation.

then ran the code
```
sudo /etc/init.d/vboxdrv setup
```

i then got
```
media@media-server:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                          *  done.
 * Recompiling VirtualBox kernel module                                      
 * Look at /var/log/vbox-install.log to find out what went wrong

```

the error log looked like this
```
Attempting to install using DKMS
  removing old DKMS module vboxdrv version  3.1.2

------------------------------
Deleting module version: 3.1.2
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/3.1.2/source ->
                 /usr/src/vboxdrv-3.1.2

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.31-17-server cannot be found at
/lib/modules/2.6.31-17-server/build or /lib/modules/2.6.31-17-server/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:152: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.

```

long story short, it didnt work and i am in the identical position to before :S


plz help

---

### Post by chuina on 2010-01-18
Hey,
Did u install linux-headers ?
I not then try to install it when finished reboot the machine.

and try to run virtualbox

thnx

---

### Post by chuina on 2010-01-18
Hey,
Did u install linux-headers ?
If not then try to install it .
```
sudo apt-get install linux-headers
```
when finished reboot the machine.
log in as usual.
and try to run virtualbox

thnx

---

### Post by Hozza on 2010-01-19
what are linux headers?? anyhoo

```
media@media-server:~$ sudo apt-get install linux-headers
[sudo] password for media: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.31-17-server 2.6.31-17.54
  linux-headers-2.6.31-17-generic 2.6.31-17.54
  linux-headers-2.6.31-17 2.6.31-17.54
  linux-headers-2.6.31-16-server 2.6.31-16.53
  linux-headers-2.6.31-16-generic 2.6.31-16.53
  linux-headers-2.6.31-16 2.6.31-16.53
  linux-headers-2.6.31-15-server 2.6.31-15.50
  linux-headers-2.6.31-15-generic 2.6.31-15.50
  linux-headers-2.6.31-15 2.6.31-15.50
  linux-headers-2.6.31-9-rt 2.6.31-9.152
  linux-headers-2.6.31-14-server 2.6.31-14.48
  linux-headers-2.6.31-14-generic 2.6.31-14.48
  linux-headers-2.6.31-14 2.6.31-14.48
You should explicitly select one to install.
E: Package linux-headers has no installation candidate
```

????

---

### Post by chuina on 2010-01-20
Sorry, for late and for an incomplete command tips.
The full command is this:

```
sudo apt-get install linux-headers-`uname -r`
```

Copy paste the command.

More details is below:
[http://www.howtoforge.com/virtualbox_ubuntu](http://www.howtoforge.com/virtualbox_ubuntu)

---

### Post by Hozza on 2010-01-20
THANK YOU VERY MUCH!! It works!!!!!

Would someone mind explaining why it works? :D

---

### Post by chuina on 2010-01-20
> THANK YOU VERY MUCH!! It works!!!!
WelCome!

> Would someone mind explaining why it works?

Linux softwares many a times requires dependency softs/libs.
In this case VirtualBox needed those softs.  
Look for the line **Then install some prerequisites for VirtualBox** by clicking _[[COLOR="Green"]here[/COLOR]]("http://www.howtoforge.com/virtualbox_ubuntu")_.

Those are dependencies needed by VirtualBox.

NOTE:However, since your VirtualBox is running so you don't need anymore dependency.;)

---

