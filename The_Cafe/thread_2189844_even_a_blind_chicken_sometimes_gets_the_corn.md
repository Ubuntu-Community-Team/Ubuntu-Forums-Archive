---
title: "even a blind chicken sometimes gets the corn"
date: 2013-11-24
forum: The Cafe
---

### Post by germanix on 2013-11-24
So there I was feeling very sorry for myself. I recently bought a brand new Thinkpad X230 with "overkill specs". A i7 cpu, very fast Samsung 840 pro ssd and 16 gigs of ram on which I then installed Ubuntu 13.10. I was expecting a very fast boot time and was somewhat disappointed when it clocked 31 seconds. My son who is an Apple fan laughed at this boot time and showed me that his MacBook air with i5 cpu booted in 7 seconds. So I sulked. Then yesterday I broke my system. Was running a live disk of Mint "debian edition" and then the machine would not shut down. I had to "pull the plug" and afterwards it would not boot again. Started in "save mode" did a "repair broken packages" and "update grub". Had no idea what I was doing realy but hoped for the best. This worked and the machine then booted again, only now it boots in 14 seconds flat. So I guess sometimes you have to break things to fix things. Ok, still not as fast as my sons Air, but then I am running a superior OS ;)

---

### Post by oldfred on 2013-11-24
Best never to force shutdown. Only if this does not work.
 
Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

I think system does tune itself after every reboot, so after several it may be faster. With my 7 year old dual core system, but with a newer SSD says it boots in 9 sec. But BIOS and grub take 15 sec so it is 25 sec or so total. 
Supposedly new UEFI is a lot quicker booting than old BIOS, did you install in UEFI or BIOS mode with your system?
You can also check log files for boot process like /var/log/dmesg and see what may be slow. Longer times between entries or a process that repeats or gives errors is worth further investigation. You also may be able to turn off some things not needed.

---

### Post by germanix on 2013-11-24
Hi oldfred, thank you for the info. Not sure I have such an SysRq button on my keybord. I do have one button called "druck" which is german for print, I could try that. UEFI is not activated in the bios settings. I bought this machine without any OS installed and am running linux only. One of the first things that I did after installation was to turn off some stuff in "start-up" hat I do not require. Anyway I think 15 seconds for boot is just fine, so I am not complaining.

---

### Post by DuckHook on 2013-11-24
My experience has been that Linux never boots up as fast as Mac because, as an open system, it must anticipate vastly more HW variety than Apple's jailware and therefore includes far more drivers in its kernel. It's easy to optimize the kernel for a Mac because the OS is designed to run on a strictly limited set of HW, all with which the developers are thoroughly familiar and guaranteed to be exactly alike on every device. If you want to see this same dynamic at work in Linux, then I recommend the following. Install Gentoo on a VM and build two different kernels: the first one using genkernel (which pulls in absolutely everything), and the second by painstakingly using the kernel build tool to choose absolutely nothing but the minimal drivers needed for your VM. The difference is so amazing that it really has to be seen to be believed. My genkernel takes about 40 seconds to load. I swear that my custom kernel loads in less than 3 seconds. That beats your son's MAC by more than 200%.

Aside from custom kernels though, in general use Linux will never load faster than Macs. That's the price of freedom. However, in defence of Linux, ask your son to try compiling an Apple kernel.

---

### Post by Werne on 2013-11-25
> **DuckHook said:**
> Aside from custom kernels though, in general use Linux will never load faster than Macs.
Actually, [Linux can match the boot time of OS X]("https://lh3.googleusercontent.com/-qpNhmhD85hs/UpMs_OLLydI/AAAAAAAAB0U/lm0ul_YKXXs/s2560/werne-ubuntu-devel-trusty-20131113-1.png"), but the BIOS post will last longer than it does on Apple platforms. That's a pretty much stock Ubuntu there and it loads Unity in 5 seconds after the BIOS post (which last for 5 seconds as well), no compiling a custom kernel and no stripping of the OS down of all that stuff that gets loaded upon boot, I actually added a few services myself by the time that boot chart was made (like sensorsd, etc).

---

### Post by mips on 2013-11-25
> **germanix said:**
> This worked and the machine then booted again, only now it boots in 14 seconds flat.

That's still pretty slow for a ssd, my old desktop boot in about 10s on 7200rpm hdd but then again I use openbox.

---

### Post by DuckHook on 2013-11-25
> **Werne said:**
> ...That's a pretty much stock Ubuntu there and it loads Unity in 5 seconds after the BIOS post...That's a pretty snazzy box you have that booted so quickly. Have you measured it in older HW? I believe that Linux boot processes will take advantage of multi-threading, so 8 threads will boot up much faster than 2. The difference on my HW between my shiny brand-new desktop and my older dual-core is considerable. Surprisingly, even an ancient single-core is marginally faster than the dual-core, but that may be due to the difference between Lubuntu and Ubuntu.

