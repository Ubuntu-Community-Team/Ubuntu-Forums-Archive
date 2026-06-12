---
title: "32bit runs faster than 64bit, go figure."
date: 2016-04-02
forum: Ubuntu, Linux and OS Chat
---

### Post by frank75 on 2016-04-02
I've been running Core2Duo laptops lately that support a 64bit OS. I picked up an HP/Compaq nc6320 and it would only "see" 3.2GB of RAM out of the 4GB of installed RAM using the 6bit Xubuntu 14.04LTS install.  I wanted to give a PAE kernel a try so I installed the 32bit version of Xubuntu and it still only saw 3.2GB of RAM but it ran faster when I did my CPU Blowfish benchmark AND being PAE it can see all the RAM that I care to install(although not on the HP because of the way the motherboard limits it.) so I installed it on my Dell D830 and it can see the same 3.9GB of RAM that the 64bit version saw and it's also faster so I guess for most of us running a 32bit system even on a 64bit laptop would actually be a bit better because not only will it run faster but from what I've read 32bit packages are a little bit lighter weight as well. Anyway, just wanted to share in case ya'll needed the info.

---

### Post by Bucky Ball on 2016-04-03
Things won't be looking good when 32bit OSs aren't so readily available, or available at all, and that day approaches apace. May be not tomorrow, maybe not next year, but that day will arrive. :|

---

### Post by oldfred on 2016-04-03
There was discussion of deemphasizing the 32 bit.

 Developer's discussion of deemphasis of 32 bit Ubuntu - Nov 2014 
[http://www.phoronix.com/scan.php?page=news_item&px=MTgzODE](http://www.phoronix.com/scan.php?page=news_item&px=MTgzODE)
[URL="http://summit.ubuntu.com/uos-1411/meeting/22353/when-should-we-stop-making-32-bit-images/"]http://summit.ubuntu.com/uos-1411/meeting/22353/when-should-we-stop-making-32-bit-images/

[/URL]Back in 2009, these test showed either 64 better or the same.
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/) 

[URL="http://summit.ubuntu.com/uos-1411/meeting/22353/when-should-we-stop-making-32-bit-images/"]
[/URL]

---

### Post by grahammechanical on 2016-04-03
I never understand what people mean when the say, "lighter in weight." Smaller file sizes? Code more compactly written?

---

### Post by yoshii on 2016-04-04
I prefer to stick with 32-bit 'buntus because I like use Wine and from what I've read on WineHQ, full 32-bit support is only there in the 32-bit versions of the OS.  Most of my favorite Wine-compatible programs are from the Win XP SP2 era or descend from that.  
Also, I still have never needed more than 4 GB for anything.  I've never run out of RAM on any type of operations or DSP.  Also, it's nice to be able to rescue old hardware and run it like it's brand new.

---

### Post by frank75 on 2016-04-04
I think there's enough Netbooks and older Laptops out there to keep 32bit Linux Op Systems alive and well for the foreseeable future.  My 64bit install of Xubuntu was using around 350Mb of RAM to run the desktop, the 32bit version is in the 250Mb range. Also it's about .30 seconds faster which I know isn't huge but still, it IS faster running.  I also agree that for most of us 4GB of RAM is more than enough to do just about anything that we do on a daily basis. 
 Either way I started my Linux journey with Ubuntu 12.04LTS and now, almost 5 years later and after going though a boat load of different Distros I'm back on Ubuntu albeit the Xubuntu version.   I think Ubuntu is probably one of the best Distros(choose the desktop that you like) because it has a fairly large organization behind it and it's pretty stable.  I think I'm going to stick with Ubuntu for a while since it does just what I need my OS to do.

---

### Post by brandon48 on 2016-04-12
This sounds like my 11 year old PC. It's pc and write speed is faster than my current PC. Which makes to sense because x64 is supposed to be better.

---

