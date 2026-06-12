---
title: "Unable to access USB devices in Virtualbox"
date: 2008-06-09
forum: Virtualisation
---

### Post by portach king on 2008-06-09
Hi Guys,
Im currently running Virtualbox 1.6.2 (But I had the exact same problem with 1.5.6) on Hardy. I've followed all the guides to get usb working and while as far as I can tell I've done nothing wrong I can't seem to be able to activate them within Windows. 
In the settings I checked USB devices and that was no problem. When I run the operating system I can see a list of all my usb devices plugged in when I right click on the usb icon or select USB from the Devices menu, but they are all greyed out and won't let me select them. If I leave the mouse over them it reads "Status: Unavailable".

Any ideas as to what's wrong? As I said I had the same trouble with 1.5.6.
Cheers in advance.

---

### Post by bmwman on 2008-06-09
Check out this guide. I had problems with mine too but I got it working following these instructions. I still prefer VMware but mine doesn't work right now so I'm stuck with Vbox :(.

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

Hope it helps. BTW you need to reboot after doing all the changes.

---

### Post by portach king on 2008-06-09
Hey bmwman,
Thanks for your help, but that didnt help unfortunatly. I already followed that guide, even the second part.
So the problem still persists

---

### Post by bmwman on 2008-06-09
I'm using Vbox 1.6.2 and wasn't able to use the USBs. After I did the changes, including the second part i could only use my printer. The rest was showing as  unavailable. But after I rebooted everyhting worked fine for me.

---

### Post by portach king on 2008-06-09
I've rebooted twice now. no change.

---

### Post by bmwman on 2008-06-09
Well that's why I prever VMware. It's soooo much better. Everything works without any tweaks. You can use bridged network (pain in the rear to set up in Virutal Box), USB doesn't need any configuration either. You can also create a virtual mashine off of your physical system and don't have to reinstall a whole new Windows to use inside of Ubuntu.

---

### Post by portach king on 2008-06-09
you mean i can access files directly off my ubuntu filesystem with vmware?

---

### Post by bmwman on 2008-06-09
Yes you can. You just share the folder from the virtual machine settings and then you can map it to the Windows as network drive or I have my MyDocuments mapped to my Home folder in Ubuntu. Also you can drag and drop files (copy/paste) from Ubuntu to VMware which you cannot do with Vbox.

---

### Post by portach king on 2008-06-09
OK, hmmm sounds tempting but I'm more eager to just get virtualbox running. If I can't I'll consider installing VMware, but I'd not sit through another Windows install and setup.

---

### Post by portach king on 2008-06-10
I'm still having the same issue and would hugely appreciate any advice.

---

### Post by hopelessone on 2008-06-10
I'm sorry i don't have the link handy but i did read that VirtualBox Binary does not support USB and the OpenSource one did if you compiled it yourself...How did you install it?

That's why i went KVM since it's going/already been integrated into the kernel..

---

### Post by portach king on 2008-06-10
I installed the .deb file for hardy -iX86 from the virtualbox website. 
What does KVM stand for?

---

### Post by Victormd on 2008-06-10
Are you using the virtual box from the repos? To get full-functioning virtual box, don't use the OSE version, install from [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI"). To get USB working is straight forward, you just have to install the extra addons from the virtual machine menu.

---

### Post by Victormd on 2008-06-10
> **hopelessone said:**
> I'm sorry i don't have the link handy but i did read that VirtualBox Binary does not support USB and the OpenSource one did if you compiled it yourself...How did you install it?

That's why i went KVM since it's going/already been integrated into the kernel..

There are two versions of virtual box available from the virtualbox.org website. One is OSE (also available in the repos) which does not support USB and the other, freeware, that does support USB...

---

### Post by hopelessone on 2008-06-10
Thanks Victormd...thats what i was trying to say.. :)

Here's the link [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

PUEL (Personal Use & Evaluation License) Version
While this is non-free and only for personal use, it adds USB support and virtual Remote Desktop support. Without this, your USB devices can't be used in the guest OS and you cannot use Windows Remote Desktop as a server in the guest OS.

---

### Post by portach king on 2008-06-10
I'm not running the open source edition. I'm going to try a complete removal and start over again I think.

---

### Post by portach king on 2008-06-10
Did a complete removal, reinstalled the Non-Open Source version again and I still have the same problem.

---

### Post by Victormd on 2008-06-10
> **portach king said:**
> Did a complete removal, reinstalled the Non-Open Source version again and I still have the same problem.

Did you install the addons? Without the addons you won't be able to access your USB.

---

### Post by Victormd on 2008-06-10
> **hopelessone said:**
> Thanks Victormd...thats what i was trying to say.. :)

Here's the link [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

PUEL (Personal Use & Evaluation License) Version
While this is non-free and only for personal use, it adds USB support and virtual Remote Desktop support. Without this, your USB devices can't be used in the guest OS and you cannot use Windows Remote Desktop as a server in the guest OS.

The PUEL is free for personal use... :)

---

### Post by portach king on 2008-06-10
> **Victormd said:**
> Did you install the addons? Without the addons you won't be able to access your USB.
 
