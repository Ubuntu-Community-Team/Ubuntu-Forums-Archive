---
title: "alpha3/daily desktop -no punchy Unity"
date: 2012-07-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-07-28
Installing the quantal-desktop-i386.iso on a Dell Dimension 3100(3GHz/Intel graphics) and finding that Unity 3D is not as punchy and snappy as it was with  alpha 1. Not really much of a regression. Just noticeable though.

 The daily really has initial video setup probs. You have to wait for Ubiquity to show up, then you can install normally.

---

### Post by ronacc on 2012-07-28
I have nothing to compare it to , I haven't had a working install from a daily or alpha since 3.5 kernel came along , todays daily installed and works , seems a bit laggy on some things but not too bad . I'm AMD64 here .

---

### Post by fjgaude on 2012-07-29
Latest kernel update, 3.5.0-6, speeds my Dell netbook mini-10, from about 40sec to 32sec, using **gtkperf**... that's a significant percentage improvement.

On my main box, Intel i5-2405S, it went from 4.2 to 2.67sec. Now what goes on here with this updated kernel?

On either machine Suspend works but will not Resume.

---

### Post by jerrylamos on 2012-07-29
> **ventrical said:**
> Installing the quantal-desktop-i386.iso on a Dell Dimension 3100(3GHz/Intel graphics) and finding that Unity 3D is not as punchy and snappy as it was with  alpha 1. Not really much of a regression. Just noticeable though.

 The daily really has initial video setup probs. You have to wait for Ubiquity to show up, then you can install normally.
Yes, Ubiquity so slow I wondered if it was broke.  Patience, Hortense, it finally showed up and actually ran.

I like crisp and sharp and snappy so I run Unity 2D.  Foggy and fuzzy and squirrelly is for other people especially the Compiz coders.

Now I would run 3D if someone has an easy performance test with meaningful results.  I've run gtkperf years ago I don't know if it would have any significance in this 3D question.

amd64 widescreen notebook.  Also have i386 3.3 gHz tower and a netbook all of which would run 3D if there was a benchmark.

Jerry

---

### Post by ronacc on 2012-07-29
If you are referring to the time from hitting return on your PW in the login window to desktop, I'm seeing that too in Gnome-Shell

---

### Post by fjgaude on 2012-07-29
> **ventrical said:**
> Installing the quantal-desktop-i386.iso on a Dell Dimension 3100(3GHz/Intel graphics) and finding that Unity 3D is not as punchy and snappy as it was with  alpha 1. Not really much of a regression. Just noticeable though.

 The daily really has initial video setup probs. You have to wait for Ubiquity to show up, then you can install normally.

Okay, using gtkperf I see the score went from 4.3sec in 12.04 than 4.2 in early 12.10 and now in A3, only 6.2. That's regression!

My box is fast, fast! Boots in five seconds, suspends in the same time.

---

### Post by balloons on 2012-07-30
There's something a bit concerning that happened in stealth to this new kernel. It's now using the deadline scheduler instead of the CFQ scheduler. That should affect your desktop "feeling", as well as maybe why things finally work for you ronacc.

If possible, try a kernel with the CFQ or another io scheduler and see if you can tell the responsiveness difference.

---

### Post by ventrical on 2012-07-31
CFQ scheduler sounds like some sort of Olympic stretching proceedure for gymnasts before they vault ... :) lol jk!!

 Could you elaborate please.

thanks.. :) lol

---

### Post by balloons on 2012-08-01
> **ventrical said:**
> CFQ scheduler sounds like some sort of Olympic stretching proceedure for gymnasts before they vault ... :) lol jk!!

 Could you elaborate please.

thanks.. :) lol

CFQ

