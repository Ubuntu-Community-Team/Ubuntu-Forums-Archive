---
title: "[SOLVED] Anyone Using Sun's Virtual Box?"
date: 2008-09-07
forum: Virtualisation
---

### Post by Killtodie on 2008-09-07
I have XP Pro running on Virtual Box.
Everything works fine cept USB. I can mount the floppy, CDROM drive but not any USB devices. I activated the USB devices and it sees it in device manager but when I try to mount one it says no usb devices detected.

Anyone know what I can do?

---

### Post by Killtodie on 2008-09-07
anyone at all?

---

### Post by Whiffle on 2008-09-07
Which version of Virtualbox?  The OSE version from the ubuntu repository, or the one off the Virtualbox website?


Also, did you add filters for each of the usb devices you want?

---

### Post by Killtodie on 2008-09-07
of the website

i did select the usb device in settings.

---

### Post by bodhi.zazen on 2008-09-07
> **Killtodie said:**
> of the website

i did select the usb device in settings.

You need to edit a system file :

[http://ubuntuforums.org/showthread.php?t=393582&highlight=USB+virtualbox](http://ubuntuforums.org/showthread.php?t=393582&highlight=USB+virtualbox)

---

### Post by Victormd on 2008-09-07
Also, you should install the guest additions. On your virtual machine menu, under DEVICES>INSTALL GUEST ADDITIONS.

---

### Post by Killtodie on 2008-09-07
my usb device list looks completely different

and I installed the guest addition

also, how do i edit as root?

---

### Post by Victormd on 2008-09-07
> **Killtodie said:**
> how do i edit as root?

in the terminal, use "sudo" before any command, i.e.,
```
sudo gedit idono.txt
```

In the case of the link you're probably trying to edit:
```
sudo gedit /etc/udev/rules.d/40-permissions.rules
```

Even though you downloaded from the site, there are 2 versions, the OSE and PUEL. If you downloaded the OSE version, you won't be able to get USB support. You can only get it from the PUEL version (someone please correct me if this has changed)...

I have the PUEL version installed + guest additions and don't remember editing anything. I installed it a while back though and at the time I was learning and messing around with a bunch of things at the same time so I may have edited something, but can't really remember. As far as I remember, it was very straight forward...

---

### Post by Killtodie on 2008-09-07
I got the Hardy version here
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

my list looks different. mode=0660 and its way under the subsystem

---

### Post by Victormd on 2008-09-07
Ok, so you have the PUEL version...

This is what my 40-permissions.rules looks like:
> # USB serial converters
SUBSYSTEM=="usb_device", GOTO="usb_serial_start"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GOTO="usb_serial_start"
GOTO="usb_serial_end"
LABEL="usb_serial_start"
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", \
					MODE="0660", GROUP="dialout"
LABEL="usb_serial_end"


---

### Post by Victormd on 2008-09-07
Have you looked at this [link]("http://www.virtualbox.org/wiki/User_FAQ")?
> USB on Ubuntu/Gutsy: Ubuntu removed support for /proc/bus/usb/*. We will address this issue in the future. Until this, edit the script `/etc/init.d/mountdevsubfs.sh and activate the four lines around line 40 (Magic to make /proc/bus/usb work). Then execute 
/etc/init.d/mountdevsubfs.sh start
From now on, there should be a directory /proc/bus/usb/ and the device entries below should be accessible by any user.

After reading a bit, this is the only thing I did. This is what my mountdevsubfs.sh looks like:
> 	#
	# Magic to make /proc/bus/usb work
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb

---

### Post by Killtodie on 2008-09-07
```
# USB serial converters
SUBSYSTEM=="usb_device", GOTO="usb_serial_start"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GOTO="usb_serial_start"
GOTO="usb_serial_end"
LABEL="usb_serial_start"
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", \
					MODE="0660", GROUP="dialout"
LABEL="usb_serial_end"
```

mine

---

### Post by Victormd on 2008-09-07
Don't worry about editing the 40-permissions.rule for now. Try the link I posted earlier and see how that works... Open a terminal and type
```
sudo gedit /etc/init.d/mountdevsubfs.sh
```
edit the lines per the link to the virtualbox FAQ (or just check the extracted portion I posted) then
```
/etc/init.d/mountdevsubfs.sh start
```
and that should do the trick...

---

### Post by Killtodie on 2008-09-07
mine alreayd looks just like yours


```

	#
	# Magic to make /proc/bus/usb work
	#
	#mkdir -p /dev/bus/usb/.usbfs
	#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	#ln -s .usbfs/devices /dev/bus/usb/devices
	#mount --rbind /dev/bus/usb /proc/bus/usb
```

---

### Post by Victormd on 2008-09-07
but you'll see that yours is commented (has # before the lines - this means that the script does not execute these commands). Remove the # before the last 4 lines:
> #
	# Magic to make /proc/bus/usb work
	#
	**[COLOR="Red"]#[/COLOR]**mkdir -p /dev/bus/usb/.usbfs
	**[COLOR="Red"]#[/COLOR]**domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	**[COLOR="Red"]#[/COLOR]**ln -s .usbfs/devices /dev/bus/usb/devices
	**[COLOR="Red"]#[/COLOR]**mount --rbind /dev/bus/usb /proc/bus/usb
then run the script.

---

### Post by Killtodie on 2008-09-07
Thanks, that did the trick, after a restart

I can now select the USB device but it says "Not permitted to open the USB device, check usbfs options"

---

### Post by Victormd on 2008-09-07
> **Killtodie said:**
> "Not permitted to open the USB device, check usbfs options"

When does it say this? From the virtualbox machine or virtualbox settings?

---

### Post by Killtodie on 2008-09-07
eh, here, take a look


[http://img355.imageshack.us/my.php?image=xpos2.jpg](http://img355.imageshack.us/my.php?image=xpos2.jpg)

does the same thing in 2000

---

### Post by Victormd on 2008-09-07
I think I know what the problem is. I'm just checking to make sure. In the mean time, go to SYSTEM>ADMINSTRATION>USERS AND GROUPS, unlock then MANAGE GROUPS and scroll down to VBOXUSERS, select it and click on PROPERTIES and see if your name is listed (and checked) under group members. If not, then check it, OK, Close and restart your virtual machine.

---

### Post by Victormd on 2008-09-07
The above should take care of any virtualbox permission issue. If not, open a terminal and type:
```
 sudo gedit /etc/group
```
and look for the line in bold (below) and you'll need the number in RED:
> polkituser: x:122:
haldaemon: x:123:
victor: x:1000:
**vboxusers: x:[COLOR="Red"]124[/COLOR]:victor**
winbindd_priv: x:125:
sambashare: x:126:victor,root
userftp: x:1001:

Then, check to see if that matches the number in your fstab
```
sudo gedit /etc/fstab
```
> ## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs **[COLOR="#ff0000"]devgid=124[/COLOR]**,devmode=664 0 0
They should match. If not, change your fstab and NOW it should work... :)

---

### Post by Killtodie on 2008-09-07
after a restart it no longer gives me the msg but the device is grayed out

---

### Post by Killtodie on 2008-09-07
fstab doesnt have that argument.

---

### Post by Victormd on 2008-09-07
Did you check the group settings under SYSTEM>ADMINISTRATION?

---

### Post by Killtodie on 2008-09-07
Yes, did check the name
here is what it looks like, doesnt even have USB anywhere in it

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=eee11c42-9c9f-4b9c-9221-faff24240415 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=cf83c9a0-9a6f-4913-92a9-08b6e2f6a3e4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by Victormd on 2008-09-07
> **Killtodie said:**
> fstab doesnt have that argument.

Then you can add it, simply copy from my quote and change the number after devgid to match yours.

Sorry if this is taking longer than we'd like, but like I mentioned earlier, it's been a while since I did this so I don't remember all the issues I had...

---

### Post by Killtodie on 2008-09-07
where do I add it to? under what line

---

### Post by Victormd on 2008-09-07
Just add to the end of the file, like this:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=eee11c42-9c9f-4b9c-9221-faff24240415 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=cf83c9a0-9a6f-4913-92a9-08b6e2f6a3e4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[B]## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=[COLOR="Red"]124[/COLOR],devmode=664 0 0[/B]


---

### Post by Killtodie on 2008-09-07
DUDE!!! AWESOME!
That worked!

You're amazing, Thanks!

---

### Post by Victormd on 2008-09-07
Ok. Hope this does the trick. Let me know if it doesn't. BTW, after editing your fstab, I believe you'll need to restart ubuntu for it to take effect.

---

### Post by Killtodie on 2008-09-07
Yes, it works. see above :D

---

### Post by Victormd on 2008-09-07
Good to know! :)

Don't forget to mark the thread as solved under **Thread Tools**...

---

