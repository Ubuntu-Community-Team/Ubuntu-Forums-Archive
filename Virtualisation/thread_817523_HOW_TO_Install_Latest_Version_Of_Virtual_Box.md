---
title: "HOW TO: Install Latest Version Of Virtual Box"
date: 2008-06-03
forum: Virtualisation
---

### Post by Matthew Wiebelhaus on 2008-06-03
***This guide will explain how to install the latest version of VirtualBox, 1.6.0, on Ubuntu. I made this guide because some have been having problems doing this and the one in the repositories is not the latest version.***

[LIST=1]
[*]Go the this location [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI) select Ubuntu 8.04 X86 from the platform and agree to the terms.

[*]Download the .deb to the desktop and make sure you have installed all the latest updates before continuing to the installation.

[*]After installing all the updates install the package. When you are installing it will display a setup box. On default it will have a box checked to compile something, you must do this or VirtualBox will not work properly.

[*]The next step will add a vboxusers group that allows for access to files in restricted directories. You have to do this because VirtualBox uses configuration files.

[*]Once this is finished you must add yourself to the vboxusers group so you can use VirtualBox. Go to System > Administration > Users and Groups. Once you have the Users and Groups window open click Unlock and type your root password. Once you have unlocked click Manage Groups. Next go to the bottom of the choices and click once upon vboxusers. Once you have clicked upon vboxusers select properties and check the box with your name beside it to add yourself to the group. Once done close all the windows.

[*]If you have finished all the previous steps you can restart your computer for all of the changes to take effect.

[*]Congratulations, you have finished setting up VirtualBox. You may have have problems with USB support and I will add this part of the guide later, im finishing some EOC geometry practice tests.
[/LIST]

***If you want to get your USB support working follow this.***

[I]Setup VirtualBox USB Support:
USB is disabled by default, so you'll probably want to enable it. Otherwise you'll get an error when you go into the "Settings" of your virtual machine. To correct this, you'll need to edit the mountdevsubfs.sh file:[/I] *[COLOR="Red"]Thanks to [http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html) for this part.[/COLOR]*

> sudo gedit /etc/init.d/mountdevsubfs.sh

You'll see a block of code that looks like this:
> #
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

Now uncomment the last 4 lines above to look like this:
> 
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

***If you update your linux kernel then you will have to use the following command to recompile the VirtualBox kernel module.*** *[COLOR="Red"]Thanks yo nhasian for this.[/COLOR]*
> 
sudo /etc/init.d/vboxdrv setup

---

### Post by nhasian on 2008-06-03
Thanks Matthew, I followed your instructions and it worked like a champ.  I noticed that Virtual Box OSE was available in the add/remove programs too so i'm not sure what the difference is.  I just followed your instructions and got the .deb installation file directly from Sun.

USB is disabled, i havent monkeyed around with it yet.  It says there is a network interface but i'm guessing its ethernet... gotta figure out how to get my wifi working in it.

---

### Post by yaknowwat on 2008-06-04
yeah i installed virtulbox 1.6 a few days after it came out lots of improvements.


I used this tutorial to install it and get it working 100%,
then i did a few other things to adjust the virtual machine to my liking.

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

---

### Post by nhasian on 2008-06-04
Thanks yaknowwat, that fixed the usb problem.  Also I wanted to mention that after updating the linux kernel today i had to recompile the virtual box kernel module by typing:

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by wwusnobrdr on 2008-06-04
Yeah I saw that due to some change in the Virtualbox classification they now cannot have the newest release in the respository due to the need to have the user click "I agree" after reading the agreement, why they couldn't simply implement this in the install, I don't know.  Version 1.6 has ~1000 bug fixes so an upgrade is recommended!

---

### Post by nhasian on 2008-06-05
no ones reads those things anyway.  I just scrolled down to the bottom and hit I Agree.  I have no idea what I agreed to.  I hope they dont take my first born.

---

### Post by Matthew Wiebelhaus on 2008-06-06
> **nhasian said:**
> Thanks yaknowwat, that fixed the usb problem.  Also I wanted to mention that after updating the linux kernel today i had to recompile the virtual box kernel module by typing:

