---
title: "Virtualbox running windows 2000 won't mount mp3 player or usb"
date: 2009-06-18
forum: Virtualisation
---

### Post by davidstri on 2009-06-18
I have an mp3 player, sony NWZ-A816, that ubuntu can't go into to, so I thought I would be able to mount it to a windows 2000 running in virutalbox. I got windows 2000 working perfectly, even the disc drive works in windows 2000, but my mp3 won't mount to it. I tried using this, [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB), from ubuntu documentation to mount it.
I added none /proc/bus/usb usbfs devgid=46,devmode=664 0 0 to the bottom of my /etc/fstab file, ran sudo mount -a, and logged in and out, but my mp3 player still wouldn't mount.
Has anyone accomplished mounting a usb to virtualbox with the free version?

---

### Post by boof1988 on 2009-06-18
According to...

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

...if you are using the OSE (open source edition) version, you wont have USB support.

If you are using the [PUEL version](http://www.virtualbox.org/wiki/VirtualBox_PUEL), you can have USB support.

I have had the same problem and had to use the [PUEL version](http://www.virtualbox.org/wiki/VirtualBox_PUEL) to enable USB support.

Hope this helps.

---

### Post by LightningCrash on 2009-06-18
Additionally, if you have an el cheapo USB hub, you can give the VM the whole tree starting with that hub. Means everything under the hub gets handed to the VM, even if you haven't manually added it.

---

### Post by boof1988 on 2009-06-18
> **LightningCrash said:**
> Additionally, if you have an el cheapo USB hub, you can give the VM the whole tree starting with that hub. Means everything under the hub gets handed to the VM, even if you haven't manually added it.

Can you give a link or something that explains or helps with this kind of setup?  I'd be interested in trying this out.

---

### Post by davidstri on 2009-06-19
I installed virtualbox puel and then installed windows 2000 on it. Everything was working perfectly the first time. I got my mp3 player to mount to windows 2000, transferred some songs from my share folder and then rebooted my real computer. After I rebooted, the usb's greyed out. They are there as an option, but I just can't click them, and when I wave my mouse over the usb option it says no usb mounted or something. Has anyone had this happen to them before?

---

### Post by boof1988 on 2009-06-19
> **davidstri said:**
> I installed virtualbox puel and then installed windows 2000 on it. Everything was working perfectly the first time. I got my mp3 player to mount to windows 2000, transferred some songs from my share folder and then rebooted my real computer. After I rebooted, the usb's greyed out. They are there as an option, but I just can't click them, and when I wave my mouse over the usb option it says no usb mounted or something. Has anyone had this happen to them before?

Have you added your *user* to the group *vboxusers*?  If you haven't done this yet (and need help), post back and we'll try to help more.  I you have already added your *user* to the *vboxusers* group, then I'm not sure what else to try.

According to [http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)...
> USB: if you are having trouble accessing USB devices in a guest, make sure that you are a member of the vboxusers system group.

---

### Post by davidstri on 2009-06-19
It's still not working even after I added myself to the group vboxusers. I guess I'll just do a clean reinstall of VB and let you know how it goes... Any idea how to do that? I tried using synaptic and the terminal but neither can remove it.

---

### Post by boof1988 on 2009-06-19
> **davidstri said:**
> It's still not working even after I added myself to the group vboxusers. I guess I'll just do a clean reinstall of VB and let you know how it goes... Any idea how to do that? I tried using synaptic and the terminal but neither can remove it.

I haven't done any of these, but they may have a little bit of useful information for you.  The first link is for a thread and the 2nd and 3rd ones are for individual posts, which might have some useful info.  For the single-post links, you can click on the red-font link in the upper right to get to the whole thread if you like (among many other methods).

[http://ubuntuforums.org/showthread.php?t=1075376](http://ubuntuforums.org/showthread.php?t=1075376)
[http://ubuntuforums.org/showpost.php?p=7055924&postcount=5](http://ubuntuforums.org/showpost.php?p=7055924&postcount=5)
<Edit: Third link removed>

---

### Post by davidstri on 2009-06-19
YESS! Turns out, all I had to do was fix my /etc/init.d/mountdevsubfs.sh file. I found this thread, [http://ubuntuforums.org/showthread.php?t=655071](http://ubuntuforums.org/showthread.php?t=655071), and just put the stuff from the thread into my /etc/init.d/mountdevsubfs.sh file, rebooted my computer and ,now, VB works!
Thanks for your help though :) guess I should've googled it a little bit more before I posted a thread.

---

