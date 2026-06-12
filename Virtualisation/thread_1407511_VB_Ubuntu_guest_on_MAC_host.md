---
title: "VB Ubuntu guest on MAC host"
date: 2010-02-15
forum: Virtualisation
---

### Post by GARoss on 2010-02-15
I had success installing XP guest on my iMac host so I decided to try Ubuntu 9.10 64bit. It installed & everything updated okay. After a reboot I needed to install Linux Guest Additions + Xorg. It seemed to install as it didn't indicate an error but Ubuntu now acts weird. After a reboot I got an 

"[ 0.0600001] kernel panic – not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the 'noapic' option. [ 0.060000]" error. Oddly that stopped but when I open VB I now get

"One or more virtual hard disks, CD/DVD or floppy media are not currently accessible. As a result, you will not be able to operate virtual machines that use these media until they become accessible later.
Press Check to open the Virtual Media Manager window and see what media are inaccessible, or press Ignore to ignore this message."

But Ubuntu does boot without errors. It is very sluggish & once a window is closed an image will linger until a mouse click. Sound hesitates, too.

I don't think Linux Guest Additions + Xorg installed correctly or maybe it needs to be configured. 
I followed this, [http://forums.virtualbox.org/viewtopic.php?f=3&t=15679](http://forums.virtualbox.org/viewtopic.php?f=3&t=15679) to install. It says, "Check /var/log/vbox-install.log" but there isn't a vbox-install.log in /var/log/ folder.

When I try "sudo vim /etc/X11/xorg.conf" in the terminal it can't find xorg.conf.

I'm lost. Do I re-install Linux Guest Additions + Xorg?
Any ideas?

Please advise.

---

