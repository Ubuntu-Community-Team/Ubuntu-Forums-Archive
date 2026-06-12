---
title: "Fastest Distro?"
date: 2009-05-27
forum: The Cafe
---

### Post by dioltas on 2009-05-27
Hi all,

So I'm thinking about making the switch from Ubuntu, it's served me well for the last few years but I think it's time to move on...
If I get a new faster laptop then I'll probably look to ubuntu again.

So I'm nearly finished my final year exams and should have some free time, looking to install the fastest system possible.

I'm thinking Arch or Gentoo with fluxbox. What do you guys think is the best option. Is compiling Gentoo very difficult?

---

### Post by LowSky on 2009-05-27
go with Arch, its a great distro, just remember to read the instructions on the wiki.

---

### Post by chucky chuckaluck on 2009-05-27
arch is fast, especially using reiserfs. i just recently reinstalled and it took me about twenty-five minutes to get it going, including X and a wm. i hear gentoo can take forever to install which, if you're looking for speed, is like driving to mars for a sale on toilet paper.

---

### Post by dioltas on 2009-05-27
> **chucky chuckaluck said:**
>  i hear gentoo can take forever to install which, if you're looking for speed, is like driving to mars for a sale on toilet paper.

Haha, good analogy. Arch it is then I suppose. Never heard of reiserfs before now. Is it as reliable as ext3?

---

### Post by ghindo on 2009-05-27
Define "fast."

---

### Post by aschwerin.moses on 2009-05-27
i wish to install arch in my system.. does anyone know how easy is it to configure xorg for 8600GT..

---

### Post by chucky chuckaluck on 2009-05-27
> **dioltas said:**
> Never heard of reiserfs before now. Is it as reliable as ext3?

i don't really know. i've never had trouble with it. i haven't tried ext3 on arch, yet (and am not likely to). you could probably search the arch forums and see what kind of things the more expert users have to say. xfs was slow and i've never needed to move very large files. 


[http://bbs.archlinux.org/index.php](http://bbs.archlinux.org/index.php)

---

### Post by dioltas on 2009-05-27
> **ghindo said:**
> Define "fast."

Fast, responsive you know. Want it to boot quickly. Want programs to open quickly, and run quickly. Don't want the system to freeze / crash. These have all become problems to some extent for me with ubuntu.

I have a lot of rubbish on my current system, so just going to back up all my music and start fresh. Looking forward to a "change of scenery" anyway. 

I'm not on my laptop at the moment, but iirc it's got 512mb ram and 1.73 GHz cpu so should be able to get some decent results with the right setup! It's a hp pavillion. Nothing wrong with Ubuntu and I'll probably switch back when I get a more powerful machine, maybe try ubuntu studio.

---

### Post by dioltas on 2009-05-27
Ya think I'll go with reiserfs so, thanks. Might as well try and sqeeze that extra bit out of it!

---

### Post by snowpine on 2009-05-27
Arch or SliTaz. Both are very fast and definitely a big "change of scenery" from Ubuntu. Or, if you want to stick with something similar to Ubuntu, try Debian or its slick derivative Sidux.

ps Don't forget about ext4, it's fast too.

---

### Post by chucky chuckaluck on 2009-05-27
> **dioltas said:**
> Ya think I'll go with reiserfs so, thanks. Might as well try and sqeeze that extra bit out of it!

if you're concerned, you could always do regular backups until you're more certain of it.


if you haven't done so, you should try out some of the lighter weight window managers (there's a bunch to choose from). on a laptop of limited power, that's just going to help all the more.

---

### Post by dioltas on 2009-05-27
Thanks for the advice lads. Just downloaded the arch iso there.

> **chucky chuckaluck said:**
> 
if you haven't done so, you should try out some of the lighter weight window managers (there's a bunch to choose from). on a laptop of limited power, that's just going to help all the more.

Ya, I think I'm gonna go with flux box. Going to setup conky and have a terminal open up at startup. Then a few keyboard shortcuts I think for firefox and music etc. 

In the instructions for arch it says all programs compiled for i686, I think my cpu is i386. Will that cause problems or should I be ok?

---

### Post by Mehall on 2009-05-27
Arch will not run on a computer older than 686.

