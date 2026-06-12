---
title: "Breezy sources.list"
date: 2005-10-01
forum: Repositories &amp; Backports
---

### Post by mouldy on 2005-10-01
I had working repositories a couple of days ago, and now, for whatever reason, the software updater tells me it couldn't connect to the repository indexes when I try to reload them.


Here is my current sources.list
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted


deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu breezy universe
deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://gb.archive.ubuntu.com/ubuntu/ breezy multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe restricted

```

What do I need to change to make it work again? I live in the UK by the way - if that's relevent.

---

### Post by Ruddigger on 2005-10-01
None of them are working? what is the error message?
I just tried them and they seem to be up...
give it another try, maybe they were down for a while

---

### Post by mouldy on 2005-10-01
[[IMG]http://img282.imageshack.us/img282/7180/screenshot6ia1.th.png[/IMG]](http://img282.imageshack.us/my.php?image=screenshot6ia1.png)

That's the error I get. I assume it means that the backport repositories are down?

---

### Post by Emerzen on 2005-10-01
Remove the backport's listed there and try this line:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

The mirromax sites were due to be shut down as backports has moved here.  If you are using Breezy, I wouldn't have hoary backports updating your system regularly as it will eventually bork your system.  Typically, turn the backports on for any package you need/can't find in Breezy and then turn them off for regular updates.  That way, if something borks your system you'll know what package was responsible and from where.

---

### Post by mouldy on 2005-10-01
[QUOTE=Emerzen]Remove the backport's listed there and try this line:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted
The mirromax sites were due to be shut down as backports has moved here.  If you are using Breezy, I wouldn't have hoary backports updating your system regularly as it will eventually bork your system.  Typically, turn the backports on for any package you need/can't find in Breezy and then turn them off for regular updates.  That way, if something borks your system you'll know what package was responsible and from where.[/QUOTE]

Thanks for the info, it fixed it :) I'll keep it commented out though, until I need it.

---

