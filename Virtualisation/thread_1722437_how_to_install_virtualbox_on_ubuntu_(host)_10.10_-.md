---
title: "how to: install virtualbox on ubuntu (host) 10.10 - windows xp (guest) &amp; share files"
date: 2011-04-05
forum: Virtualisation
---

### Post by Claus7 on 2011-04-05
Hello,

I had faced a problem with office in wine, due to an update and due to time constraints I had to fix this asap. What I came out with was to give a try to virtualbox. 

I wanted just: 1) to install virtual box on ubu (host-main operating system)
2) to install windows on it (inside virtual box, guest operating system)
3) to install office
4) to be able to share files between ubu and *dose with easiness...

So, this took place on ubu maverick. This how to is for just a quick reference and has the type of someone just keeping notes. Hope it will give an easy hand...

**1) Installation of virtualbox**

Open synaptic and type in the search box: virtualbox
then choose: virtualbox-ose, virtualbox-ose-qt, virtualbox-ose-dkms and virtualbox-guest-additions

**2)Configuration of VB**
Go to Applications->Accessories->Virtualbox OSE
and click it.

the options you will get are pretty straightforward. Just some notes. I chose 600MB RAM, as 512 are the recommended for xp. 10GB are more than adequate for minor things (this is the space that the virtual op will occupy). Other say that 5 are ok as well. About image type (dynamic or static) choose what you think appropriate. I chose (I think) dynamic...

**3) Installation of xp**
In general, you put your xp cd inside your cdrom tray and the installation goes as normal. Yet, I faced the problem of: could not read from the boot medium

and the system halted. 
Solution: a) Go to machine->settings->system and fix the order of the booting devices.
b) this is tricky: you have to have ticked the box near the name of your cdrom drive (while you are running the session of xp, in virtual box, which means that you have selected your virtual machine to run) in order for the installation to proceed. The place is under Devices in the new window. Accidentally I unticked it and I was having this message.

**4) Installation of office** 
Just put the cd inside your tray, after the installation of xp, and go to start->mycomputer and install the program as usual.

**5) share folders**
In ubuntu, just create a folder wherever you like. Then open virtualbox and go to Settings->Shared folders and on the right choose the green (+). Browse your ubuntu machine and find the folder you just created. Do not check the read-only option, yet check the recommended one. 

Then start xp inside vb and choose Devices->Install guest additions. (There you will be prompted to install some drivers that might put your computer at rick. I chose yes to all and in order to find the folder in xp, inside vb so as to place files I went to:
start->my computer->internet places->and you will find the folder in question. This is were you place files from your xp in order to see them in ubuntu.

Hope it gave some clues, quick and nice. The bad thing is that some minor details are missing cause I did not keep notes while doing so. 

Regards!

---

### Post by Claus7 on 2011-04-05
Hello,

In order to fix the size of your virtualbox window, check out the resolution options of your xp session (right click on desktop -> properties and change resolution). This might help you to save a lot of time from troubleshooting...

Regards!

---

### Post by Claus7 on 2011-04-18
Hello,

you can bypass this by doing the smart solution described here:
[http://ubuntuforums.org/showpost.php?p=8406158&postcount=4](http://ubuntuforums.org/showpost.php?p=8406158&postcount=4)

Regards!

---

### Post by Claus7 on 2012-03-10
Hello,

in the previous configuration I wanted to test usb support because I wanted to connect a usb device under windows environment. The version of VB I was using was 3.2.8 and no matter what I tried (ok not so many things, mostly tampering with users and groups) I was not able to succeed.

So I took a look about virtual box puel edition and the website:
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
in order to download the extension pack for usb support.

Steps:
[LIST=1]
[*]from ubuntu tweak enabling the ppa repository for VB
[*]updating without risking the installation already done and the corresponding data
[*]downloading the extension pack from the aforementioned website
[*]installing it from the settings of virtual box (do not try to install it by clicking on it, it did not work for me)
[*]and you are set
[/LIST]

Notes: 
[LIST]
[*]the new version of VB at the time is 4.1.8
[*]the same applies for the extension pack
[*]after you boot windows (guest) you will see on the low right end corner a message about updating VM Virtualbox guest additions. In order to do that go to:
devices (on top of the window with the guest os inside) and click install guest additions
[/LIST]

The whole procedure worked with usb device. Also you will notice a new icon in the bottom bar of your guest os, along with a usb option on the right (manager window), while you have to load your guest os (do not forget from there to activate it).

Kind regards!

---

### Post by Claus7 on 2012-11-24
Hello,

> **Claus7 said:**
> Hello,

...
The whole procedure worked with usb device. Also you will notice a new icon in the bottom bar of your guest os, along with a usb option on the right (manager window), while you have to load your guest os (do not forget from there to activate it).

Kind regards!

in order to activate any device go to the icon of usb as described above, do right click and tick the device you want to be visible from your guest OS.

Regards!

---

### Post by wildmanne39 on 2012-11-25
Old thread closed.

---

