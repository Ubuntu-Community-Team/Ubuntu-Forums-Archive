---
title: "distro changing"
date: 2010-09-20
forum: The Cafe
---

### Post by sandyd on 2010-09-20
I have (as some of you might know) been using gentoo since june. However, its becoming an increasing problem, as there is not as much software and it takes a lot of time to compile. I initially moved to gentoo because I was able to customize it for my needs, and for its low memory usage. Im currently deciding between ubuntu, and opensuse. ideas?

---

### Post by Denis Krajnc on 2010-09-20
Ubuntu for sure. It's the best Linux based operating system for sure, because there are thousands of people working on it.

---

### Post by kamaboko on 2010-09-20
Try Mint Debian.

---

### Post by cj.surrusco on 2010-09-20
Well, what exactly are you looking for in an distro? You are bound to get biased answers on a *Ubuntu* forum anyway, since most of the people here prefer it to all other operating systems.

---

### Post by sandyd on 2010-09-20
> **cj.surrusco said:**
> Well, what exactly are you looking for in an distro? You are bound to get biased answers on a *Ubuntu* forum anyway, since most of the people here prefer it to all other operating systems.

im looking for customization, and non-heavyness

---

### Post by kaldor on 2010-09-20
> **kamaboko said:**
> Try Mint Debian.

Mint Debian ftw!


@ Carlee/Sandyd/whoever you are ;)

Mint Debian (LMDE) adds the Mint tools (mintmenu, mintinstall, etc) to a Debian Testing base. It's 100% compatible with Debian and is quite a lot lighter than Mint/Ubuntu.

I've been using it since release on two computers now. Love it to death.

---

### Post by Bachstelze on 2010-09-20
Ubuntu, duh.

---

### Post by sandyd on 2010-09-20
> **Bachstelze said:**
> Ubuntu, duh.

you know that im a die hard KDE fan right? :D and that each time I install some form of ubuntu, I have to screw with pulseaudio, because thats the only thing that allows me to have some form of sound eh? :D. But then again, I might upgrade to maverick just for the fun of it...

---

### Post by cj.surrusco on 2010-09-20
> **sandyd said:**
> im looking for customization, and non-heavyness

Well pretty much every Linux distro has a good level of customization available, but for lightness, you might want to try Xubuntu, or even lighter, Lubuntu. 

I see other people are recommending Mint, but I from what I read, Mint is an OS that focuses on usability, so probably not customization as much.

---

### Post by cariboo on 2010-09-20
I'd use any of the mini.iso's to install a basic system, and then add on what you need from there.

I have an Apple G4 running Debian lenny, for what I use it for (playing mp3s) I just installed a cli system and added just the programs I needed.

Ram usage:

```
free -m
             total       used       free     shared    buffers     cached
Mem:           311        255         56          0          4        204
-/+ buffers/cache:         46        265
Swap:          464          0        464
```

Hard drive usage:

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             9.0G  862M  7.7G  10% /
tmpfs                 156M     0  156M   0% /lib/init/rw
udev                   10M  640K  9.4M   7% /dev
tmpfs                 156M     0  156M   0% /dev/shm
willy:/media/music    298G   93G  206G  31% /media/music
```

cpu usage:

```
mpstat
Linux 2.6.26-2-powerpc (puntzi) 	20/09/10 	_ppc_

