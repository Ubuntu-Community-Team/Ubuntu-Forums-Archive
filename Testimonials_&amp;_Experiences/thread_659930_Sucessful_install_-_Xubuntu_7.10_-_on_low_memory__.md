---
title: "Sucessful install - Xubuntu 7.10 - on low memory / limited drive space laptop"
date: 2008-01-06
forum: Testimonials &amp; Experiences
---

### Post by azteech on 2008-01-06
This weekend I successfully installed Xubuntu 7.10 on my Dell Inspiron 7500. The laptop has the following specs:

P2 400MHz (Intel 440BX chip set, PDA400 processor)
128Mb Ram (2x 64Mb, PC-100 SODIMM) (not shared with video card)
6.4 GB HD (FUJITSU) 
TORiSAN 8x DVD-ROM / Sanyo LS-120 Combo unit
ATI® 3D Rage Mobility-P 2x AGP, 8Mb Video Card (on board memory)
15" XGA LCD
3Com 10Mbps PCMCIA NIC
3Com 56K PCMCIA Modem
S-Video TV out

System has been idle and collecting dust for almost a year now. However, I need a mobile system again, but found I didn't want to shell $ out for a new laptop, nor did I want to stay within the confines of proprietary software; so I opted to go open source on the laptop. 

Laptop was purchased a while back with Win98SE installed on it. Instead of just formatting the HD and installing Xubuntu, decided to to test (and stress) the laptop by setting up a dual boot option. Over the course of three weekends, and numerous hours researching possible causes :-k, attempted to install Ubuntu/Kbuntu/Edbuntu 7.10, 7.04, and Linux Mint (Ubuntu derivative) with no success. ](*,) Each attempt froze when loading the LiveCD. I even downloaded and tried installing the alternate CD versions for each of them - all failed - each time when the OS installer was setting up software (various percentages toward the end of the installation process). As a last resort, having read it required less resources, decided to try Xubuntu.

Having failed with the other LiveCds, downloaded the alternate CD ISO for Xubuntu 7.10. After burning the ISO file to CD, started installing the new OS. During installation used GParted to split the HD into 3 partitions as follows: 3GB for Win 98, 3GB Xubuntu and 256Mb for swap. Elected to use Grub for booting the system. Suffice to say the install went smoothly, with no additional hitches encountered. I will admit installation went extremely slow; it took the better part of 8 hours to get everything installed and running. IMO this is due to the low memory, limited HD space, and Internet connection speed limitations (when obtaining software updates during install). Happy to say Xubuntu even set up the video card and LCD monitor resolution and refresh rates properly:). Resolution is set up for 1024x768 800x600 640x480, 24-bit color depth. @ 60MHz refresh.

( [IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] Note: According to Dell documentation, 1024x768/24-bit/60Mhz is the max resolution/color depth/refresh rate the LCD can handle. You can obtain higher resolutions by using an External Monitor)

I know most may say that dual booting with such a small HD was almost a worthless effort. But it was a challenge I wanted to tackle, as well as use the experience for what seemed a good test of the system; I wanted to see if it could be done. Now that my project task has been accomplished I plan to back up the win98 partition, reformat the HD, and reinstall Xubuntu. Additionally, since I have a spare 20GB HD (from a dead laptop) at my disposal, I will probably replace the 6.4GB HD with it. Regardless of what HD I use, I plan on upgrading to 512Mb memory to increase system performance and stability. 

There is one other thought I have, after reading numerous How-Tos for using flash drives in one fashion or another, and that is to use a USB Flash drive to store my /home partition on. That way I will always have my data with me where ever I go.:)

By going open source, and adding upgraded memory and HD, I figure I will be able to use the laptop for say another 5 years or more before having to buy a more powerful one.

