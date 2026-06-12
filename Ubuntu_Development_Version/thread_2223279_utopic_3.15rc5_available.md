---
title: "utopic 3.15rc5 available"
date: 2014-05-10
forum: Ubuntu Development Version
---

### Post by rtalcott on 2014-05-10
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc5-utopic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc5-utopic/)

---

### Post by fooman on 2014-05-12
```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Utopic Unicorn (development branch)
Release:    14.10
Codename:    utopic
3.15.0-rc5-foomans-custom-kernel
```

---

### Post by slickymaster on 2014-05-12
```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Utopic Unicorn (development branch)
Release:	14.10
Codename:	utopic
3.15.0-031500rc5-generic
```

---

### Post by rtalcott on 2014-05-12
My machines with Intel and nVidia graphics are running well with 3.15 but NOT anything with AMD/ATI....anyine else having this problem?

---

### Post by rrnbtter on 2014-05-17
Greetings,
It went live with todays updates.
Linux rrnbtter-Satellite-L305 3.15.0-1-generic #3-Ubuntu SMP Fri May 16 16:20:39 UTC 2014 i686 i686 i686 GNU/Linux

---

### Post by e-a-botjes on 2014-05-20
Hi.. Tried the 3.15.0-031500rc5-generic on an [COLOR=#000000][FONT=sans-serif]Asus X53SD and the virtual box kernel is not loaded during boot (at least vbox gives errors)
How should I report this bug and to whom should i reach out to help finding the RootCause?

Regards
Edzo[/FONT][/COLOR]

---

### Post by slickymaster on 2014-05-20
> **e-a-botjes said:**
> Hi.. Tried the 3.15.0-031500rc5-generic on an [COLOR=#000000][FONT=sans-serif]Asus X53SD and the virtual box kernel is not loaded during boot (at least vbox gives errors)
How should I report this bug and to whom should i reach out to help finding the RootCause?

Regards
Edzo[/FONT][/COLOR]

You can report it here: [https://bugs.launchpad.net/ubuntu/+source/virtualbox]("https://bugs.launchpad.net/bugs/bugtrackers/virtualbox-trac")

---

### Post by fjgaude on 2014-05-20
Well, kernel 3.15.0-1 came as an update this morning and it seems to work just fine with everything I tried, even Blue Tooth.

Oh, Virtual Box works just fine.

---

### Post by sammiev on 2014-05-20
> **fjgaude said:**
> Well, kernel 3.15.0-1 came as an update this morning and it seems to work just fine with everything I tried, even Blue Tooth.

I had the last 4 or 5 hours to play with it and have no issues to report at this time.

---

### Post by ventrical on 2014-05-20
```

ventrical@ventrical-Asus-Overclock:~$ uname -a
Linux ventrical-Asus-Overclock 3.15.0-1-generic #5-Ubuntu SMP Mon May 19 22:16:33 UTC 2014 i686 i686 i686 GNU/Linux
ventrical@ventrical-Asus-Overclock:~$ 



```

---

### Post by ubername on 2014-05-20
Can't get beyond lightdm with 13.15.0-1 at the mo (i.e. I can select user and enter password but then it just hangs) tried reinstalling nvidia, I'll try another user.

---

### Post by fjgaude on 2014-05-20
No issues for me with Intel graphics HD4600 Haswell motherboard.

---

### Post by ventrical on 2014-05-20
Ok on my SandyBridge G630.

  I blew out my overclocked system at 5.220GHz.  Overvoltage. I'm going to try and recover.
EDIT: Actually it was a 'nVidia taints kernel' but recovery from GRuB fixed it.

---

### Post by e-a-botjes on 2014-05-21
Where can I find the 3.15.0-1 ?
Until now I usally look at [http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline)
There the 3.15.0-0 is still present

---

### Post by slickymaster on 2014-05-21
> **e-a-botjes said:**
> Where can I find the 3.15.0-1 ?
Until now I usally look at [http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline)
There the 3.15.0-0 is still present

kernel 3.15.0-1 came as an update in Utopic. Have you already run```
sudo apt-get update && sudo apt-get dist-upgrade
```

Anyway it's available here: [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/)

---

### Post by Alan F on 2014-05-21
> **e-a-botjes said:**
> Where can I find the 3.15.0-1 ?
Until now I usally look at [http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline)
There the 3.15.0-0 is still present

Main Ubuntu Utopic repositories

Ubuntu:~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Utopic Unicorn (development branch)
Release:	14.10
Codename:	utopic
3.15.0-1-generic

---

### Post by slickymaster on 2014-05-21
Merged [3.15.x now in]("http://ubuntuforums.org/showthread.php?t=2225278") thread with this one, since they are both just general announcements on similar topics.

---

### Post by grahammechanical on 2014-05-21
Daily update did not bring in the 3.15 kernel for me. I have a lot of packages held back and for several days the daily update has only brought in a few miserable MBs. I do not like that situation. I always get tempted to run dist-upgrade. Stability? Who needs stability? Oops!
 
Actually, no "oops" so far. Well only a little "oops". The Ubuntu splash screen looks like it has been through a black hole - stretched out. Now, let us see if the update to the mir libraries has made the Unity8 session more usable.

---

### Post by ventrical on 2014-05-21
> **grahammechanical said:**
> Daily update did not bring in the 3.15 kernel for me. I have a lot of packages held back and for several days the daily update has only brought in a few miserable MBs. I do not like that situation. I always get tempted to run dist-upgrade. Stability? Who needs stability? Oops!
 
Actually, no "oops" so far. Well only a little "oops". The Ubuntu splash screen looks like it has been through a black hole - stretched out. Now, let us see if the update to the mir libraries has made the Unity8 session more usable.


This is the old synaptic paradox that takes place once in a while. Try using synaptic to update. Why this happens, I don't know.

---

### Post by e-a-botjes on 2014-05-21
I retrieve the .deb files by hand from the mainline website and then add them by hand with the dpkh -i command. 
So just 14.04 here with some manual kernel upgrades so now and then. no ppa with kernel releases.
I like the manual part in the kernel upgrades.. any location where i can download the 3.15.0-1 .deb files?

---

### Post by jerrylamos on 2014-05-21
> **rtalcott said:**
> My machines with Intel and nVidia graphics are running well with 3.15 but NOT anything with AMD/ATI....anyine else having this problem?

Well, this post is from an Acer 5253 dual processor notebook with:
 
VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6310]

on :

vendor_id	: AuthenticAMD
cpu family	: 20
model		: 1
model name	: AMD E-350 Processor
stepping	: 0
microcode	: 0x5000029

with 64 bit:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.10
DISTRIB_CODENAME=utopic
DISTRIB_DESCRIPTION="Ubuntu Utopic Unicorn (development branch)"
Linux Aspire1 3.15.0-1-generic #5-Ubuntu SMP Mon May 19 22:18:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Only problem so far is frequent gparted failures which do not produce a crash report and result in linux getting all tangled up and dying.  Nothing left to run ubuntu-bug.

---