[http://en.wikipedia.org/wiki/CFQ](http://en.wikipedia.org/wiki/CFQ)
[http://en.wikipedia.org/wiki/Completely_Fair_Scheduler](http://en.wikipedia.org/wiki/Completely_Fair_Scheduler)

BFS
[http://en.wikipedia.org/wiki/Brain_F*ck_Scheduler](http://en.wikipedia.org/wiki/Brain_F*ck_Scheduler) (yes, you'll need to edit the url, it's really called a curse word)
[http://users.on.net/~ckolivas/kernel/](http://users.on.net/~ckolivas/kernel/)

and Deadline

[http://en.wikipedia.org/wiki/Deadline_scheduler](http://en.wikipedia.org/wiki/Deadline_scheduler)


Googling should get you more.

All that to say, the kernel team switched the default to deadline, meaning your I/O interactivity experience (aka, the snappiness feeling) is different than before. It also means folks like ronacc whose system might not have liked the previous scheduler can now boot and operate. It's hard to pinpoint this as the reason, but since he can suddenly use his PC, it's the largest change I know of that *just* happened in this kernel release.

---

### Post by ventrical on 2012-08-01
Thanks guitara. Makes much more sense now.  If it includes other systems to work properly  then I am not going to complain about it. I was just making an observation, really.

---

### Post by ronacc on 2012-08-01
my luck didn't last too long after some updates wouldn't boot jul 30 am , daily's from jul 30 and 31 no good either , jul 30 installer crashes jul 31 dvd won't even boot .  I may just give up and wait for 13.04 , Ive wasted enough time and dvd's that this is getting tiresome .

---

### Post by ventrical on 2012-08-01
> **ronacc said:**
> my luck didn't last too long after some updates wouldn't boot jul 30 am , daily's from jul 30 and 31 no good either , jul 30 installer crashes jul 31 dvd won't even boot .  I may just give up and wait for 13.04 , Ive wasted enough time and dvd's that this is getting tiresome .

 just created an Aug 1st daily Usb startup. Ubiquity is working really good on all my machines since my last daily a couple of days ago .. but the opening live screen is all distorted on ATi, Intel and nVidia graphics cards.

 I'm just about to try again with todays daily.

---

### Post by ronacc on 2012-08-01
I'll try todays daily later , I wish SDC would reliably make bootable sticks for me but is hasn't since the start of 12.10 most of the time it makes the stick ok but my bios don't see it as bootable , so I end up burning a dvd for a lousy few megabytes that they just can't bear to leave out of the dailys .

---

### Post by ventrical on 2012-08-01
Ok... today's daily zsync worked great on my 2.8GHz, 512MBSdram with:
```

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600] (Secondary)

```

SDC worked just fine and the opening bootup screen craze&fuzzy seems to have been resolved.

Off to try it on some older nVidias. I may have to use alternate on the older adapter cards.

---

### Post by ventrical on 2012-08-01
The daily worked fine  (with nomodeset) on this <older> machine:

```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] LPC Controller (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: NVIDIA Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
ubuntu@ubuntu:~$ 

```Also very punchy Unity 2D in USB live mode.

 Nice progress !

---

### Post by ventrical on 2012-08-01
> **ronacc said:**
> I'll try todays daily later , I wish SDC would reliably make bootable sticks for me but is hasn't since the start of 12.10 most of the time it makes the stick ok but my bios don't see it as bootable , so I end up burning a dvd for a lousy few megabytes that they just can't bear to leave out of the dailys .

There were a bunch of SDC updates just a few hours ago.

 Whats your PC system again?

---

### Post by ronacc on 2012-08-01
gigabyte ga m55plus mobo , amd 64x2 4600 , 4gb ddr2 , nvidia 7600 gs , rtl8185 wireless . 6 drives 2 ide 4 sata + 1 ide dvd .

---

### Post by ventrical on 2012-08-01
> **ronacc said:**
> ... . 6 drives 2 ide 4 sata + 1 ide dvd... .

  I had a problem on my Dell D 3100 and my current Intel Dual Core where I tried to have  IDE and SATA set up together. USB will not work. The only way to get USB to work was to disable either the IDE or the SATA.  Why ? I don't know .. but the architechture I am using is not as current as  which what you are using so it may be a horse of a different colour.

---

### Post by ronacc on 2012-08-01
just to be on the safe side I'm d/l'ing the whole daily I've just been zsync'ing .

---

### Post by ventrical on 2012-08-01
> **ronacc said:**
> just to be on the safe side I'm d/l'ing the whole daily I've just been zsync'ing .


That may be the answer because it happened to me  with transitions in Precise where I waited too long to zsync , something got froze or locked and I could not get a good .ISO going.

---

### Post by ronacc on 2012-08-01
> **ventrical said:**
> I had a problem on my Dell D 3100 and my current Intel Dual Core where I tried to have  IDE and SATA set up together. USB will not work. The only way to get USB to work was to disable either the IDE or the SATA.  Why ? I don't know .. but the architechture I am using is not as current as  which what you are using so it may be a horse of a different colour.

this box isn't all that new I built it just for testing about 3 or 4 years ago . I have never had a problem with this box with a mixed sata Ide  config , but its predecessor was a nightmare if you had both sata and IDE drives it wouldn't boot off of an IDE dvd drive only a sata dvd which were about as common as hens teeth at that time , it drove me crazy trying to figure out that I had to unplug my sata hd's to get the dvd to boot , that mobo lasted about 2 months before I ripped it out and burned it in my trash barrel .

---

### Post by ventrical on 2012-08-01
> **ronacc said:**
> this box isn't all that new I built it just for testing about 3 or 4 years ago . I have never had a problem with this box with a mixed sata Ide  config , but its predecessor was a nightmare if you had both sata and IDE drives it wouldn't boot off of an IDE dvd drive only a sata dvd which were about as common as hens teeth at that time , it drove me crazy trying to figure out that I had to unplug my sata hd's to get the dvd to boot , that mobo lasted about 2 months before I ripped it out and burned it in my trash barrel .


Thanks for sharing that experience. I am planning to upgrade some of my mobos .. but I am not in a rush. I am going to keep trying to get both IDE and SATA going on the existing ones I have.

 Let me know if downloading the entire .ISO works because the zsyncs are usually working great here.

---

### Post by ronacc on 2012-08-01
they must be updating the .iso or something the d/l has stalled at 12 mb 3 times on me 2 times on ubuntu and once after I rebooted into sabayon to check if I had a networking problem on top of everything else .

---

### Post by ventrical on 2012-08-01
> **ronacc said:**
> they must be updating the .iso or something the d/l has stalled at 12 mb 3 times on me 2 times on ubuntu and once after I rebooted into sabayon to check if I had a networking problem on top of everything else .

Geepers .. you have been having some rough days over there :)

---

### Post by ronacc on 2012-08-01
yeah as far as this round of ubuntu goes , if it weren't for bad luck I'd have no luck at all !

---

### Post by jerrylamos on 2012-08-02
> **ronacc said:**
> yeah as far as this round of ubuntu goes , if it weren't for bad luck I'd have no luck at all !
Totally apparent to us users is Ubuntu is dedicated to adding as much "floss" "eye candy" "Compiz overhead" as possible depending on people buying ever faster more expensive pc's to make up for the non-application overhead.  Compiz buzzes right along even when I'm using full screen applications and there is really nothing Compiz is doing is even visible.

So Ubuntu-2D has been a bright spot for me.

Well, there's still Debian - I'm running Debian LXDE on my Raspberry Pi.  Running O.K. 

Jerry

---

### Post by ronacc on 2012-08-02
> **jerrylamos said:**
> Totally apparent to us users is Ubuntu is dedicated to adding as much "floss" "eye candy" "Compiz overhead" as possible depending on people buying ever faster more expensive pc's to make up for the non-application overhead.  Compiz buzzes right along even when I'm using full screen applications and there is really nothing Compiz is doing is even visible.

So Ubuntu-2D has been a bright spot for me.

Well, there's still Debian - I'm running Debian LXDE on my Raspberry Pi.  Running O.K. 

Jerry

my problem isn't compiz , its the 3.5 kernel , it will panic and lock up even from console with both x and lightdm not running . dosen't do it with 3.4 or any other distro ( 2 debian 2 sabayon 1 suse )

I do agree with you about the eye candy overload  , a waste of resources .

---

### Post by cariboo on 2012-08-02
> **jerrylamos said:**
> Totally apparent to us users is Ubuntu is dedicated to adding as much "floss" "eye candy" "Compiz overhead" as possible depending on people buying ever faster more expensive pc's to make up for the non-application overhead.  Compiz buzzes right along even when I'm using full screen applications and there is really nothing Compiz is doing is even visible.

So Ubuntu-2D has been a bright spot for me.

Well, there's still Debian - I'm running Debian LXDE on my Raspberry Pi.  Running O.K. 

Jerry

As usual, your complaint really doesn't make much sense, if you have a relatively up-to-date computer system, you shouldn't even notice compiz is running, unless you've added some customization via compizconfig-settings-manager. On my system, chromium with several tabs open, uses more resources than compiz.

My relatively up-to-date system uses a 3 year old AMD Athlon II X2 240 CPU, the same age Nvidia GeForce 210 graphics card and 2GiB of ram. at idle compiz on my system uses 1.6% cpu cycles, 6% ram.

---

### Post by fjgaude on 2012-08-02
> **cariboo907 said:**
> As usual, your complaint really doesn't make much sense, if you have a relatively up-to-date computer system, you shouldn't even notice compiz is running, unless you've added some customization via compizconfig-settings-manager. On my system, chromium with several tabs open, uses more resources than compiz.

My relatively up-to-date system uses a 3 year old AMD Athlon II X2 240 CPU, the same age Nvidia GeForce 210 graphics card and 2GiB of ram. at idle compiz on my system uses 1.6% cpu cycles, 6% ram.

Right on, man! My six-month old system, Sandy Bridge, shows compiz taking 85MB out of my 8GBs and 0% CPU at idle.

---

### Post by ventrical on 2012-08-02
> **cariboo907 said:**
> As usual, your complaint really doesn't make much sense, if you have a relatively up-to-date computer system, you shouldn't even notice compiz is running, unless you've added some customization via compizconfig-settings-manager. On my system, chromium with several tabs open, uses more resources than compiz.

My relatively up-to-date system uses a 3 year old AMD Athlon II X2 240 CPU, the same age Nvidia GeForce 210 graphics card and 2GiB of ram. at idle compiz on my system uses 1.6% cpu cycles, 6% ram.


For the most part compiz has the unique property of being at 'sleep' when there is no desktop activity. Firefox is what eats all the CPU cycles here. Not compiz. I like compiz and the effects.  I am not a gamer like many are here .. but I still like the way compiz handles certain desktop features. That is probably the main reason I got a GEforce 210 also. I just like those effects - easy on the eyes :)

---

### Post by ronacc on 2012-08-02
even worse , after todays update noe I can't even log into my updated precise install , when I try as soon as I hit return on my password it falshes to console for a couple of seconds , says something about plymouth common failed and then returns me to the login screen . using one of my sabayon installs to d/l todays daily , how embarrassing .

---

### Post by ventrical on 2012-08-06
Ok.. on an already updated install of Quantal , punchy Unity is BACK !! :)

---

