---
title: "Very slow desktop environment?"
date: 2014-09-11
forum: Ubuntu Studio
---

### Post by mrule on 2014-09-11
Hi, sorry if this is redundant, I was unable to find any clues from searching the forum.

I'm running Ubuntu Studio 14.04 on a reasonably powerful machine. Recently, the system has started to become unusably slow. 

For example, today I tried to open a folder on the desktop. After waiting for 5 minutes I got bored and took a long walk -- the folder was open when I returned, but obviously this is unacceptable performance. 

I am posting from the machine in question, and once something loads it does seem to function. For example, it only took about 15 secdonds ( still about 30x longer tha I would have expected ) to open Firefox. Now that Firefox is open, it seems to be relatively responsive. 

I do not remember experiencing such long latencies in the past and I have to assume that there is a problem with (Thunar?) that is to blame?

---

### Post by mrule on 2014-09-11
Update: iotop says that there is a "find / -ignore_readdir_race" process clogging disk IO. Does anyone know what this is, why it is here, why it is breaking disk IO, whether it is safe to disable it, or how to disable it? Do you think it is related to an operation I started, or is it built in?

---

### Post by mrule on 2014-09-11
Update: also there is an "mount.ntfs /dev/sdd1 /media/$user/$drive" process taking up a smaller, but substantial amount of IO capacity (28%). To my knowledge there are no processes actively reading or writing data to $drive. Is it possible that there is some problem here that is fixable?

---

### Post by mrule on 2014-09-12
Update: I'm not sure if this is related, but one of the background process that was clogging disk IO is related to the issue discussed here : [http://ubuntuforums.org/archive/index.php/t-1434614.html](http://ubuntuforums.org/archive/index.php/t-1434614.html)

I've killed that process and the system is currently more responsive but I don't know if the two things are actually related. I also do not know how to permanently disable this 'find' command. Does anyone know what this is for and how to turn it off? ( or whether it is advisable to turn it off )

---

### Post by mrule on 2014-09-22
Update: anyone know why "thunar --daemon" might take 100% of the disk IO capacity at login? Is this just thunar loading? I'm still experiencing a fairly unresponsive system. For example, it took about 50 seconds to start gedit today. Could this be an issue with a bad disk? Or is Ubuntu Studio just inherently slow like this?

---

### Post by sudodus on 2014-09-22
Hi,

I'm running Xubuntu now, and it has Thunar. But it is 12.04 LTS. I have also a partition with Ubuntu Studio 12.04. I have *not* had such problems.

1. Are you running the low-latency kernel in Ubuntu Studio? That might get problems in some situations (the price for the low latency).

2. I know that Thunar wants to build a data-base (of the files) at boot or login. This keeps the computer busy for a while, but after that, it should work fast (faster than without that data-base).

3. Will things work better if you let the computer run  "thunar --daemon" until it is satisfied (without pushing it with your commands)?

Maybe a combination of thunar's data-base-building and the low-latency kernel can cause your problems. In that case it might work better if you use another file browser, for example nautilus  or pcmanfm. But if you remove thunar, you may be problems with the desktop, unless you know how to replace that function. I would not recommend that.

There might also be problems with the file system or with the hard disk drive (logical or physical problems), that some file or sector on the drive is hard or impossible to read.

---

### Post by DJonsson2008 on 2014-09-23
I'm having the same problems as MrRule. With Ubuntu Studio 14 Thunar is sluggish and the desktop keeps disappearing.
The 2 problems may be unrelated, but about to load Kubuntu or Lubuntu to try to isolate the problem to the 
desktop. As the hardware seems O.K. 

Been using Xubuntu and Ubuntu Studio for years since Hardy, but have not had these problems before.
Any help would be apprecated.

---

