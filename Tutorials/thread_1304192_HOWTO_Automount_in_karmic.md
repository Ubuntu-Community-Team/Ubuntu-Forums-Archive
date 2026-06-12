---
title: "HOWTO: Automount in karmic"
date: 2009-10-29
forum: Tutorials
---

### Post by Elcid247 on 2009-10-29
I really like the new release, its GR8 in everyway especially that im an intel graphics user so i LOVE how everything works right now its never been better.

i had a few minor issues and 1 of them was automount on startup.

Since "Hal" is being deprecated, and ubuntu moved to devicekit-disks, i had a hard time figuring out how to set my drives to autmount on startup like i used to do with editing /etc/hal/fdi/policy/preferences.fdi and setting automount to ture.

i just found a solution for it, thanks to this

do this
```
sudo gedit /lib/udev/rules.d/95-devkit-disks.rules
```


at the end **BEFORE**
```
LABEL="devkit_disks_end"
```

just add
```
RUN+="/bin/mount -t auto /dev/sda6 /media/Programs"
```

of course replace /dev/sda6 with ur drive number and /media/Programs with the mount point u like. repeat for every drive and ur done :D

i also added this rule, dunno if its needed, it was supposed to set me as the owner but i still have to enter my pass if i wana unmount and remount a drive again but i dont care...

```
KERNEL=="/dev/sda[0-9]", OWNER="user"
```

FINALLY! found a solution for this it has been bugging me like hell!

[CENTER]:KSEnjoy:KS[/CENTER]

---

### Post by Koala Kid on 2009-11-06
Elcid247, thank you very much, works like a charm here. \\:D/

---

### Post by OobNosferatu on 2010-01-21
> **Elcid247 said:**
> I really like the new release, its GR8 in everyway especially that im an intel graphics user so i LOVE how everything works right now its never been better.

i had a few minor issues and 1 of them was automount on startup.

Since "Hal" is being deprecated, and ubuntu moved to devicekit-disks, i had a hard time figuring out how to set my drives to autmount on startup like i used to do with editing /etc/hal/fdi/policy/preferences.fdi and setting automount to ture.

i just found a solution for it, thanks to this

do this
```
sudo gedit /lib/udev/rules.d/95-devkit-disks.rules
```


at the end **BEFORE**
```
LABEL="devkit_disks_end"
```

just add
```
RUN+="/bin/mount -t auto /dev/sda6 /media/Programs"
```

of course replace /dev/sda6 with ur drive number and /media/Programs with the mount point u like. repeat for every drive and ur done :D

i also added this rule, dunno if its needed, it was supposed to set me as the owner but i still have to enter my pass if i wana unmount and remount a drive again but i dont care...

```
KERNEL=="/dev/sda[0-9]", OWNER="user"
```

FINALLY! found a solution for this it has been bugging me like hell!

[CENTER]:KSEnjoy:KS[/CENTER]

Thanks! But I just noticed that 95-devkit-disks.rules says don't edit this file since it will be changed with every update...

---

### Post by Elcid247 on 2010-02-17
> **OobNosferatu said:**
> Thanks! But I just noticed that 95-devkit-disks.rules says don't edit this file since it will be changed with every update...

Well a better way turned up, see [this]("http://ubuntuforums.org/showthread.php?t=785263")


thanks Alot joeb454!!!!

---

### Post by listerdl on 2011-10-30
I am running Lucid, why don't i have this file?

---

