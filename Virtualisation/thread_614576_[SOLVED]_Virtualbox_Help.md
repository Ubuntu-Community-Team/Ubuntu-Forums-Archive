---
title: "[SOLVED] Virtualbox Help"
date: 2007-11-16
forum: Virtualisation
---

### Post by rcdeacon on 2007-11-16
I just did a fresh install of Gutsy. I need to get virtualbox wprlomg/ I have installed it (NOT from the repo but from their site), but I need help changing the permissions on the vboxdrv file. I am sort of migrating from the kde world and gnome, specifically Ubuntu does things differently. There must be an EASY way to do change permissions. Also I need to add a usbusers group in order to get usb working. There are a number of posts that deal with this usb issue but not many that are EASY to understand for a Gnome newbie! Any help will be appreciated.

---

### Post by Slingshot on 2007-11-16
Hi **rcdeacon**, try this. open a console, type sudo nautilus, make you way too /dev and select vboxdrv, right mouse to properties > permissions and change to your needs.

I havent done this, but I would try System > Administation > User and groups > manage groups > add group "usbuser" and tick the check box beside your user.

Hope this helps
SlingShot

---

### Post by rcdeacon on 2007-11-16
Thank you Slingshot. I appreciate the help.

---

### Post by rcdeacon on 2007-11-16
Now I am getting this error, "Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer." I think this is a problem with the usbfs.

---

### Post by rcdeacon on 2007-11-16
I did manage to get usb working part way. Now the usb devices are "grayed out". I can see them there but I cannot use them. I'm sure this too is related to those modified usb user files.

EDIT: hate to have to post again but after some THOUGHT and some INVESTIGATION I got it working again. Thanks for the help but this one is solved!

---

### Post by Banacek on 2007-11-16
That's good but could you elaborate, please? On the event of another person having your same problem it could be helpful to know how you got it to work and why. What thought and investigation brought you to your solution?

By the way, no call for you to hate to have to post again as it should be a pleasure to post here.

---

### Post by rcdeacon on 2007-11-16
I DID NOT have the correct "devid" in the /etc/fstab file.

---

### Post by Amin1_0_1 on 2007-11-16
Hi man
I have the same error massage "Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer."
But i can't get what you did to fix it please help me.THX

---

### Post by bodhi.zazen on 2007-11-16
> **Amin1_0_1 said:**
> Hi man
I have the same error massage "Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer."
But i can't get what you did to fix it please help me.THX

There are several options :

[http://doc.gwos.org/doku.php/doc:office:virtualbox#enable_usb_devices](http://doc.gwos.org/doku.php/doc:office:virtualbox#enable_usb_devices)

---

### Post by Amin1_0_1 on 2007-11-16
Thank you it works great!

---

### Post by rcdeacon on 2007-11-16
This link helped me get working. [https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/151585](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/151585)

---

### Post by CoryLuLu on 2008-04-17
link is dead for me. 

anyone relink?

---

### Post by caste381 on 2008-04-19
Here's the solution:
with root privileges, open the file /etc/init.d/mountdevsubfs.sh with a text editor and remove the following character ```
#
```
Save the file and open /etc/fstab (always while using root privileges).
At the eof, add this line: ```
none /proc/bus/usb usbfs devgid=1000,devmode=664 0 0
``` Now save, reboot your machine and you should be able to use your usb devices.
Hope it helps.
Greetings from Italy.

---

### Post by bodhi.zazen on 2008-04-19
The link has been moved to here :

[noparse]http://gaming.gwos.org/doku.php/udsf:virtualbox[/noparse]

---

### Post by seijling on 2008-10-27
Hey all, I just tried what caste381 said and it worked great!

As I found this a little confusing at the time, I only uncommented the following in my mountdevsubfs.sh file:

```
#
	# Magic to make /proc/bus/usb work
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
}
```

Thank you very much. 

Using Ubuntu 8.04
VirtualBox 2.04
Acer 8204 WLMi, T2500 dual core "yonah"

---

### Post by DoDoENT on 2008-11-05
> **seijling said:**
> Hey all, I just tried what caste381 said and it worked great!

As I found this a little confusing at the time, I only uncommented the following in my mountdevsubfs.sh file:

```
#
	# Magic to make /proc/bus/usb work
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
}
```

Thank you very much. 

Using Ubuntu 8.04
VirtualBox 2.04
Acer 8204 WLMi, T2500 dual core "yonah"

Hi! I'm using intrepid and have the same error, but the file /etc/init.d/mountdevsubfs.sh looks completely different. Any help would be appreciated.

---

### Post by rwap on 2008-11-06
> **DoDoENT said:**
> Hi! I'm using intrepid and have the same error, but the file /etc/init.d/mountdevsubfs.sh looks completely different. Any help would be appreciated.


Same Here.. I get this error, on 8.10


Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}
Callee: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}

