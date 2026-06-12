---
title: "Wine Cd-rom issue"
date: 2010-05-11
forum: Wine
---

### Post by Chodam on 2010-05-11
I am having troubles getting to install games because of the multiple disc change.
I have tried to direct the path to /media/cdrom0/
though each time I put the disc in the drive for example. the path changes to the name of the cd I punt in in this case media/INSTALL/. (diabloII).

Is there a way that I can permanently change the path and name to the dvd drives through wine/playitonlinux or maybe even the terminal?

Any help would be greatly appreciated :)

---

### Post by asdfoo on 2010-05-11
> **Chodam said:**
> I am having troubles getting to install games because of the multiple disc change.
I have tried to direct the path to /media/cdrom0/
though each time I put the disc in the drive for example. the path changes to the name of the cd I punt in in this case media/INSTALL/. (diabloII).

Is there a way that I can permanently change the path and name to the dvd drives through wine/playitonlinux or maybe even the terminal?

Any help would be greatly appreciated :)

if you read the Wine faq it will tell you to use 'wine eject'

---

### Post by nandor73 on 2010-06-17
This also might be related to [bug 554642]("https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/554642").

---

### Post by mc4man on 2010-06-17
The combo of no fstab entry, the security bit, and if the case multiple disks can be addressed by either creating an fstab entry or probably better using the cli for install.

This will show the softlink drive letter for your drive
```
ls -l ~/.wine/dosdevices
```

Then - Ex. of drive d, .exe named setup.exe

```
wine D:/setup.exe
```

If it's a multiple disk install, when prompted just push eject button on drive, insert the next disk and click on <whatever> in prompt box.

(wine eject is not needed with this command, the drive is not 'locked'

---

### Post by cogadh on 2010-06-17
Clarification: "wine eject" *might* not be needed, it depends on how the installer is accessing the drive at the time of the swap. Some games, like the original Call of Duty, still require you to use "wine eject" to swap the disks, even when using that method.

---

### Post by nandor73 on 2010-06-20
mc4man, this gets into another problem: Wine does not autodetect a CD Rom device ([see this link]("http://ubuntuforums.org/showthread.php?t=1457243")), and I can't find any directory to assign to the wine D drive which would connect to the CD drive.  ls -l ~/.wine/dosdevices gives me

lrwxrwxrwx 1 nderby nderby 10 2010-06-16 19:42 c: -> ../drive_c
lrwxrwxrwx 1 nderby nderby  8 2010-06-16 08:46 d:: -> /dev/sr0
lrwxrwxrwx 1 nderby nderby  1 2010-06-16 08:46 z: -> /

but /dev/sr0 is a block file, not a directory.

Is anyone else having this problem?

---

### Post by mc4man on 2010-06-20
> Is anyone else having this problem? 
I just realized i was making a rather big mistake.

I'd filed a bug on this quite some time ago and it was pretty much ignored till recently.
Scott Ritchie brought up the softlink deal and it seemed 'right' here - except i'd forgotten I'd set an fstab entry for the drive on this machine 9and obviously wasn't paying close enough attention.

Here's the bug which I consider to still  be an issue - the easiest way around is just to create a fstab entry and static mountpoint.

[https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/554642](https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/554642)

Then everything returns to normal as before

I don't see any big issue having an fstab entry for your drive(s) in lucid, people who updated retained their's, only fresh installs don't have


Typical fstab for /dev/sr0

```
/dev/sr0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Don't forget to create the mountpoint
```
sudo mkdir /media/cdrom0
```

---