No kernel.

Try Debian, installing only what you want, or go with Gentoo.

---

### Post by Daisuke_Aramaki on 2009-05-27
If you intend to have highly responsive system that should do nothing more than what you wish or nothing less, then you should go for something that gives you absolute control right after the bootstrap installed. and then its up to you to build your system the way you want. i believe source based distros offer the maximum control in that regard, since you can even build programs by removing support for some unnecessary libraries you might not need. only pitfall is compilation time. but it doesn't bother me at all.

---

### Post by chucky chuckaluck on 2009-05-27
> **dioltas said:**
> In the instructions for arch it says all programs compiled for i686, I think my cpu is i386. Will that cause problems or should I be ok?

you're out of luck.

---

### Post by dioltas on 2009-05-27
Oh well, think I'll try something else so, maybe debian or gentoo. Must check whether my laptop is 386 or 686 when I get home. Can't remember but I've a feeling it's 386. 

Thanks for the help, better go do some study for my last exam :)

---

### Post by Skripka on 2009-05-27
> **dioltas said:**
> 
In the instructions for arch it says all programs compiled for i686, I think my cpu is i386. Will that cause problems or should I be ok?

[B][I][U]
Your CPU is NOT i386.[/U][/I][/B]

I don't even have to ask what kind of processor you have to know that.  If you are running Ubuntu on your machine, you are at least running an i486, bare minimum.  Ubuntu will NOT RUN on an i386 CPU.

What exact make of CPU do you have?  PentiumII/III/IV etc?

---

### Post by chucky chuckaluck on 2009-05-27
> **dioltas said:**
> Oh well, think I'll try something else so, maybe debian or gentoo. Must check whether my laptop is 386 or 686 when I get home. Can't remember but I've a feeling it's 386. 

Thanks for the help, better go do some study for my last exam :)

you could always try a minimal installation of ubuntu. you already know it works on your laptop. i think, also, you can choose reiserfs, but i don't know how you'd go about it.

---

### Post by Skripka on 2009-05-27
> **chucky chuckaluck said:**
> you could always try a minimal installation of ubuntu. you already know it works on your laptop. i think, also, you can choose reiserfs, but i don't know how you'd go about it.

If he actually had an i386, Ubuntu wouldn't install or even run. ;)

---

### Post by chucky chuckaluck on 2009-05-27
> **Skripka said:**
> If he actually had an i386, Ubuntu wouldn't install or even run. ;)

he has it on there now.

---

### Post by dioltas on 2009-05-27
haha, ok probably not i386 so :redface:. Must have been thinking of an old computer I was working on or something. I'll check it when I get home. All going well Arch Linux it is. Thanks a lot!

---

### Post by Skripka on 2009-05-27
> **chucky chuckaluck said:**
> he has it on there now.

I refer you to this document:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Which specifically says that, at the bottom of that page:

> 
Absolute Minimum Requirements
Intel 486 processor 
32 MB of system memory (RAM) 
300 MB of disk space


---

### Post by chucky chuckaluck on 2009-05-27
> **Skripka said:**
> I refer you to this document:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Which specifically says that, at the bottom of that page:

why are you referring me to it? i didn't say anything about what kind of processor he has.

---

### Post by SuperSonic4 on 2009-05-27
Just put in the live cd and find out - if it throws up an error you know it won't work XD.

I would go for a CLI installation of arch. It really depends what you want to do with it

---

### Post by HappyFeet on 2009-05-27
A minimal install of Debian is also very fast. And easier.

---

### Post by kk0sse54 on 2009-05-27
Gentoo, download the minimal CD and do a stage3 by following the handbook to the word. The initial compiling will probably be the worst, depending on how fast your computer is though I can usually set Gentoo up in around a day and that's with me going to school. Plus the vast majority of that time doesn't require you to sit around and watch over it, so grab a good lunch and watch some TV :)

---

### Post by gn2 on 2009-05-28
Antix is worth a look.

---

### Post by monsterstack on 2009-05-28
If you boot Ubuntu with "init=/bin/sh", it'll probably boot up in about two seconds. I reckon all of the awesome terminal commands you can type in afterwards will execute almost instantly.

---

