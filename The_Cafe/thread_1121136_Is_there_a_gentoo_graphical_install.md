---
title: "Is there a gentoo graphical install?"
date: 2009-04-09
forum: The Cafe
---

### Post by dragos240 on 2009-04-09
Hello, i've been trying to install gentoo for some time now, and well..... it's too hard!!!!!!!! I have a wifi wpa2 connection, dir doesn't work, poweroff doesn't work, reboot doesn't work, and not even halt is there!!! Is there an easier way to install this? Or a nice guide on how to install it, like something on ONE page? Please help, I want a nice barebones distro.

---

### Post by Mokoma on 2009-04-09
> **dragos240 said:**
> Hello, i've been trying to install gentoo for some time now, and well..... it's too hard!!!!!!!! I have a wifi wpa2 connection, dir doesn't work, poweroff doesn't work, reboot doesn't work, and not even halt is there!!! Is there an easier way to install this? Or a nice guide on how to install it, like something on ONE page? Please help, I want a nice barebones distro.

try arch. ive heard loads of good stuff about that!

---

### Post by Mr-Biscuit on 2009-04-09
Haven't used it in a while.
Emphasize this part---> I think- not sure- that the live dvd may have such.

---

### Post by cardinals_fan on 2009-04-09
Yes, but you should not use it under any circumstances.  It is hideously buggy and does not work well at all.

Gentoo isn't supposed to work out of the box.  That's not the point.

For an "easier" barebones distro, you should use Arch.  CRUX is my favorite barebones setup, but it doesn't sound like it would be right for you if you don't want to learn anything.  You might also want to try SliTaz as it is very light and simple (though I'm biased here because I'm on the team).

---

### Post by dragos240 on 2009-04-09
> **Mokoma said:**
> try arch. ive heard loads of good stuff about that!

I have but I'd like to be able to compile from source easier too, I want to try to move away from package managers, if i can compile from source easier, and I have a nice barebones easily customizable distro, then i'm a happy penguin :)

> **cardinals_fan said:**
> Yes, but you should not use it under any circumstances. It is hideously buggy and does not work well at all.

Gentoo isn't supposed to work out of the box.  That's not the point.

For an "easier" barebones distro, you should use Arch. CRUX is my favorite barebones setup, but it doesn't sound like it would be right for you if you don't want to learn anything. You might also want to try SliTaz as it is very light and simple (though I'm biased here because I'm on the team).

Hold up!! I never said I didn't want to learn anything..

---

### Post by cardinals_fan on 2009-04-09
> **dragos240 said:**
> I have but I'd like to be able to compile from source easier too, I want to try to move away from package managers, if i can compile from source easier, and I have a nice barebones easily customizable distro, then i'm a happy penguin :)
AUR?

Maybe you should try SliTaz.  Tazwok makes it easy to build your own packages from source.

Anyway, you seem to have contradictory needs.  You want a system with minimal autoconfiguration, but you don't want to do the work to set it up.

---

### Post by Eisenwinter on 2009-04-09
You can compile from source in Arch with great ease.

There's a thing called ABS - the Arch Build System - it's basically a portage system.

Read more about it in the Arch wiki.

---

### Post by Skripka on 2009-04-09
> **dragos240 said:**
> I have but I'd like to be able to compile from source easier too, I want to try to move away from package managers, if i can compile from source easier, and I have a nice barebones easily customizable distro, then i'm a happy penguin :)



COUGH, Yaourt, COUGH.

---

### Post by Stupendoussteve on 2009-04-09
Gentoo uses a package manager, the packages just happen to be built by the package manager on the fly...

The "all-in-one-page" Gentoo install guide is at [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1) - It is long, it is complicated, but it is complete.

It is worth learning how to use the command line before attempting a Gentoo (or Arch, really) install though. This can be accomplished just as easily on Ubuntu.

---

### Post by cardinals_fan on 2009-04-09
> **dragos240 said:**
> 
Hold up!! I never said I didn't want to learn anything..
Prove me wrong :P.  If you want "a nice guide on how to install it, like something on ONE page", you obviously don't want to put yourself in a situation you aren't prepared for.  I personally consider that the best way to learn.  You can look at the amount of work required by Gentoo and think one of two things:

a) I want a new distro that doesn't take this much work...
b) I want to reread the [Handbook]("http://www.gentoo.org/doc/en/handbook/index.xml") and struggle until I learn how to do it.

You reacted with **a**, when only **b** will teach you something.

Have you used Slackware?  It isn't source-based, but it can be a good intro to the uber-minimal distros.

---

### Post by dragos240 on 2009-04-09
> **cardinals_fan said:**
> Prove me wrong :P.  If you want "a nice guide on how to install it, like something on ONE page", you obviously don't want to put yourself in a situation you aren't prepared for.  I personally consider that the best way to learn.  You can look at the amount of work required by Gentoo and think one of two things:

