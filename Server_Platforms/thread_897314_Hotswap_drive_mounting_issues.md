---
title: "Hotswap drive mounting issues"
date: 2008-08-22
forum: Server Platforms
---

### Post by BiGG D on 2008-08-22
So after having instaled heron, and being amazed that X Windows worked like a champ right out of the box (This usually winds up being the bain of my *nix existence) I thought that if I slapped a nice new shiney drive into an available sata hotswap drivebay on my home server that it would just auto-mount & I could move forward with config'ing samba and moving some goodies over...

UmmmKAY, Not quite... so here I am in Xming (From my winders box) trying to bring up the contents of this new drive of mine (Already previously partitioned, formatted ext3, etc.) and I get the error message of "Cannot mount volume. error org.freedesktop.DBus.Error.AccessDenied." Details ~> "A security policy in place prevents this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" error name "(unset)" destination "org.freedesktop.Hal")"

-However when I try the same action locally from the box (Places ~> 1000.2 GB Media) it prompts me for my password since Im mounting it & at this point I can inspect the drive from XMing on my windows machine.

Long story short, how do I get this drive (and the others I plan on adding) to mount by default without anyone logging in to this headless box, and still have removeable hotswap ability?

Thanks,
D

---

### Post by windependence on 2008-08-22
Might want to learn a bit of CLI if you are gonna run a headless box. You'll need to add a line to your fstab to mount it at boot, but I'd have to look around to see if hot swap is even an option on Linux. You'd have to mount it like a USB drive. 

You'll want to try mounting it first by hand from the command line so you know it will mount smoothly.

-Tim

---

### Post by BiGG D on 2008-08-23
Well...

Thats the part thats kind of throwing me, below is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=61f301da-24af-43b2-8032-dcc1a9dce58d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=286e5204-3443-43e3-9c01-bbe6552ed8a4 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


According to gparted, sdb1 is my boot drive (and everything here works perfectly fine here), and sda1 is the drive in question that Im having issues with. Since fstab is saying remount readonly I tried to bring it up in Xming now & I get the same result. I do "sudo mount -a" (No textual responce from the shell when issuing this command) and still the same result in the GUI. I realize Im not the 1337'est person on the planet -But it doesnt seem like Im that far away from being where I want to be...   :/

Let me know what needs to be done, or what Ive done incorrectly...

Thanks,
D

---

