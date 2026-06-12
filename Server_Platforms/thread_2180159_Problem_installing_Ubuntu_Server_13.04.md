---
title: "Problem installing Ubuntu Server 13.04"
date: 2013-10-11
forum: Server Platforms
---

### Post by TtWPcr7 on 2013-10-11
Hello,

Today I decided to "recycle" my old PC and try to make it a server, and chose ubuntu for this task. Unfortunately, it doesn't work...
All I get is a "ntldr is missing". I know it's a windows error (there is a Windows XP on the hard drive), but I don't want Windows and I'm trying to install Ubuntu server through an USB boot (after using UNetbootin).

I have no way to format the hard drive, and I have tested the USB boot and it worked on my laptop.
The PC in question is very old, the CD drive is unusable (broken ITE wires), 1Gb RAM and 1.8GHz 2 cores CPU, 164Go Sata hard drive. When in the boot, it says that I have no slave drive and a master drive (the one I stated before).

What should I do?

Thank by advance and have a nice day.

---

### Post by Dreamer Fithp Apprentice on 2013-10-12
> **TtWPcr7 said:**
>  I have tested the USB boot and it worked on my laptop.
The PC in question is very old, That may be the heart of the problem. Possibly it does't support booting from usb devices. Even if it does, you may have to enable it in the bios settings or and set it to check for bootable usb devices FIRST. If it sees what looks like a bootable disk earlier in the boot order it will try to boot it and it isn't bootable it will fail with something like what you see. Watch the screen closely as it boots and it will probably say something like "press del to run setup". Whatever it says, do it and look for settings for enabling usb boot, booting usb first (oddly that's often seperate from boot order, damfino y), and boot order.

If it just plain isn't able to boot from usb, as opposed to merely being set to not look there first, the easiest thing would be to install a cd-rom drive, even if only temporarily. Alternately, some real wiz may be able to tell you how boot something from floppy that will then look to the usb to continue the boot, but how to do THAT I haven't a clue.

---

### Post by TtWPcr7 on 2013-10-12
I managed to snag an external sata reader, and installed Ubuntu Server 13.04 on it. Now, I get "Bootmgr is missing". I know the problem, the drive is NTFS, but I can't format it to FAT, I only have the option to make it NTFS. Any idea on how to repair it?

---

### Post by Dreamer Fithp Apprentice on 2013-10-15
> **TtWPcr7 said:**
> I managed to snag an external sata reader, and installed Ubuntu Server 13.04 on it.It is not clear to me what that means.> **TtWPcr7 said:**
> Now, I get "Bootmgr is missing".When you do WHAT exactly? It is much more likely someone will suggest something useful if you state clearly EXACTLY what you've done. It sounds to me like maybe you attached a usb external drive to some computer (the same one, or some other?) and installed 13.04 on it. If it was on another computer and you didn't disconnect the drives in that computer before installing, then you have no boot manager on the external drive, and the other computer's boot manager probably has a spurious entry for booting the external drive that isn't there.

Have you or have you not succeeded in booting the computer you are trying to install ubuntu on from some installation media, such as a usb stick with a live system? If you can I'd boot live, rather than "direct to installer" and run gparted and delete ALL partitions on the drive in question and create however many new partitions of whatever sizes you want and format them to a linux native format. How may partitions, what sizes and what file formats are advisable depends on system specs and intended use. After that I'd run the installer. You might can do all this IN the installer without using gparted but if the OEM put in a "hidden" partition (which offense should be punishable forced immersion in stale rhinoceros urine for 3 days) I'm not sure they can be deleted with built in partitioner. Maybe.

If you have NOT been able to boot that machine from installation/live media, even after trying the bios settings I mentioned in my first post (which I'm not clear if you did or not) then I'd physically remove the hard drive and take it to someone else and ask them to repartition and format it for you. Then after shutting down the computer they use to do that and disconnecting all hard drives but yours (if they are serious geeks and understand grub inside and out they can skip this step, but otherwise not) THEN install ubuntu on it. Then shutdown, remove your drive and reconnect theirs. You may still wind up with driver issues, but you most likely will at least be able to boot in safe mode to fix them. 

BTW, if that sounds like too much work, you can get a cd drive new for about 15 bucks. It would be easier.

Good luck.

---

