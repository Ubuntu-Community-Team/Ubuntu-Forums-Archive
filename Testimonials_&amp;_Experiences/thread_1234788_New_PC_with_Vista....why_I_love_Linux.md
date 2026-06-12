---
title: "New PC with Vista....why I love Linux"
date: 2009-08-08
forum: Testimonials &amp; Experiences
---

### Post by mdsmedia on 2009-08-08
I've just received my new notebook. It has Vista pre-installed. It's my first chance to "work" with Vista. My first impression of Vista is that I like some things about it but I generally hate it.

One thing that brings this to the fore is defragmenting. I'm not complaining about having to defrag your hard drive. That's a given. What annoys me is that the defrag tool in Vista is even less informative than that in XP. 

What I love about Linux is that it tells you what it's doing. XP's defrag utility isn't as graphic as its predecessor, but it gave you an idea of how your drive looked before and after defrag. 

Vista tells you nothing! I've just defragged a new Vista install and I have no idea what the drive looks like before or after the defrag.

There are things I like about Vista....compared with XP.....but Linux is just more informative.

---

### Post by HappyFeet on 2009-08-08
Are you going to put linux on your new notebook? Or at least dual boot?

---

### Post by Tamlynmac on 2009-08-08
> HappyFeet
Are you going to put linux on your new notebook? Or at least dual boot? 	

I'd put money on - betting he will. :D

> mdsmedia
I've just received my new notebook


You didn't define what the specs of your new laptop are. I'm considering purchasing a new laptop and am interested in an 18.4" model. Wondered what brand you purchased and what the specs are? Be interested to see how Ubuntu integrates. Have you tried the live cd yet?

---

### Post by jazgator on 2009-08-08
My wife's computer, HP slimline 7600 running windows XP Home edition was taking so long to boot up and do anything, you could start the computer and go prepare a cup of coffee and return to find an hourglass for a cursor. Defragmented, optimized etc.. nothing seemed to work. Tired of the stress, desided to reformat the computer and load Ubuntu. System booted up immediately, recognized all hardware and helped select the right support files needed to customize to the system. What a difference, she now is a convert. Thanks for the new freedom from Windows environment.
 
Did I mentioned the system runs like a top? :P

---

### Post by HappyFeet on 2009-08-08
> **jazgator said:**
> My wife's computer, HP slimline 7600 running windows XP Home edition was taking so long to boot up and do anything, you could start the computer and go prepare a cup of coffee and return to find an hourglass for a cursor. Defragmented, optimized etc.. nothing seemed to work. Tired of the stress, desided to reformat the computer and load Ubuntu. System booted up immediately, recognized all hardware and helped select the right support files needed to customize to the system. What a difference, she now is a convert. Thanks for the new freedom from Windows environment.
 
Did I mentioned the system runs like a top? :P
That's really great to hear. Stories like yours are what keep me going. 

Do not hesitate to ask any questions you may have.

Hey Mdsmedia, is your avatar John Lennon?

---

### Post by windows-killer on 2009-08-08
> **mdsmedia said:**
> I've just received my new notebook. It has Vista pre-installed. It's my first chance to "work" with Vista. My first impression of Vista is that I like some things about it but I generally hate it.

One thing that brings this to the fore is defragmenting. I'm not complaining about having to defrag your hard drive. That's a given. What annoys me is that the defrag tool in Vista is even less informative than that in XP. 

What I love about Linux is that it tells you what it's doing. XP's defrag utility isn't as graphic as its predecessor, but it gave you an idea of how your drive looked before and after defrag. 

Vista tells you nothing! I've just defragged a new Vista install and I have no idea what the drive looks like before or after the defrag.

There are things I like about Vista....compared with XP.....but Linux is just more informative.

you can always get a third party app that does a better job than the defaul defrag utility. I found the MS defrag utility useless, so I use a third party one.

---

### Post by jazgator on 2009-08-09
> **HappyFeet said:**
> That's really great to hear. Stories like yours are what keep me going. 

Do not hesitate to ask any questions you may have.

Hey Mdsmedia, is your avatar John Lennon?
Thanks for the links, I will be studying and learning as we go.. :)

---

### Post by mdsmedia on 2009-08-09
> **windows-killer said:**
> you can always get a third party app that does a better job than the defaul defrag utility. I found the MS defrag utility useless, so I use a third party one.
I was thinking of doing that...in fact that was the first thing that I had in mind. I wanted something which would show me what was being moved and the extent of framentation before AND after defrag. What do you use, and is it Vista or XP you're using it for?

HappyFeet, yes I'm going to dual or triple boot, Ubuntu and Arch. And yes, my avatar is John Lennon.

The Machine is a Toshiba Satellite Pro L300, with Celeron Mobile 2.26 GHz, 160GB hard drive, 1GB RAM upgradable to 2GB. It's pretty low spec, but was quite cheap and is still about twice what my old laptop has. It's a 15 inch (or thereabouts) monitor...wide screen.

I installed Jaunty no problem, but when I tried installing Arch it gave me a "fatal error" on starting cfdisk to partition the drive. It's something to do with Toshiba's partitioning defaults. I'm googling to try to sort it out, hopefully without having to reinstall Vista, but if I have to and that fixes it I will. I haven't spent much time on it, as yet, in Ubuntu. My old laptop is still sitting beside me, with Ubuntu, until I get everything onto the new machine.

---

### Post by mdsmedia on 2009-08-12
Latest episode(s):

I managed to easily shrink the Vista partition with Gparted LiveCD (btw, the Gparted included in Ubuntu works far more nicely...maybe I got a bad Gparted image...the partitioner works well, but then I have to use a paper clip to expell the CD and reboot via the power button).

Installation of Ubuntu was a snap. To think, I was always scared of doing this......not the installation as such, and maybe because it was a fresh install and no data was involved, the trepidation was less. 

The Vista recovery set involves FOUR DVDs, but I'm glad I created them, because I ended up wiping the drive (deliberately) and had to "recover" Vista.

The fun started while trying to install Arch. I'd get to the partitioning section and cfdisk had fits over the 1st partition being all wrong (can't rememeber what the exact error was, but it has something to do with Toshiba's partitioning scheme). It has about 1.5MB unformatted at the start of the drive, then 1.46GB of Toshiba System something or other. cfdisk gives a Fatal Error message and that's the end of that.

I spent a few hours last night wrestling with partitions, trying to get around the Toshiba issue. I wiped the drive in installing Arch, but then Vista only wanted to be installed in SDA1.

I'll google and see if I can't find a method of creating a Vista system disk so that I'm not limited to the Toshiba recovery disks and maybe I can get around it that way.

Anyway, this morning I "recovered" Vista, will now reinstall Ubuntu, then wrestle with getting Arch to either ignore the Toshiba partitioning or find some convoluted method to hold my hands over Vista's eyes and install Arch without Vista knowing.

One of the forum solutions I found said that cfdisk is a newer utility but fdisk is older but nicer and works better. 

I've tried bypassing the partitioning and going on to organising mount points, and maybe I'll go that route again, with the drive already partitioned. I seemed to get tripped up doing that, but maybe it was something I overlooked.

Arch uses cfdisk and I'm not sure if I can find a way to use something else that will bypass the error it trips up on. Ubuntu had no problem whatsoever installing, so it's frustrating that Arch slips up at that stage.

---

