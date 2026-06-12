---
title: "Antivirus system for cleaning Windows platform viruses?"
date: 2010-03-26
forum: Security
---

### Post by RhapsodyOfFire on 2010-03-26
Hello. This is my first thread in these forums .:KS
I would like to use my Ubuntu 9.10 Karmic system to scan and clean viruses from Windows based HDD. I have KlamAV, AVG, and AVAST. I couldn't get F-prot to work. I don't find a debian package of it and don't know how to install tar.gz and the tutorials don't help a lot. Are there other antivirus solutions which are good for cleaning Windows OS but work on Linux/WINE? I wonder if I can install antivirus software in WINE and scan with no problem the hard disks.

---

### Post by HermanAB on 2010-03-26
Linux support for viruses is very limited...

You would be better off using BartPE:
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

### Post by rejuvenate on 2010-03-26
there few antivirus developed but not to strong...
you can use clam antivirus which is on ubuntu itself..

sudo aptitude install clamav clamav-daemon clamav-freshclam

then for tk frontend follow this link...

[http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html](http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html)

---

### Post by Sir Jasper on 2010-03-26
Hi,

I assume you have active malware prevention running in Windows since prevention is totally superior to detection and cure? If you do not, the home version of avast! is free and highly rated. Also, you have a much wider choice of full or on-demand scanners and "fixers" which run in Windows 2000 up (rather than via 'buntu).

I use Wine and I have broadband and I frequently download a-squared USB version to my desktop, unpack it and run it (the free version not the command line version included in the download). I only use it on my 'buntu home directory (as my Wine configuration is set to limit the use of Wine to my Home directory). I also use avast! for Debian in the same way.

My regards

---

### Post by Matti L on 2010-03-27
One way I came up with was using Windows in VirtualBox (or any other virtual machine software) and then install what ever windows antivirus program there and use VBox shared folders to share your windows partition and scan it.

These might come in handy too:
[FREE Bootable AntiVirus Rescue CDs Download List]("http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/")

---

### Post by RhapsodyOfFire on 2010-03-29
> **Matti L said:**
> One way I came up with was using Windows in VirtualBox (or any other virtual machine software) and then install what ever windows antivirus program there and use VBox shared folders to share your windows partition and scan it.

These might come in handy too:
[FREE Bootable AntiVirus Rescue CDs Download List]("http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/")
Thanks a lot dude! There is a Trinity Rescue Kit which is exactly what I need with auto update feature and is completely free Linux based boot system. This way I can scan on the infected computer without removing the HDD and add it to my PC. Currently it says AVG don't work but BitDefender and Avast are great too! :D

---

