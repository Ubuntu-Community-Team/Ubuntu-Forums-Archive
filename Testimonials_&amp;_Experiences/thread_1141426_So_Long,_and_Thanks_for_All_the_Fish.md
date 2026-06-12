---
title: "So Long, and Thanks for All the Fish"
date: 2009-04-28
forum: Testimonials &amp; Experiences
---

### Post by iris-n on 2009-04-28
I'm biding you all farewell, as I'm abandoning Ubuntu in favour of Debian. Allow me to qualify. For me, the main advantages of the distros are:

Debian

1 - Stability
2 - Technical excellence

Ubuntu

1 - Up to date software
2 - Ease of use

I'm getting old. I don't wanna deal with buggy software just for the sake of the latest and greatest. So the tradeoff for me is advantageous. I'm sad that new software can't be equated with good software, but I understand why is that so. And software that I care and use enough to want the latest version, I can compile it myself (minefield), and won't be bothered by the bugs. I may even help to solve some. But software that I'm not in a love relationship with them, well, I just want they to stay out of the way and work. I can survive with a year old version of OpenOffice or GNOME.

And ubuntu does have strange bugs. I used to enable the -proposed repos, so I could help to iron out new bugs and pay back the community. Except that it wasn't quite so. I've never managed to get a bug fixed. Even when I sent a patch. Either they were dupes or they sit there unconfirmed for ages. So I was burning myself for no good.

When I lost respect for the distro was sometime about the end of last year, when they released a broken xkb-data. I mean, honestly, what's so hot and exciting about keyboards that merits a hasty release? And who in their right mind lets a such horribly broken package hits the repos? I updated and suddenly my keyboard was changing a to æ and all sorts of weird stuff. Sure, a fix came briefly, but the reputation was shaken.

So debian lenny was released. I waited until Jaunty was ready too, so I could compare them. Well, Jaunty was... jaunty, for the lack of a better world. Or fluffy. Pretty. But had the same problems of the other versions. So I formatted my pc and installed lenny. It worked like a charm. I could tweak just about everything without generating strange bugs. Sure, I'd never be able to install and configure it like I did when I had first encountered linux. But I've learned a lot with ubuntu, and I will be forever grateful. The point is, now I can. And it made hellava difference. I had a machine that had the same functionality of my old ubuntu, but ran much faster in my shitty hardware, without the hundred or so cruft packages that are installed by default and you can't quite remove.

Just as an anecdotal piece of evidence, I've metered the boot times of my pc:

Intrepid: 86 s
Jaunty:	  68 s
Lenny:	  53 s

Yes, not very important, but significant as Jaunty was touted for faster boots, and Lenny, with the same software installed, and none of the speed improvements, is noticeable faster. Yes, I know that old software is almost always faster than new software, but if the age isn't harmful, I don't see a problem.

So, ubuntu is not for me anymore. It was really good using it for about 2 years. Taught me a lot about linux and computers. And I hope I've managed to contribute something back, helping people in the fora. But now, debian is my lover.

So long, and thanks for all the fish.

---

### Post by benj1 on 2009-04-28
well its all about personal preference at least with linux you have the choice of distros.
farewell

don't forget you towel):P

---

### Post by loomsen on 2009-04-28
Hello.

I agree in most points. Jaunty now finally made move on and leave ubuntu.
I used to run debian already, tho it kept causing system freezes cause of my wlan, so I moved back to ubuntu. But imo the new release is a mess to deal with. Whatever it is, it could've been avoided just like that, IPv6 M instead of Y and this would be just fine. DontZap should've been a positive option instead of default. Python, not shipping 2.6.29, whatever it is, it's not what I expected.

But, concerning the whole bunch of packages ubuntu ships with, not that I would disagree, but you can easily install a minimal system and pull in some core packages to have a minimal gnome desktop, for instance. Not even gedit or firefox are installed that way, plus, rather than wasting time purging what i don't want, i can use the same time to set up my OS like I want it to be.

However, I'm gonna give fedora a serious try upon their final release. I already liked it more than ubuntu, running the live cd. Not much of a difference as it ships with gnome 2.26 too, but whats different I enjoied. The system services configuration for instance.
Oh, and for testing packages in debian, or just setting up clean build environments or so, i'd recommend setting up chroots. You'll enjoy.

So long
Just my 2 ct :)

---

### Post by HappyFeet on 2009-04-28
It's OK if you do not enjoy Ubuntu anymore. Use what works for you. As for myself, Jaunty is a pleasure to use. Peace.

---

### Post by iris-n on 2009-04-28
maybe it was bad luck of mine then. I already had a functioning system, with some tricky software installed (mostly research stuff), and didn't want to start from scratch. So I went on purging things, which led to strange bugs that I didn't really want to solve. I assumed if I built up the system the same behaviour would incur. What has especially annoyed me is the ubuntu-desktop package. You can't really remove it, if you want to do a full upgrade. And it depends on numerous things that I don't need. So I'd rather get a distro who does not enforce a particular desktop setting.

In installing debian, I did just that. Installed a basic system, then gnome-core, and went adding my favourite apps. It's the darndest thing.

