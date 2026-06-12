---
title: "Tomtom GPS USB Port"
date: 2010-11-17
forum: Wine
---

### Post by JohnPta on 2010-11-17
The software for a tomtom GPS installs perfectly under wine. However that same software does not see the tomtom gps which is connected via the USB port. The software says "NO Device connected" 
In Ubuntu the gps is available when connected via the USB port.
Anybody some Ideas how I can make the GPS visible for the tomtom software in WINE??

(PS: The software used on the tomtom is LINUX so why no linux supporting software?? Anyway this is a problem for later)

---

### Post by jotto! on 2010-11-17
Not sure, but is it similar to when using a usb device in a virtual machine? ie you have to unmount it from the linux system for it to be seen by the virtual machine and possibly wine in this case?

---

### Post by JohnPta on 2010-11-19
Even the virtual machine does not see the device connected to the USB port. In other words NO success in Wine and NO success in virtual machine.

---

### Post by Handssolow on 2010-11-30
There are two issues here as I see it.

1.TomTom doesn't currently support Linux users.
2.Wine's implementation of USB connected devices is still in its infancy. Although TomTom Home will run under Wine, a TomTom device connected by USB isn't recognised, as wont many other devices connected by USB with Wine.

In the longer term, say 5 years, I see the demise of the dedicated stand alone car satnav. Soon most phones will have the features you find on TomTom. Heck, my digital camera even has a GPS chip which will identify where I've taken my photos.

Perhaps TomTom might eventually release a Linux version of their TomTom Home to extend its life before they are overtaken by the phone market.

---