a) I want a new distro that doesn't take this much work...
b) I want to reread the [Handbook]("http://www.gentoo.org/doc/en/handbook/index.xml") and struggle until I learn how to do it.

You reacted with **a**, when only **b** will teach you something.

Have you used Slackware?  It isn't source-based, but it can be a good intro to the uber-minimal distros.

Oh I mislead you, I didn't mean one page, i meant all the data on one page, so i can print it out rather than go link to link. Such as the [arch beginners guide]("http://wiki.archlinux.org/index.php/Beginners_Guide"), rather than gentoos guide where you have to jump from link to link, i have a wpa connection so it's hard to connect to the internet in non-gui, this is what I was saying.

---

### Post by yabbadabbadont on 2009-04-09
> **cardinals_fan said:**
> Yes, but you should not use it under any circumstances.  It is hideously buggy and does not work well at all.
And it is no longer supported anyway.  It had this bad habit of destroying the partition tables of **every drive in the machine**...  (I perform regular backups now  ;))  Always follow the instructions for a manual stage3 installation.  You can use any Linux live CD/DVD that works with your system to perform the install.

> **cardinals_fan said:**
> Gentoo isn't supposed to work out of the box.  That's not the point.
Wrong.  It works "out of the box" as long as the box has been properly opened according to the well documented instructions.  :D

---

### Post by cardinals_fan on 2009-04-09
> **dragos240 said:**
> Oh I mislead you, I didn't mean one page, i meant all the data on one page, so i can print it out rather than go link to link. Such as the [arch beginners guide]("http://wiki.archlinux.org/index.php/Beginners_Guide"), rather than gentoos guide where you have to jump from link to link, i have a wpa connection so it's hard to connect to the internet in non-gui, this is what I was saying.
Hey, give CRUX a shot.  It isn't really any harder than Gentoo (I find it easier; read my comparison [here]("http://grubbn.org/otheros/showthread.php?tid=249&pid=3004#pid3004")).  It has a great and to-the-point handbook: [http://crux.nu/Main/Handbook2-5](http://crux.nu/Main/Handbook2-5)
> **yabbadabbadont said:**
> And it is no longer supported anyway.  It had this bad habit of destroying the partition tables of **every drive in the machine**...  (I perform regular backups now  ;))
I can sleep easy at night now.
> **yabbadabbadont said:**
> 
Wrong.  It works "out of the box" as long as the box has been properly opened according to the well documented instructions.  :D
Good things in life take time.  Like opening boxes...

---

### Post by dragos240 on 2009-04-09
Okay, I want to get gentoo, ragardless, although the erases all partitions on drive part doesn't sound welcoming. Yes i know Ii'm stubborn, but I do want to learn, can you give me a link, please?

---

### Post by binbash on 2009-04-09
If you read the gentoo handbook and you can't install it still, do not install gentoo.

---

### Post by dragos240 on 2009-04-09
> **binbash said:**
> If you read the gentoo handbook and you can't install it still, do not install gentoo.

