---
title: "VirtualBox Kernel Driver Error"
date: 2008-09-11
forum: Virtualisation
---

### Post by splicer707 on 2008-09-11
I get this error when attempting to run VirtualBox.
Only a beginner and I'm quite lost.

---

### Post by hildebrand_us on 2008-09-11
Have you installed virtualbox correctly?
This is the rough procedure I remember doing on a terminal to install on a machine:-
First ensure that you are updated with the latest repository.

1. sudo apt-get install virtualbox-ose virtualbox-ose-source module-assistant

2. sudo module-assistant prepare

This prepares your module setup ensuring that your headers package is alright because this is the one against whom all the modules are compiled.

3. sudo module-assistant auto-install virtualbox-ose

This installs the necessary modules.

4. sudo modprobe vboxdrv

This loads the module.

5. Open the virtualbox software and you can use it.

Don't forget to edit in the line vboxdrv in the file /etc/modules so that it gets automatically loaded henceforth on reboot. (sudo gedit /etc/modules and enter vboxdrv in a new line).
HTH

---

### Post by vishzilla on 2008-09-11
Another solution, if you're looking for the latest version of Virtualbox download it from [here]("http://www.virtualbox.org/wiki/Linux_Downloads")

all you need is to double click and install the .deb file

Cheers

---

### Post by novus721 on 2008-09-11
> **hildebrand_us said:**
> Have you installed virtualbox correctly?
This is the rough procedure I remember doing on a terminal to install on a machine:-
First ensure that you are updated with the latest repository.

1. sudo apt-get install virtualbox-ose virtualbox-ose-source module-assistant

2. sudo module-assistant prepare

This prepares your module setup ensuring that your headers package is alright because this is the one against whom all the modules are compiled.

3. sudo module-assistant auto-install virtualbox-ose

This installs the necessary modules.

4. sudo modprobe vboxdrv

This loads the module.

5. Open the virtualbox software and you can use it.

Don't forget to edit in the line vboxdrv in the file /etc/modules so that it gets automatically loaded henceforth on reboot. (sudo gedit /etc/modules and enter vboxdrv in a new line).
HTH

So I tried using this method, but I couldn't get step 3 to work - I get 
```
 Compilation of the kernel module FAILED! VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them and execute /etc/init.d/vboxdrv setup as root
```

So I use gedit and I get 
```
Makefile:139: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
```

I tried going to the VB website and just doing a fresh install of the 2.0 version, but that screw up when the kernel compiles as well. I really need to get this VM working, otherwise I need to switch back to XP because I have coursework dependent on Windows software - any ideas anyone???

---

### Post by Therion on 2008-09-11
Here's [the tutorial](http://www.ubuntu-unleashed.com/2007/10/howto-integrate-windows-xp-desktop-into.html) I used to get VB up and running on Hardy.  

It might mention Gutsy here, or there, but I followed the steps, exactly as outlined, and my VB install of WinXP ran like a charm.

---

### Post by novus721 on 2008-09-11
not bad but it doesn't address the main issue, unfortunately

I know how to get the vbox program, it's just not installing properly to my kernel set

that set would also be 8.04.1, so you all know

---

### Post by Therion on 2008-09-11
Did you add yourself to the Virtual Box Users Group?

Also, 8.04.1 is not your kernel set; that's your Ubuntu release version.  They're two totally different things.

Lastly, the tutorial tells you much more than how to GET Virtual Box; it tells you how to set it up.

Oops... One other thing.  Are you trying to install the OSE version or the one from the Add/Remove programs list?  

The OSE version is much easier to configure.

---

### Post by novus721 on 2008-09-11
I stand corrected - 2.6.22-14-generic would be my kernel, sorry about that!

I've tried to install it multiple ways - through apt-get, by downloading it from the site, through add/remove...all give me the same kernel error, and none will let me compile it.

---

### Post by novus721 on 2008-09-11
so now I got to the point where it's asking me to get linux-headers-2.6.22-14-generic, which is exactly what I have! what gives?

---

### Post by Therion on 2008-09-12
> **novus721 said:**
> I stand corrected - 2.6.22-14-generic would be my kernel, sorry about that!

I've tried to install it multiple ways - through apt-get, by downloading it from the site, through add/remove...all give me the same kernel error, and none will let me compile it.
I suggest you uninstall everything Virtual Box.  Go to the tutorial I gave you and follow it, step-by-step starting with step one.  There are two different versions of Virtual Box and what with all the installing and who knows what else that's been done, I think you should try starting off with a clean slate.

There is nothing TO compile.  You download a .deb file.

---

