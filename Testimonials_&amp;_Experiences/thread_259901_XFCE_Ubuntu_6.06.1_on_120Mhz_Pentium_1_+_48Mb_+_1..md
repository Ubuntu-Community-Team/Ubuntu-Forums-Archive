---
title: "XFCE Ubuntu 6.06.1 on 120Mhz Pentium 1 + 48Mb + 1.5Gb"
date: 2006-09-18
forum: Testimonials &amp; Experiences
---

### Post by K.Mandla on 2006-09-18
Just to show it can be done, this is Turbo, a no-name 120Mhz Pentium 1 desktop with 48Mb memory and a 1.5Gb hard drive. Turbo is sporting a fresh-brewed copy of Ubuntu 6.06.1, with an exceedingly sparse XFCE desktop installed. 

[CENTER][[IMG]http://img158.imageshack.us/img158/2138/img0005cw7.th.jpg[/IMG]](http://img158.imageshack.us/my.php?image=img0005cw7.jpg)[/CENTER]

Video is courtesy of an ATI Mach64 PCI video card. I pulled the sound card, the SCSI adapter and the modem (all ISA cards) just to keep things as clean and simple as possible. The NIC is an ancient Intel Ethernet PRO 100 pulled from the carcass of a Compaq desktop.

[CENTER][[IMG]http://img158.imageshack.us/img158/5224/img0001sl7.th.jpg[/IMG]](http://img158.imageshack.us/my.php?image=img0001sl7.jpg)[/CENTER]

Installation took about six hours, with four of that going to hardware troubleshooting (it's a new-to-me machine). Only two or so went to the necessary tweaks and adjustments to keep Turbo in a manageable state. Turbo is running the stock Ubuntu 2.6.15-26-386 kernel (the 686 drove him batty -- but I had to try it) and a 16-bit desktop at 1024x768.

[CENTER][[IMG]http://img158.imageshack.us/img158/7576/img0004br3.th.jpg[/IMG]](http://img158.imageshack.us/my.php?image=img0004br3.jpg)[/CENTER]

The only real problem is that Turbo's only mouse connection is via serial port. And I don't have a proper serial mouse (my adapters don't seem to work), so I'm mouseless. Which makes things a little difficult to use. ... #-o 

Why? 

Why not?! :biggrin:

---

### Post by jason.b.c on 2006-09-18
In the first picture , Why do you have a hard drive sticking out of the front of the black one...??

What's the disk in the xubuntu machine..??   Grub floppy..??

---

### Post by K.Mandla on 2006-09-18
The black one is a dual Xeon that I put an extra DVDRW in. It came from a machine that had a molded case tray and I had to take it off to salvage the drive. The inner tray is white, which is what you're seeing.

The floppy is a copy of Smart Boot Manager; Turbo won't boot from CD. :)

---

### Post by mips on 2006-09-18
Why not use something lighter like Fluxbox or are you into S&M ? ;)

---

### Post by Lord Illidan on 2006-09-18
I think Damn Small Linux is a better bet...and it works with serial mice, I've tried it myself.

---

### Post by K.Mandla on 2006-09-18
:D No, I'm just used to the interface. Openbox or Fluxbox would be a better fit, that's for sure. But until I get my hands on a working serial mouse and can be sure there's no fault in the connection, anything other than Ratpoison is pointless.

Get it? Pointless??! Hahaha! :lol: 

#-o Sorry. :oops:

---

### Post by K.Mandla on 2006-09-18
> **Lord Illidan said:**
> I think Damn Small Linux is a better bet...and it works with serial mice, I've tried it myself.
Yeah, but I had to try. DSL makes things too *easy*. :D

---

### Post by Lord Illidan on 2006-09-18
> **K.Mandla said:**
> Yeah, but I had to try. DSL makes things too *easy*. :D

lol!!

Want a challenge?? Install Vista on that.:-\"

---

### Post by K.Mandla on 2006-09-18
:D

I actually used the DSL 3.0.1 disc to prepartition the drive. I like the dir_index option for ext3, and I needed terminal access to preformat it.

---

### Post by K.Mandla on 2006-09-18
Ratpoison to the rescue!

After a quick *sudo aptitude install x-window-system-core ratpoison firefox*, I can get Turbo online now. I couldn't do it before, because I couldn't reach the Applications menu without a mouse.
[CENTER]
[[IMG]http://img230.imageshack.us/img230/2067/img0007wt2.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=img0007wt2.jpg) [[IMG]http://img230.imageshack.us/img230/5938/img0008ky5.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=img0008ky5.jpg)[/CENTER] 

It's clumsy for me, but it saves me $8 for a new serial mouse. 

I also managed to shave the boot time (to less than 2:30 #-o ) by stripping out most of ubuntu-minimal and ubuntu-standard, and disabling just about every service I could find. Of course, my Firefox start time is probably the worst on the forum. ... :rolleyes: 

Whoa! What a hot rod! :lol:

---

### Post by jason.b.c on 2006-09-18
> It's clumsy for me, but it saves me $8 for a new serial mouse. 

What..? , It dosen't have a mouse..??

What about a serial-to-ps2 adapter..??

Does it not have the ps2 port for a regular mouse..?

---

### Post by cptnapalm on 2006-09-18
This is one of the neat things about the free *nix: make old machines useful again.

---

### Post by K.Mandla on 2006-09-18
> **jason.b.c said:**
> What..? , It dosen't have a mouse..?? ...
Nope, it predates PS/2 ports. There's no PS/2 mouse port and the keyboard connects through the old-fashioned five-pin DIN plug. It's about as big around as your thumb and takes an adapter to get it going. You can still find the adapters in computer stores, but they're very pricey.

I can connect a PS/2 mouse through a serial port with an adapter, but for whatever reason, the PS/2 mice I use don't work (no matter what OS I use). I've used PS/2 ball mice and even an optical USB plus USB-to-PS/2 connector plus PS/2-to-serial connector, but no dice. (Not that I expected that to work, really.)

I have to find a straight serial-only mouse to connect it, but those things are about $8 new online. I don't see them at Staples. I could check my mom-and-pop computer store, but something tells me it would be about as much, maybe more. And even then, it might be that the motherboard is faulty. :( 

I have other options. There used to be PS/2 connector riser cards, but I think those were motherboard-dependent. I could also find a PCI USB card and connect that way, but that's probably more expensive than a serial mouse.

But this is only an experiment, and I don't plan on keeping Turbo for long. So I'm not keen on spending money on it. 

> **cptnapalm said:**
> This is one of the neat things about the free *nix: make old machines useful again.
Exactly! Or at least functional. ... :D

---

### Post by Dr. C on 2006-09-18
> **Lord Illidan said:**
> lol!!

Want a challenge?? Install Vista on that.:-\"

Actually if you want a real challenge. Install VMWare Server and then install Vista in a VM on that ](*,)

---

### Post by CydoniaRaven on 2006-09-19
KMandla, it seems that almost every time I come to this forum you manage to put a silly grin on my face.  Half the time I come in here just to see if you've done something new.  Absolutely fantastic. :KS

---

### Post by K.Mandla on 2006-09-19
:biggrin:

---

### Post by SoundMachine on 2006-09-19
Almost same setup apart from the CPU being an IBM Cyrix +166 and the videocard is S3 something, with xubuntu it crawls, with DSL, it flies.

---

### Post by jdong on 2006-09-19
> **K.Mandla said:**
> :D

I actually used the DSL 3.0.1 disc to prepartition the drive. I like the dir_index option for ext3, and I needed terminal access to preformat it.

Dude,

(1) Congrats on getting Xubuntu installed on that. Your story has really brought me great entertainment for this afternoon.

(2) dir_index is honestly the LEAST of your performance worries given that system ;)

(3) You can enable dir_index at any time with any existing ext3 volume, just run tune2fs -O dir_index /dev/device. As large directories that deserve indexing are accessed, they will be indexed on-the-fly. If you want to force this indexing to all happen ahead of time (I have no idea why, except if you're bored or something), boot onto a LiveCD and run "e2fsck -fD /dev/device". DO NOT run e2fsck on a mounted partition, even a read-only mounted partition!

---

### Post by K.Mandla on 2006-09-19
> **jdong said:**
> Dude,

(1) Congrats on getting Xubuntu installed on that. Your story has really brought me great entertainment for this afternoon.
Thanks! It was a dirty job, but someone had to do it. ;)

> **jdong said:**
> (2) dir_index is honestly the LEAST of your performance worries given that system ;)
Ain't that the truth! And I'm sure everyone is dying to know if it makes a difference, but I will NOT be doing speed tests with this machine! :rolleyes: :D

> **jdong said:**
> If you want to force this indexing to all happen ahead of time (I have no idea why, except if you're bored or something), boot onto a LiveCD and run "e2fsck -fD /dev/device". ...
Oooh! Thanks for that tip! I'll have to try that. ...

---

### Post by jdong on 2006-09-19
> **K.Mandla said:**
> 


Oooh! Thanks for that tip! I'll have to try that. ...

Just to make sure I made it clear, you have to run at least the tune2fs command to activate dir_index. The fsck command just forces all the indexing to happen ahead of time rather than on first encounter.


Good luck :)


and P.S. dir_index really doesn't do much unless you have thousands or hundreds of thousands of entries in a directory -- in which case that system would choke anyway :)

---

### Post by K.Mandla on 2006-09-19
Right on. I'll give it a shot. Thanks again!

---

### Post by enopepsoo on 2006-09-19
48 MB of RAM would have been a lot in those days.  Does it use simms or dimms?:-o 

awesome project btw.

---

### Post by K.Mandla on 2006-09-19
Simms -- 2x8Mb and 2x16Mb. That would have been a lot back then. It actually only had 32Mb in it to start with, but I added the 16Mb sticks to bump it up above 36Mb and keep the installer from crapping out.

---

### Post by kircher on 2006-09-20
Wow, this story has given me courage to install Xubuntu on a Celeron 433MHz, with 160MB ram, and a 4.3GB hd. It has on-board sound, on-board graphics (by SIS if I remember correctly), and a PCI network card and PCI modem. My Dad has never used a personal computer in his life (he's 50) and he thinks it's time to learn, and that machine should do him for what he'd use it for, and to learn at least. I was going to use Windows 98, but why not show him Linux instead? Besides, I know it would be a nightmare finding the drivers for Windows 98 for that machine, I know it was 3 years ago when I last formatted it.

---

### Post by K.Mandla on 2006-09-21
Give it a shot. It should work ... just make sure you give yourself plenty of time to get the job done.

And if X/Ubuntu seems sluggish, try Zenwalk or something similar. Ubuntu on the 120Mhz machine was completely irrational, totally irresponsible and utterly ridiculous. But there are plenty of distros that are tuned for hardware even that old.

But at 400Mhz+, you'll be fine. Good luck! :KS

---

### Post by jason.b.c on 2006-09-21
> **K.Mandla said:**
> Simms -- 2x8Mb and 2x16Mb. That would have been a lot back then. It actually only had 32Mb in it to start with, but I added the 16Mb sticks to bump it up above 36Mb and keep the installer from crapping out.

Damn.! , That thing is so old it has SIMMS in it..???

GEEEEZZZ...:D    Well hey , It runs though HUH..?  :D 

Did you ever get a mouse working on it yet..? , What type of adapter is that, that you have..?

I know at Best Buy you can buy a whole conversion kit for like ten bucks and it comes with alot..  I know , Because i need to get one so i can finish building my router wich is an old computer and that old style ( stupid keyboard and mouse ports ) motherboard...;)

---

### Post by K.Mandla on 2006-09-21
No, unfortunately I didn't. I used a PS/2 to serial converter, but for some reason no mice would work for me. 

I think it was a hardware fault. When I got it, it had an upgrade copy of Windows 95 on it and the mouse didn't work in that OS either. 

In any case, my only interest in it was to see if it would run Ubuntu, and since it's been done, it has no real purpose for existence. I've stripped it and I'm taking it to the recycle center later, to join its brethren in the great electronic afterlife. ... :cry: 

Perhaps one day it shall become a toaster, and make small children happy by giving them warm toast to eat. ... :confused:

Hmm. I think I can get a line on a 486SX. Now THAT would be a challenge. ... :tongue:

---

### Post by cunawarit on 2006-09-21
My first dabs into Linux recently happened with an old PentiumII 300 with two hard drives of 4Gb and 40gb, and 224 Mb of RAM. This is the machine I used when doing my PhD, which I started in 1998. It ran DSL and Debian nicely using fluxbox! Ubuntu ran, but I wouldn’t call it usable. 

Last week I got a Celeron 700 from Ebay for £30, it has a 10Gb hard drive and 128 of RAM. Runs Debian VERY nicely using fluxbox, I can even see some YouTube videos without that much skipping, and it plays Mp3 files no problem nicely when browsing the web. 

Now I am wondering what to do with the PII...

I do have a 2.53GHz Celeron D with 1 Gb of RAM and an 80Gb hard disc. However, this is my windows machine that connects me to the Internet via a USB ADSL modem. Sadly  the modem doesn’t work with any Linux distro I have tried, so until I invest on a router this machine will remain a Windows XP only machine. 

Hopefully Vista when it comes out, I am looking forward to that :)

---

### Post by jason.b.c on 2006-09-22
> **K.Mandla said:**
> 

Hmm. I think I can get a line on a 486SX. Now THAT would be a challenge. ... :tongue:

Well you should check out these pages..:eek: [http://www.opus.co.tt/dave/indexall.htm]("http://www.opus.co.tt/dave/indexall.htm"), Because i'm sure it can be done with this.. ==> [http://www.cisnet.com/glennmcc/]("http://www.cisnet.com/glennmcc/")

Be sure to check the whole page carefully... There's alot of really cool stuff..;)

---

### Post by alcamus on 2006-09-23
> **K.Mandla said:**
> Perhaps one day it shall become a toaster, and make small children happy by giving them warm toast to eat. ... :confused:

One more reason I should never read the forums while eating a late breakfast. The ensuing spit-take forced me to clean keyboard and monitor of partially chewed corn flakes.

I should have been eating toast.

---

### Post by K.Mandla on 2006-09-23
Good point. Next time I shall include a cereal-spitting disclaimer. :)

---

### Post by jdong on 2006-09-23
> **K.Mandla said:**
> 
Perhaps one day it shall become a toaster, and make small children happy by giving them warm toast to eat. ... :confused:


No, no, that's called a Pentium 4 Prescott... and you can use the leftover energy to blow-dry your hair, too :)

---

### Post by PatrickMay16 on 2006-09-23
> **K.Mandla said:**
> And if X/Ubuntu seems sluggish, try Zenwalk or something similar. Ubuntu on the 120Mhz machine was completely irrational, totally irresponsible and utterly ridiculous. But there are plenty of distros that are tuned for hardware even that old.

COCK-BENIS. Hello there.

Let me tell you. My brother left lying around a computer with an AMD K6-2 150MHz, and 256MB RAM. So I was messing around with it.
Now, I could get Ubuntu running kind of usable on it as a desktop, but I had to use the lightest programs possible.

I turned off all the unneeded services, used IceWM for the window manager, links2 with the -g option for web browsing, XMMS for playing audio, and rox-filer for drawing a desktop and managing files. 
I also tried using GAIM, which was kind of slow but good enough to use. 

So it worked alright, actually, though I understand that most people will probably want to use a more full-featured web browser. I tried using Mozilla, but it was awfully slow and therefore unusable. I imagine the same goes for firefox.

Here's a screenshot of that machine once I got it going nicely.
[http://img.photobucket.com/albums/v299/dusthillguy/penoch.jpg](http://img.photobucket.com/albums/v299/dusthillguy/penoch.jpg)

EDIT: Oh, BTW, I used Breezy and did a server install.

---

### Post by K.Mandla on 2006-09-23
Right on! That's a winner. That wallpaper is mighty crazy, though. ;)

If I had a proper mouse I might have pushed this one a little more. I'm sniffing around for something of the same caliber that doesn't have the same hardware issues so I can build it up proper. Just in the interest of science, of course.

We should have a contest: Best GUI on the slowest machine. With a 64Mb ceiling on memory and a 166Mhz cap on processor speed. Disk space is irrelevant. 

We can call it the MinBuntu Challenge!

Winner gets all the losers shipped to them at their expense. :KS

---

### Post by jdong on 2006-09-24
With hardware resources that low, realistically you'd want to be using almost a pure GTK1 environment... Either choose carefully from ubuntu repositories, or go with a distribution designed for old hardware (Puppy, Vector, Feather, DSL, and so on)


Personally, I'd recommend turning such systems into servers or other textmode appliances. The GPU is likely too weak to provide any meaningful performance... maybe MARGINAL performance as an X terminal to another machine, but don't expect a great performer out of a 166 with a 2MB video card ;)

---

### Post by JohnW on 2006-09-24
> **kircher said:**
> Wow, this story has given me courage to install Xubuntu on a Celeron 433MHz, with 160MB ram, and a 4.3GB hd...

Should be fine, I've got three 350MHz machines standing side by side at the moment, trying to get Openvpn bridging going between them.  One has the same 160Mb of ram as yours, perfectly usable.

I installed from the alternate 6.06.1 Xubuntu cd, because that's what I always use now, but I guess even the gui installer would have worked on such a massive amount of ram! :)

---

### Post by JohnW on 2006-09-24
> **K.Mandla said:**
> ...The only real problem is that Turbo's only mouse connection is via serial port. And I don't have a proper serial mouse (my adapters don't seem to work), so I'm mouseless. Which makes things a little difficult to use. ... #-o 


Brilliant post, K.Mandla!

Isn't that mouse issue understated though?  A **little** difficult???  I couldn't even get to square one, the top panel Application menu.  Many distros have a shortcut as standard for this, such as ctrl+escape.  Has a bug report already been submitted on this?  (I'm a beginner, I've not yet figured out how to do bugzilla).

I looked to see where you're located.  If it had been UK I'd have sent you a spare serial mouse!

---

### Post by jdong on 2006-09-24
ALT+F1 is the KDE/GNOME standard shortcut for the main application menu.

---

### Post by JohnW on 2006-09-24
> **jdong said:**
> ALT+F1 is the KDE/GNOME standard shortcut for the main application menu.

Fine with me.

Though you might have trouble getting the xfce guys to accept alt+f1, it's already used to get documentation.

I don't mind whether it's alt+f1 or ctrl+escape, as long as there **is **at least one such shortcut and there's a visual cue first time the system is booted (e.g. a dialog box).

Right now I think xfce has **no **shortcut for this, which seems like the worst possible choice for a guy without a mouse. :(

---

### Post by K.Mandla on 2006-09-24
> **JohnW said:**
> Right now I think xfce has **no **shortcut for this, which seems like the worst possible choice for a guy without a mouse. :(
I think you're right. I tried to surf around for keyboard shortcuts for XFCE before switching to Ratpoison, but didn't find much. I also tried that "right-click" key that most keyboards have. No dice.

It's not a big deal, but it did kind of hamstring XFCE, which otherwise is my \\:D/ No-1 fav DE!!!!!!111oneonene :tongue: :KS :KS =P~ 

:roll:

---

### Post by JohnW on 2006-09-26
> **K.Mandla said:**
> ...It's not a big deal, ...

(Panto time!) Oh yes it is!  It IS a big deal. :(

There are people out there who hate mice.  There are even people out there who are physically incapable of using a mouse.

I can see that a specialist distro focussing on, say, a community of artists, might reasonably make a mouse a requirement.  I cannot see why any general purpose distro should lock out a mouseless user.  If this is the intention of Xfce then it seems Ubuntu made a very poor choice and should have gone with some other desktop.  Otherwise it's "humanity to others, except others who don't use a mouse!".

Sorry, I'm drifting off topic.  Inspiring photos of an inspiring install -- a great thread to direct people to when they say "I've got this old machine, I'm thinking of throwing it away!".  Thanks!

---

### Post by K.Mandla on 2006-09-27
> **JohnW said:**
> Oh yes it is!  It IS a big deal. :(
You're right. I should have suffixed that to be "It's not a big deal *for me*," but I'm with you in principle. Cheers. 8)

---

### Post by K.Mandla on 2006-10-01
Just my luck: I got a real serial mouse today. Sigh. :rolleyes:

---

### Post by vaibhav on 2006-10-10
> **K.Mandla said:**
> Just to show it can be done, this is Turbo, a no-name 120Mhz Pentium 1 desktop with 48Mb memory and a 1.5Gb hard drive. Turbo is sporting a fresh-brewed copy of Ubuntu 6.06.1, with an exceedingly sparse XFCE desktop installed. 


This reminds me of the Red Hat 9 installation I had done some time back. The machine had only 24MB of RAM.
Did not run X though, only console mode.

Funny thing was Anaconda wouldn't run due to insufficient memory. I installed it on another machine, tar'ed the whole partition, burnt it on a CD and untar'red it on this machine. Minor modification to fstab, and all was set!

I used that machine for a while to surf the web through lynx.

---

### Post by K.Mandla on 2006-10-10
> **vaibhav said:**
> This reminds me of the Red Hat 9 installation I had done some time back. The machine had only 24MB of RAM.
Did not run X though, only console mode.

Funny thing was Anaconda wouldn't run due to insufficient memory. I installed it on another machine, tar'ed the whole partition, burnt it on a CD and untar'red it on this machine. Minor modification to fstab, and all was set!

I used that machine for a while to surf the web through lynx.
That is an EXCELLENT idea. Hmmm. ... :-k

---

### Post by NoWhereMan on 2006-10-11
> **K.Mandla said:**
> That is an EXCELLENT idea. Hmmm. ... :-k

w3m is installed by default, afaik

---

### Post by meheheh on 2006-10-15
Well. I'm trying to install Xubuntu now with the alternate installer on a 133 MHz Pentium 1 with MMX 32 MB RAM (the installer did warn me) and a 2 GB hard drive. It's a IBM ThinkPad 310ED I picked up for $10 at a garage sale today.

---

### Post by K.Mandla on 2006-10-15
Lucky you! I've been trying to piece together something in the sub-120 range for a few weeks. I can find motherboards and memory, and a hard drive isn't a problem, but for some reason processors are sparse. I'll have to keep my eyes open. :)

---

### Post by meheheh on 2006-10-15
It's taking forever to install though.... I'm not that big a fan of the Ubuntu/Debian installer.

---

### Post by raintheory on 2006-10-18
I have a 133mHz Pentium 1 32mb RAM Laptop as well that I would *love* to experiment with...   However the CD-ROM is shot on it.  :(

---

### Post by K.Mandla on 2006-10-18
If you have a network jack, you might be able to install via [Netboot]("https://help.ubuntu.com/community/Installation/Netboot").

---

### Post by vaibhav on 2006-10-19
Or maybe via a USB stick.

---

### Post by raintheory on 2006-10-19
Well unfortunately I dont think it can boot from USB or anything.  

Also the Ethernet is via Cardbus, and not built-in...

Thanks for the tips though, I won't be giving up on this guy.

---

### Post by jhenager on 2006-11-01
This machine would be by no means a recordholder, but I put 6.06 on a K6-2 450 MHz machine last night. I believe it has 98MB of RAM. It took a couple of hours. Didn't do any tweaks or anything. I just wanted to put Ubuntu on it so I could install Klik and get Tux Paint for my little girl. She loves the program, even though she constantly gets stuck because she clicks outside the paint area and changes Stamp to Text or something else, and keeps calling me back in to get the ladybug or penguin back.
It isn't very snappy, but I wouldn't call it unusable, either.

---

### Post by K.Mandla on 2006-11-01
Did you use Ubuntu, or Xubuntu for that? Xubuntu would run like a champ on it, and might be a little more snappy. 

(I used to have a K6-2 450. Ye gods, I loved that machine. ... :D Sigh. The good old days.)

---

### Post by compuguy1088 on 2006-11-15
Now what I've been working with a sub 500 Mhz computer, it may not be as impressive a feat as a sub 200 Mhz, but it works well for its specs. Its an Inspirion 7000 with a 333 Mhz Mobile Pentium II, 384Mb of ram, and a 4 GB hard drive. I got Xubuntu 6.10 working on it pretty well, with a bootup time of 1:52, which is ok. It gets the job done, with basic things, web browsing, etc. It also has a Broadcom 4306 PCMIA card for wireless, using the BCM43xx driver, which works with Network Manager as well.

---

### Post by Dr. C on 2006-11-15
I have installed Ubuntu Edgy on a Celeron 400 MHz laptop with 192 MB of RAM and 2.5 MB of Video RAM. Runs very well. Also very quiet the fan rarely goes on now unlike the previous OS. Ubuntu Edgy only uses 91 MB of RAM.

---

### Post by mysticrider92 on 2006-11-18
> **K.Mandla said:**
> Lucky you! I've been trying to piece together something in the sub-120 range for a few weeks. I can find motherboards and memory, and a hard drive isn't a problem, but for some reason processors are sparse. I'll have to keep my eyes open. :)

Have you looked at [www.tigerdirect.com?](www.tigerdirect.com?) I have seen AMD Semprons for less than $30 there. 

The idea to have a contest to see who can get a graphical Linux on a 166mhz processor might actually be fun. I found one distro that said it could run a graphical desktop with 4mb of ram.


I am going to see if my dad will let me try this on our 166mhz Pentium MMX that currently is running DOS.

---

### Post by K.Mandla on 2006-11-18
> **mysticrider92 said:**
> Have you looked at [www.tigerdirect.com?](www.tigerdirect.com?) I have seen AMD Semprons for less than $30 there. 
I did finally find one that was complete ... [a 75Mhz Pentium Dell]("http://www.ubuntuforums.org/showthread.php?t=294292"). And remember, that's *75Mhz*, not 750Mhz. And this machine was *120Mhz*, not 1.2Ghz. These are much, much slower than Semprons.

> **mysticrider92 said:**
> The idea to have a contest to see who can get a graphical Linux on a 166mhz processor might actually be fun. I found one distro that said it could run a graphical desktop with 4mb of ram.
Most definitely. I have laptops with only 2Mb VRAM that run Linux just fine. A little sluggish on redraw rates, but that's not really the fault of Linux; it's a hardware thing.

If anyone is keen on probing the lower limit, they're probably going to have to stoop to the 486 genre, or perhaps even 386-era hardware -- if those machines will even run Linux. I know Linux (DSL specifically) will run on a [486SX at 33Mhz]("http://www.damnsmalllinux.org/486.html"), but you have to find one of them first. ... ;)

Then, of course, there's that [286 machine running minix as a Web server]("http://minix1.woodhull.com/faq/srvr286.html"). It's fun to look at that one ... if you can get to it. It's usually too overwhelmed to respond; try when it's early, early morning in Europe. ;)

---

### Post by videodrome on 2006-11-19
Note that Serial Mice are often at the thrift stores for $1. I'm sure I could get you one if you message me.

---

### Post by greggonzo1 on 2007-01-03
Hello. I had posted on your website about installing 6.1 on my HP N3270 notebook. I followed your instructions to the T. My problem is that I do not have any GUI installed. Using startx I get the error message "command not found".

This computer previously had 6.06 and then 6.1 on it just straight from the CD. It would run in GNOME. XFCE, KDE, but it was terribly slow. I didnt have anything on it so I found your site and went on to follow the instructions. Used KillDisk, Partitioned the drives and installed a server (command line) installation. I re-ded this 2x because the first time I only partially installed Xfce and I didnt want to mess things up further.

Please tell me how I can get a GUI on my system (syntax). I like the sound of the system you had set up. But have no idea how to get to that point. 
Thanks for your advice
-Greg

---

### Post by K.Mandla on 2007-01-03
Hi Greg. It looks like there's some sort of quirk on straight XFCE installations under Edgy, where the standard *startxfce4* command doesn't work (or isn't properly set up) at first. I'll see what I can do to get a solution. Cheers. :D

---

### Post by CREEPING DEATH on 2007-07-21
> **K.Mandla said:**
> Ratpoison to the rescue!

After a quick *sudo aptitude install x-window-system-core ratpoison firefox*, I can get Turbo online now. I couldn't do it before, because I couldn't reach the Applications menu without a mouse.
[CENTER]
[[IMG]http://img230.imageshack.us/img230/2067/img0007wt2.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=img0007wt2.jpg) [[IMG]http://img230.imageshack.us/img230/5938/img0008ky5.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=img0008ky5.jpg)[/CENTER] 

It's clumsy for me, but it saves me $8 for a new serial mouse. 

I also managed to shave the boot time (to less than 2:30 #-o ) by stripping out most of ubuntu-minimal and ubuntu-standard, and disabling just about every service I could find. Of course, my Firefox start time is probably the worst on the forum. ... :rolleyes: 

Whoa! What a hot rod! :lol:

Wow you have the same monitor I do!
Why are you using EXT3?  My understanding is EXT2 or ReiserFS is faster on older machines.

CD

---

### Post by Kowalski_GT-R on 2007-07-24
hi,

[http://ubuntuforums.org/showthread.php?t=503144](http://ubuntuforums.org/showthread.php?t=503144)

not quite a 120Mhz, but still.....:) I was quite chuffed

solved the same mouse issue using a pci usb card and a cheap mouse

ciao,

Andre

---

### Post by imperius69 on 2008-10-11
> **K.Mandla said:**
> Nope, it predates PS/2 ports. There's no PS/2 mouse port and the keyboard connects through the old-fashioned five-pin DIN plug.

so u telling me that thing is older than my 286 ibm ps1 machine who as ps2 entry for mouse and keyboard :lolflag:

---

### Post by K.Mandla on 2008-10-11
> **imperius69 said:**
> so u telling me that thing is older than my 286 ibm ps1 machine who as ps2 entry for mouse and keyboard :lolflag:
Well, I thought that the PS/2 mouse port wasn't available until the PS/2 itself became popular, but I could be wrong. If you have a PS/1 with a PS/2 mouse port on it, that would be cool. :)

I said "predates" mostly because that PS/2 port was another proprietary shape that eventually became commonplace. I've found machines as new as 1996 or 1997 that still only had fat DIN ports and relied on riser boards for that mini-plug style. 

Fun though, huh? :biggrin:

---

### Post by imperius69 on 2008-10-12
would be cool no, its cool :p

Still have it, still works, with original mouse and keyboard :)

IBM PS-1
20 Mb HD, 1Mb Ram, 10 MHz CPU, Floppy drive, original DOS 4.0

[http://en.wikipedia.org/wiki/PS/1](http://en.wikipedia.org/wiki/PS/1)

:)

mine is the 2011 model, but NO MODEM, so the wiki info is wrong about that.

:guitar:


PS - i wonder if there is a linux that works on it :lolflag:

---

### Post by darrenn on 2008-10-13
Would this computer work with the new xubuntu? How about the fluxbox version of linux mint?

---