I tried the /etc/init.d/mountdevsubfs.sh  file but it looks very different...

Help?

Thanks

---

### Post by DoDoENT on 2008-11-06
I think I've found a solution - still not tested.

My inspiration for solution is here: [http://wiki.ubuntuusers.de/VirtualBox/Benutzung#USB-Geraete-verwenden](http://wiki.ubuntuusers.de/VirtualBox/Benutzung#USB-Geraete-verwenden)

Since I'm not expert in german, it would be great if someone from Germany translated this guide. As much as I understood, we should add the following line into /etc/fstab:
usbfs	/proc/bus/usb	usbfs	devmode=664	0	0

and then "sudo mount usbfs"

After that, opening File->Preferences in VirtualBox doesn't show me an error anymore.

---

### Post by rwap on 2008-11-07
I found something similar,

> Only the first part regarding fstab is necessary in Intrepid, the rest only is needed in hardy.

In your fstab you need to put:

none /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0

being XXX the group ID of your user when you look under System-Administration-Users&Groups for the group usbusers

This worked for me, except I changed none to usbfs- whatever difference that makes.. Virtualbox now see my usb devices and they work in the virtual xp :)


My USB key works, but for some reason I get a BSOD on my canon I70 printer- still trying to figure that one.

My goal is to be able to sync my palm in xp via virtualbox- Hopefully.

Thanks!

---

### Post by rwap on 2008-11-07
I figured the BSOD out, I think I just needed to reboot- This is beautiful! I can even use my networked canon imageclass D660 that doesnt work in ubuntu :(  :)  

I hope my palm syncs.

EDIT-
I got it!

It worked right away with the cable but, It took a while for the bluetooth, I had problem with the com ports- there aren't any by default- so I loaded the BT drive in windows- I just used the MS version it automatically downloaded.. then go to the BT settings in windows and add the device then add incoming com ports in the BT settings- set palm's hotsync to those ports and boom. it works via bluetooth :)

I'm so happy. :) :)

---

### Post by salemboot on 2008-11-18
Maybe its just the version of the .deb binary.

I made a little script as domount no longer comes with ubuntu it would seem.

#!/bin/sh
#----------------------
mkdir -p /dev/bus/usb/.usbfs

mount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644

ln -s .usbfs/devices /dev/bus/usb/devices

mount --rbind /dev/bus/usb /proc/bus/usb



That gets rid of the error for 8.10 ibex.


l8r

---

### Post by zeddock on 2008-11-24
Can you please give a little more detail on this?  I am hesitant, as a newb, to use it as it doesn't say what error or what versions it impacts or works correctly on.

I just did a freash OS install on 8.10 64 bit.  Installed new virtualbox, which is supposed to have iPhone connection fixed.  It did not work.

I have to muddle in fstab, add myself and root to virtualboxusers group and finally turn 2.0 usb on and off and on.

Finally, the iPhone was throwing errors on the Unbuntu side... something to do about mounting and locking...  I unmounted in Ubuntu, unchecked the iPhone in XP virtual, then rechecked it.

That is NOT fixed.<laughs>

zeddock

---

