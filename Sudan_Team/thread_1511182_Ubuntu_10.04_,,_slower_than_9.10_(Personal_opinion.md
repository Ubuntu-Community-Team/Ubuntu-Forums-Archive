---
title: "Ubuntu 10.04 ,, slower than 9.10 (Personal opinion)"
date: 2010-06-16
forum: Sudan Team
---

### Post by abdoamcig on 2010-06-16
[SIZE="3"]I cann't keep silence more than this !

Ubuntu 10.04 is the slowest version ever in ubuntu's diffrent version!

,,

Did you noticed that ? or that's just happened to me !?

I wished that if didn't upgrade to this worse version!

,,

Now i need solutions ,, Ideas ! 

[/SIZE]

---

### Post by zero-n on 2010-06-16
what do you mean by slow ?

slow boot
slow application
bad performance
etc ...

---

### Post by 4chan on 2010-06-16
for me lucid boot faster than karmic, but after log in (GDM) there's a 10-15 seconds gap before gnome panels shows up.

---

### Post by snowpine on 2010-06-16
It is unlikely that a new release (with a new kernel, libraries, applications, etc.) would be *exactly* the same speed as the old release on all possible hardware configurations. The best Canonical can hope for is that it is faster on more hardware than it is slower on.

That being said, if you want to actually provide some details, maybe someone can give you tips to make 10.04 faster on your hardware. ;)

---

### Post by tripolitan on 2010-06-16
You must have upgraded instead of freshly installed 10.04. Did I guess right?

I did both, upgraded from 9.10 on my main machine, runs same or slower. A fresh install looked after the problem. On a different machine, I wiped out 8.04 and installed 10.04 and found that the boot time is noticeably faster.

---

### Post by oldsoundguy on 2010-06-16
four machines.  All upgraded from on line.  All run faster. (the LTS to LTS had display issues that was solved by removing the carry over xorg and re-booting.)

---

### Post by abdoamcig on 2010-06-17
Zero one ,

Yes, Little slow boot, Slow application process!


> **tripolitan said:**
> You must have upgraded instead of freshly installed 10.04. Did I guess right?

Sure I did that ! But does i need to format all my data to get faster and newer version every time !

,,

Dear all, I'm thinking seriously to back to windows ! Really ! 

I can't wait more on this , Pressure under work !

---

### Post by Adntu on 2010-06-17
3bdo
it is an old advice: Don't upgrade, do a fresh install.
you better keep your data in your /home, and just wipe out the rest of the hard disk and reinstall.
I hope it will fix all your problems alright.
don't give up that easy!

---

### Post by oldsoundguy on 2010-06-17
A lot of files get dragged along when you upgrade!  And some of them are really useless (xorg.conf for one .. video is now handled differently.)

So the USUAL method is to save your ~/home folder.  Many save it to a separate partition, but I found that a thumb drive works just as well without going through the partitioning song and dance.

Then install OVER the old version or format and do a clean install and then bring the ~/home folder back BEFORE you go get the updates for the new install.

IF you do it that way, your home folder will update along with the OS and you will lose NO data. (unless you created folders for data OUTSIDE of your home folder .. if you did that, save those when you save the home folder.)

---

### Post by tripolitan on 2010-06-18
Why is mine the same or slower (while a fresh install is faster on another machine)? Do you think that my file system is too fragmented?

---

### Post by tripolitan on 2010-06-18
> **abdoamcig said:**
> 
Sure I did that ! But does i need to format all my data to get faster and newer version every time !

If you use LTS (I think everyone should), you only need to do it once every 3-4 years.

Same for Windows:
-Fresh re-install every 3-4 years (Whether the Windows version is upgraded or not)

---

### Post by Uruz on 2010-06-18
Mine's slower too, and I miss the old boot screen and Nautilus...

---

### Post by OtakuWrath on 2010-06-18
It feels like its straining to run on my computer.. like my desktop is running in Java or Shockwave or a Virtual Machine.. it still runs okay.. i just figured my problem was because i used Wubi to install. my system is kinda old so I'm used to the lag and CPU spikes.. :)

---