Regardless, this laptop will always be way slower than my Sempron 3000+ desktop, which by the way is set up for Dual-booting with Ubuntu 7.10 (used for everything except banking and taxes) :) and WinXP (for banking/taxes) :(.

Hopefully, in the not so far off future, those who want choice, can rid themselves of the need for high cost hardware upgrades and proprietary software that needs to be patched/upgraded/replaced every-so-often because some manufacturer said we need to. Hopefully the Dell's and HP's of the software world will realize that we need quality software made for, or ported to Linux; software drivers for the hardware we use, or for personal finances/banking/taxes/games (even though there are some really good ones out there for the Linux platform), and others-yet-listed.
This is not to say that I believe software should be totally free of cost; I'm no fool, everyone deserves to be compensated in some shape or fashion for their time, and efforts, put forth during development/marketing/support of the software they created, or helped to create/modify/upgrade. But I mostly want to  applaud those who have unselfishly given of their time to develop the necessary open source hardware and firmware drivers, as well as all the application and utility software we use today; many of them receive little to no compensation for their accomplishments, and sometimes even less recognition for their efforts and contributions to the Linux community. Without them we most certainly would not be where we are today in the open source arena.

I apologize for getting off track a bit, and am truly not looking to start a flame war because my thoughts may not mesh with those of others. This last bit of ranting are my own thoughts about choices and options; Freedom to chose how and when we want to upgrade our systems and software; or chose what software to use, how we want to use it, manipulate it, and share our modifications for it, without being told you can't do that because it is not compatible or it is proprietary. IMHO, only when this happens can we truly shed the behemoths of the proprietary world.

Hope you enjoyed reading about my experiences, and are able to learn something that may be of use to you or someone you know. and again, if I offended anyone with my rantings above, I apologize; And say let's move on to bigger and better things and times. ):P

---

### Post by steve_d on 2008-01-06
Congrats on getting it installed, 

I have been toying with the idea of installing Ubuntu on my mothers laptop, shes running an older thinkpad which has xp on it (and really shouldn't). Shes getting a new laptop in a few months, but I'm interested to know what difference you see between using win98 on your laptop, and using xubuntu, as far as OS load speed, smoothness when loading programs, and general web browsing.

Thanks
-Steve

---

### Post by BeardlessForeigner on 2008-01-06
I recently installed Xubuntu 7.10 on my dad's 550 MHz AMD computer with 256 MB RAM and integrated graphics. This computer was a dual boot with XP. I noticed no speed difference between firefox in Xubuntu and IE in XP, or between file browsing in the two systems when I had hoped too to see a significant improvement in Xubuntu.

---

### Post by Agent86 on 2008-01-08
> **BeardlessForeigner said:**
> I recently installed Xubuntu 7.10 on my dad's 550 MHz AMD computer with 256 MB RAM and integrated graphics. This computer was a dual boot with XP. I noticed no speed difference between firefox in Xubuntu and IE in XP, or between file browsing in the two systems when I had hoped too to see a significant improvement in Xubuntu.

IMO Xubuntu 7.04 (or older) is much faster on low-performance machines than 7.10. I originally had Xubuntu Dapper on my Celeron 333MHz/512 MB/onboard graphics machine, and stepped the upgrades through Edgy, Feisty and finally Gutsy, spending a couple days on each version to look for any problems. Everything ran at acceptable speeds until Gutsy. I think the additional Gnome dependencies introduced in Gutsy killed the speed advantages of XFCE, on older machines like mine or your dad's, at least.

I just installed Xubuntu Gutsy on a Duron 600 MHz/128 MB/ATI Rage Fury machine and it feels no faster than the Celeron. I'm going to upgrade the memory to 512 MB and video to an Nvidia 6200 card and see how it does.

I tried Xubuntu 7.10 on an older VAIO laptop and it wasn't very stable. I tried Fluxbuntu 7.10rc but it doesn't feel much like Ubuntu/Xubuntu. I'm going to go back and try Xubuntu 7.04 on it since memory and video upgrades on this laptop aren't very affordable.

OTOH, a Duron 800 MHz/256 MB/Nvidia MX400 machine of mine handled the move from Xubuntu Feisty to Gutsy without much slowdown.

So you might try Xubuntu 7.04 on your dad's computer. If that's no help, I HIGHLY recommend Puppy Linux, which I run as a Live CD on the Celeron and the VAIO when I feel the need for speed - it flies and Puppy Linux 3.01 has excellent support for wireless networking, especially Ralink cards. Puppy handled my RT61 card w/ WPA easier than any *buntu flavor/version ever has. Puppy has a wide range of available software, but nothing like the *buntu repositories.

---

### Post by azteech on 2008-01-09
> **steve_d said:**
> Congrats on getting it installed, 

I have been toying with the idea of installing Ubuntu on my mothers laptop, shes running an older thinkpad which has xp on it (and really shouldn't). Shes getting a new laptop in a few months, but I'm interested to know what difference you see between using win98 on your laptop, and using xubuntu, as far as OS load speed, smoothness when loading programs, and general web browsing.

Thanks
-Steve
Thanks.

After playing with it a bit, will try to summarize my findings:

1) Find there is little difference in OS load times between Xubuntu 7.10 vs Win98. Difference is so minor that I would not recommend installing 7.10 on the Thinkpad if your intent is to gain speedy OS load times. However, I must point out that I did notice a slight change in load times, in favor of Xubuntu, after changing out the HD (6.4 GB HD to the 20 GB HD); plus i have observed a decrease in HD activity now that I have switched over to the 20 GB HD (most likely caused by heavy use of swap memory).

2) As far as smoothness and system response goes, I experienced what I perceived to be excessive wait times for applications to respond. Once the apps did open, I experienced slow responses to actions I requested (music playback, using OpenOffice (oO), playing a game (solitaire), etc). 
As observed in the "System Monitor" application panel, program loading often pegged CPU load at 100% (causing screen to freeze), with average norm being 50-60% (causing intermittent response lags), and extremely heavy use of the swap partition (on 6.4 GB HD swap partition was constantly at 85%+; on the 20GB HD, swap partition is averaging 25% usage). User memory used is reported to be roughly 48% when idle, roughly 59% when downloading OS updates, and 65-95% when installing updates or running apps. In all cases, I had system monitor running to observe system loading.
My suspects for this are:
    - the additional Gnome dependencies introduced into Xubuntu 7.10 (causing heavier loading of the PII/400MHz processor and video card)
    - low memory (128Mb) (instability and slow responsiveness of apps) (note: system memory is not shared with video card);
    - the limited 3GB HD space I initially installed 7.10 onto (heavy usage of swap space, plus instability and slow responsiveness of apps)
IMO, all these have killed reported speed advantages XFCE supposedly had when installed on older machines (as reported by others).  
Here i would have to give the advantage to Win98; apps were quicker in response and smoother to operate (oO, FF, music playback, etc). 

3) Web browsing - No discernible difference when using Firefox on 7.10 or Win98. Just remember to set tell Firefox to ignore IPV6 in the about:config screen before using the browser on either OS. Advantage: Win98 - app load time, as well as smoother response. Once loaded, there appears to be no discernible speed difference when using FF to browse the Web on either OS. However, wouldn't recommend opening more than one or two tabs at a time when using FF on either OS.

