---
title: "Dual booting Ubuntu and a light OS for cloud computing (like Dell Latitude ON)"
date: 2008-08-19
forum: The Cafe
---

### Post by wersdaluv on 2008-08-19
I am going to get a very portable laptop pretty soon. When that happens, I want my laptop to have a "light mode." I got the idea from Dell's Latitude ON (see [http://www.pcworld.com/article/149896/2008/08/.html](http://www.pcworld.com/article/149896/2008/08/.html) ). 

I want an OS (or something like that if you won't call it an operating system) that boots very fast and that enables me to do my PIM work, open my web browser, and some light office work when I am on the go. I am a student so there are times when I need to do something quick on my computer so my computer needs to boot and shut down quickly, too. The idea really is like Latitude ON.

I'm thinking of dual booting Ubuntu and some light distro. The light distro would serve as my Latitude on (or something like my Blackberry). I want to be able to share my home partition between the two so that my documents and PIM files are synchronized. 

What do you suggest for me to do? Dual boot with something like fluxbuntu? Does that boot quick enough? 

Will I not have a problem with sharing my home partition between the light OS and full-blown Ubuntu? If so, what are my alternatives?

Do you think that having this light OS thing is a good idea? Why or why not?

EDIT:
I think, I want a version of Ubuntu that will let me use Evolution, Pidgin, gnome panel, and Firefox (and some other basic apps that I could have forgotten about). I want to be able to use the latest versions of those apps so that I can share my home partition with my full-blown Ubuntu and light OS. Is there a solution that would make Ubuntu that small? Stuff like printing and other advance things could be removed.

EDIT:
Something like splashtop would be nice :D see [http://www.splashtop.com/splashtop_overview.php](http://www.splashtop.com/splashtop_overview.php) . It's just that, I still prefer something that would run Ubuntu apps so that I can use my home partition.

---

### Post by billgoldberg on 2008-08-19
> **wersdaluv said:**
> I am going to get a very portable laptop pretty soon. When that happens, I want my laptop to have a "light mode." I got the idea from Dell's Latitude ON (see [http://www.pcworld.com/article/149896/2008/08/.html](http://www.pcworld.com/article/149896/2008/08/.html) ). 

I want an OS (or something like that if you won't call it an operating system) that boots very fast and that enables me to do my PIM work, open my web browser, and some light office work when I am on the go. I am a student so there are times when I need to do something quick on my computer so my computer needs to boot and shut down quickly, too. The idea really is like Latitude ON.

I'm thinking of dual booting Ubuntu and some light distro. The light distro would serve as my Latitude on (or something like my Blackberry). I want to be able to share my home partition between the two so that my documents and PIM files are synchronized. 

What do you suggest for me to do? Dual boot with something like fluxbuntu? Does that boot quick enough? 

Will I not have a problem with sharing my home partition between the light OS and full-blown Ubuntu? If so, what are my alternatives?

Do you think that having this light OS thing is a good idea? Why or why not?

Arch linux with fluxbox. or if you really want lightweight: puppy linux or damn small linux.

---

### Post by snowpine on 2008-08-19
I agree with Bill; Fluxbuntu does not boot any quicker than regular Ubuntu.

---

### Post by TwiceOver on 2008-08-19
I'm not a distro expert but Puppy boots really fast even on my old 300mhz P2 that sits in the garage.

---

### Post by conundrumx on 2008-08-19
I've been thinking about doing something like this as well.  I have an SD card in my laptop at all times, and I'd like to use it for a fast booting OS.  It's unfortunate I can't use the Intel Turbo Memory/Robson chip for it.

---

### Post by Takmadeus on 2008-08-19
Go puppy all the way, or if you can (I don't know how good it would be) use gentoo and compile it specifically for your hardware ;)

---

### Post by wersdaluv on 2008-08-19
I'm really considering puppy but will I be able to install Hardy's versions of firefox, gnome panel and its applets, and Evolution?

---

### Post by wersdaluv on 2008-08-19
To give you an idea, something like this is what I want [http://www.engadget.com/2008/08/15/dells-latitude-on-instant-os-detailed-screenshooted/](http://www.engadget.com/2008/08/15/dells-latitude-on-instant-os-detailed-screenshooted/)

---

### Post by snowpine on 2008-08-19
> **wersdaluv said:**
> To give you an idea, something like this is what I want [http://www.engadget.com/2008/08/15/dells-latitude-on-instant-os-detailed-screenshooted/](http://www.engadget.com/2008/08/15/dells-latitude-on-instant-os-detailed-screenshooted/)

The reason these systems run so fast is that they are embedded into ROM. You will never get that kind of instant-on with a "normal" hard-disk based installation. :)

---

### Post by wersdaluv on 2008-08-19
> **snowpine said:**
> The reason these systems run so fast is that they are embedded into ROM. You will never get that kind of instant-on with a "normal" hard-disk based installation. :)
I want something like that :D How do I do it? :D

---

### Post by snowpine on 2008-08-19
> **wersdaluv said:**
> I want something like that :D How do I do it? :D

Buy a Dell! :) Seriously, a lot of the next-generation Atom computers are going to have a separate, minimal OS hard-wired into the motherboard (Splashtop is another example). I think it is a very cool idea, and it's an exciting time to be shopping for a new notebook computer with all the new technologies.

But let's say your laptop doesn't have this feature... what is your 2nd best choice? I say, create a separate partition on your hard drive and install the lightest, fastest Linux that still gives you the features you need. I am biased towards Ubuntu (because these are the Ubuntu forums) but honestly I don't think anything based on Ubuntu is what you need in this situation. You are going to have to decide what you can live without. Instead of thinking "I want to have the latest and greatest versions of everything," think "what are the one or two tasks I use the most when I'm on the run?"

---

### Post by Superkoop on 2008-08-19
I was thinking of trying to do something like this too, but I would actually prefer something so minimal that the most I can do is use Abiword + terminal. Meaning no internet, no actual desktop, no other programs, just a linux terminal and Abiword.
And I would like usable Abiword within 5seconds.

How fast of a boot time could I probably get with a superminimal puppy like I have described? I would probably have to do all of the customizing, but it would be worth it I think.

---

### Post by wersdaluv on 2008-08-20
> **snowpine said:**
> Buy a Dell! :) Seriously, a lot of the next-generation Atom computers are going to have a separate, minimal OS hard-wired into the motherboard (Splashtop is another example). I think it is a very cool idea, and it's an exciting time to be shopping for a new notebook computer with all the new technologies.

But let's say your laptop doesn't have this feature... what is your 2nd best choice? I say, create a separate partition on your hard drive and install the lightest, fastest Linux that still gives you the features you need. I am biased towards Ubuntu (because these are the Ubuntu forums) but honestly I don't think anything based on Ubuntu is what you need in this situation. You are going to have to decide what you can live without. Instead of thinking "I want to have the latest and greatest versions of everything," think "what are the one or two tasks I use the most when I'm on the run?"
Yeah. Dells are cool but they wont fit my budget. I'm probably getting an MSI PR200 for about $800. 

I'm thinking about that 2nd OS thingy. I want it to completely boot as quick as 15 seconds or faster. I just need it to do simple things. Would that be feasible without an OS that I can put on my ROM? Could I put an OS like Puppy Linux or DSL on my ROM?

---

### Post by wersdaluv on 2008-08-21
Bompppp

---

### Post by init1 on 2008-08-22
I'd recommend SliTaz. If you run it compressed, apps will load almost instantly.

---

### Post by ghindo on 2008-08-22
> **init1 said:**
> I'd recommend SliTaz. If you run it compressed, apps will load almost instantly.Coincidentally, K.Mandla just [made a post today]("http://kmandla.wordpress.com/2008/08/22/or-you-could-just-use-slitaz/") about how fast SliTaz is.  He claims that it boots in about 16 seconds.  I'm not sure how much he's modified it, but SliTaz sounds pretty darn fast, regardless.

---

### Post by mips on 2008-08-22
> **wersdaluv said:**
> I want something like that :D How do I do it? :D

There are howtos out there on hacking Splashtop to run on other hardware. I 'think' the howtos allow for install to USB Flash & Hard drive.

I will have a look and get back to you.

Edit: Have a look at the links below on how to hack splashtop.
[http://www.phoronix.com/scan.php?page=article&item=splashtop_hacked&num=1](http://www.phoronix.com/scan.php?page=article&item=splashtop_hacked&num=1)
[http://www.phoronix.com/forums/showthread.php?t=11610](http://www.phoronix.com/forums/showthread.php?t=11610)
[http://www.phoronix.com/forums/showthread.php?t=11653](http://www.phoronix.com/forums/showthread.php?t=11653)
[http://www.phoronix.com/forums/showthread.php?t=11644](http://www.phoronix.com/forums/showthread.php?t=11644)
[http://www.phoronix.com/forums/showthread.php?t=11474](http://www.phoronix.com/forums/showthread.php?t=11474)

The above should get you going.

---

### Post by wersdaluv on 2008-08-23
Wow! Thanks for the responses. Could Slitaz be as fast as Splashtop?

---

### Post by mips on 2008-08-23
> **wersdaluv said:**
> Wow! Thanks for the responses. Could Slitaz be as fast as Splashtop?

Only way to find out is to try. I suspect though that Splashtop will load faster.

---

### Post by regomodo on 2008-08-23
#

---

### Post by wersdaluv on 2008-08-23
After googling, it seems to me that splashtop boots faster. Maybe, it;s because Splashtop is installed on the computer's rom. Is Slitaz already the fastest distro?

---

### Post by mips on 2008-08-27
> **wersdaluv said:**
> After googling, it seems to me that splashtop boots faster. Maybe, it;s because Splashtop is installed on the computer's rom. Is Slitaz already the fastest distro?

Why don't you try Splashtop on a USB flash stick?

---

### Post by wersdaluv on 2008-08-27
> **mips said:**
> Why don't you try Splashtop on a USB flash stick?
Good idea

---

