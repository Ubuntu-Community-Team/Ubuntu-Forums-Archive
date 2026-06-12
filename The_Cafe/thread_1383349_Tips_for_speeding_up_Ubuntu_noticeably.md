---
title: "Tips for speeding up Ubuntu noticeably?"
date: 2010-01-17
forum: The Cafe
---

### Post by humphreybc on 2010-01-17
Hi there,

So I've been using Ubuntu for a year or so. I'm fairly experienced, and I have already implemented a few tweaks to try and speed up my laptop.

BUT I want to squeeze everything out of my hardware!

What else can I do to speed up stuff? I'd prefer things that I can easily remember for when I do a fresh install...

Danke Schon!

---

### Post by Paqman on 2010-01-17
Got plenty of RAM? Start using ramdisks, and install preload.

---

### Post by ssam on 2010-01-17
most of the simple generic ways to speed up ubuntu are installed by default. (though i don't understand why preload is not installed by default).

you could switch to smaller programs with less features. abiword is faster than openoffice, but can't do as much. you could disable features that you don't need.

if there are specific places where you think ubuntu or its applications are slow, you could learn to profile them, and find out what the problem is, and how it could be fixed.

or you could use gentoo to make a highly optimised distro. it lets you optimise to your CPU, and dissable compile-time features (accessibility, support for various file formats etc) in software.

---

### Post by markp1989 on 2010-01-17
you can try replacing gnome with openbox or another light window manager

---

### Post by mkvnmtr on 2010-01-17
It looks to me like I am going to install Lubuntu when it is ready with 10.04. That might be your best option. It is much lighter and seems to lack a lot of the apps that I never use. I have the LXDE desktop on a PCLinux distro and I really like it. I think if you want fast Ubuntu that will be it.

---

### Post by humphreybc on 2010-01-17
Eh no it's not painfully slow. I'm running Gnome. Specs are fairly decent:

Intel Core 2 Duo 2.2Ghz
ATI HD2600 512mb
3GB DDR2 RAM

I was just wondering what else I could do to increase responsiveness.

I found [this thread]("http://ubuntuforums.org/showthread.php?t=189192") which I'll look through tomorrow.

Thanks for your responses thus far.

---

### Post by gradinaruvasile on 2010-01-17
Use Xubuntu instead of the default Gnome. I use it and its very noticeably faster - and the comp has Core2Duo 2.0 GHz CPU.

In Gnome there are some apps/processes that not many use. Nautilus itself is a bloated piece of software, there are linked apps like Evolution that has background processes etc. Windows draw/move slower than in Xubuntu
Its a bit of bloatware if you ask me.

Also use lighter apps where you can - as browser i recommend Chromium - it kicks Firefox's *** in rendering speed and stability (even in its current alpha/beta stage) - i tested it in slower hardware too and it rocks.
And as a rule of thumb avoid non-native-GTK apps where you can.

---

### Post by ratcheer on 2010-01-17
Run bum and deselect the services you don't need.

Tim

---

### Post by John Bean on 2010-01-17
> **gradinaruvasile said:**
> Use Xubuntu instead of the default Gnome.
...
as browser i recommend Chromium - it kicks Firefox's *** 
...


This reply doesn't really address the question, since the speed gained is at the cost of lost functionality. Taken to its logical conclusion this approach leads to the answer not use a desktop at all... ;-)

---

### Post by humphreybc on 2010-01-17
Wow I just installed preload and it does make a huge difference. This should be installed by default.

I already use Google Chrome, I've already disabled startup services and applications, I've already removed unused applications/residual config data/orphaned packages etc etc

I guess there's not much else one can do except go to XFCE - But I like Gnome too much :)

---

### Post by Psumi on 2010-01-17
> **John Bean said:**
> This reply doesn't really address the question, since the speed gained is at the cost of lost functionality. Taken to its logical conclusion this approach leads to the answer not use a desktop at all... ;-)

Is there a multi-client IM for terminal? (IE: Pidgin/Ayttm for Desktop)

Is there a web browser for terminal that can run flash and not botch up javascript, etc?

Is there a gstreamer-backend terminal media-player with repeat-one track forever option?

> **humphreybc said:**
> Wow I just installed preload and it does make a huge difference. This should be installed by default.

No, it shouldn't. I have a 512 MB RAM System still, and am not giving it up for anything anytime soon, and by a minimal install GNOME/XFCE take up as much as 212 MB at the most I have seen alone (almost 300 MB RAM for installing an APP while doing other things), so preloading it all (the entire OS) into RAM wouldn't cut it for me.

---

### Post by John Bean on 2010-01-17
> **Psumi said:**
> Is there a multi-client IM for terminal? (IE: Pidgin/Ayttm for Desktop)
(etc)

I think you're suffering from irony deficiency ;-)

---

### Post by cascade9 on 2010-01-17
If you arent using 64bit already, install it next time. Its faster in general, and a lot faster on some tasks. 

Also, while this doesnt help that much, its worth doing- go into your BIOS and turn off all the junk you dont need (typically serial ports, parallel port). If you have a floppy disc but dont use it (90%+ of computers) disconnect the floppy drive, and turn it off in BIOS as well.

---

### Post by oldschoolrockstar on 2010-01-17
I have an old sony vio laptop that holds a whopping 10 gig hard drive and 128mb or ram at the most. I run it under Fluxbuntu, but I had to installed Ubuntu 9.04 first to get my wireless card working, disable and deleted all the programs I didn't need. Then I installed the Fluxbuntu from the package manager. I rebooted the computer and changed the desktop sessions from Ubuntu to Fluxbuntu. Now I can actually what youtube videos and my music doesn't skip from my dvd drive. That's noticeably faster to me.

---

### Post by joey-elijah on 2010-01-17
> **cascade9 said:**
> If you arent using 64bit already, install it next time. Its faster in general, and a lot faster on some tasks. 

Also, while this doesnt help that much, its worth doing- go into your BIOS and turn off all the junk you dont need (typically serial ports, parallel port). If you have a floppy disc but dont use it (90%+ of computers) disconnect the floppy drive, and turn it off in BIOS as well.

Doh! I -never- remember to do that! I swear my BIOS also tries loading typewriters, dinosaurs, blimps, robots from the future and holographic stickers from the 90's. (i.e. it's slow, so thanks for the tip!)