### Post by jsampaio57 on 2010-12-25
At last, a light at the end of the tunnel...
You should try [http://pytomtom.tuxfamily.org](http://pytomtom.tuxfamily.org)
Still in version 0.5, but at least, it can recognize a TomTom device connected to the usb port, and do some actions as GpsQuickFix, Backup and restore, and handle POI.
Download the pyTomTom.tar.gz file (the .deb didn't install in my machine), and extract it's folder. Connect the TT device; go to the folder extracted and execute pytomtom.sh

This is a long lasting, but promissing begin. Cheers, and Merry Christmas!

Jorge

---

### Post by jsampaio57 on 2010-12-25
just a correction, yes, the .deb installed using dpkg
$ sudo dpkg -i pyTomTom.deb

It shows in the Accessories
Cheers

---

### Post by marin123 on 2010-12-25
> **Handssolow said:**
> There are two issues here as I see it.

1.TomTom doesn't currently support Linux users.
2.Wine's implementation of USB connected devices is still in its infancy. Although TomTom Home will run under Wine, a TomTom device connected by USB isn't recognised, **as wont many other devices connected by USB with Wine.**

In the longer term, say 5 years, I see the demise of the dedicated stand alone car satnav. Soon most phones will have the features you find on TomTom. Heck, my digital camera even has a GPS chip which will identify where I've taken my photos.

Perhaps TomTom might eventually release a Linux version of their TomTom Home to extend its life before they are overtaken by the phone market.

its impossible to make programs under wine recognize mass storage. if i could get that working, i could say goodbye to dual booting :)

---

### Post by tango_ninja on 2010-12-25
> **JohnPta said:**
> Even the virtual machine does not see the device connected to the USB port. In other words NO success in Wine and NO success in virtual machine.

Have the exact same problem but Wine doesn't play nice with usb.

---

### Post by handy on 2010-12-26
> **jsampaio57 said:**
> 
At last, a light at the end of the tunnel...
You should try [http://pytomtom.tuxfamily.org](http://pytomtom.tuxfamily.org)
Still in version 0.5, but at least, it can recognize a TomTom device connected to the usb port, and do some actions as GpsQuickFix, Backup and restore, and handle POI.
Download the pyTomTom.tar.gz file (the .deb didn't install in my machine), and extract it's folder. Connect the TT device; go to the folder extracted and execute pytomtom.sh

This is a long lasting, but promissing begin. Cheers, and Merry Christmas!

Jorge 

> **jsampaio57 said:**
> 
just a correction, yes, the .deb installed using dpkg
$ sudo dpkg -i pyTomTom.deb

It shows in the Accessories
Cheers

Thanks for posting Jorge, that's great news for Tom Tom owners. :)

I'll have to check it out with my wife's Tom Tom. (She uses OS X, so we have no desperate need for Linux support at this stage, though I always prefer my Arch desktop to OS X.)

---

### Post by Handssolow on 2010-12-28
So near yet so far far away.

I was hoping that pyTomTom might be a fix which would have TomTom Home recognising that my 910 was connected to my PC's USB socket but no. It's a separate program that may or may not be working with my connected 910. I didn't seem to be able to look at what POIs I had already installed on my satnav.

The good news is that I ran TomTom Home under Wine and it installs the latest version, 2.7.6.2056. I can also login to my TomTom account. Ubuntu recognises my 910 is connected and even in TomTom Home>Tools>preferences I can browse what's on the 910.

But as far as the main part of TomTom Home is concerned, I've not got a device connected.

Anyone getting pyTomTom to work in meaningful way?

---

### Post by AClark on 2011-01-04
I have TomTomHome 2.8.0.2146 working perfectly in Virtualbox 3.2.12 (WinXP Sp3 - Haven't tried Win7 yet)

Also installed under Wine 1.2 with same results as others have reported - software seems to run normally - can log in - "no device attached"

pyTomTom seems to work OK as far as it goes but I don't see any option to download/install map updates

Have TomTom XXL 540 TM - Linux box is Ubuntu 10.04 64bit

I am brand new to GPS auto nav devices so I could be missing some feature that I don't even know about yet.

---

### Post by Handssolow on 2011-02-11
I've see someone suggesting Microsoft requested TomTom not to develop software for Linux users. This sounds a bit paranoid, true or not the evidence points in this direction. TomTom seems deaf to requests and has offered little or nothing in the way of assistance to Linux users, save for offering the Linux stuff that is on the satnav. WineHQ has this test report of an earlier version of TomTom Home. Here they did get their satnav device recognised by renaming the drive a: but no updates as the model wasn't covered.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5367](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5367)

The floppy switch was being used here also to get mass storage devices recognised under Wine

[http://my.opera.com/theoperalink/blog/index.dml/tag/Wine](http://my.opera.com/theoperalink/blog/index.dml/tag/Wine)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7502](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7502)

No luck here using this work round with my TomTom satnav. I have noticed that if I Apply after selecting a different Type in Drives, my TomTom satnav senses this and a Please Wait message and temporarily red cross appears on the satnav screen. I won't buy another TomTom satnav.

Edit: This is probably a false trail but looking for any differences between my TomTom Home installs in Wine and XP, I noticed two extra files in XP under TomTomHome/xul/components, they are, compreg.dat and xpti.dat. A thought, what happens after a fresh install of TomTom Home on a windoze PC, is a connected satnav device recognised before TTH has a chance to connect to the internet? There's me now being paranoid.

TomTom's approach could be that they want to protect their intellectual property and prevent use of things such as piratebay sourced maps?

more here
[http://osdir.com/ml/wine-bugs/2010-06/msg04342.html](http://osdir.com/ml/wine-bugs/2010-06/msg04342.html)

---

### Post by linux4me on 2011-02-24
I've got TomTom Home and an XXL 550 working in VirtualBox 3.2.12 (PUEL) with Winblows 7. Although it seems like TomTom Home is slow downloading things and installing them, it works. However, when I upgraded VirtualBox to 4.0.4 and installed the Expansion Pack to get USB 2.0 working, I got a grayed out device for the TomTom in Devices in VB, and TomTom Home would not recognize the device (of course). My other USB device, my HP printer, worked just fine. This seems like a problem with VB 4.0.4 and the TomTom, and not TomTom Home.

To make sure I was right, I uninstalled the 4.0.4 Guest Additions, removed VB 4.0.4, then reinstalled VB 3.2.12 and installed the 3.2.12 Guest Additions. My TomTom is now recognized again, and it's downloading updates as we speak.

I found [this post]("http://forums.virtualbox.org/viewtopic.php?uid=43242&f=7&t=39231&start=0#p176376") on the VirtualBox site that recommends making yourself a member of the "disk" group (System -> Administration -> Users and Groups -> Manage Groups) as a workaround. I haven't tried it yet, but it certainly sounds like a fix for the problem I was having.

I really wish TomTom would just make the update files available as a download for those with an account on their site. My XXL is recognized by Ubuntu 10.10 and I can browse the contents of it in Nautilus. It seems like it would be no big deal for them to provide the files for us in a form that would allow easy updates. Then we wouldn't all have to waste so much time screwing around in virtual environments trying to get their devices to work!

---

### Post by RT236 on 2011-03-08
Reading the apparent lack of being able to use a TomTom with updates via Linux has stopped me from purchasing a TomTom.  I will continue to look for a more Linux friendly GPS unit.  TomTom's loss.  We need several.

---

### Post by linux4me on 2011-03-08
> **RT236 said:**
> Reading the apparent lack of being able to use a TomTom with updates via Linux has stopped me from purchasing a TomTom.  I will continue to look for a more Linux friendly GPS unit.  TomTom's loss.  We need several.

I agree. It's appalling, especially because it seems like they're using Linux as the OS for the devices. If you find a good, Linux-friendly GPS unit, please post.

---

### Post by RT236 on 2011-03-08
> **linux4me said:**
> I agree. It's appalling, especially because it seems like they're using Linux as the OS for the devices. If you find a good, Linux-friendly GPS unit, please post.

I've been Googling around and from what I've seen it looks like Garmin is possibly more friendly for maps updates, etc.  Anyway, here is a site below I found interesting on Garmin stuff for Linux.

"Garmin Map Updates And Linux"  [http://x2q.net/garmin-map-updates/](http://x2q.net/garmin-map-updates/)

---

### Post by tlcstat on 2011-03-09
Greetings, 
My XXL TomTom works perfectly in Vbox 4.04. All updates and also manage from computer works from the VM. I backup my TomTom with Lucky Backup in Ubuntu. 
tlcstat

---

### Post by RT236 on 2011-03-09
> **tlcstat said:**
> Greetings, 
My XXL TomTom works perfectly in Vbox 4.04. All updates and also manage from computer works from the VM.  I backup my TomTom with Lucky Backup in Ubuntu. 
tlcstat

Thanks for the info!  Very appreciated!!! ):P

---

### Post by tlcstat on 2011-03-09
Greetings,
If your gps doesn't show-up in the Vbox VM click on devices/USB and put a check in the box next to TomTom. 
Also make sure you check for TomTom Home updates for updates to Home itself before you update anything, especially the maps. If you install a new map and don't install the TomTom Gps Application Update you may get freezing. This is all completely manageable in Vbox, so don't panic. So it works like this.
Update Home
Update the GPS App if available (this is done from "Manage TomTom".
Update Map.
Plan trip under Navigate and take a test drive to make sure you don't have any freezing before you take a trip. 
If all of the links on the GPS work from Manage my TomTom then you shouldn't have any problems when using them from the touch screen. Back it all up in Ubuntu using Lucky Backup or your favorite backup program.
FYI
tlcstat

---

### Post by RT236 on 2011-03-22
> **tlcstat said:**
> Greetings,
If your gps doesn't show-up in the Vbox VM click on devices/USB and put a check in the box next to TomTom. 
Also make sure you check for TomTom Home updates for updates to Home itself before you update anything, especially the maps. If you install a new map and don't install the TomTom Gps Application Update you may get freezing. This is all completely manageable in Vbox, so don't panic. So it works like this.
Update Home
Update the GPS App if available (this is done from "Manage TomTom".
Update Map.
Plan trip under Navigate and take a test drive to make sure you don't have any freezing before you take a trip. 
If all of the links on the GPS work from Manage my TomTom then you shouldn't have any problems when using them from the touch screen. Back it all up in Ubuntu using Lucky Backup or your favorite backup program.
FYI
tlcstat

Thanks for your reply on this.  I wanted to let you know how this went, but the difference was I got it to work with a Garmin with absolutely no problems either.  I had just placed an order for a Garmin when I saw your reply, so decided to try it with the Garmin, and it worked!!!

Garmin Nuvi 255
VirtualBox 4.0.4
Ubuntu 10.04
Windows XP SP3

I had the problem with USB grayed out in VirtualBox and I could not select it.  I had set the filter for the Garmin and lsusb also showed it. After much hair pulling I found a tutorial on How to Fix VirtualBox USB Support.  I was not a member of the vboxusers group and hence could not access USB in my case from the VirtualBox.  I'm listing this in case someone else has a similar problem [http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml](http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml)  After doing this one needs to log out and back in to update the changes.

Thanks for your help and having pointed me in the right direction.  I just did a 1 hr. update of the maps and it went flawlessly.

Thanks!!!

---