11:31:06 AM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
11:31:06 AM  all   10.49    0.00    0.49    0.32    0.06    0.03    0.00   88.60     62.77
```

---

### Post by sandyd on 2010-09-20
hmm... starting from debian minimal looks nice. I already have a cd of it since all my servers run it. But I have to ask, just how well documented is debian? One of the other reasons why I loved gentoo was that everything from a-z was very well documented, even how to establish an ipv6 runnel with he's tunnelbroker.

---

### Post by Bachstelze on 2010-09-20
> **sandyd said:**
> you know that im a die hard KDE fan right? :D and that each time I install some form of ubuntu, I have to screw with pulseaudio, because thats the only thing that allows me to have some form of sound eh? :D. But then again, I might upgrade to maverick just for the fun of it...

I'm very glad I don't have to worry about sound anymore, if it's still an issue. ;) I have installed Kubuntu Karmic on my mom's laptop, though, and she doesn't seem to have any issues with sound...

As for SuSE, I'm running it as a Xen dom0, so not very relevant to your thread I guess. I gave it a try for a few weeks as a desktop, but found it a lot slower than Ubuntu. The package manager, especially. That was with 10.3, don't know if it has improved since.

---

### Post by drawkcab on 2010-09-20
> **Denis Krajnc said:**
> Ubuntu for sure. It's the best Linux based operating system for sure, because there are thousands of people working on it.

Alert:  Critical Thinking Failure

[http://en.wikipedia.org/wiki/Argumentum_ad_populum](http://en.wikipedia.org/wiki/Argumentum_ad_populum)

---

### Post by kaldor on 2010-09-20
> **drawkcab said:**
> Alert:  Critical Thinking Failure

[http://en.wikipedia.org/wiki/Argumentum_ad_populum](http://en.wikipedia.org/wiki/Argumentum_ad_populum)

This.

Although Ubuntu's doing a good job in some areas, it's falling flat on its face in others.

---

### Post by Bachstelze on 2010-09-20
> **kaldor said:**
> 
Although Ubuntu's doing a good job in some areas, it's falling flat on its face in others.

Namely?

---

### Post by MooPi on 2010-09-20
In the past I've jumped around alot. But for the last year or two I've used Ubuntu almost exclusively. I'm now reconsidering this and weighing the options for which other distro to experiment with. The distros under consideration are Fedora, Chakra, Archbang, PCLinux/openbox & Debian

---

### Post by Ctrl-Alt-F1 on 2010-09-20
I've never benchmarked Suse but it has always been significantly slower than Ubuntu as packaged by default.

I would give arch a try.  I once had a blazing fast arch desktop.  Other than that I'd try Ubuntu or Fedora.  Last time I checked, if you download the DVD version of Fedora, you can choose which major packages get installed during setup.

---

### Post by sidzen on 2010-09-20
> **sandyd said:**
> I initially moved to gentoo because I was able to customize it for my needs, and for its low memory usage. Im currently deciding between ubuntu, and opensuse. ideas?

Neither one of those is "low memory usage."  Why limit yourself to them?

If you know gentoo, slackware is the next logical step forward, not those, I would say.  (I know -- everyone has an opinion just like they have an . . .)

*Salix 13.1.1 XFCE* would be logical.

The new *aptosid* would be a challenge you may enjoy, if Debian is on your agenda.  

In any case, 
Best wishes!

---

### Post by sandyd on 2010-09-20
> **kaldor said:**
> This.

Although Ubuntu's doing a good job in some areas, it's falling flat on its face in others.

methinks kde falling harder on its face... you should have seen what hapenned when I installed kdepim/akonadi with kde 4.5..

---

### Post by sandyd on 2010-09-20
> **sidzen said:**
> Neither one of those is "low memory usage."  Why limit yourself to them?

If you know gentoo, slackware is the next logical step forward, not those, I would say.  (I know -- everyone has an opinion just like they have an . . .)

*Salix 13.1.1 XFCE* would be logical.

The new *aptosid* would be a challenge you may enjoy, if Debian is on your agenda.  

In any case, 
Best wishes!

I, essentially want to spend less time maintaining my computer than working on it. Im currently leaning heavily on debian minimal atm... You see, I am good with linux, so I dont need all these user frieldly stuff that make distros more heavy. at the same time, I still want to have an easy to maintain distro (a difficult setup is no problem, as long as maintaining isnt).

---

### Post by Dragonbite on 2010-09-20
> **sandyd said:**
> you know that im a die hard KDE fan right? :D and that each time I install some form of ubuntu, I have to screw with pulseaudio, because thats the only thing that allows me to have some form of sound eh? :D. But then again, I might upgrade to maverick just for the fun of it...

I've thrown openSUSE on my laptop for a while, partially to get used to KDE which is pretty nice.

With openSUSE, any program you don't find in the repositories you have a good chance to find in the openSUSE Build Service (OBS) with an easy [_software search_]("http://software.opensuse.org/113/en").  Plus there is OMG!SUSE! with tips, applications and info regarding openSUSE.

Unfortunately, I tried updating to KDE 4.5 and that just didn't work on my system.  Other people have gotten it working but it doesn't seem to like my computer so I've given up.

Actually I just installed Fedora 13 KDE and have been pleasantly surprised!  Not only has it worked fine for me, including desktop effects, but things like changing Konquerer from KHTML to WebKit engine, or Plasma Netbook Workspaces has worked a heck-of-a-lot better than it ever did in openSUSE!

So if you are looking for a pretty good KDE that gives you room to customize I wouldn't rule-out Fedora.  Fedora will provide you with an as-upstream-as-possible KDE environment that works.

---

### Post by snowpine on 2010-09-20
> **sandyd said:**
> I have (as some of you might know) been using gentoo since june. However, its becoming an increasing problem, as there is not as much software and it takes a lot of time to compile. I initially moved to gentoo because I was able to customize it for my needs, and for its low memory usage. Im currently deciding between ubuntu, and opensuse. ideas?

I know you are a very experienced Ubuntu/Kubuntu user :) have you ever used Opensuse before? If not, it might be fun to learn something new.

---

### Post by sandyd on 2010-09-20
> **snowpine said:**
> I know you are a very experienced Ubuntu/Kubuntu user :) have you ever used Opensuse before? If not, it might be fun to learn something new.

you have noo idea how many oses this laptop has endured :D. Lets see... mac osx, windows 7, windows XP, Ubuntu, Gentoo, Fedora, Opensuse, debian.... anyways... goodbye gentoo... Ill miss you.... im going to replace you with debian minimal...

---

### Post by Dustin2128 on 2010-09-20
> **sandyd said:**
> im looking for customization, and non-heavyness
I'd recommend arch. Slack is pretty hefty on the default install, but I'd highly recommend it because it makes for a rock solid system, though you may have to compile a significant amount of software.

---

### Post by CraigPaleo on 2010-09-20
> **sandyd said:**
> im looking for customization, and non-heavyness

In that case, you might want to try this remix. [Tutix Ubuntu Remix]("http://pinoy-computing-tips.blogspot.com/2010/06/ubuntu-tutik-remix-1004.html") It's a light-weight version of Ubuntu with more themes included.

---

### Post by sidzen on 2010-09-22
"I, essentially want to spend less time maintaining my computer than working on it.
I still want to have an easy to maintain distro."

Lowest maintenance distro I ever used was Element with bastille attached.  Didn't do much to it at all for a long time.  Customizing the GUI would be fun, too.

Low maintenance is a plus for many things -- I can agree with *that* !
:wink:

---

### Post by KdotJ on 2010-09-22
I'd recommend Arch, pacman is great. Also they have the Arch User Repository (AUR) which has loads of packages... And you can use the nifty 'yaourt' tool to install and manage them easily

---

### Post by Dragonbite on 2010-09-22
> **sidzen said:**
> "I, essentially want to spend less time maintaining my computer than working on it.
I still want to have an easy to maintain distro."

Lowest maintenance distro I ever used was Element with bastille attached.  Didn't do much to it at all for a long time.  Customizing the GUI would be fun, too.

Low maintenance is a plus for many things -- I can agree with *that* !
:wink:

That's what brought me to Ubuntu in the first place, and why I have that as the family desktop (which I don't get much time on, so I don't want to be spending all of my time maintaining it when I do get some time on it!)

---

### Post by undecim on 2010-09-22
> **sandyd said:**
> im looking for customization, and non-heavyness

Then I recommend a minimal Ubuntu install or Arch.

Ubuntu minimal I think is easier to setup/use overall, but probably has a little more fat on it than Arch (though still being at a healthy weight)

Both would require you to install only what you need from binary repositories (though both also allow you to compile those packages from source if you need to patch them or use different configs)

If you've been using Gentoo, you should be experienced enough to handle either one.

---

### Post by Dragonbite on 2010-09-22
> **undecim said:**
> Then I recommend a minimal Ubuntu install or Arch.

Ubuntu minimal I think is easier to setup/use overall, but probably has a little more fat on it than Arch (though still being at a healthy weight)

Both would require you to install only what you need from binary repositories (though both also allow you to compile those packages from source if you need to patch them or use different configs)

If you've been using Gentoo, you should be experienced enough to handle either one.

openSUSE and Fedora, installed from the DVD or NetInstall, allows you to pick what apps you want right in the beginning or you have the option to install from a LiveCD.

---