---

### Post by joey-elijah on 2010-01-17
> **humphreybc said:**
> Wow I just installed preload and it does make a huge difference. This should be installed by default.

I already use Google Chrome, I've already disabled startup services and applications, I've already removed unused applications/residual config data/orphaned packages etc etc

I guess there's not much else one can do except go to XFCE - But I like Gnome too much :)

Switching window manager just to get better performance on CURRENT GEN hardware is not an acceptable recommendation IMO. :P 

I probably could squeeze a ton more performance out of my hardware if one tried (and one hadn't accidentally reinstalled Ubuntu using a x86 disc >_<). 

going of on a tangent, having only ever used x64 bit Ubuntu since Gutsy it's really -odd- using x86 and not having to use some of the 'hacks' or 'fudges' to get some things to run... 

Any-noddle - Thanks for mentioning preload tho Mr HBC, i'll check that out. =)

---

### Post by humphreybc on 2010-01-17
Heh yeah I've been using 64 bit ever since I first installed Ubuntu.

I was looking for more "un obvious" ways to speed up Ubuntu.

> 
I swear my BIOS also tries loading typewriters, dinosaurs, blimps, robots from the future and holographic stickers from the 90's. (i.e. it's slow, so thanks for the tip!)


Haha!

So turning off BIOS stuff can make a difference on performance? I never knew...

---

### Post by gradinaruvasile on 2010-01-17
Well i never noticed any... 
Primarily its the Desktop Environment (Gnome, Xfce, KDE etc) that shapes the overall experience. 
Xfce is the fastest (and uses the least amount of RAM) of all i used (from the above 3) - there are faster ones, but not officially supported.

---

### Post by k64 on 2010-01-17
I would recommend [building your own kernel]('http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.3.tar.bz2').

---

### Post by ssam on 2010-01-18
i made a brainstorm entry
[Install preload by default]("http://brainstorm.ubuntu.com/idea/23356/")

---

### Post by nothingspecial on 2010-01-18
On my oldest and crappiest machine (which is actually my main one). I installed Ubuntu Minimal, xorg, openbox and firefox. It`s my fastest computu.

The cli is the fastest way to run ubuntu.

I wouldn`t have bothered with the last 3 except I like to see all your fancy avatars.

---

### Post by humphreybc on 2010-01-18
Preload has made a huge difference on my machine. I don't have a "before" video, but check out this one I just made today. Apps open at light speed, it's blazingly quick and responsive. The jerks are just due to recordmydesktop.

[http://www.youtube.com/watch?v=DMDjzqc9cIo](http://www.youtube.com/watch?v=DMDjzqc9cIo)

---

### Post by Psumi on 2010-01-18
For those using preload:

> preload monitors applications that users run, and by analyzing this data, predicts what applications users might run, and fetches those binaries and their dependencies into memory for faster startup times. 

Note that installing preload will not make your system boot faster and that preload is a daemon that runs with root priviledges. 

From ubuntu package site.

---

### Post by k64 on 2010-01-18
Here's some instructions on building a custom kernel:

Extract the [source tarball]('http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2') recursively inside /usr/src. Note that there is a cleanly made directory inside the tarball where ALL files are located.

Once extracted, open a terminal and run ```
$ sudo make xconfig
``` provided you have Qt 3 installed. From here, you can check and uncheck kernel modules to be built.

Once you have configured the kernel for just the hardware you need: ```
$ make dep && make clean && make bzImage && make modules
```.

Once this command runs its course, copy the kernel image into /boot, rename it to "vmlinuz", and run ```
$ sudo make modules_install
```.

You may need to edit your grub configuration file to boot the new kernel. You will notice a huge performance increase.

---

### Post by lswb on 2010-01-18
I agree with everything k64 said except his last sentence.

---

### Post by mamamia88 on 2010-01-19
nvm

---

### Post by Telecaster72 on 2010-01-19
From that video i would say, turn off desktop effects ;-)
No but seriously, try out xfce or lxde, use light icon themes, i installed lxde that uses openbox, my system after i boot is using a whoppin' 95 MB ram, and that is a default Karmic installation...
Lxde is somewhat not dry behind the ears, but xfce has matured well into a fullfledged gnome or kde beater...

---