You mean guest additions? If yes, then I have installed the addons. If not, please indulge!

---

### Post by chandra on 2008-06-10
This is for the PUEL VB 1.60 deb.

Follow the steps outlined at:

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

and at:

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

Also, I found that [COLOR="Red"]not[/COLOR] enabling the USB 2.0 Controller in "Settings" allowed reliable recognition of USB devices.

HTH.

Chandra

---

### Post by Victormd on 2008-06-10
Yes, the guest addons...
Have you configured the virtual machine to accept serial connections (under the machine settings on the virtualbox startup window)?

I'm not at home so I can't lookup the proper names... when I get home, I'll check the proper paths and terminology for you...

---

### Post by chandra on 2008-06-10
Or better still, follow these guidelines:

[http://ubuntuforums.org/showthread.php?t=817523](http://ubuntuforums.org/showthread.php?t=817523)

---

### Post by Victormd on 2008-06-10
When you open Virtualbox, select the virtual machine you wish to setup and click on settings, go to USB and mark Enable USB Controller. USB 2.0 controller messes up my virtual machine so I don't use it...
Let me know if this works...

---

### Post by portach king on 2008-06-10
Thanks Victormd, USB was indeed selected and I had already trried it with bothe USB 2.0 option both on and off, it made no difference.
I've already looked that post too Chandra, thanks though!

---

### Post by Victormd on 2008-06-10
Just out of curiosity, what USB devices are you trying to access? You mentioned that your printer worked so I'm guessing your USB connection is(was) working as well but not recognizing the devices...

---

### Post by portach king on 2008-06-10
Actually I never mentioned my printer. I'm trying to access my external HD, it has files on it I wish to edit using a piece of windows software (that won't work in Wine). I'm including an image, perhaps it explains things a little better. as you can, I simply cannot select any USB devices even though I've edited mountdevsubfs, etc., enabled USB in the settings and installed Guest Partitions...
It's very confusing. I remember having no problem getting it to work on Gutsy.

[IMG]http://img178.imageshack.us/img178/4600/screenshotdonalxprunninyv0.png[/IMG]

---

### Post by Victormd on 2008-06-10
Sorry, it was **bmwman** who mentioned his printer...
Here are a few questions (mostly dumb but often overlooked)...
The last time you used your external HD, did you properly shut down windows?
Does Ubuntu mount your external HD? If so, for now, you can share your external HD (using shared folders), which will grant you access to your files. If not, then most likely, the last time you used your external drive, it was not "safely removed" under windows...

I'm back at work (windows) so when I get back home, I'll check somethings and we can try to solve this...

---

### Post by portach king on 2008-06-10
Hey Victormd, your really amazing. Thanks for all your help. To answer your questions.
Honestly I have no idea what state I shut down windows last time I used the external HD, it was at least two months ago and would have been with Virtualbox running on Gutsy. It still should allow me to try an mount it though, even if there was an error. Maybe I'm wrong.
Ubuntu has no problem reading/writing with the external HD.
Will share folders allow me to edit and save the files though. I far as I remember files are unwritable on Guest operating systems using virtualbox which wouldn't do me much good.
Thanks again to everyone offering any kind of help, I hope that with your help I can get to the bottom of this puzzling situation.

---

### Post by Victormd on 2008-06-10
If you can read it in Ubuntu, then it was safely removed or shut down properly (otherwise, it wouldn't even mount). I should be heading home in a while so I'll be able to give you more assistance.

Sharing should let you read/write with not problems, but there is an option that you have to setup (should be straight forward).

Be back in a bit...

---

### Post by Victormd on 2008-06-10
Ok, now I really don't know what to say. It's been a while since I've used my Virtual windows, and before, it was working just fine and I don't know if it's because of all the updates, I can't get it to work anymore... In my case, it doesn't even show up under the Devices menu, it simply says "no available devices" (even though it shows up in ubuntu)...

Portach king, using the "Shared Folders" does allow you to read and write. You have to setup your shared folders granting full access, otherwise, it's read-only (see attachment)... Hopefully that will get you through until we sort this virtualbox-usb situation...

---

### Post by portach king on 2008-06-10
Wow. OK, well if nothing else I'm glad I was able to shine a light onto a serious problem. Thanks again Victormd, I hope this can be resolved.

---

### Post by Victormd on 2008-06-10
I followed [this guide ]("http://www.ubuntu-unleashed.com/2008...rdy-heron.html")and got it to work with my external HD...

You said you've tried it already, but I'd give it a second step-by-step to be sure.

Did you get file sharing to work?

---

### Post by portach king on 2008-06-11
Hey Virctormd, I followed that guide again. I made a mistake the first time when following the second part of the guide (I didn't quite understand what was meant with the bold number), but I followed it more carefully this morning and it now works. Sorry for all the trouble, and thanks for your amazing help.

---

### Post by Victormd on 2008-06-11
No problem!
Just an off-topic question, were you able to get your sound to work with virtualbox?

---

### Post by portach king on 2008-06-11
Yes, I just selected pulseaudio. Works fine! :)

---

### Post by Victormd on 2008-06-13
Ok, just thought I'd ask... :)

Have fun

---

