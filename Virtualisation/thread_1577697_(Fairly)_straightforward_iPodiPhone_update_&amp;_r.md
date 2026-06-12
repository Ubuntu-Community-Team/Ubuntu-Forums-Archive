---
title: "(Fairly) straightforward iPod/iPhone update &amp; restore in Virtualbox or VMWare"
date: 2010-09-19
forum: Virtualisation
---

### Post by ajhunt on 2010-09-19
Thanks to [Roo's blog]("http://www.lowtek.ca/roo/2009/itouch-firmware-upgrade-with-vmware/"), I believe I've found a reasonably straightforward way of updating or restoring an iPod/iPhone. My setup is Vbox 3.2.8 running Win 7 Starter and iTunes 10. A word of caution though - the steps below will temporarily disable your USB mouse if you have one (not a problem for me as I'm running a laptop). The problem relates to how the USB driver changes when in update/restore mode and here's how to temporarily fix that:

1. Create a file /etc/modprobe.d/blacklist-usb:

```
sudo gedit /etc/modprobe.d/blacklist-usb
```

and copy the following lines to the file:

blacklist snd_usb_audio
blacklist usbhid

2. Reload udev to refresh the configuration we just changed:

```
sudo service udev reload
```

3. Forcefully remove the kernel modules (ignoring the "all conf files need .conf..." message):

```
sudo /sbin/modprobe -r snd_usb_audio
sudo /sbin/modprobe -r usbhid
```

4. Perform the upgrade under VBox/VMWare. I understand this works flawlessly in VMWare but you'll need to keep activating the iPod entry in Devices - USB for VBox. This will disconnect periodically through the upgrade/restore process - essentially keep an eye on your iDevice and each time the screen changes check that the iDevice is ticked in Device - USB. If not, click it to be active. This will ensure that iTunes maintains contact with your device to complete the process. If you miss one then eventually you'll get the iTunes error because it's timed out. Just try again and keep a closer eye (although if you were preforming an upgrade you'll find that you need to do a full restore if you timeout). I had to reactivate the USB connection 3 times to upgrade my iPod Touch.

Hopefully you've successfully complete the upgrade/restore so you need to perform these steps to undo the changes made earlier:

5. Run this from the terminal:

```
sudo rm /etc/modprobe.d/blacklist-usb
sudo service udev reload
```

Job done!

---

### Post by .nedberg on 2010-09-19
I am using VirtualBox to update/restore my iPhone. Never did anything like this and no problem with usb mouse/keyboard.

I just created a usb-filter for my iPhone (I filter for vendor ID: 05ac). My iPhone (and other iDevices) are automaticaly connected to the virtual machine. It is reconnected when the device reboots, so there is never a problem!

---

### Post by ajhunt on 2010-09-19
.nedburg,

Lucky you! I've not had any problems syncing but updating/restoring has always been a non-starter and there are hundreds of posts out there to prove it! I too have a usb filter with the same vendor id but not found this resolves the upgrade/restore problem. I wanted to update my touch to ios 4.1 and tried without any modifications to see if anything had changed since I last tried and it hadn't - the iPod was left in restore mode with Vbox unable to reload the driver. Hence my search for a solution.

Still if you've had no problems then all power to you!

BTW - the USB mouse reference in the post is a temporary condition resulting from the resolution steps (disabling of usbhid).

I have retained the usb filter for the iPod in recovery mode and have compared the 2. Without the steps in the original post, Vbox does not recognise the iPod in recovery mode from which the recovery mode filter was created.

Recovery Mode:

Vendor ID: 05ac
Product ID: 1281
Revision: 0000
Serial No: CPID:8720 CPRV:13 CPFM:03 SCEP:04 BDID:00 ECID:000001EA8615AD8C IBFL:01 SRNM:[9C002EJ975J]

Normal Mode:

Vendor ID: 05ac
Product ID: 1299
Revision: 0001
Serial No: ada4884a5193c5b3782d7460502366f35d68faf0

---

### Post by nicolasbock on 2010-09-21
.nedberg, could you explain in more detail how you set up such a filter? I presume you are using udev and some clever rule?

Thanks

---

### Post by .nedberg on 2010-09-21
No, it is in the settings for the virtual machine. 

I shut down the machine and connect my iPhone. Then I open settings and create a new USB filter. I leave everything empty except vendor id. 

This will connect everything made by Apple to this vm. Also when the iPhone is in recovery mode. 

I am not by my machine right now. If you need more help, please just post back!

---

### Post by nicolasbock on 2010-09-21
Thanks, I see. I am using vmware, but I have not noticed a filter option like the one you describe. What struck me was ajunt's post and his trick of unloading the usb kernel modules. I have tried that trick and unfortunately it's not just my mouse that goes missing when I unload usbhid. It's also the keyboard, and I need to connect and old PS/2 keyboard to be able to do anything. This is pretty annoying, so I was hoping that by using a udev rule I could avoid having to unload anything. I would simply tell udev to not worry about the iPod.

---

### Post by nicolasbock on 2010-09-21
I found this alleged solution:

[http://teknofire.net/articles/2009/01/08/using-linux-and-vmware-to-update-iphone-firmware/](http://teknofire.net/articles/2009/01/08/using-linux-and-vmware-to-update-iphone-firmware/)

which unfortunately has not worked out for me so far. I have not been able to figure out how to get the initramfs to apply the usbhid options. I figured though that this trick might be helpful to others, since it seems to imply that you don't have to unload usbhid but rather give it some options to prevent it from binding to your iPod.

---

### Post by jaalburquerque on 2010-10-28
This link also seems relevant to finding a solution which does not require unloading the usbhid module:
[http://nick.zoic.org/2010/02/24/iphone-itunes-windows-xp-virtualbox-ubuntu/](http://nick.zoic.org/2010/02/24/iphone-itunes-windows-xp-virtualbox-ubuntu/)

---

### Post by Heubel on 2012-01-20
I found a super simple solution based on this post:

[http://nick.zoic.org/art/apple/itunes-virtualbox.html](http://nick.zoic.org/art/apple/itunes-virtualbox.html)

As I they states, each time iPad recovers, it gives a new ID to the USB, so we can easily create a filter in Virtualbox USB devices and leave the ID field blank in order it will not be specific anymore. The steps are:

1) Plugin your iPad into USB;
2) Access your VM's settings and select USB;
3) Select the icon with USB (plus signal) "Add Filter From Device (Alt+Ins) and select your Apple connected device;
4) Click in the icon below to edit your new USB filter;
5) Delete all the fields (just in case) besides the first one "Name:";
6) Start your Virtual Machine, your iTunes might pop-up and ask for the recovery process;
7) Keep an eye on your USB status and quickly reconnect your iPad when it drops (I needed to make it 2 times);