```
sudo /etc/init.d/vboxdrv setup
```

Thanks for this I will add to the guide and give you credit.

---

### Post by dm6257 on 2008-06-08
I am using VirtualBox 1.6.2 on Hardy and it works great

When the Ubuntu update process updates the kernal I get the error message others have mentioned and run /etc/init.d/vboxdrv setup.  That fails and I am asked to review an error log which shows the following:

/etc/init.d/vboxdrv: 311: /usr/lib/virtualbox/src/build_in_tmp: not found

I don't have a /use/lib/virtualbox/src folder.

I remove VirtualBox using Synaptic, re download the package from the Sun site, re-install and 10 minutes later everything is fine agan.

I am doing something wrong in the install process.

Thanks
dm6257

---

### Post by Matthew Wiebelhaus on 2008-06-08
When ubuntu updates the linux kernel you have to recompile the VirtualBox kernel im not sure how to do this yet but im going to figure it out.

First make sure you run this as root

> /etc/init.d/vboxdrv setup

that should be how you recompile the kernel and if that dosent work you may have to reinstall each time the Linux kernel is updated.

---

### Post by buntunub on 2008-06-08
Hi, using your method, virtualbox installs fine and everything appears to go smooth, but after adding a virtual machine and configuring it and then clicking on "Start", all I get is a box with a black screen. It appears to be doing something more or less, because when I exit out of the VM I can see the machine loading up in like a frozen state. This happens even with my WinXP virtual machine ive setup. Any ideas what could cause this?

See attachments for a look at what im talking about.

---

### Post by Jensss on 2008-06-09
When I start a new session to install XP I get an error:
```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

 
```

But when I do that I get the following error:
```
jens@jenslaptopubuntu:~$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found
```

What's wrong?

---

### Post by nlindberg877 on 2008-06-09
I followed the original tutorial, and now the package will not show up in Applications>System Tools 

I also tried Alt+f2 and typing virtualbox, and it would not load.

Any ideas?

---

### Post by inportb on 2008-06-09
Just a reminder -- Virtualbox 1.6.2 is now available. By all means, upgrade!

> **nhasian said:**
> Thanks Matthew, I followed your instructions and it worked like a champ.  I noticed that Virtual Box OSE was available in the add/remove programs too so i'm not sure what the difference is.  I just followed your instructions and got the .deb installation file directly from Sun.

USB is disabled, i havent monkeyed around with it yet.  It says there is a network interface but i'm guessing its ethernet... gotta figure out how to get my wifi working in it.

Of course. You can find the differences on virtualbox.org

---

### Post by Cuzit on 2008-06-23
> **nlindberg877 said:**
> I followed the original tutorial, and now the package will not show up in Applications>System Tools 

I also tried Alt+f2 and typing virtualbox, and it would not load.

Any ideas?

I am also having this problem.

Add/Remove Programs said I had one broken package, but when I filtered out the broken packages in Synaptic, it came up with no results.  It also won't let me update, telling me to check my Network connection (which, obviously, works fine).

Any help?

---

### Post by pac2715 on 2008-06-25
i tried the tutorial as well but when executing the /etc ... command, i received the following error:

Makefile:127: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

any suggestions?

---

### Post by dunkar70 on 2009-07-21
The following lines have worked well for installing recent (post 2.2) versions on my Ubuntu systems...

```

# Set your distribution
   distroCode=jaunty
   vboxVersion=virtualbox-3.0
# Add the authentication key to APT
   wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
# Create a .list file to add the repository
   echo "deb http://download.virtualbox.org/virtualbox/debian ${distroCode} non-free" | sudo tee -a /etc/apt/sources.list.d/virtualbox.list
# Install packages
   sudo apt-get install dkms ${vboxVersion}
# Add yourself to the new vboxusers group
   sudo adduser ${USER} vboxusers
# Identify the groupid for the vboxusers group and a line to the fstab file.
   s=`grep vboxusers /etc/group`
   echo "## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=${s//[!0-9]/},devmode=664 0 0" | sudo tee -a /etc/fstab

```

---

