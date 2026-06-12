---
title: "Hmmm: Virtualbox &amp; Ipod + Windows stuff"
date: 2009-08-14
forum: Virtualisation
---

### Post by prickee on 2009-08-14
Info: I have a triple boot, XP, Vista, & Ubuntu Jaunty. I'm pretty much in Ubuntu all of the time and only go back to Windows is 
1) the lady needs to or 
2) I need to sync some apps/music to my Ipod Touch

Well now that I have Vista installed in Virtualbox do I really need to reboot to windows?  Are there any limitation?  My thinking is if I install iTunes can I do my iPod stuff within linux?  Of course all of this is without a lot of knowledge on SunVB..

Thnx n advance...

---

### Post by jocampo on 2009-08-14
> **prickee said:**
> Info: I have a triple boot, XP, Vista, & Ubuntu Jaunty. I'm pretty much in Ubuntu all of the time and only go back to Windows is 
1) the lady needs to or 
2) I need to sync some apps/music to my Ipod Touch

Well now that I have Vista installed in Virtualbox do I really need to reboot to windows?  Are there any limitation?  My thinking is if I install iTunes can I do my iPod stuff within linux?  Of course all of this is without a lot of knowledge on SunVB..

Thnx n advance...

well...I do not use iTunes :-) ... so, can't tell exactly its behaviour. But besides performance and graphic acceleration (something I guess you don't need on this case) the virtual machine will act similar. Now...if you need to plug your iPod into your host so, in turn, the VirtualMachine can get or download the iPod/Music info into your iPod... in theory, should work. VirtualBox supports USB using "virtual USB controller".

I would give VirtualBox a chance... yes...

---

### Post by theGlitch on 2009-08-14
yup that's exactly what I do (but with XP). what you need to make sure you do is setup USB listeners in the VB before you start it.

Click the settings button and you'll find a tab for USB. plug in your iPod (and whatever else you want the VB to recognize) then on the right you'll see something that lets you create a new USB connection. Click and select the device(s) you have plugged in. Start your virtual machine and it should work. If not you'll need to add the following line to the bottom of your fstab:

> Add this line to the bottom of /etc/fstab, replace the devgid number with your devgid:
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

[http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu](http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu)

---

### Post by Grenage on 2009-08-14
Can you not use Amarok or the like instead?

---