### Post by billgoldberg on 2009-05-28
> **dioltas said:**
> Hi all,

So I'm thinking about making the switch from Ubuntu, it's served me well for the last few years but I think it's time to move on...
If I get a new faster laptop then I'll probably look to ubuntu again.

So I'm nearly finished my final year exams and should have some free time, looking to install the fastest system possible.

I'm thinking Arch or Gentoo with fluxbox. What do you guys think is the best option. Is compiling Gentoo very difficult?

Gentoo will be faster than Arch but it's a bit harder to use.

I would just go with Arch and Fluxbox together with lightweight apps (pcmanfm, epiphany, ...)

---

### Post by .Maleficus. on 2009-05-28
Gentoo if you want the fastest possible, Arch if you're sane.  If you're really worried about speed, I'd go with Arch + abs, compiling any programs that you use frequently.  ABS will allow you to copy a build script from their rsync tree which when executed, will download the source, compile, and pacman will still be aware that the program is installed.
> **billgoldberg said:**
> Gentoo will be faster than Arch but it's a bit harder to use.

I would just go with Arch and Fluxbox together with lightweight apps (pcmanfm, epiphany, ...)
epiphany-git is the only package that would be worthwhile to him, since all of the others in the AUR require gnome-desktop.

---

### Post by TheSlipstream on 2009-05-28
Did anyone even *consider* that the OP may not yet have mastered Linux? I recommend Puppy Linux as a lightning fast and pre-organised distro. I find Arch annoying with its poor hardware detection (YMMV) and pointlessly lengthy install process.

---

### Post by gn2 on 2009-05-28
> **TheSlipstream said:**
> ~ pointlessly lengthy install process.

The longer it takes and the more work involved, the higher the degree of satisfaction at completing the task.

(IMO) It's an average distro with a fair bit of Emperor's New Clothes about it.

---

### Post by dioltas on 2009-05-28
Thanks for the advice lads. Should be able to manage Arch alright I'd say Slipstream, I've set up servers and stuff before on older machines. Should have some free time anyway so looking forward to a bit of a challenge!

My processor is a Pentium M, so i686 alright.. :)

Plan is arch with fluxbox, and a few light weight apps.

---

### Post by binbash on 2009-05-28
Do not go for gentoo unless you know what you are doing.Go for arch, it is easier to install.

---

### Post by gn2 on 2009-05-28
> **binbash said:**
> Do not go for gentoo unless you know what you are doing.

How do you learn without trying?

---

### Post by snowpine on 2009-05-28
> **TheSlipstream said:**
> I find Arch annoying with its poor hardware detection (YMMV) and pointlessly lengthy install process.

Arch does not have poor hardware detection; the user installing it is the hardware detector. ;)

---

### Post by Delever on 2009-05-28
Arch is not actually fast. If you add time required for setting it up.

Go with Arch only if you want lots of unique configuration options, because if you just need standard GNOME with file sharing, automatic video/vbox driver recompilation, same pulseaudio and same services... In the end speed won't differ much.

---

### Post by Skripka on 2009-05-28
> **TheSlipstream said:**
>  and pointlessly lengthy install process.

a)  Your 1st Arch install teaches you a great deal about how things work.

b)  Your 1st Arch may take an hour or 2 if you are being careful.  My second I did in less than 1/2 an hour.

---

### Post by SomeGuyDude on 2009-05-28
> **TheSlipstream said:**
> I recommend Puppy Linux as a lightning fast and pre-organised distro. I find Arch annoying with its ... pointlessly lengthy install process.

:lolflag:

The amount of actual time I spend getting a fully setup Arch install is, oh, mayyyybe five minutes. Ten at the most. The rest of the time is spent sitting there waiting for downloads and updates to finish. For a minimal, fully-usable desktop all you have to do is (not counting things like "hit next" or "say yes"):

1) Put the host name in /etc/hosts
2) Set root password
3) Restart
4) Set a user
5) Install ALSA/X
6) Install your DE/WM, tossing hal/fam into the daemons array
7) Start 'er up.

There's a LOT less involved than you'd think. The giant Beginners Guide isn't all about teaching you what to do as teaching you about the various files. You're not going to be editing modprobe, mkinitcpio, or fstab for example.

