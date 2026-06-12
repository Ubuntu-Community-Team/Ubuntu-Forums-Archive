---
title: "HowTo: Install Virtualbox 1.6.x with USB support in Ubuntu 8.04 (Hardy)"
date: 2008-06-14
forum: Virtualisation
---

### Post by docplastic on 2008-06-14
# This post describes the procedure to install VirtualBox 2.1 in Ubuntu 8.10 (Intrepid) with USB support.

# Browse to [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and check if there is a package for your Ubuntu version and CPU architecture.

# Open a terminal (press simultaneously the ALT and F2 keys and enter: gnome-terminal)

[LIST]
[*]**sudo aptitude -R install build-essential dkms** # Install virtualbox kernel rebuilding utilities
[/LIST]

[LIST]
[*]**wget [http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-xxxx.deb](http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-xxxx.deb)** # download the right .deb package for your CPU
[/LIST]
 
[LIST]
[*]**sudo gdebi virtualbox-xxxx.deb** # Install it
[/LIST]

[LIST]
[*]**grep vboxusers /etc/group || sudo groupadd vboxusers** # if needed add the "vboxusers" group
[/LIST]
 
[LIST]
[*]**sudo usermod -aG vboxusers $USER** # In order to use VirtualBox an user must be added to the "vboxusers" group. You may add other (space separated) users after $USER
[/LIST]
 
# To add **USB support**, you need to execute the following code:
[LIST]
[*]**echo "none /proc/bus/usb usbfs devgid="$(sed '/plugdev/!d;s/plugdev:x:\(.*\):.*/\1/' /etc/group)",devmode=664 0 0" | sudo tee -a /etc/fstab**
[/LIST]

# Rebuild the virtualbox kernel modules
[LIST]
[*]**sudo /etc/init.d/vboxdrv setup**
[/LIST]

# Let the system update all the changes. Please note that "sudo mount -a" will not be enough.
[LIST]
[*]**Logout and Login again**
[/LIST]

# If you still have trouble, post here the results of the following command:
[LIST]
[*]**id $USER ; grep usbfs /etc/fstab ; grep plugdev /etc/group ; grep "domount\(.*\)usbfs" /etc/init.d/mountdevsubfs.sh**
[/LIST]

---

### Post by spanella47 on 2008-06-19
the command you gave didnt work becuase it popped out the wrong devgid... replaced with the vboxusers # on my system

btw, for newbies, its easier to use System -> Administration -> Users and Groups to manipulate groups to make sure your adding things correctly

also not necessary to logout/login, just run this in your terminal or Alt+F2:
```
sudo mount -a
```

---

### Post by docplastic on 2008-06-20
> **spanella47 said:**
> 
also not necessary to logout/login, just run this in your terminal or Alt+F2: sudo mount -a

You are partially right, mount takes care of the fstab part.

But it does not help with the users/groups part.

So, for now, logout and login seems to be the best procedure.

J.

---

### Post by randykelli on 2008-08-26
Doc hit this one out of the park!  I had the problem and it fixed it.  Thanks soooo much, Doc.

-Randy  :)

---

### Post by trestamanos on 2008-09-22
I just finished installing Version 2.0.2 and I got Windows running jsut fine.

does this thread support 2.0.2?
I tried that command and Windows on Vbox still doesnt recognize the USB

---

### Post by howefield on 2008-09-22
Try this..


In terminal type
```
sudo gedit /etc/init.d/mountdevsubfs.sh
```

Uncomment the last 4 lines above to look like this:
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

In terminal type
```
sudo gedit /etc/fstab
```

and append the following to the fstab then save/exit:

## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

Might need a reboot.

---

### Post by docplastic on 2008-09-23
To trestamanos: 
  Yes. It is also valid for version 2.0x.

To howefield and others:
  I prefer to keep things simple.

  In the VirtualBox own way, one should edit mountdevsubfs.sh and /etc/fstab.
  But it seems that just adding the usbfs entry with devgid=plugdev, is simpler and does the job pretty well.

  Also note that it is risky to assume that plugdev's devgid will always be 124.

---

### Post by EnGorDiaz on 2008-09-23
guys if you cant usb install guest aditions vis the menu of vbox an you shoul get some sound an graphics aswell

---