And yes, DontZap is really sad. The typical n00b thing that hinders functionality. But I don't get your point about python. It shipped 2.5, AFAIK, which is quite recent and well tested. 2.6 would break things.

Neat stuff, chroot. If I had known it last time I compiled wireshark much woe would've been spared.

As for fedora, wouldn't touch it. Has very beta software, will probably break worse than ubuntu. But if you have the blood, best of luck.

The good thing is that we all have a choice. So share and enjoy! :tongue:

---

### Post by HappyFeet on 2009-04-28
> **iris-n said:**
> 
As for fedora, wouldn't touch it. Has very beta software, will probably break worse than ubuntu. But if you have the blood, best of luck.


I agree. I have tried it and quickly uninstalled it. It's not that I could not figure it out, it's just that as you stated, it breaks too much. Heck, it was broken from the start. But in all fairness, I'm sure there are people out there who use it and love it. To each their own.

---

### Post by loomsen on 2009-04-28
> **iris-n said:**
> In installing debian, I did just that. Installed a basic system, then gnome-core, and went adding my favourite apps. 
Yes, that's what I meant. You can easily do the same with every ubuntu image, just choose expert install or install a CLI or you may even setup your own menu. 

Aptitude even is included during installation, so you have a solid packagemanager and won't have to search to much from shell.

ubuntu-desktop package is just a meta-package, basically it tells apt to read it and depend on everything written to it.

There are ubuntu-minimal and ubuntu-standard metapackages too, ubuntu-standard, gnome-core and xserver-xorg-core plug gnome-session and you'd have the same as with debian.

Nevertheless, the choice would and should be debian if you wanna go like that.

--> Fedora: Yes, I know the betas aren't what you want to install, just grabbed some live images and liked it. Just downloading the preview, which is equal to testing state. 
As I've usually got different OSs installed, one is my main system, usually stable, and the others are for testing purposes only. So will Fedora be until the final. Then I might reconsider, if it actually leaks stability.
However, ubuntu, which happened to be my main OS for quite some time now, will be replaced. Bummer actually, but well...

Gonna give [LFS](http://www.linuxfromscratch.org/) a try as well, could take some time to set it up completely, but as I said, gonna put it on another, maybe my network hd or so, and work on from time to time. Doesn't need to be done all at once, at least what [LFS](http://www.linuxfromscratch.org/) concerns.
But once it's setup, I guess it will be hard to beat.

---

### Post by growled on 2009-04-28
I've played with nearly all the Top 15 on Distrowatch, and I've found that Linux is Linux. You can take any distro and configure it like you want it to be. If you can't that's your fault and not the distro.

---

### Post by omghax on 2009-04-28
> **growled said:**
> I've played with nearly all the Top 15 on Distrowatch, and I've found that Linux is Linux. You can take any distro and configure it like you want it to be. If you can't that's your fault and not the distro.

I completely agree.

---

### Post by Syirrus on 2009-04-28
> **growled said:**
> I've played with nearly all the Top 15 on Distrowatch, and I've found that Linux is Linux. You can take any distro and configure it like you want it to be. If you can't that's your fault and not the distro.

Agreed, but on a more positive note, that is what Linux and open source is all about... choice.

I have had success so far with 9.04 which is a first for me and ubuntu on my desktop (using it since warty).  I used Lenny and loved it and I'm loving 9.04.

---

### Post by iris-n on 2009-04-29
> I've played with nearly all the Top 15 on Distrowatch, and I've found that Linux is Linux. You can take any distro and configure it like you want it to be. If you can't that's your fault and not the distro.

Oh, indeed? Silly me, I thought that it was ubuntu's fault when gnome-power-manager began crashing on every other shutdown. And when the system sound themes suddenly stopped worked. And when my numeric keypad turned into a mouse controller, without no chance of going back. Really, that was all my fault. I must have been a really naughty boy to deserve all that.

And coincidentally, it all began when I tried trimming down ubuntu's cruft. Obviously it isn't bad design, it's me who has done wrong.

On a more serious note, I think that these bugs wouldn't have appeared if I built the system bottom up, instead of top down. But I'd already lost my respect, and decided to build the system using Debian.

I've used many Linux distros too. Specifically, Ubuntu, OpenSuSE, Fedora, Slack, Arch, FreeBSD (unix-like, if you must) and now Debian. And what I've found is that there are distros that are much more tinker-friendly than others. I could do insane things with Arch that didn't brought it down. SuSE had a bad habit of showing useless error messages. And so on. 

I may have corrected the bugs? Sure. But why? They shouldn't have shown up in the first place. I have indeed hunt one down, because, you know, it's my fault, and what I've encountered? It was caused by a gconf key that only ubuntu set that way. Very boring, to say the least. And time consuming to fix. So no, not gonna deal with that.

---

### Post by ukripper on 2009-04-29
Jaunty is the best release for me so far of all distros.

Use what works for you mate! In the end linux is all that matters...

---

### Post by Bios Element on 2009-04-29
> **iris-n said:**
> ~Snip~

He wasn't really trying to flame you, But your response was just rude.

---