Did you even read my posts? I need something on one url, not the guide that keeps linking to other urls. This is why I cannot use the handbook, and I can't connect to the net via non-gui inerface, I would try it if I could. But it's not working :(

---

### Post by Eisenwinter on 2009-04-09
> **binbash said:**
> If you read the gentoo handbook and you can't install it still, do not install gentoo.
I agree. I also think it's crucial to have the handbook in a printed form, by your hand (haha, get it? hand book by your **hand**, so cool!), if you plan to install it from the live environment Gentoo provides.

Using some console browser to read the documentation while installing, is very uncomfortable, and not recommended.

cardinals_fan suggested CRUX, I agree with that, I hear good things from CRUX users, and some Gentoo users say that Gentoo adds a lot of complications to it's installation process, something CRUX doesn't do.

---

### Post by cardinals_fan on 2009-04-09
> **dragos240 said:**
> Okay, I want to get gentoo, ragardless, although the erases all partitions on drive part doesn't sound welcoming. Yes i know Ii'm stubborn, but I do want to learn, can you give me a link, please?
**WARNING: As yabbadabbadont said, this is outdated and no longer supported**

i686: [http://bouncer.gentoo.org/fetch/gentoo-2008.0-livecd/x86/](http://bouncer.gentoo.org/fetch/gentoo-2008.0-livecd/x86/)
amd64: [http://bouncer.gentoo.org/fetch/gentoo-2008.0-livecd/amd64/](http://bouncer.gentoo.org/fetch/gentoo-2008.0-livecd/amd64/)

---

### Post by cardinals_fan on 2009-04-09
> **Eisenwinter said:**
> 
Using some console browser to read the documentation while installing, is very uncomfortable, and not recommended.

Why?  I use elinks for most of my browsing.

---

### Post by dragos240 on 2009-04-09
So gentoo is officially dead? Why?

---

### Post by Eisenwinter on 2009-04-09
> **cardinals_fan said:**
> Why?  I use elinks for most of my browsing.
Well, I guess that most of my elinks experience in a CLI-only environment, weren't with a proper 1024x768 resolution and font settings, leading to the huge ugly font that makes 5 lines of text spreadout through the whole screen :lolflag:

---

### Post by cardinals_fan on 2009-04-09
> **dragos240 said:**
> So gentoo is officially dead? Why?
No.  The graphical installer is officially dead, because it was a moronic idea in the first place and poorly executed to boot.  I gave you the link to the live CD images, as you so explicitly requested.  The Minimal/Install CD (which is what you should use) is found here, as are all the other CDs (even the live installer):

[http://www.gentoo.org/main/en/where.xml](http://www.gentoo.org/main/en/where.xml)

---

### Post by Stupendoussteve on 2009-04-09
> **dragos240 said:**
> So gentoo is officially dead? Why?

No, it is not. The graphical installer was abandoned because it is broken, and in general a waste of the release engineering team's time. The normal way to install Gentoo via the handbook is still alive and well.

I already posted the link to the handbook all in one page. It's easy to access by hitting the link at "Latest version, all in one page" - [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1)

If you are using a different architecture than x86, you should use a different handbook.

---

### Post by dragos240 on 2009-04-09
> **cardinals_fan said:**
> No.  The graphical installer is officially dead, because it was a moronic idea in the first place and poorly executed to boot.  I gave you the link to the live CD images, as you so explicitly requested.

Thanks :) I'm going to install ubuntu on a virtual machine and then partition a new ext2 filesystem for gentoo and see if it dualboots, if not, I'm going to see if I can find a good guide on how to install gentoo, on a single URL. I figure if I have to print all those pages, it will take as much time (if not more) than installing gentoo itself, which i've heard takes a long time.

---

### Post by dragos240 on 2009-04-09
> **Stupendoussteve said:**
> No, it is not. The graphical installer was abandoned because it is broken, and in general a waste of the release engineering team's time. The normal way to install Gentoo via the handbook is still alive and well.

I already posted the link to the handbook all in one page. It's easy to access by hitting the link at "Latest version, all in one page" - [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1)

If you are using a different architecture than x86, you should use a different handbook.


OH MY NON-EXISTANT-RELIGIOUS-FIGURE!!! This is what i've been looking for!!!!!!!!!!!! Thank you so much!!!!!!!!!!!!1

---

### Post by cardinals_fan on 2009-04-09
> **dragos240 said:**
> Thanks :) I'm going to install ubuntu on a virtual machine and then partition a new ext2 filesystem for gentoo and see if it dualboots, if not, I'm going to see if I can find a good guide on how to install gentoo, on a single URL. I figure if I have to print all those pages, it will take as much time (if not more) than installing gentoo itself, which i've heard takes a long time.
The handbook is the best guide you will find, and a one-page version has been provided.  This is what people mean when they talk about the "complexity" of Gentoo; read my comparison linked to above for more.

Don't underestimate the time required to install Gentoo.  Unlike CRUX, the actual install is source not binary (pretty stupid in my opinion, since you have to upgrade it all eventually anyway).  It can take a LONG time.

---

### Post by Eisenwinter on 2009-04-09
> **dragos240 said:**
> OH MY NON-EXISTANT-RELIGIOUS-FIGURE!!! This is what i've been looking for!!!!!!!!!!!! Thank you so much!!!!!!!!!!!!1
You really couldn't go to the gentoo website and fetch it yourself huh? 

lol...

---

### Post by dragos240 on 2009-04-09
> **cardinals_fan said:**
> The handbook is the best guide you will find, and a one-page version has been provided.  This is what people mean when they talk about the "complexity" of Gentoo; read my comparison linked to above for more.

Don't underestimate the time required to install Gentoo.  Unlike CRUX, the actual install is source not binary (pretty stupid in my opinion, since you have to upgrade it all eventually anyway).  It can take a LONG time.

I'm prepared. I have finally found what I was looking for! I canceled the graphical install and am preparing to print out the full page! I thank all of you! This will be an interesting experience, wish me luck ( I might need it )

---

### Post by dragos240 on 2009-04-09
> **Eisenwinter said:**
> You really couldn't go to the gentoo website and fetch it yourself huh? 

lol...

Well..... At first I only saw the guide the way it was, so I just walked away before I knew enough.

---

### Post by Eisenwinter on 2009-04-09
alright then, good luck, may the force of Linus be with you.

---

### Post by cardinals_fan on 2009-04-09
> **dragos240 said:**
> I'm prepared. I have finally found what I was looking for! I canceled the graphical install and am preparing to print out the full page! I thank all of you! This will be an interesting experience, wish me luck ( I might need it )
Good luck.  Remember; even if your install is borked after 15 hours of compiling, violence is not the answer!

---

### Post by dragos240 on 2009-04-09
> **cardinals_fan said:**
> Good luck.  Remember; even if your install is borked after 15 hours of compiling, violence is not the answer!

I've learned that many times, many many many times before.

EDIT: Hopefully I won't go mad, I just did a print preview so I could find out how many pages it was. The x86 handbook, is 86 pages. I'm going to need a lot of paper.......

---

### Post by yabbadabbadont on 2009-04-09
> **dragos240 said:**
> I've learned that many times, many many many times before.

EDIT: Hopefully I won't go mad, I just did a print preview so I could find out how many pages it was. The x86 handbook, is 86 pages. I'm going to need a lot of paper.......

There is no need for that.  As I stated earlier, you can use *any* linux live cd/dvd that works with your machine.  Knoppix, systemrescuecd, even the Ubuntu live cd/dvd will work.  Just choose one that will get you internet access and has a browser installed.  That way you can view the manual without printing it.  The Knoppix one is nice in that you can browse the web while things are compiling.  (or listen to music, or watch videos...)

---

### Post by Eisenwinter on 2009-04-09
I printed the handbook for Gentoo 2007.0 min amd64, about a year ago, at work.

Good thing they have a laser printer there, the end document ended up being 67 pages long.

So much paper, I couldn't even staple it together in one piece, I had to staple every X pages together, and create a few packs.

As far as installation goes, yeah, after about 7 hours of downloading stage3 and portage, configuring, compiling, my system broke.

I was beyond mad, I mean, not even mad, it's just so <insert word, can't find feeling>, so I ended up putting Debian Etch on instead.

---

### Post by dragos240 on 2009-04-09
> **yabbadabbadont said:**
> There is no need for that.  As I stated earlier, you can use *any* linux live cd/dvd that works with your machine.  Knoppix, systemrescuecd, even the Ubuntu live cd/dvd will work.  Just choose one that will get you internet access and has a browser installed.  That way you can view the manual without printing it.  The Knoppix one is nice in that you can browse the web while things are compiling.  (or listen to music, or watch videos...)

Thats not what i'm saying, I can't connect to the internet while in a non-gui state, because of my wpa2 connection, so it won't matter anyways.

---

### Post by yabbadabbadont on 2009-04-09
> **dragos240 said:**
> Thats not what i'm saying, I can't connect to the internet while in a non-gui state, because of my wpa2 connection, so it won't matter anyways.

All of the live cd/dvds that I listed provide a full X windows graphical environment...  and I would be pretty surprised if the latest Knoppix didn't support your wireless adapter.

Edit: If you can't (for whatever reason) connect to the internet while in a "non-gui state", then Gentoo is most likely not for you.  It will be anywhere from a few, to many, hours before you have X installed and working.  And you will have to have an internet connection in order to install the system anyway.

---

### Post by albinootje on 2009-04-09
> **dragos240 said:**
> Is there an easier way to install this?

Well, it won't help you very much, but just for the record.. a few years ago I tested VidaLinux, (Gentoo with a GUI install) and that was pretty cool back then.

[http://en.wikipedia.org/wiki/VidaLinux](http://en.wikipedia.org/wiki/VidaLinux)
[http://distrowatch.com/table.php?distribution=vlos](http://distrowatch.com/table.php?distribution=vlos)

The current website seems to be completely in spanish now, and the last release was from 2006, but I'm posting this so that someone else might continue something along these lines where VidaLinux stopped.

By the way, I've always found Gentoo Linux interested, and their documentation used to be pretty good. Unfortunately the Gentoo wiki lost most of the original content because of some server (or serving?) problem.

---

### Post by cardinals_fan on 2009-04-09
> **dragos240 said:**
> Thats not what i'm saying, I can't connect to the internet while in a non-gui state, because of my wpa2 connection, so it won't matter anyways.
That might rule out Gentoo.

CRUX includes wpa_supplicant in opt on the CD (if I remember right), so that might be an option.

---

### Post by yabbadabbadont on 2009-04-09
Another alternative might be to install Sabayon.  [http://www.sabayonlinux.org/](http://www.sabayonlinux.org/)

It is based on and, I believe, uses the Gentoo portage tree.  Only it is easier to install and will get you to a working system in a shorter period of time.  Once you have become familiar with it, it wouldn't be much of an issue to then switch to Gentoo.

---

### Post by Stupendoussteve on 2009-04-09
Gentoo also includes wpa_supplicant on the CD, I believe.

---

