---
title: "RatelUltra do I need to change BIOS to bootCD?"
date: 2011-02-06
forum: System76 Support
---

### Post by jr223 on 2011-02-06
Hello,

Another quick question.
I wanted to back up my Ratel Ultra with CloneZilla.
This involves booting from a bootable CD.

When I put the CD in the CD/DVD drive and rebooted the Ratel the system did the normal thing and booted directly to the OS Ubuntu that is on my system.

I did a reboot again this time selecting F11 if not mistaken boot menu.
This however is the boot menu for the preinstalled Ubunt, rescue mode mem test etc.

I re-booted again to the bios and noticed the boot order was Hardsk then the other perephrieals.
So if I want to boot from my CD do I need to change the order heare?
I guess I'm being a litte overly careful on what I do with the system, because it is new but please if you would let me know, it would be greatly appreciated.

Thanks
Jeff

---

### Post by Flyers2391 on 2011-02-06
I don't have a Ratel but I've changed the order without any harm on many computers.  If it doesn't do what you want, you can always jump back in the BIOS and change the order back.  

If you are going to want to boot to a CD when there is one already in the tray, it can't hurt to leave it there.  You may even want to move USB/peripheral to the #2 slot and have the hard drive at #3.

---

### Post by jr223 on 2011-02-07
> **Flyers2391 said:**
> I don't have a Ratel but I've changed the order without any harm on many computers.   You may even want to move USB/peripheral to the #2 slot and have the hard drive at #3.

Thanks Flyers2391!

This is really a kinda neat feature.
I guess it has to do with security.
Anyway, I re-booted my Ratel about 2-3 times.
Each time I would press F2 for the Bios settings.
Each time the system would bypass the Bios and boot into Ubuntu.

Finally I decided to put my CD/DVD in the tray and reboot, which I did.
As soon as the F2 for Bios settings came up I pressed it.
This now got me into the Bios where I changed the boot order saved it and re-booted.
Now my CD/DVD booted without any problems.
So in a nut shell to change the bios settings for the Ratel you need to have a CD/DVD in the drive other wise it is ignored and normal boot occurs.
My feeling on this is it is a low level security measure to stop someone from randomly booting the system with say Ubuntu live and looking at all your files.

Never the less I really am getting to enjoy this machine.

---

### Post by isantop on 2011-02-07
Good to hear you got that sorted out. You should also be able to choose what device to boot from by pressing F12 on boot up. This will override the BIOS setting on a one-time basis

---