### Post by ranser on 2010-08-06
> **OtakuWrath said:**
> i just figured my problem was because i used Wubi to install.

So if you install ubuntu with wubi it is much slower than a regular install?

For me too things are running very slow. I had on my laptop (centrino 1.6 Ghz, 512 Mb RAM) Jaunty, Karmic, Lucid (now) and all of them are laggy. WinXP is very fast in comparison. I tried also in Karmik Xubuntu and it was a mess as well. 
Now I'm waiting maybe for Lubuntu to have a normal user-experience with Linux. Didn't try other distros. I have on my desktop Kubuntu Lucid and it runs pretty smooth. I guess Ubuntu doesn't like laptops.

---

### Post by salemboot on 2010-08-08
In all likelihoods, yes.

Upgrades are never better across version.

If your computer was made for a particular operating system then it runs the best on that operating system.

With Linux it's a general rule that if a distribution is released about the same year after your laptop was made then run that distribution.  

Distributions behave differently depending on at least Ten criteria. 
1. Level of freedom-hysteria the maintainers hold to
2. Target architectures of the distribution
3. Idiosyncrasies of the distribution maintainers
4. Proprietary support by hardware manufactors
5. Whims of the kernel developers for the kernel version chosen
6. Xorg developer idea change for the version include
7. Problems introduced by package rot
8. Interface changes including notification sub-systems
9. Lack of support for old features in new software
10. Unsolved problems that were ignored and worked around

It's the choice you make by choosing this ever-changing distribution.  We can look to Microsoft for example, who continuously and reluctantly patched XP for Nine years.  The GUI and driver interfaces didn't change.  

From 9.10 to 10.04 lots did change.
Hal was dumped for input device support in Xorg.
There was the inclusion of the boot splash which coupled with kernel mode settings ( KMS ) was guaranteed to shake up older NVidia cards.

This game of hop on the next train only guarantees you'll always be riding a train.   You never stop.  Always in flux, it's insanity.

If 9.10 was working for you then by all means download the ISO and install it.  

32bit
[http://mirrors.gigenet.com/ubuntu/9.10/ubuntu-9.10-desktop-i386.iso](http://mirrors.gigenet.com/ubuntu/9.10/ubuntu-9.10-desktop-i386.iso)

64bit
[http://mirrors.gigenet.com/ubuntu/9.10/ubuntu-9.10-desktop-amd64.iso](http://mirrors.gigenet.com/ubuntu/9.10/ubuntu-9.10-desktop-amd64.iso)

Everything else  :popcorn:
[http://mirrors.gigenet.com/ubuntu/](http://mirrors.gigenet.com/ubuntu/)


Good example,  1. 6.06 fast on my 1.0Ghz / 1GB ram.
2. 6.06 fast on my core duo 1.6Ghz / 1GB ram
3. 6.06 fast on my P3 600Mhz / 256 MB ram

All other versions have been hit or miss or not even worth mentioning.

But I don't blame anyone.  Find one that works.

---

### Post by patmagee1024 on 2010-08-16
I have a 9.10 installation I've been using since it came out and decided to install 10.04 to have a comparison. I converted my two 1TB data drives to ext4 under 9.10 and was pleased with the performance difference. For the last few weeks I've been hammering 10.04 doing the same thing, running vmware, moving files around, etc and I have experienced performance issues, mostly in the disk I/O area. I have also seen a slow memory leak that eventually uses up essentially all system memory while using vmware. The only way to get it back is to reboot (reminiscent of windows.) Yea, 10.04 boots like a lightning bolt but my virtual machines run much slower. I reboot back under 9.10 and the performance issues are gone. Keep in mind the virtual machine files are the same ones on the same drives, only the OS is different.

Dont get me wrong, I think 10.04 is fantastic. Hopefully in the near future the performance issues will be resolved and I'll be able to use it as a replacement for 9.10.

---

### Post by patmagee1024 on 2011-05-14
As a follow up to my previous post, I learned the kernel changed and there was a disk i/o performance hit due to the way the new kernel handled ext4. A quick change in fstab to include nobarrier fixed my performance issues with 10.04. I immediately saw the performance increase back to what I was getting with 9.10.

---

