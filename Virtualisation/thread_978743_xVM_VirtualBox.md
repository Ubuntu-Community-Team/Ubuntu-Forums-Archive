---
title: "xVM VirtualBox"
date: 2008-11-11
forum: Virtualisation
---

### Post by th1bill on 2008-11-11
[COLOR="DarkRed"]I made the mistake of upgrading to 8.10 and I can no longer use my XP Virtual box.When I go Apps.>System Tools>Sun xVM VirtualBox>Start it tells me VirtualBox kernal driver not installed.  Is there any way to fix this?[/COLOR]

---

### Post by skillllllz on 2008-11-11
Upgrading to 8.10 was no mistake, my friend. This is a simple incompatibility issue that is easy to resolve. There are two ways:

First and foremost, I would be sure to download and (re)install the latest version of Virtualbox, ver 2.0.4, as it has been improved for use with Intrepid. During the (re)install it will remove any old kernel modules and compile a new one for you, automatically.

Secondly, in the event that you cannot, or choose not to (re)install the latest version, you may simply open up the terminal application and enter the following:
```
sudo /etc/init.d/vboxdrv setup
```The kernel module could take a few minutes to recompile, depending on your system specs, so be patient. Once it's finished, you should have a fully functioning VirtualBox... Wooowhoooo! Enjoy :)

---

### Post by th1bill on 2008-11-11
[COLOR="DarkRed"]I went to the terminal and pasted thecommand line and recieved a message to check the log.  The log reads as follows;[/COLOR]> 
Attempting to install using DKMS
info: No menu item ` removing old DKMS module vboxdrv version ' in node `(dir)Top'.

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 1.6.2
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/1.6.2/source ->
                 /usr/src/vboxdrv-1.6.2

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.24-19-generic cannot be found at
/lib/modules/2.6.24-19-generic/build or /lib/modules/2.6.24-19-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:127: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
I will next go to Sun and see if I can find the latest version for Intrepid.

---

### Post by th1bill on 2008-11-11
[COLOR="DarkRed"]I went to Sun/Downloads and elected to install using gdebi package installer and recieved the following;[/COLOR]

> VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them (the package name is probably linux-headers-<version> whereby <version> can be determined by 'uname -r') and execute

  /etc/init.d/vboxdrv setup

as root.
[COLOR="DarkRed"]I will ex4ecut the command in the terminal next.[/COLOR]

---

### Post by th1bill on 2008-11-11
[COLOR="DarkRed"]I cut and pasted the command line and it returned;[/COLOR]
[COLOR="DarkRed"]I cut and pasted and returned the following;[/COLOR]
> root@spare:/home/th1bill# /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

> Attempting to install using DKMS
  removing old DKMS module vboxdrv version 

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>
  removing old DKMS module vboxdrv version 

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 2.0.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.0.4/source ->
                 /usr/src/vboxdrv-2.0.4

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.24-19-generic cannot be found at
/lib/modules/2.6.24-19-generic/build or /lib/modules/2.6.24-19-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:142: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
[COLOR="DarkRed"]It looks to me like I loaded Intrepid and somehow kept the old kernel.  I have no idea how to fix it either, being a newbie.[/COLOR]

---

### Post by skillllllz on 2008-11-11
Run the following command from the terminal to find out what kernel you are actually running:
```
uname -r
```

---

### Post by th1bill on 2008-11-11
2.6.24-19-generic


I do not know how that can be but that is the read out.  I opened the synaptio manager and found the latest kernal listed and I clicked it for reinstall but no change.

---

### Post by th1bill on 2008-11-11
[COLOR="DarkRed"]Since at start up I see Ubuntu 8.04 and the ....19 generac kernel and since the Synaptic manager lists the headers for [/COLOR]2.6.27-7[COLOR="DarkRed"] is it possible to just edit my grub  menu and maybe fix this?[/COLOR]

---

### Post by skillllllz on 2008-11-12
I don't believe that's the proper way to go about this. Use synaptic to (re)install these two packages:

linux-headers-generic
linux-image-generic

---

### Post by th1bill on 2008-11-12
[COLOR="DarkRed"]Skillllllz,
... You have a great sense of patients and I really do thank you for hanging in here with me.
... Using Synaptic I did a fresh install on both packages and rebooted before attempting tp install the latest version of xVM VBox but I still get the same message and at the terminal, uname -r still returns the wrong kernel.[/COLOR]

---

### Post by skillllllz on 2008-11-12
Hey, it's my pleasure; I like helping our community when and where I can. 

You're kernel issue has me rather stumped. I'm not sure how to proceed. My concern is that if you resort to manually editing grub, you may end up with a system that fails to boot at all. I really hope someone with greater knowledge in this area chimes in with ideas. In the meantime, I will do some sifting of the net, ala google, for solutions. Hang in there, we'll get things running smooth again.

---

### Post by th1bill on 2008-11-13
Skillllllz'
[COLOR="DarkRed"]... Through the Ubuntu lists mail server I have found the answer.  By going to the synaptic I determined that the new kernel. 2.6.27-7, was resident on my system and that for some unknown reason the install did not change my /boot/grub/menu.lst to reflect it's presence.

... By going to the Terminal  and typing > sudo gedit /boot/grub/menu.lst followed by typing my password in iwas able to scroll down past all the comments (marked with ## or #) I cut and pasted the following to repair my system and install the latest version of xVM VirtualBox.[/COLOR]

> title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic
root=UUID=d0357aa7-0f56-456b-8ce9-2b6fe6d8e429 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic
root=UUID=d0357aa7-0f56-456b-8ce9-2b6fe6d8e429 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

[COLOR="DarkRed"]For those brave souls that will dare to attempt this please note!

... Do not remove any of your other entries, you might just render you machine useless if you do.  Also note the Old Entry and read down to the "kernel line."  On that line compare the sequence following "root=' with your oold string, I believe they must be the same.
... I hope that someone with more knowledge than I will come along and correct or confirm what I have   just said because I received my syntax from the perwon on the list.[/COLOR]

---

### Post by skillllllz on 2008-11-14
Hey, that's really great! I'm glad you were able to solve it. Thank you for posting the solution; I'm certain others will find it useful.

---

