---
title: "minimal internet only boot ?"
date: 2007-11-28
forum: The Cafe
---

### Post by delfick on 2007-11-28
hello

I was wondering....

how possible would it be for a distro who's sole purpose is to boot as fast as possible into an internet browser...

as in when it boots, the only thing you can do is browse the internet.

would be great if all you want to do is use the internet for a minute and the computer is turned off...

(happens to me quite often when I want to check gmail, gmail calendar, google docs (google addict I know), though sometimes all I want to do is check an 'real' website as well :D.....

cause if all this distro did was surf the net, then I assume it'd take less than a minute to be operational.....

any thoughts, ideas, put downs, people wanting to do this ??

:D

and it might actually make a use for webOs' after the novelty wears off :D
(and to avoid too much backlash, this wouldn't at all aim to replace the current functional desktops at all)

---

### Post by popch on 2007-11-28
I'm not quite sure, but I seem to remember reading an article about a motherboard manufacturer who put Linux with a Browser into the BIOS. Possibly Asus, possibly two or threee weeks ago.

---

### Post by delfick on 2007-11-28
I read that article

edit : still have it bookmarked [http://www.phoronix.com/scan.php?page=article&item=869&num=1](http://www.phoronix.com/scan.php?page=article&item=869&num=1)

(infact I think it could be inspiration for my idea.... :D)

though my idea might even be more basic than that.......

where the aim is to be usable as quickly as possible and have the single purpose of browsing the internet...

---

### Post by Dragonbite on 2007-11-28
Should be possible.

You could probably do a minimal install (server install?) from an alternative CD, add X windows and Firefox (w/Flash and Java?) and see about setting Firefox to auto-start.

I've thought about this project too, even if the website it opens up to is a local intranet site (which is what I'd have to do because I'm dial-up).

If you want it like a kiosk into the local intranet ONLY I think there are ways to limit Firefox and even make it so you cannot save to the hard drive (like no /home/ directory to call your own, or no write permissions?)

*Hmm... if I get a more powerful laptop for myself I can take this old/weak laptop and set it up as a web appliance and put it in the kitchen.... argh! Now I'm going to be thinking of this instead of the dozen or so projects at home I already have!!*

EDIT: Thinking about it, I don't know if Firefox would be the better or Opera/Mozilla (SeaMonkey?) that includes  eMail client. This way you still only open 1 application to browse but it also runs your email and since GMail now includes IMAP connection you don't have to actually download anything.  Food for thought.

---

### Post by n3tfury on 2007-11-28
> **delfick said:**
> 



would be great if all you want to do is use the internet for a minute and the computer is turned off...



your hardware will hate you in due time.

---

### Post by Dragonbite on 2007-11-28
> **n3tfury said:**
> your hardware will hate you in due time.
My computers already hate me, so I've nothing to lose ;)

---

### Post by bernied on 2007-11-28
I don't think you need X, [links2](http://en.wikipedia.org/wiki/Links_%28web_browser%29) will run in the framebuffer.

But something tells me you'll spend more time setting this thing up than you'll ever save with your fast switching on.

---

### Post by Dragonbite on 2007-11-28
> **bernied said:**
> I don't think you need X, [links2](http://en.wikipedia.org/wiki/Links_%28web_browser%29) will run in the framebuffer.

But something tells me you'll spend more time setting this thing up than you'll ever save with your fast switching on.

Can it handle FLASH?
I think it would be best to stick with the more mainstream only because they are more supported for things such as FLASH and AJAX which Google uses intensively.

---

### Post by Depressed Man on 2007-11-28
> **popch said:**
> I'm not quite sure, but I seem to remember reading an article about a motherboard manufacturer who put Linux with a Browser into the BIOS. Possibly Asus, possibly two or threee weeks ago.

Probably the EEE PC? My friend got one, I tried it out. Sort of neat (but I could never use it since it's so small plus it's so limited power wise).

---

### Post by popch on 2007-11-28
> **Depressed Man said:**
> Probably the EEE PC? 

Not the EEE PC but a motherboard. Someone already has found it:

> **delfick said:**
> I read that article

edit : still have it bookmarked [http://www.phoronix.com/scan.php?page=article&item=869&num=1](http://www.phoronix.com/scan.php?page=article&item=869&num=1)
.

---

### Post by init1 on 2007-11-28
> **delfick said:**
> hello

I was wondering....

how possible would it be for a distro who's sole purpose is to boot as fast as possible into an internet browser...

as in when it boots, the only thing you can do is browse the internet.

would be great if all you want to do is use the internet for a minute and the computer is turned off...

(happens to me quite often when I want to check gmail, gmail calendar, google docs (google addict I know), though sometimes all I want to do is check an 'real' website as well :D.....

cause if all this distro did was surf the net, then I assume it'd take less than a minute to be operational.....

any thoughts, ideas, put downs, people wanting to do this ??

:D

and it might actually make a use for webOs' after the novelty wears off :D
(and to avoid too much backlash, this wouldn't at all aim to replace the current functional desktops at all)
TTY basically does that. It's only 5MB and has retawq. 
[http://www.minimalinux.org/ttylinux/showpage.php?pid=1](http://www.minimalinux.org/ttylinux/showpage.php?pid=1)

---

### Post by delfick on 2007-11-28
yay, some decent conversation :D

> **init1 said:**
> TTY basically does that. It's only 5MB and has retawq. 
[http://www.minimalinux.org/ttylinux/showpage.php?pid=1](http://www.minimalinux.org/ttylinux/showpage.php?pid=1)

> command line interface, no graphical user interface (GUI)

maybe not :D


I will try with the server install when I get my new harddrive
sounds promising......

---

### Post by delfick on 2007-11-28
> **bernied said:**
> I don't think you need X, [links2](http://en.wikipedia.org/wiki/Links_%28web_browser%29) will run in the framebuffer.

But something tells me you'll spend more time setting this thing up than you'll ever save with your fast switching on.

I don't think it'd be worth it having it that basic

of course I don't know how it all works, so I assume it's silly to think it'd be possible just to have it boot up with a single firefox window and the lack of ability to do anything else ?

---

### Post by K.Mandla on 2007-11-28
Mach Boot does that, sort of. It's a live CD that goes straight to a desktop with minimal software but with Internet access.

[http://www.machboot.com](http://www.machboot.com)

Debian-based too, which is what surprised me. I got to the desktop in 100 seconds on a K6-2 450Mhz. :shock: (No joke, either.)

---

### Post by delfick on 2007-11-28
that looks even more promising :D

I'm trying that after work today 

it says on the site that's it's a livecd...

do you think it'd be possible to install it on hardrive as well, for convenience ?? :D

thnx

---

### Post by K.Mandla on 2007-11-28
I tinkered with that a little bit, and I think it could work. You'd have to point grub at the ISO and see if it can get things going properly. I never fully set it up that way, although it is very tempting. :-k

---

### Post by init1 on 2007-11-28
I can't believe I forgot this! Slitaz sounds like what you're looking for. It's only about 25MB.
[http://www.slitaz.org/index.en.html](http://www.slitaz.org/index.en.html)

---

### Post by n3tfury on 2007-11-28
> **K.Mandla said:**
> Mach Boot does that, sort of. It's a live CD that goes straight to a desktop with minimal software but with Internet access.

[http://www.machboot.com](http://www.machboot.com)

Debian-based too, which is what surprised me. I got to the desktop in 40 seconds on a K6-2 450Mhz. :shock: (No joke, either.)

lol, check the vid:

[http://www.geocities.jp/digitalinfra1960/293857293857/20060226.1.mpg](http://www.geocities.jp/digitalinfra1960/293857293857/20060226.1.mpg)

---

### Post by delfick on 2007-11-29
> **init1 said:**
> I can't believe I forgot this! Slitaz sounds like what you're looking for. It's only about 25MB.
[http://www.slitaz.org/index.en.html](http://www.slitaz.org/index.en.html)

that also looks promising, thnx :D

will have a look at these options now, will get back later with results.. :D

---

### Post by delfick on 2007-11-29
hmm, I seem to have no writable cds and I can't find a tutorial that explains how to boot a livecd from the harddrive rather than from the cd...

anyone want to assist there ?? :D thnx

maybe K.Mandla could expand a little on your last post ?? :D

---

### Post by aimran on 2007-11-29
> **n3tfury said:**
> lol, check the vid:

[http://www.geocities.jp/digitalinfra1960/293857293857/20060226.1.mpg](http://www.geocities.jp/digitalinfra1960/293857293857/20060226.1.mpg)

Getting an error with that

---

### Post by aimran on 2007-11-29
It's ok I provide links:

[http://youtube.com/watch?v=bjLXCwK0jQA](http://youtube.com/watch?v=bjLXCwK0jQA)

---

### Post by n3tfury on 2007-11-29
> **aimran said:**
> Getting an error with that

don't blame me that their site is down

[http://www.machboot.com/](http://www.machboot.com/)

kthx.

---

### Post by delfick on 2007-11-29
well slitaz was quite a dissapointment for me :(

What I did was spend half an hour waiting for gparted to make a few gig extra space for me on my harddrive (which is very near full)

then I copied the data from the iso to that partition

finally figured out what harddrive it was (in grub terms, in this case (hd0,2) and what grub lines to use to make it boot

finally get it booting, only to be stopped half way for same ata1 error about sata drives or something (not sure why or what) which took forever to get past

finally got past that to the login part and had no idea what to log in as, so had to restart (again) and find the login name is "hacker". So I booted back up again, finally got there, put in the username to log in, typed in "startx" and realised that it doesn't seem to be able to recognise my wireless mouse or keyboard and hence can't do anything in it (these are the only mouse and keyboard I own)

so that was a failure (for me)...

hopefully machboot is so much better :D
but that's for tomorrow, it is one in the morning over here and I'm tired

....

---

### Post by delfick on 2007-11-29
hmm, the negative side of asking for a heap of hours at work, they ring you early in the morning.............................

anywho, just tried machboot before I get ready for work....

copied it from iso to the harddrive and don't have a clue, so I posted this [http://bbs1.machboot.com:8000/mini/BBS/index.html#1](http://bbs1.machboot.com:8000/mini/BBS/index.html#1)

that bbs thing is cool :D


...

---

### Post by RAV TUX on 2007-11-29
Upon reading this thread I new that this had been done some time ago, I found it:

It's called Browser Appliance a minimal Gnome appliance with Firefox.


> [SIZE=4]** Browser Appliance**[/SIZE]

[ # x86 VMware (R) Virtual Appliance: VMware Player Image]("http://www.rpath.org/rbuilder/downloadImage?fileId=5779")
[                         #                     x86 Parallels, QEMU (Raw Hard Disk): Raw Hard Disk Image]("http://www.rpath.org/rbuilder/downloadImage?fileId=5780")
[                         #                     x86 Demo CD (Live CD): Demo CD (Live CD)]("http://www.rpath.org/rbuilder/downloadImage?fileId=5783")

Project Home Page  
[http://wiki.rpath.com/wiki/Appliance:Browser Appliance]("http://wiki.rpath.com/wiki/Appliance:Browser")

Description
The Browser Appliance allows users to securely browse the Internet using Mozilla Firefox. Included is just enough rPath Linux and GNOME desktop to run Firefox. You can run the Browser appliance instead of your normal web browser to protect against adware and spyware infections or to safeguard personal information. The Browser appliance can be configured to automatically reset itself after each use, so personal information is never stored permanently. 
                
            Getting Started
                Download one of the virtual appliance images and boot it. No login or password is required, the virtual appliance will boot directly into GNOME and start Firefox automatically.
                
            Support
                The Browser appliance is a community supported project. Questions about Browser appliance should be raised on the Browser appliance discussion list: [http://www.rpath.org/rbuilder/project/browser/mailingLists](http://www.rpath.org/rbuilder/project/browser/mailingLists)[http://www.rpath.org/rbuilder/project/browser/](http://www.rpath.org/rbuilder/project/browser/)

I haven't tried this so I wouldn't know how well it works, the project has been active since 2006, and the current version is 1.0. ;)

---

### Post by RAV TUX on 2007-11-29
> **RAV TUX said:**
> Upon reading this thread I new that this had been done some time ago, I found it:

It's called Browser Appliance a minimal Gnome appliance with Firefox.


[http://www.rpath.org/rbuilder/project/browser/](http://www.rpath.org/rbuilder/project/browser/)

I haven't tried this so I wouldn't know how well it works, the project has been active since 2006, and the current version is 1.0. ;)
Demo CD (Live CD)
                
                
267 MB

---

### Post by delfick on 2007-11-30
cool :D

I've copied the iso contents to a spare partition as I was doing with the other two, and I've added 

> title		internet
root (hd0,2)
kernel /vmlinuz root=/dev/null
initrd /initrd.img

to grub

but it gives me kernel panic, something about not finding init or something...

so what is the correct thing to put into grub?

thnx :D

---

### Post by koenn on 2007-11-30
> **delfick said:**
> 
how possible would it be for a distro who's sole purpose is to boot as fast as possible into an internet browser...

as in when it boots, the only thing you can do is browse the internet.

I did something similar to create 'kiosks' to browse through a webapplication (the catalog of a public library). I used some old pc's + a base console only install of ubuntu + X + fluxbox + firefox, with some autostart features here and there. 

notes :[http://users.telenet.be/mydotcom/howto/linuxkiosk/fluxbox.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/fluxbox.htm)

---

### Post by delfick on 2007-11-30
cool

that's a lot of information you have over there :)

will get to that eventually :D

thnx

---

### Post by Tundro Walker on 2007-12-01
Now just team the web-app distro with [i-RAM]("http://www.anandtech.com/storage/showdoc.aspx?i=2480"), and you'll have an [insanely fast booting]("http://www.youtube.com/watch?v=1PiYgBhAkAM&feature=related") web-appliance.

---

### Post by popch on 2007-12-01
> **delfick said:**
> as in when it boots, the only thing you can do is browse the internet.

Ah, you are thinking of MS Vista in 'restricted functionality mode'?

---

### Post by delfick on 2007-12-01
restricted functionality mode can even do that ??

lol :D

---