### Post by lian1238 on 2008-10-04
Although I'm using Gutsy and installed with the deb from their website and I didn't have USB support. Now I do! Thanks! I can't see the medal icon under docplastic's post. How come?
Anyway, thanks again! I'm the happiest man alive!!

---

### Post by ace214 on 2008-10-04
Thanks for the post.

For the record, I had to go into fstab and change the gid from 46 which the command seemed to do automatically to 124.

---

### Post by lian1238 on 2008-10-05
> **ace214 said:**
> For the record, I had to go into fstab and change the gid from 46 which the command seemed to do automatically to 124.
Mine's 46 and it works.

---

### Post by zeddock on 2008-10-18
What about on 8.10?

Can't follow the same directions for changes
> Uncomment the last 4 lines above to look like this:
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb


Thanx.

zeddock

---

### Post by johnmata on 2008-10-21
Hello,

I have tried everything listed within this thread, yet I still can't see my USB device (flash memory drive) within the guest operating system.  Any help is appreciated.

Host: Ubuntu 8.04, Hardy Heron
Guest: Windows Vista

Thanks,
John

---

### Post by dustinmadness on 2008-10-22
Here is a step by step guide for 8.04 (everything works like a charm on my Kubuntu and XP guest)

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

BTW: I would like to migrate my Kubuntu 8.04.1 to 8.10 as soon as it reach RC status. Is there USB support works with current 8.10 beta and current version VBox (2.0.2)? Anyone tested it? Results?

---

### Post by SiXhEaD on 2008-10-28
Perfect on Ubuntu 8.10 Beta :KS

---

### Post by james.wilde on 2008-11-19
[QUOTE=docplastic;5184568]# 
 
# To add **USB support**, you need to execute the following code:
[LIST]
**echo "none /proc/bus/usb usbfs devgid="$(sed '/plugdev/!d;s/plugdev:x:\(.*\):.*/\1/' /etc/group)",devmode=664 0 0" | sudo tee -a /etc/fstab**
[/LIST]

# Rebuild the virtualbox kernel modules
[LIST]
**sudo /etc/init.d/vboxdrv setup**
[/LIST]

That did it!  The top command made all the difference.  Now I see my iPod in iTunes and will be able to close down the Windows box.

Thanks a lot, Docplastic.

//James

---

### Post by mgmechanics on 2009-01-19
Thanks for a lot!
I had this problem: Virtual Box shows this message:
---------------------------------------------------
Failed to access the USB subsystem.

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

Result Code:
NS_ERROR_FAILURE (0x00004005)
Component:
Host
Interface:
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}
Callee:
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}
-----------------------------------------------------

The solution was:

$ grep vbox /etc/group
vboxusers:x:125:michael
------------^^^-------------


$ sudo gedit /etc/fstab

<insert this line in /etc/fstab>
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0
--------------------------------^^^------------------

sudo mount -a

------------------------------------
hint: the underlined "125" is the id of the group "vboxuser" on my system. Your system may be different. Please see the output of "grep vbox ..." command for this id on your system.

tested successfully with Ubuntu 8.10 (intrepid ibex) und virtual Box 2.1.0 at 2009-01-19
("successfully" = the message didn't appear)

---

### Post by williane on 2009-01-27
ubuntu 8.1 64bit
virtualbox 2.1.2 _AMD64 - running XP sp3
latest itunes (8.1 i think, dont have it open atm)

After VB install windows would recognize the iphone as a camera but itunes wasnt seeing it. This finally worked for me:

1.  echo "none /proc/bus/usb usbfs devgid="$(sed '/plugdev/!d;s/plugdev:x:\(.*\):.*/\1/' /etc/group)",devmode=664 0 0" | sudo tee -a /etc/fstab


2.  sudo /etc/init.d/vboxdrv setup


3.  Logout and Login again


Works great after that

---

### Post by susenj on 2009-05-16
Thank you so much howefield!
i tried your idea and i am running my pen drives in virtual boxes .
no reboot needed in my case.
Thanks again!:p:p
you rockk!

> **howefield said:**
> Try this..


In terminal type
```
sudo gedit /etc/init.d/mountdevsubfs.sh
```Uncomment the last 4 lines above to look like this:
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

In terminal type
```
sudo gedit /etc/fstab
```and append the following to the fstab then save/exit:

## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

Might need a reboot.

---

