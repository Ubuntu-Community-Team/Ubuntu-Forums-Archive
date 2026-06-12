---
title: "Create a USB bootable banking OS"
date: 2010-11-04
forum: Security
---

### Post by scuccii on 2010-11-04
Hello,
 
With all the financially driven malware on the internet these days I'd like to create a scaled down version of Ubuntu that does the following:

[LIST=1]
[*]Boots from a USB thumb drive.
[*]Boots directly to a browser.
[*]Isn't persistent and won't save settings or locked down to read only.
[*]Has a PDF viewer.
[*]Has no access to anything besides the PDS veiwer and the browser.
[/LIST]I'd like to give these to users here that make financial transactions on Windows machines on daily basis. I don't want them to have multiple machines, but if they can boot to a USB drive to make these transactions I'd feel a lot safer. Its almost like making a kiosk on a USB stick.
 
Any ideas?

---

### Post by surfer on 2010-11-04
this is a remix of (more or less) what you are looking for. it's in german though: [c't Bankix]("http://www.heise.de/ct/projekte/Sicheres-Online-Banking-mit-Bankix-284099.html")

the nice feature is: you burn the iso on a cd (without closing the session), run it a first time, configure it and install missing software, then, on shutdown it writes the changes to the cd and finalizes the session.

i prefer to use it on a read-only usb stick though. which also works nicely.

---

### Post by HermanAB on 2010-11-05
Howdy,

The Mandriva installation Live CDs are dual mode.  If you copy a Mandriva ISO to a USB stick using dd, then it will boot and run, with no hassle.

However, I think that your sense of paranoia is maybe a holdover from your Windows experience.  Relax and enjoy your Ubuntu system and forget about trojans, viruses and banking problems.

---

### Post by artie_effim on 2010-11-05
Your could roll your own in less than an hour using Ubuntu Server, remastersys and unetbootin.

Step one - install Ubuntu Server, install Login Manager, Window Manager, Browser and PDF reader of your choice.  Uninstall what you don't want/need.
Step two - muck around with Login Manager to boot directly to default user.
Step three - make ISO with remastersys
Step four - burn ISO to bootable USB with unetbootin

OR....

Search for Ubuntu kisok  - maybe the work is already done for you.

---

### Post by scuccii on 2010-11-05
The reason I wanted to get this done is because I have some clients that would like an alternative to using Windows for banking. They don't want anything else besides the ability to go into a Web broswer and save PDF's of there statements. 
 
Does anyone know of any good documentation on locking down an Ubuntu install? By this I mean what services should be uninstalled, iptables, programs removed, etc.....

---

