---
title: "A new low: Ubuntu 6.06.1 + 75Mhz Pentium + 64Mb + 1.5Gb + Openbox"
date: 2006-11-06
forum: Testimonials &amp; Experiences
---

### Post by K.Mandla on 2006-11-06
Just to show it can be done ... again ... this is a Dell Dimension 8200 P75t, [service tag]("http://support.dell.com") 5c7xg. 

[CENTER][[IMG]http://img212.imageshack.us/img212/4410/img_0001.th.jpg[/IMG]](http://img212.imageshack.us/my.php?image=img_0001.jpg) [[IMG]http://img212.imageshack.us/img212/4915/img_0003.th.jpg[/IMG]](http://img212.imageshack.us/my.php?image=img_0003.jpg) [[IMG]http://img212.imageshack.us/img212/2306/img_0002.th.jpg[/IMG]](http://img212.imageshack.us/my.php?image=img_0002.jpg)
[/CENTER]

This is a 75Mhz Pentium machine loaded up with 64Mb of SIMM chips, a massive 1.5Gb Western Digital Caviar hard drive, Ubuntu 6.06.1 and Openbox 3.3.1. 

[CENTER][[IMG]http://img212.imageshack.us/img212/3359/img_0004.th.jpg[/IMG]](http://img212.imageshack.us/my.php?image=img_0004.jpg)[/CENTER]

This machine dates back to 1995, and arrived at my doorstep replete with ISA network and sound cards and onboard S3 graphics. I added a slightly newer CDROM because the one in it wouldn't read a 700Mb CD. Best of all, it has PS/2 mouse and keyboard ports; this time I wasn't hamstrung by the absence of a working pointer device. :evil: 

I yanked everything but the essentials and wiped the drive clean. A server installation took 3.5 hours, with another hour or so to get a GUI in place. This uses ObConf and ObMenu (which means Python, et al, needed installation), XFE as a file manager and the XFCE terminal window for CLI access. Conky is keeping me advised of the system resources.

Bootup takes about three minutes, maybe more. Opening a terminal window takes close to 15 seconds. Everything moves impossibly slow at 75Mhz. It's like having your brain pressed through a bowl of mashed potatoes. :roll:

[CENTER][[IMG]http://img212.imageshack.us/img212/1900/img_0005.th.jpg[/IMG]](http://img212.imageshack.us/my.php?image=img_0005.jpg)[/CENTER]

In the end though, we have a 16-bit desktop at 1024x768 with transparent terminal windows. Best of all, the desktop boots on less than 22Mb, the entire installation takes less than 500Mb and you get a relatively working system with what amount to -- literally -- junk parts.

Functional? No.

Practical? No.

Fun? Heck yes! 

**P.S.: **The sharp-eyed viewer will notice that my IP address is 0.0.0.0. The ISA network card was disfunctional, my spare PCI network card is too new for the machine, and I can't find the Intel PRO 100 card I used to get [Turbo]("http://www.ubuntuforums.org/showthread.php?t=259901") online.

So how do you get kernel upgrades, install Openbox and Python and upgrade to a full GUI from a server installation without a network connection? 

Ah, grasshopper, you must be sneaky, like me. ... :mrgreen:

**P.P.S.: **I think this is about the bottom of the barrel for me. It's getting amazingly hard to find a working, complete system that predates this generation. Perhaps if you have an old 66Mhz Packard-Bell 486DX in the garage you can give it a try, but for myself, I'm out.

---

### Post by _lynX on 2006-11-06
Ubuntu never ceases to amaze me. Very nice!

How long did the install take?

---

### Post by d3v1ant_0n3 on 2006-11-06
Great work! Do you chew glass and nails for an encore? :p

---

### Post by pelle.k on 2006-11-06
kewl!
I have installed dapper on to a pentium pro 133 with 96 mb ram, and that was acctually with xfce as DE. I figure it would have ran a little better with openbox/fluxbox.
75 mhz is hard to beat though!

Why don't you set up a complete "desktop" in bash? w3m/links for browsing, mplayer (framebuffer) watching movies (you can acctually run mplayer with ASCI output if you want to!!), screen/dtach for virtual desktops, mpd for listening to music, autofs for mounting devices, nano as text editor, alsamixer as volume control. set it to boot in 1024x768 in grub. you get the picture. could be pretty sweet. And l33t for that matter. :)

---

### Post by raqball on 2006-11-06
Love it! Great post :)

---

### Post by machoo02 on 2006-11-06
Fantastic!  K.Mandala, I think that you need a better title than 'Ubuntu Master Roaster'.  How about: The Reanimator? Keeper of Lost Motherboards? Grand Master Flashmemory?  I've got an old toaster and a TI-82, wanna give them a go?

---

### Post by K.Mandla on 2006-11-08
> **_lynX said:**
> How long did the install take?
Around four hours or so, plus or minus the time it took to troubleshoot and concoct a way of updating and installing a GUI without a network connection. Took me a while, but worked great in the end.

> **d3v1ant_0n3 said:**
> Great work! Do you chew glass and nails for an encore? :p
:D ... I mean, :twisted: 

> **pelle.k said:**
> Why don't you set up a complete "desktop" in bash? w3m/links for browsing, mplayer (framebuffer) watching movies (you can acctually run mplayer with ASCI output if you want to!!), screen/dtach for virtual desktops, mpd for listening to music, autofs for mounting devices, nano as text editor, alsamixer as volume control. set it to boot in 1024x768 in grub. you get the picture. could be pretty sweet. And l33t for that matter. :)
Not a bad idea. I've toyed with the idea of a [text-only system]("http://www.ubuntuforums.org/showthread.php?t=260946"), if only as a music machine. But it's one of those back-burner projects that just never seems to be a priority. And now I'm all about building debootstrap installs and trying to boot to an iso that's on a hard drive. ... Sigh. :-k

> **machoo02 said:**
> Fantastic!  K.Mandala, I think that you need a better title than 'Ubuntu Master Roaster'.  How about: The Reanimator? Keeper of Lost Motherboards? Grand Master Flashmemory?  
Hmm. ... The Reanimator ... hmm ... :-k

> **machoo02 said:**
> I've got an old toaster and a TI-82, wanna give them a go?
Don't tempt me! :D

---

### Post by lazyart on 2006-11-08
If you leave the soundcard in, it could cron it's away along as an alarm clock... I'm just curious if you would have to set it 5 minutes ahead so that it can wake you up on time.

---

### Post by DoctorMO on 2006-11-08
My first computer was an 486DX 66Mhz, DOS and windows 3.11, that was back in 1992/3 when those machines cost a fair bit. that died and I didn't get my hands on a working computer until 1999 when I got a Pentium 75Mhz, god bless skips. It originaly has 8MB of RAM but like the one shown here we got it up to 64MB by finding the rare 16MB SIMMs (72pin, 16bit bus each?). but mine had a 500MB HDD upgraded to 4GB later on. it was running Photoshop 6 on a modded version of windows 98 SE, I gave it to a friend who replaced his 8088 in 2002.

I would have loved to have gotten my hands on Linux at that stage, stoped all the mucking about with windows.

---

### Post by GStubbs43 on 2006-11-08
Nice... I didn't even know dell made white computers... :-D

---

### Post by lazyart on 2006-11-08
I just looked at the picture of the guts... 2 ISA slots and one shared PCI/ISA. SIMM memory. A cpu with a heatsink.. no fan!  And good ol' COAST (**C**ache **O**n **A** **ST**ick sitting close by.

Ubuntu core says 386... anyone willing to go lower!?!

---

### Post by justin whitaker on 2006-11-08
Man, we need to bow at the foot of the master. What's next K.Man? Damn Small Ubuntu?

---

### Post by K.Mandla on 2006-11-09
> **justin whitaker said:**
> Man, we need to bow at the foot of the master. What's next K.Man? Damn Small Ubuntu?
:D Nah. Ubuntulite has that covered. These are just for my own edification, and to prove it can be done. It's nice to think that 11-year-old hardware is still, in a way, usable.

> **lazyart said:**
> Ubuntu core says 386... anyone willing to go lower!?!
I was wondering if it actually would, to be honest. I know DSL will run on a 66Mhz 486DX, but I was under the impression that was the absolute bottom rung. 

I don't know. The 386 machines I see at the recycling center are all in shambles and don't even have 3.5-inch floppies. I'm guessing you could netboot them somehow, but it would be ... so ... slow ... that I would pull out my hair trying it. 

> **GStubbs43 said:**
> Nice... I didn't even know dell made white computers... :-D
:D A looong time ago. They'll swing back after a while. After the silver phase is over. ;)

> **DoctorMO said:**
> It originaly has 8MB of RAM but like the one shown here we got it up to 64MB by finding the rare 16MB SIMMs (72pin, 16bit bus each?).
That's them. I pulled these from a P-2 I found and was shocked that they worked. I was going to keep it as low as possible, but (as you will recall) SIMMs have to be put in as pairs, and 32Mb alone is too little to run the installer.

> **lazyart said:**
> If you leave the soundcard in, it could cron it's away along as an alarm clock... I'm just curious if you would have to set it 5 minutes ahead so that it can wake you up on time.
And would be cheaper than a new alarm clock at Wal-Mart. :KS

---

### Post by voided3 on 2006-11-14
Am I seeing things or did that comp have an ATX power supply connector? A wasn't aware that ATX was around in '95. Anyway, hats off to you, I always have fun playing with old hardware and finding uses for it, usually as web browsers and music libraries. My slowest comp is 200mhz, but it used to be 166mhz (until I got creative with the board jumpers.... mmwahaha; to be safe I actually put a fan on the cpu though since it didn't have one). I got WinXP to run on it, but I think i'm going to put Damn Small Linux on it since it would be far better suited to the hardware setup (might even be QUICK *gasp*). Firefox and Winamp run just fine on XP, but because of all of the background stuff i can't control, it drags pretty bad unless i let it sit and sort things out for ten minutes after it boots (it's on the internet via ethernet). I think I might give Xubuntu a shot though first since i've grown accustomed to Ubuntu after having it for a while (hardly use WinXP anymore except for games, which I hardly do since I have other games on Ubuntu). 
Anyway, I always love to see the old stuff come off the basement shelves and onto the desktop. It's fun, educational, and practically free. Plus if it dies, you can give it a Viking funeral and find another one! (or recycle it like a responsible adult... harhar) Keep us posted on the calculator :-D

---

### Post by K.Mandla on 2006-11-14
> **voided3 said:**
> I got WinXP to run on it, but I think i'm going to put Damn Small Linux on it since it would be far better suited to the hardware setup (might even be QUICK *gasp*). Firefox and Winamp run just fine on XP, but because of all of the background stuff i can't control, it drags pretty bad unless i let it sit and sort things out for ten minutes after it boots (it's on the internet via ethernet). I think I might give Xubuntu a shot though first since i've grown accustomed to Ubuntu after having it for a while (hardly use WinXP anymore except for games, which I hardly do since I have other games on Ubuntu). 
If you haven't tried already, and if you're keen on using XP on that machine, you could look into [nLite]("http://www.nliteos.com/"), which strips out the XP install disc and leaves only the parts you want. I used to use it to build custom XP install discs for a 200Mhz machine I kept to listen to the BBC online. Like you mention, it was sluggish, but if it worked.

If you try Xubuntu and it doesn't work out for you, try learning Openbox. The machine in this post would have been utterly overwhelmed with Xubuntu, but with Openbox, it was almost usable. It's definitely worth learning, even if just for that.

Have fun!

---

### Post by darkhatter on 2007-03-10
all you need to do is get out an old geforce and show off some beryl screenshots

---

### Post by tsmgroup2 on 2008-11-10
Not to be a show-off or anything, but I still have a Tandy 1000 SX and a 2000, One works and the other needs looked at.

I also use to have the TRS-80 Model one and coco two as well, both have been placed in better homes, I hope.

I had two 486 DX's that were given away to any route travelers that wanted them.

My point is there are still a few old systems around and operating, I'm still looking for an ISO of ubuntu that can work very easily on the older less fortunate systems with only the bare essentials.

Thanks for the help and experience with Openbox, I for one, will definitely look into and start using it...

Any help in finding such an iso for future usage would be more than appreciated.

---

### Post by armandh on 2008-11-10
I have a 486-160mhz [an AMD 120 with the buss at 40 not 33 mhz] 3PCI slots 1 shared with an ISA and one more isa. it is happy running 98se but does not boot from a cd and I am not willing to spend the time [I'm collecting SSI and there isn't time to waste]

I did get DSL older equ. distro to fly on a 166 P1 think pad.

---

### Post by Paradoxfox93 on 2008-11-10
Dude I know a guy who had a P75-16MB laptop (IBM) and I could never even get windows 98 to be fully functional on that machine (It was designed to run 95).  Hardcore yo...I wish I'd have known about Linux back then too...


Right now I'm trying to put hardy on a P4-2.0Ghz with 256 DDR2100 (IBM A31)  It takes forever to load the live CD...I don't think it will.  I have some lessons to learn from this.

---

### Post by armandh on 2008-11-11
more memory! 256meg is barely enough to run on and as I recall a problem while partitioning. I got around this once with a seperate swap drive used during setup.

---

### Post by Paradoxfox93 on 2008-11-11
> **armandh said:**
> more memory! 256meg is barely enough to run on and as I recall a problem while partitioning. I got around this once with a separate swap drive used during setup.

That's interesting.  The alternate install worked fine, took a while but runs like a peach (Well....still working on tweaking the video and then getting sound to work later today).  The memory will be had but I'd like to write a post-install customization script (for video and sound tweaks and fixes) with custom xorg.conf whatever else I need to fix.

I must say this thread has indeed inspired me on this project!

---