At this point, only the HD has been changed out and I have gone to an Xubuntu-only install on the 20 GB HD (though I did initially set up the 20GB HD for dual-boot just to test differences). I have yet to upgrade memory beyond the original 128Mb. I have no doubt once memory is upgraded to 256Mb memory (or more), that Xubuntu 7.10 will surpass Win98 in all aspects. 

Remember, I pursued this to stress test the laptop, as well as satisfy my curiosity for "can it be done". For the time being, I plan on maintaining 7.10 on the laptop. However, if I do not see a marked difference after upgrading memory (after I get tax refund back), I will probably fall back to an earlier version of Xubuntu.

So, IMHO I would recommend that you install an earlier version of Xubuntu (7.04, 6.10, or 6.06) on your mom's Thinkpad, as well as have minimum of a Pentium II/400Mhz processor (or better), 256Mb ram, and some breathing room on the HD.

---

### Post by wolfen69 on 2008-01-09
glad to hear you got it going. in the future, you may be interested in this [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) 

i got ubuntu installed (with the fluxbox DE) on an old Dell with only 64mb ram. it actually runs decent too.

---

### Post by azteech on 2008-01-09
> **wolfen69 said:**
> glad to hear you got it going. in the future, you may be interested in this [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) 

i got ubuntu installed (with the fluxbox DE) on an old Dell with only 64mb ram. it actually runs decent too.

Thanks wolfen69. Wish I had known the document existed before going through all the trials. But, hey I learned things :) ....
But now that I know it exists, will go through it, and see where I can make improvements.

---