A few years ago, I had the chance to measure the boot speeds of Apples and PCs (on various OSes) that had roughly the same HW specs. No default configurations were faster than Apple boxes. The rankings were roughly as follows:

1. Linux with minimalized kernel
2. Apple
3. Linux with standard kernel
4. Windows

Windows was always dead last by a large margin. Standard configuration Linux had a wide range depending on the distro. Among the "full" distros, Arch was usually the fastest, Ubuntu in the middle and both Fedora and Sabayon were relatively slow. I'm not counting special distros like Tiny, Damn Small or Slitaz because that would be comparing apples to oranges (okay, okay... feeble joke). I don't claim that these results were in any way scientific or even thorough. They're completely anecdotal. They are also a couple of years old and a lot changes in that time.

---

### Post by Werne on 2013-11-26
> **DuckHook said:**
> That's a pretty snazzy box you have that booted so quickly. Have you measured it in older HW?
AMD FX 8320 @4.2GHz, 8GB DDR3-1066 CL7 RAM and a 120GB Kingston SSDNow V300+, it's a budget build. I did measure it on older hardware (Intel Core 2 Duo E4500 @2.92GHz, 2GB DDR2-800 CL6 @1066GHz, same SSD and OS) and the result is 6 seconds. Not a 6 seconds difference, a 6 seconds boot time. The biggest time-consuming task drive seek time, the transfer time of an SSD is quite high (it was connected to a SATA II controller), and boot doesn't really need that much processing power at all on a standard PC.

> **DuckHook said:**
> I believe that Linux boot  processes will take advantage of multi-threading, so 8 threads will  boot up much faster than 2.
Yes, Linux features parallel boot (insserv) which allows using makefile-style boot sequence, that way it'll boot faster by using multiple cores for initializing services. It's enabled out-of-the-box on Ubuntu. If it isn't, running the following will configure it:
```
sudo dpkg-reconfigure insserv
```
I personally can't see the use for it, difference between parallel boot and single-core boot on a standard system is marginal, the biggest performance impact is dealt by the storage drive.

By the way, those 14 seconds OP mentioned is incredibly slow for an SSD, especially one like the Samsung 840 Pro since it has an even faster seek time than my V300+. On my PC, Debian boots in 14 seconds, but it has /var and /home located on a SATA II hard drive so it takes time to load user configuration and stuff, and Debian's initscripts is slower than upstart on Ubuntu. Ubuntu also has only one 66GB partition located on the SSD, so there is no HDD seek time bottleneck, which is the reason it boots in 5s. Plus, my SSD is a SandForce and it suffers a performance penalty with TRIM, it would be faster if I were to disable it (~230-270MB/s with TRIM enabled, ~320-380MB/s with TRIM disabled).

> **DuckHook said:**
> Windows was always dead last by a large margin.
Have you tried benching Win8? From what I understand, that thing uses some kind of hybrid boot which uses hibernation to boot faster. Don't know how that one would compare against Linux and OS X, my guess is that it would either be slower or on-par, judging by it's HDD boot time and processing power dependency (Windows is different than Linux, it relies heavily on both CPU power and storage speed).

---

### Post by DuckHook on 2013-11-26
> **Werne said:**
> Have you tried benching Win8? From what I understand, that thing uses some kind of hybrid boot which uses hibernation to boot faster. Don't know how that one would compare against Linux and OS X, my guess is that it would either be slower or on-par, judging by it's HDD boot time and processing power dependency (Windows is different than Linux, it relies heavily on both CPU power and storage speed).Have never tried Windows 8 and am happy that I will likely never have to. This was about two and a half years ago, so it was XP, Vista and W7. Not much difference between them actually, but if I recall, in descending order, it was W7, XP, then Vista as slowest of the slowpokes. I read somewhere that W8 takes advantage of hybrid boot only when there is a SSD acting as cache, but frankly don't know anything about it, so it's just a passing rumour to me. Actually, if there is one thing I *don't* fault Windows with, it is slow boot times. They have to take into account even more HW variety than Linux does, and one of the drawbacks of a micro-kernel is that each driver must be mapped to the kernel and loaded individually (at least, that's my understanding--maybe I'm just spouting nonsense).> On my PC, Debian boots in 14 seconds, but it has /var and /home located on a SATA II hard drive so it takes time to load user configuration and stuff...I'm curious... have you ever tried bcache? I would think that leaving everything on the HDD but enabling intelligent caching of absolutely everything from the SSD would load just as fast as a pure SSD install. I have an SSD/HDD combo on my main box and just like you, I leave /home /var /tmp and /swap on the HDD. It Loads plenty fast enough for me so I've never tried bcache, but it sounds fascinating. What I've read about it leads me to believe that I would have to compile bcache into the kernel, which seems to be too much trouble for too little gain.> Plus, my SSD is a SandForce and it suffers a performance penalty with TRIM, it would be faster if I were to disable it (~230-270MB/s with TRIM enabled, ~320-380MB/s with TRIM disabled).If you want to squeeze out the very last iota of performance, then consider nixing "discard" and setting up trimming as a cron job. I've only read about it, have no personal experience with it myself, so use at your own risk.

