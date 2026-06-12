---
title: "Ubuntu 7.04 &amp; External disinfection of windows installed drives"
date: 2007-05-04
forum: Server Platforms
---

### Post by Wiebelhaus on 2007-05-04
I'm in need of some advice , I'm using Ubuntu 7.04 at home as well as my wife  without issue , at work i need to setup a Ubuntu 7.04 installation that can be used to disinfect drives with windows installed via an external hard drive enclosure , meaning you would pull the hard drive from the infected system temporarily install it in this external enclosure , flip the switch & windows sees it as an external drive , Ubuntu does this as well but it's inconsistent , allot of times I do not have permission to delete or remove anything from the external drive.

Better yet , the anti-virus cant remove the infected file either , I've tried Avg-Free , Clamtk , Anti-vir , the idea is to have a workstation to disinfect windows pcs which is immune to inadvertent cross contamination , that can also be used to work with...

The working part is great , people love it and want it for themselves , any suggestions or if anyone has this type of thing setup , could you please share your configuration? thanks!




Automatix - Auto read/write ntfs/fat32 installed
Ntfs3 app installed

---

### Post by nomb on 2007-05-04
I've had a lot of issues (not just with ubuntu) dealing with external usb drives.  Things in the past that have helped me:

used chown to change owner to my user
used chmod to change permission to 777
create an fstab entry with rw permissions

Not sure exactly what you need to do though.  When you plug in an external drive what does dmesg and mount say?

---

### Post by Wiebelhaus on 2007-05-04
> **nomb said:**
> I've had a lot of issues (not just with ubuntu) dealing with external usb drives.  Things in the past that have helped me:

used chown to change owner to my user
used chmod to change permission to 777
create an fstab entry with rw permissions

Not sure exactly what you need to do though.  When you plug in an external drive what does dmesg and mount say?


Ntfs log file is unclean...

Disk must be bad , going to try another , thanks for the suggestions.

---

