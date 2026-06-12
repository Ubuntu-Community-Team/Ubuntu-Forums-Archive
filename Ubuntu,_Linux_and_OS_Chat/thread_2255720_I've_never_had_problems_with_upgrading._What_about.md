---
title: "I've never had problems with upgrading. What about you?"
date: 2014-12-07
forum: Ubuntu, Linux and OS Chat
---

### Post by Linuxman1900 on 2014-12-07
In the last 2 years I have gone from a lot of distributions, but decided to huck my Ubuntu 12.04 disc onto my new laptop. After that I upgrade to 14.04 without problems. But this isn't just this laptop. I have used Ubuntu on a lot of machines, and none of them have ever had upgrading problems. Can anybody else say the same?

---

### Post by Gone fishing on 2014-12-07
I think I've been usig Ubuntu since Warty but it might be Hoary. Ubuntu upgrading has got much, much better, it could be a bit hit or miss in the early days. I alway used to just whip the / partition and keep my home directory then migrate all my data accross.

---

### Post by Linuxman1900 on 2014-12-07
I've always just done LTS-LTS upgrades, since LTS is more stable for me, and I don't like only having 9 months of support on non-LTS releases.

---

### Post by d-cosner on 2014-12-07
Upgrading to the next release has always worked well for me. I have not tried upgrading from LTS to LTS yet but I am sure I will at some point. Nice to hear there has been good results with that type of upgrade. :)

---

### Post by ian-weisser on 2014-12-07
Upgrading since Breezy.
Once I upgraded manually, sneakernetting hundreds of packages from my network connection at work. Successfully.

Two upgrade failures:
One was my own fault about 6 or 7 years ago - I didn't remove conflicting non-Ubuntu software before starting the upgrade. And I *knew* it was conflicting. I just didn't remember or plan until too late.
The other was a bug about 4 years ago in an init script deleting a /var/run symlink at shutdown that left the system crippled until I manually fixed it. The patch was released about two weeks later. The current set of smoke-testing scripts would have discovered it. 

I remember when this forum was full of whole classes of Xorg display bugs that no longer exist.
I remember when this forum was full of whole classes of printer configuration issues that no longer exist.
I remember when this forum was full of whole classes of audio problems that have vanished.
And I remember when a new release of Ubuntu meant two weeks in this forum of unrelenting crash reports, lost-data complaints, hardware reversions, and other nightmares that made you scared to upgrade. All long gone, thanks to the QA Team and the Testing Team and their 2009-2012 push for better build infrastructure, an awesome testing infrastructure, standardized hardware testing tool (checkbox), standardized crash and bug data collection (apport and whoopsie/daisy), automated testing, daily development images, and much more.

---

### Post by craig10x on 2014-12-08
Have never had the experience of an LTS to LTS upgrade, but every upgrade i did on the 6 month versions so far have been 100% PERFECT...the smoothness has been amazing...I do run a "stock" ubuntu (in other words, don't make major modifications) and i always remember to turn off any ppas (actually, i only have one which is for Google Chrome)...I have a back up flash drive with all my data, just in case, and also make an iso of the new version of ubuntu (also, just in case a fresh install would be needed) but so far, amazingly....each one has been smooth as butter :D

Seems like the quality control of the ubuntu upgrades is very good at this point in time, as long as you don't throw any "curves" in it's path ;)

---

### Post by cariboo on 2014-12-08
The only problem upgrade I ever had was back in 9.04 on an HP laptop that has since gone to the recyclers. I attempted to upgrade using wireless, and some of the dowloaded packages were corrupted. Simply running:

```
sudo apt-get -f install
```

solved the problems, but it did take the better part of a day to do it.

---

### Post by mastablasta on 2014-12-09
> **cariboo907 said:**
> The only problem upgrade I ever had was back in 9.04 on an HP laptop that has since gone to the recyclers. I attempted to upgrade using wireless, and some of the dowloaded packages were corrupted. Simply running:

```
sudo apt-get -f install
```

solved the problems, but it did take the better part of a day to do it.

same here, only solution wasn't as simple. it was on laptop from 13.10 to 14.04. i lost desktop and i had to clear the cache and donwloaded packages and then rerun the upgrade& overwrite... well i can't remember exaclty, btu it was more like 4 or 5 commands and some troubleshooting. never again with a wi-fi...

---

### Post by mörgæs on 2014-12-09
It's interesting to see that people open a thread to tell that an upgrade worked, not that it failed. It is indeed newsworthy if a huge process like this is getting stable.

Good for you but I am still getting poor results. Besides, I don't see the reason for upgrading: Since data is always available in a back up elsewhere a fresh install is done in half an hour.

---

### Post by Rob Sayer on 2014-12-09
I only did an upgrade once and had no problems.  But I've seen too, too many problems with it here.  I agree with post #9 - better to do a clean reinstall.

It's particularly easy to reinstall (assuming it's the same distro/DE) if you install with a separate /home partition.

---

### Post by craig10x on 2014-12-09
It usually goes well if you use a basic "stock" ubuntu (no major modifications) turn off your ppas, and have a good solid internet connection...Otherwise, i would agree, you would be better off with a clean install...
As i mentioned earlier, that's what i got, so it works great and as long as it continues to do so, i will keep doing them...;)

---

### Post by CantankRus on 2014-12-09
Never upgrade so I can be sure any problems I may have are not due to upgrade
and I just like the idea of starting fresh to fix little problems I may have introduced with my fiddling.

Home folder is copied to another drive as a simple backup then perform new install.
Run a script to install my favourite applications and another to customize using gsettings.
Copy over some .configs/files, load a saved compiz profile, make a few minor tweaks and 
I'm good to go in not much more than half an hour. :p

---

### Post by cariboo on 2014-12-09
> **mörgæs said:**
> It's interesting to see that people open a thread to tell that an upgrade worked, not that it failed. It is indeed newsworthy if a huge process like this is getting stable.

Good for you but I am still getting poor results. Besides, I don't see the reason for upgrading: Since data is always available in a back up elsewhere a fresh install is done in half an hour.

There are several valid reasons for doing an upgrade, even if you have a good backup strategy. Before the release of a new version, so that any bugs can be reported, or just after the tool-chain has been uploaded, to start testing the development version.

---

