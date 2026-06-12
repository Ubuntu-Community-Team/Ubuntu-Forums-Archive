---
title: "Upgraded, But Do I have UbuntuStudio or Ubuntu ???"
date: 2016-09-11
forum: Ubuntu Studio
---

### Post by Rick St. George on 2016-09-11
Here is my Readout ...

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

Note, it does not say UbuntuStudio ???  And if it is not, is there a command I can use in Terminal to install it?

Thanks!
Rick

---

### Post by #&amp;thj^% on 2016-09-11
I am not sure if this will be any more descriptive or not but give it a try.
```
inxi -F
```
If inxi is not installed already
```
sudo apt install inxi
```
Very light weight and dose not pull-in much.
Info for inxi: [https://www.unixmen.com/inxi-find-system-hardware-information-linux/](https://www.unixmen.com/inxi-find-system-hardware-information-linux/)

---

### Post by Rick St. George on 2016-09-11
Tried to install the following, but Computer CRASHED and Shutdown!

```

sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

INXI shows the following;

CPU~Octa core AMD FX-8320 Eight-Core (-MCP-) speed/max~1400/3500 MHz Kernel~4.4.0-36-lowlatency x86_64 Up~4 min Mem~873.8/15997.3MB HDD~250.1GB(73.8% used) Procs~267 Client~Shell inxi~2.2.35

---

### Post by PaulW2U on 2016-09-11
> **Rick St. George said:**
> Note, it does not say UbuntuStudio ???  
It won't as all flavours of Ubuntu identify as "Ubuntu". The underlying operating system is common to all flavours.

What did you upgrade from, Ubuntu or Ubuntu Studio? You will have the same flavour after the upgrade as before.

Ubuntu uses Unity as its desktop environment while Ubuntu Studio uses Xfce, the same as Xubuntu but with a lot of extra applications installed.

---

### Post by howefield on 2016-09-12
If it helps, the output of..

```
cat /var/log/installer/media-info
```

should tell you which installation media was used initially for the install, ie, it should say ubuntu-studio if that is what was used.

---

### Post by #&amp;thj^% on 2016-09-12
> **howefield said:**
> If it helps, the output of..

```
cat /var/log/installer/media-info
```

should tell you which installation media was used initially for the install, ie, it should say ubuntu-studio if that is what was used.
+1 I was racking my brain on that one last nite just could not remember the syntax ](*,)
Thanks howefield...welded into memory now.:)

---

### Post by howefield on 2016-09-12
> **1fallen said:**
> +1 I was racking my brain on that one last nite just could not remember the syntax ](*,)
Thanks howefield...welded into memory now.:)

Cool and welcome, hope you are well 1fallen :)

---

### Post by #&amp;thj^% on 2016-09-12
> **howefield said:**
> Cool and welcome, hope you are well 1fallen :)

Sorry Off topic.
Thank You that means a lot to me.:)

---

### Post by Rick St. George on 2016-09-14
> **PaulW2U said:**
> It won't as all flavours of Ubuntu identify as "Ubuntu". The underlying operating system is common to all flavours.

What did you upgrade from, Ubuntu or Ubuntu Studio? You will have the same flavour after the upgrade as before.

Ubuntu uses Unity as its desktop environment while Ubuntu Studio uses Xfce, the same as Xubuntu but with a lot of extra applications installed.

I upgraded from UbuntuStudio from 14.04 to 16.04.

Thanks Guys!

Peace,
Rick

---

### Post by eggplant3 on 2016-09-17
> **Rick St. George said:**
> I upgraded from UbuntuStudio from 14.04 to 16.04.

Thanks Guys!

Peace,
Rick

I did the same except I went through 15.04. 14.04->15.04->16.04.01. From 14.04 to 15.04 Ubuntustudio upgrade turned of a lot of repos that was essential to ubuntustudio so I think my upgrade turned into a standard ubuntu. I thought that it didn't turn out so good so I made a backup of my /home and installed Ubuntustudio 16.04.01 from scratch. Much better. Although I do have some other problem that is not connected to the upgrade.

---

### Post by Rick St. George on 2016-09-19
> **eggplant3 said:**
> I did the same except I went through 15.04. 14.04->15.04->16.04.01. From 14.04 to 15.04 Ubuntustudio upgrade turned of a lot of repos that was essential to ubuntustudio so I think my upgrade turned into a standard ubuntu. I thought that it didn't turn out so good so I made a backup of my /home and installed Ubuntustudio 16.04.01 from scratch. Much better. Although I do have some other problem that is not connected to the upgrade.

So, I am still at a loss as to whether I have upgraded to UbuntuStudio v16.04 or not. I know that there is a lack of support for upgrading a lot packages/software that we are used to in UbuntuStudio and maybe that is part of the problem as to where did all the programs go??? See list [here]("https://wiki.ubuntu.com/UbuntuStudio/PackageList"), and [here]("https://help.ubuntu.com/community/UbuntuStudio/Applications").

It seems a simple fix to Run;
```
 lsb_release -a
```

and have it show exactly which version/flavor is installed.  Just a suggestion. Then we would not be asking such seemingly mudane questions in a forum.

Thanks!
:popcorn:

---

