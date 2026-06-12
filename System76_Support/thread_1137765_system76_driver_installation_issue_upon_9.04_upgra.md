---
title: "system76 driver installation issue upon 9.04 upgrade"
date: 2009-04-25
forum: System76 Support
---

### Post by VOLKOV9 on 2009-04-25
I'm following the directions at [http://knowledge76.com/index.php/JauntyUpgrade](http://knowledge76.com/index.php/JauntyUpgrade) and running into trouble.  When I "Go to *System* &#8594; *Administration* &#8594; *System76 Driver*. Click the *Install Drivers* tab, then click *Install*," the first time it gave me a message along the lines of "Ubuntu supports all the packages" or something and quit.  This made me suspicious, so I did it again to confirm, and now it opens a new little window that never does anything (screenshot attached).

Help?  Thanks.

---

### Post by VOLKOV9 on 2009-04-25
So immediately after posting this, I got a kernel panic, rebooted, and upon logging in had everything set to default.  Now, the *Install Drivers* button gives me the original message: "All drivers for this system are provided by Ubuntu."  So I guess that's not a problem?

However, now is there a way to restore all the settings I had before?  My first couple of boots after upgrading, they were all still here - they disappeared after this kernel panic.

I'll post again if the kernel panic recurs (I used to have trouble with it, starting after the upgrade to Intrepid, and you guys helped me fix it, but that opened up a can of worms that never got resolved...).

Thanks in advance.

edit: PS.: Every time I reboot, all my settings are reset to default.  For instance, moving panels around, changing the color of panels, what I have on the panels, etc. etc.

---

### Post by thomasaaron on 2009-04-26
> "All drivers for this system are provided by Ubuntu." So I guess that's not a problem?

That's not a problem.

> Every time I reboot, all my settings are reset to default. For instance, moving panels around, changing the color of panels, what I have on the panels, etc. etc.

Sounds like something didn't go exactly right in the upgrade. Try running this command...

mv .gnome .gnome.backup

And then reboot your machine. Then, try doing some modifications and rebooting.

If that doesn't work, you may have to run this command to get back to where you are now...

mv .gnome.backup .gnome

Also, which System76 model do you have?

---

### Post by VOLKOV9 on 2009-04-26
System76 Serval | nVidia 512 MB GeForce 8600M GT | Realtek ALC 268 | Core 2 Duo T9300 2.5 GHz 800 MHz FSB 6 MB L2 | 4 GB - 2 x 2 GB DDR2 667 MHZ | 200 GB 7200 RPM SATA

---

### Post by VOLKOV9 on 2009-04-30
a couple of boots after posting this, the little hard disk check it does occasionally while booting up returned code 4, which sent me to a terminal screen, where I ran fsck, which encountered a whole mess of problems to fix.  When it booted up, it was of course to the default settings screen, but I (eventually) noticed that the time zone had fixed itself (I guess the default time zone is not mine, central).  So I moved a panel, rebooted, and it stayed there!

I'd still like to find my old settings - any suggestions on restoring them?

I don't have any ~/.gnome but I do have ~/.gnome 2 so I tried doing what you said except with that, and it had no effect that I noticed.

Also, today I had a similar fsck bootup experience, (noticeably fewer problems, but still many).  This isn't impairing my computing experience except by making an occasional boot take much longer, but it sure seems ominous.

Thanks again.

---

### Post by thomasaaron on 2009-04-30
Did you choose the ext4 filesystem?

---

