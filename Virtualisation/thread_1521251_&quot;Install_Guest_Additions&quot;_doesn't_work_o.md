---
title: "&quot;Install Guest Additions&quot; doesn't work on Windows XP guest OS"
date: 2010-06-30
forum: Virtualisation
---

### Post by Objekt on 2010-06-30
For the last couple of versions of the Virtualbox Windows Guest Additions, I have been unable to install updated Guest Additions in the standard way.  That is, the Devices->Install Guest Additions... menu item does nothing, except it opens the tray on my DVD/CD-RW drive.  

I do have Windows Guest Additions 3.2.0r61806 installed on the Windows XP guest OS, but I had to download the new Guest Additions CD image manually.  I can't remember where I got that CD image, so I have no idea where to download the newer 3.2.6 Guest Additions image.  So far, Googling has turned up nothing helpful.  Oracle seems to have it well-hidden.

So how do I get the latest Guest Additions installed?  It seems that Oracle assumes the "Install Guest Additions" item will always work, so they provide no way to download the CD image directly.  What a pain.

FWIW, I am using Virtualbox 3.2.6 PUEL, not OSE.  I have the Oracle Virtulabox repository in my software sources, so I get prompted for updates as they're released.

---

### Post by Fire_Chief on 2010-06-30
If you open the Virtualbox interface, go to the File menu and select the Virtual Media Manager, you will find a tab that says CD/DVD Images. The VBoxGuesAdditions.iso should be listed in the box. If it is present, then we can easily mount it in the guest.

Open the settings for the selected virtual machine. Go to Storage. Click on the CD icon under IDE Controller. In the right hand part of the window, click on the pull down menu next to CD/DVD Device and choose VBoxGuestAdditions.iso. Click OK.

The CD should mount inside of your Windows XP VM. If it doesn't autorun, then just open My Computer, open the CD drive, and run the setup.exe file.

Cheers!

---

### Post by Objekt on 2010-06-30
I know how to do all that.  The problem is not installing the Guest Additions, it's getting the CD image to install from.  All I have is the last one, 3.2.0r61806.  I keep getting a notification that there is a new set of Guest Additions available when I start my Windows XP virtual machine, but I can't install them because I can't get the CD image.

[s]Isn't there some way to download the CD image, without the "automagic" menu item within Virtualbox?  Since the menu item is broken, I can't download the CD image from whatever secret URL Virtualbox would normally use.[/s]

Finally, I found the URL.  For future reference, it's here: [http://download.virtualbox.org/virtualbox/]("http://download.virtualbox.org/virtualbox/")

I was able to install the Guest Additions after mounting the new CD image, as you described.  This isn't really "fixed" because the "Install Guest Additions..." menu item seems to be permanently broken.  But, it's able to be worked around, and I guess that's worth something.

---

