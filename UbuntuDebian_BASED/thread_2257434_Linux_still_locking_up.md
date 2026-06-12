---
title: "Linux still locking up"
date: 2014-12-19
forum: Ubuntu/Debian BASED
---

### Post by dallase1 on 2014-12-19
I have Cylon Linux installed on my system that is based on Ubuntu 12.04lts and it is locking up on my system just like the offical Ubuntu 12.04lts did 

Release 12.04 (precise) 32-bit

Kernel Linux 3.2.0-75-generic-pae
GNOME 3.4.2
  Available Memory 3.8 GiB (I have built in Video that uses some of the Memory on the Motherboard for it's video memory)
This is the first system where I used the built in Video and not a separate Video Card

CPU Intel® Core™ i3-3220 CPU @ 3.30GHz × 4 

Graphics Intel® Ivybridge Desktop x86/MMX/SSE2

Memory 1 Kingston KHX1600C9D3/4G 4GB DDR3 Memory Module 1600 CL9 240 Pin DIMM
This Memory Module was recommended by ASUS the manufacture of my Motherboard which is a P8 B75-M/CSM it has SATA 3GB and SATA  6GB IDE Ports on it.

It was running just fine when I had it running off a USB Hard Drive without any hard drives hooked to the 6GB SATA Port but then after I hooked up a hard drive to the 6GB SATA Port but was still running Cylon off the USB Drive it locked up ironicly shortly after I thought to my self "So far it has not locked up"

When I say lock up I mean a solid Lock up where the mouse does not move and the keyboard does not respond (Num lock Caps Lock won't respond) so hitting Ctrl Alt F-4 or F-1 or F-2 does nothing and when I hit the reset button on my computer it takes about 5 seconds before it resets powers off and then back on. I've Never had my computer lock up while running Windows 7 but I don't really use Windows 7 that much so maybe it's justt because I'm not running it long enough for it to happen.

It is totally random sometimes it will go days without locking up and other times it will lock up and I will hit reset and then boot in recovery mode and it will locks up there or after exiting recovery mode after I run a check all file systems (the equivalent of Check Disk for Linux forgot what exactly it is called)

I had mint running for a while and it was stable but I don't like it's interface (Cinnamon) 

I never had this problem untill Ubuntu 12.04lts, all other versions all ran flawlessly and booted up real fast but I had a older system before I got 12.04 and that system had regular IDE ports on it and one SATA port 1.5 Meg or what ever came before SATA 3 GB but after regular PATA IDE.

---

### Post by rewyllys on 2014-12-20
Since you had Mint running satisfactorily, why not try it again with a different desktop manager, for example, MATE?  Or you could try Linux Mint Debian.

---

### Post by dallase1 on 2015-01-05
I did not try Mint again because I did not like it's boring outdated interface that was not very Modern and 3-D like Gnome in Ubuntu 12.04. I think what was causing the lock up was either the Mac Theme I tried to install or the Cairo Dock because shortly after installing the Cario dock app my system locked up so I uninstalled it and reinstalled Docky and now so far my computer has not locked up. [-o<

Why would software cause a Hard Lockup? I thought Linux was supposed to prevent software from totally crashing it. That is Windows Job to be un secure and allow programs to crash ones system.:lolflag:

> **rewyllys said:**
> Since you had Mint running satisfactorily, why not try it again with a different desktop manager, for example, MATE?  Or you could try Linux Mint Debian.

Aperently I was wrong because my system locked up twice 2 days agao, I was running Windows XP in Vmplayer and when I minimized the XP Program it locked up right in the middle of it animating with the suck it into the dock animation, they keyboard was locked up so I could not Crtl Alt Del or do that Ctrl Alt F4 thing or the other thing with the Sys Rq key that I read somewhere so I had no choice but to hit the reset button on my computer case and this time it reacted immediately instead of taking the way it used to do when it would seem to not respond but then 10 seconds later my PC would cut off and back on again.It strangly happed shortly after I had posted a comment on a Youtube video about Unity being better then Gnome saying that my system had not locked up for a month. I had also just installed Ubuntu 14.04 with the Unity desktop on my external USB Hard drive which did not boot up but that should not have any effect on my system since I did not even put Bootloader on my internal hard drive that Cylon Linux was installed on.

[QUOTE=dallase1;13201153]I did not try Mint again because I did not like it's boring outdated interface that was not very Modern and 3-D like Gnome in Ubuntu 12.04. I think what was causing the lock up was either the Mac Theme I tried to install or the Cairo Dock because shortly after installing the Cario dock app my system locked up so I uninstalled it and reinstalled Docky and now so far my computer has not locked up. [-o<

Why would software cause a Hard Lockup? I thought Linux was supposed to prevent software from totally crashing it. That is Windows Job to be un secure and allow programs to crash the system?

---

### Post by dallase1 on 2015-01-17
Why has no one respomded or answered my question? Why do they just tell me to not post the same subject twice and ask me why I did not stick with Mint? It's annoying to have a major problem and not get help from the Ubuntu Community that is supposed to be there to help.

---

### Post by sdrisk8262 on 2015-02-03
I am having the same problem with an older system, the GUI will work for a few secs but I can't click on anything to open but firefox and it crashes before I can do a search.  All the old fixes I found isn't working and most of them are dated 2012!!  Guess kernels have been updated, or servers are down so where the fixes could once be found are no longer there or directories moved.  I know that I have a Nvidia FX5200 that worked flawlessly in 10.04 after installing the Nvidia-173 drivers from Nvidia.  This system won't run long enough for me to go there and to download their driver.  Found a site that used the terminal to use apt-get to download it and after I do the computer is totally unusable.  The hold shift during boot to start Ubuntu safe mode isn't working so I have to do a fresh wipe and reinstall just to end up with the same problem again after I try someone elses "fix".  All fixes are out-date and do not work now.  Tried upgrading to 14.04 and it is just to much for my old computer, tried reinstalling 32-bit versions of 8.04, 10.04, 12.04 from the official Ubuntu ISO and they all fail before the install is complete.  The only install that I have gotten to work was the netboot 12.04 32-bit iso. If I swap to terminal mode right away it doesn't crash but the "fixes" I've found using terminal crashes it every time and I get garbage on screen forcing another wipe and reload.

---

### Post by Habitual on 2015-02-03
> **dallase1 said:**
> It's annoying to have a major problem and not get help from the Ubuntu Community that is supposed to be there to help.We're volunteers. Don't take it personally.

---

### Post by dallase1 on 2015-02-07
Sounds like you problem is far worse then mine. My system has been very stable for over a month now and the problem seems to have been fixed, mayde it was finally fixed in one of the updates. But every time I've said my system was finally stable and no longer locked up or I posted that it seems to be stable now and lock up free, it locks up shortly after that as if I jinxed it or it heard me say that and then decided to lock up again, of course that is silly and superstitious and I don't believe in jinks but it's a strange coincidence.
Now that I have posted that my systems seems stable I will see if it locks up after a day or to or maybe a few hours from now.

Maybe you should try Robo Linux at Robolinux.org it's based on Debian sable.

---

### Post by buzzingrobot on 2015-02-07
Many Ubuntu derivations exist, many of them are very much niche distributions. Without direct experience with the specific distribution someone is asking about, it's difficult to attempt specific answers or make specific recommendations.  "Based on" Ubuntu means they've changed some things.

---