---

### Post by SomeGuyDude on 2009-05-28
> **Delever said:**
> Arch is not actually fast. If you add time required for setting it up.

Go with Arch only if you want lots of unique configuration options, because if you just need standard GNOME with file sharing, automatic video/vbox driver recompilation, same pulseaudio and same services... In the end speed won't differ much.

Unless you're spending five days setting up Arch I doubt the time spent there is going to make even a dent in your overall speed increase.

That said, your second point is pretty much spot-on. There's no NEED to use Arch. If you like GNOME and all it comes with, are adjusted to Ubuntu's package management system, then just stick with Ubuntu.

---

### Post by sertse on 2009-05-28
On the other hand, if the performance that much better? If you got a state of the art rig, the sheer grunt of your hardware would make any difference negligible. 

In the case of the more modest setup, good app selection does much more for computer reactivity. I have plastered many times on the screenshot thread of my debian nearly-xfce (a few individual components replaced with lighter alternatives) setup using only 55ram for example. This is from a debian base install building up, which is still "easier" than Arch. 

Then there are things like Crunchbang, with is practically OOTB, and still quite light and fast...

---

### Post by stwschool on 2009-05-28
Personally I want to take on the Arch and gentoo challenges at some point, mostly for the education, but for everyday use, Ubuntu is just fine. You can strip it as bare as you like and it'll do a decent job for most tasks. So for general use I've got my nice Gnome+Compiz+gnome-do setup, while for gaming through wine and other demanding apps or when I just want my machine super-fast, I use openbox which I've tweaked to my needs. One distro to rule them all.

---

### Post by chucky chuckaluck on 2009-05-28
i think it's possible to install arch without significantly learning anything new. i've installed arch five times and i still don't know asterisks.

---

### Post by dioltas on 2009-06-02
Hey guys. Managed to install Arch without problems. Installed flux and firefox. It's fairly fast at the moment. Gotta sort out my network settings and stuff, at the moment using iwconfig.. 

Here's my output from top:

```
[SIZE="4"]Tasks:  63 total,   3 running,  60 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.7%us,  0.7%sy,  0.0%ni, 98.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    505480k total,   269404k used,   236076k free,    11716k buffers
Swap:   996020k total,        0k used,   996020k free,   129904k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 2844 user      20   0  175m  65m  21m R  1.3 13.3   0:20.09 firefox            
 2897 user      20   0  2212  988  808 R  0.3  0.2   0:00.01 top                
    1 root      20   0  1692  580  512 S  0.0  0.1   0:00.54 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 work_on_cpu/0      
    8 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
   14 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
   15 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0 [/SIZE]
```

Firefox is really killing me, but If that's a problem I might try something like dillo. Alot to sort out yet, but I'm fairly happy with Arch. Just wanted to say thanks for the advice!

---

### Post by handy on 2009-06-02
Arch or SliTaz.  They both have their pluses & minuses.

If you have an ATi GPU, you may find some troubles with Arch & X if you use the ATi closed source drivers.  This may depend on which ATi GPU you have.

If you go with SliTaz, there is a much smaller amount of software available for it, so have a look at their list & see if it satisfies.  It is much easier to be up & running with SliTaz, & it is tiny too.

---

### Post by handy on 2009-06-02
> **dioltas said:**
> 
Firefox is really killing me, but If that's a problem I might try something like dillo. Alot to sort out yet, but I'm fairly happy with Arch. Just wanted to say thanks for the advice!

Firefox works fine with Arch, I'd keep looking for why you have a problem there.

---

### Post by K.Mandla on 2009-06-02
I'm late to the discussion (again), but for what little my opinion is worth, Arch is extremely fast when compared with Ubuntu, and Crux is that much faster again than Arch. 

The downside of course being that making the move from a precompiled, packaged binary distro to a source-based one, is that you have to build it all yourself. :|

---

### Post by dioltas on 2009-06-02
> **handy said:**
> Firefox works fine with Arch, I'd keep looking for why you have a problem there.

Killing me was a bit of an overstatement i suppose. Just that it uses alot of memory. Not a problem at the moment because nothing else i'm running is very resource hungry.

---