Happy recovering!

---

### Post by mcgrete on 2012-08-16
Heubel and others -

Thank you for the feedback and advice!  Expanding on this for recent experience with Virtualbox 4.1.16 and 4.1.18 and viewing some related posts...

My original system:

Virtualbox 4.1.18
Host Ubuntu 10.04LTS(64bit)
Guest Windows7(64bit)

I had similar problems with failed attempts to 'update' an ipod touch 4(G) OS in iTunes 10.6.  I tried on a 2nd (different) computer with Linux host (Ubuntu 10.04LTS) and WindowsXP(32bit) guest (Virtualbox 4.1.16)--> had the same problem.  The original error code was 1602 on the 1st PC, then it remained 1604 on the 1st PC and 2nd PC.  

Apple support indicated it was a problem with security software, but did so without querying about my system details (my support was expired, and they gave me the website that I had already read).  

I tried to resolve on a 3rd computer - straight WindowsXP32bit; it failed to restore on this as well (iTunes 10.6).  Error code 1604.  This was quite disappointing, as I thought that this would have resolved the issue.  I did not try pressing power and home buttons simultaneously or similar after this failure on the 3rd PC - perhaps doing so and trying on Windows host would have worked...not sure.

I noticed that the USB connection seemed to drop-off on the Virtualbox attempts (obviously, this did not apply to the 3rd PC with XP host and no Vbox).  That lead me to finding this post and tip, which solved my problem - namely, delete all text in the Virtualbox Manager GUI's USB filter for the ipod device, with the exception of the Manufacturer.  I observed that in the 'restore' or 'recovery' mode, the name of the ipod device is different than before the 'upgrade' attempt; the name also changes after the 'restore' reaches a certain stage.  Hence, if the filter is not set to accept all Manufacturers that are 'Apple Inc.' the guest OS drops the ipod device.  This is different than issues some may have had with synching - as I don't believe the name changes in such a case.

What I found troublesome, was that even on a straight XP host (no Vbox) that I was unable to 'restore' or 'recover' from the botched 'upgrade' with an improper filter setting.  For me, it was easy to modify the filter and attempt the 'restore' from my original guest (W7); not sure if it was necessary to 'restore' on the original OS that resulted in my 'crashed' and presumed 'bricked' ipod, but it worked.

Note, I also found a post on a related issue, where the screen resolution of the guest OS appears to impact speed of iTunes during synch or other operations.  [https://forums.virtualbox.org/viewtopic.php?f=7&t=18715&start=0](https://forums.virtualbox.org/viewtopic.php?f=7&t=18715&start=0)
Not sure it matters, but I changed my screen resolution to 800x600 for the above 'restore'.


Thanks

---