---

### Post by oldfred on 2013-11-26
I originally used discard, but after reading several of the opposing view points changed to the cron task.

       Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

gksu gedit /etc/cron.daily/trim
sudo chmod +x /etc/cron.daily/trim

  ```
#!/bin/sh
# trim
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
# if separate partition on SSD
# fstrim -v /home >> $LOG


```    

last few entries in my log
> *** Sun, 24 Nov 2013 08:03:45 -0600 ***
/: 2017529856 bytes were trimmed
*** Mon, 25 Nov 2013 07:45:44 -0600 ***
/: 2018480128 bytes were trimmed
*** Tue, 26 Nov 2013 07:48:11 -0600 ***
/: 18846908416 bytes were trimmed



---

### Post by germanix on 2013-11-26
@Duckhook, thanks, I get your point, I will tell my son to go and play with the kids and leave us grown-ups alone.
@Mips, now you have gone and spoiled the friendship, calling my 14 seconds "slow". I feel like an old man now ;)

---

### Post by Werne on 2013-11-27
> **DuckHook said:**
> Have never tried Windows 8 and am happy that I will likely never have to. This was about two and a half years ago, so it was XP, Vista and W7. Not much difference between them actually, but if I recall, in descending order, it was W7, XP, then Vista as slowest of the slowpokes. I read somewhere that W8 takes advantage of hybrid boot only when there is a SSD acting as cache, but frankly don't know anything about it, so it's just a passing rumour to me. Actually, if there is one thing I *don't* fault Windows with, it is slow boot times. They have to take into account even more HW variety than Linux does, and one of the drawbacks of a micro-kernel is that each driver must be mapped to the kernel and loaded individually (at least, that's my understanding--maybe I'm just spouting nonsense).
Vista was by far the slowest, I don't know what they did to it but it took it nearly a minute and a half just to boot. Not to mention it was slow as sloth even after it boots.

And both Windows and Linux have to account for the same type of hardware, though I believe Linux has to account even more since it's universal unlike Windows that has split home/server/business/etc systems. Windows Server has a different hardware compatibility and kernel than Windows Home, and Home has a different kernel than Professional, they are all split and the hardware support differs a lot (especially RAM, co-processor, and multi-socket support).

Win8, when there's a caching SSD, it stores the data onto that SSD. If there is none, it'll store it in RAM instead. But they managed to turn it into a dumb system initially, upon Win8 release if anything happened and the hibernation data got corrupted or destroyed (power failure or something), it would fail to boot and you needed to repair or reinstall the OS, it got fixed later on. You have no idea how may Win8 systems I had to repair since that thing got released, people would have hybrid boot on cause it boots fast, turn off the PC, unplug it from the wall socket (usually to fiddle with hardware inside or when there's a thunder storm), and it wouldn't boot anymore. I honestly don't know how they managed to mess that one up.

> **DuckHook said:**
> I'm curious... have  you ever tried bcache? I would think that leaving everything on the HDD  but enabling intelligent caching of absolutely everything from the SSD  would load just as fast as a pure SSD install. I have an SSD/HDD combo  on my main box and just like you, I leave /home /var /tmp and /swap on  the HDD. It Loads plenty fast enough for me so I've never tried bcache,  but it sounds fascinating. What I've read about it leads me to believe  that I would have to compile bcache into the kernel, which seems to be  too much trouble for too little gain. 
I was researching that and it does require compiling that into the kernel. It wouldn't be much of a problem though, I can compile the stock Wheezy kernel under 10 minutes and Debian gets kernel updates once in a blue moon. But Wheezy is my main OS and it's used to fix the rest of them if they break (I use Ubuntu development and Arch alongside Wheezy) so I honestly don't care how fast it boots as long as it's solid as a rock.

> **DuckHook said:**
> If you want to squeeze out the very  last iota of performance, then consider nixing "discard" and setting up  trimming as a cron job. I've only read about it, have no personal  experience with it myself, so use at your own risk.
To be honest, I had an 80GB 5400RPM 2.5" SATA I drive I ripped out of a laptop prior to switching to an SSD, so I'm more than happy with the current speed (28MB/s compared to 280MB/s is not a small change). Besides, when it comes to storage, I'm looking more at maximum longevity than maximum performance, I'd rather have my data than a speedy boot time. ;)


@oldfred Hmm, that article does seem interesting. I'll look into discard vs cron TRIM and see if there's an actual advantage to switching over to cron.

---

### Post by Morbius1 on 2013-11-27
> even a blind chicken sometimes gets the corn
I thought it was a squirrel who was vision challenged ... and it was nuts he couldn't find.

---

### Post by llanitedave on 2013-11-27
Apples and oranges, nuts and corn, chicken and squirrels.  We sure are agricultural here!

---

