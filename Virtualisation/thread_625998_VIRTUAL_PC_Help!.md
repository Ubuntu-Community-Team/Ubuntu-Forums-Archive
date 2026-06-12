---
title: "VIRTUAL PC Help!"
date: 2007-11-28
forum: Virtualisation
---

### Post by illbashu on 2007-11-28
ok, i got VM sever set up and i installed windows Pro. xp. the problem is it wont  recognize usb drives... :/ any help will be greatly appreciated!!!

---

### Post by pebo on 2007-11-28
Have you set up VM tools?

---

### Post by illbashu on 2007-11-28
yes.... it still wont see the usb items like my sony psp slim... i checked on vm on the tool bar and checked usb and vm itself doesn't see the usb  item..

yes, my psp is usb mode....

---

### Post by -grubby on 2007-11-28
tried virtualbox?
EDIT: nevermin

---

### Post by fjgaude on 2007-11-28
> **illbashu said:**
> ok, i got VM sever set up and i installed windows Pro. xp. the problem is it wont  recognize usb drives... :/ any help will be greatly appreciated!!!

See this post, Msg #4, for solution:

[http://ubuntuforums.org/showthread.php?t=626062](http://ubuntuforums.org/showthread.php?t=626062)

Good luck. VMware Server is rock solid with everything that it supports.

---

### Post by illbashu on 2007-11-28
ya, i dont get what he means by "Lines 42-45 get uncommented, starting with #mkdir -p /dev/bus/usb/.usbfs."

---

### Post by fjgaude on 2007-11-28
See msg #7 of post:

[http://ubuntuforums.org/showthread.php?t=626118&highlight=Vmware](http://ubuntuforums.org/showthread.php?t=626118&highlight=Vmware)

Keep asking questions if this doesn't do it for you.

---

### Post by illbashu on 2007-11-28
You remove the "#" mark to uncomment. You will have to do it with the superuser command "sudo". Count down the lines in the file until you get to "mkdir -p " and delete the #s in front of each of the four lines.

.. i dont get it...

this is how mine looks 

#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

---

### Post by ewr2san on 2007-11-28
#commented line
uncommented line
#still a commented line
still an uncommented line


So to uncomment those lines you would need to edit them and remove the leading # symbols.

With the exception of #! on the first line of a file, # is a pretty nearly universal unix comment token.

---

### Post by illbashu on 2007-11-28
ok, i made it like this

```
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb
```

it still wont find the usbs devices... :( took off the #s

---

### Post by illbashu on 2007-11-29
bump, any one elce have any help?

---

### Post by illbashu on 2007-11-30
can someone help me!@:mad:

---

### Post by patagonik on 2007-12-06
Hy there!

I did uncomment those lines as well and nothing happened. VMware does not recognize my usb devices.

Could be nice to have some help here!!!

Mny many thanks!

---

### Post by patagonik on 2007-12-06
Ok, got it!

Maybe you've already tried but if you power off the guest machine, you are allowed to add devices to it. **Notice that i've previously followed all the suggestions posted above!!!**

With WinXP off, go to **VM->Settings** and you'll see that you are allowed to **ADD devices**. Select USB Controller and it will then appear listed above.

Power on your Guest system, go to **VM->Removable Device->USB Devices** and you'll have them all listed there. As it was commented before, they will disappear from Linux, but will be recognized on WinXP... that's it!

Hope that this will help someone.

---

### Post by michaelsharman on 2009-01-04
@patagonik - thanks for your tip, got me going on 8.10 when nothing else would!

---

