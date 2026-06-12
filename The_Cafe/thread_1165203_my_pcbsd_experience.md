---
title: "my pcbsd experience"
date: 2009-05-20
forum: The Cafe
---

### Post by wsonar on 2009-05-20
Basicly I wanted to go with KDE because I found myself using the kde apps in gnome because they where better than the gnome alts.

So I decided to try the acclaimed PC-BSD

I'm currently posting this from an unconfigured video card so that's pretty frustrating to start

jaunty automatically detected and offered me the restricted driver and worked perfectly

I've tried all these drivers for my system on pc-bsd and can't get video to work to save my life currently a have a help post on the pc-bsd forum for this

besides that jaunty installs faster and boots faster

I'm sure it will be somewhat decent after I get my video working

but that's my pc-bsd experience so far.

---

### Post by wsonar on 2009-05-20
from the looks of the community I may be waiting a while
there's a lot of spam on there board

```
Who is online
Who is online 	In total there are 19 users online :: 5 registered, 1 hidden and 13 guests
Most users ever online was 263 on Thu Nov 01, 2007 12:14 am

Registered users: Ask Jeeves [Bot], dasnova, Google [Bot], MSN [Bot], Yahoo [Bot]

based on users active over the past 5 minutes
Legend :: Administrators, Global moderators
```

---

### Post by wsonar on 2009-05-20
So I found this

[http://lists.pcbsd.org/pipermail/testing/2007-September/000437.html]("http://lists.pcbsd.org/pipermail/testing/2007-September/000437.html")

I had to use the vesa driver

lets see if compiz works now

---

### Post by wsonar on 2009-05-20
things still seem pretty choppy

---

### Post by wsonar on 2009-05-20
So I guess after getting these updates then I can choose the nvidea driver it did make me accept the agreement for the nvidea driver during install so hopefully after that things will start coming together

---

### Post by wsonar on 2009-05-20
So I'm still having to use the Crappy Vesa driver

anybody have any luck with video drivers using a IBM thinkcenter 8113?

until I get the correct video driver I'm sure everything will be choppy

---

### Post by baseface on 2009-05-20
what video card are you using?

---

### Post by baseface on 2009-05-20
oh and *perhaps*, you could read the freebsd hcl before you try installing pcbsd.

---

### Post by wsonar on 2009-05-20
To sum it up Jaunty up and running perfect out of BOX

PCBSD Would not install video  driver properly so system is still useless

---

### Post by baseface on 2009-05-20
what card are you using?

---

### Post by wsonar on 2009-05-20
> **baseface said:**
> what video card are you using?

It's onboard I think it's intell chipset

---

### Post by ibuclaw on 2009-05-20
FYI, NViDIA support is terrible and choppy, ATi support is worse ...

Though, when I did comparison benchmarks (between FBSD and Linux, Linux performing 25% more efficient in FPS) it was PCBSD Beta1 I used, and I couldn't tell where the problems in in FreeBSD started and the problems in KDE 4.1 ended, so things may have changed since then, but I doubt it.

---

### Post by baseface on 2009-05-20
> **wsonar said:**
> It's onboard I think it's intell chipset
 
well a for sure answer would probably help.
and it would also benefit you to RTFM. 
did you check the freebsd hcl BEFORE installing pcbsd? i doubt it. no bsd is like linux.

---

### Post by Icehuck on 2009-05-20
> **wsonar said:**
> To sum it up Jaunty up and running perfect out of BOX

PCBSD Would not install video  driver properly so system is still useless

Hate to say it, but this post here makes me think you aren't qualified to install PCBSD.  

Especially when you are saying you put Nvidia drivers on what seems to be an Intel graphics chip.

---

### Post by wsonar on 2009-05-20
> **baseface said:**
> oh and *perhaps*, you could read the freebsd hcl before you try installing pcbsd.

Being that the release is a modern OS and newer than my hardware
I didn't think I would have to

Nothing jumped out and said I should check the HCL being that 

> PC-BSD is a free operating system with ease of use in mind. Like any modern system, you can listen to your favorite music, watch your movies, work with office documents and install your favorite applications with a setup wizard at a click.

---

### Post by wsonar on 2009-05-20
> **Icehuck said:**
> Hate to say it, but this post here makes me think you aren't qualified to install PCBSD.  

Especially when you are saying you put Nvidea drivers on what seems to be an Intel graphics chip.

it is intel I junp around a few systems so I wasn't sure at first

I know all about PC hardware and software  this isn't my first rodeo OK

---

### Post by wsonar on 2009-05-20
> **baseface said:**
> well a for sure answer would probably help.
and it would also benefit you to RTFM. 
did you check the freebsd hcl BEFORE installing pcbsd? i doubt it. no bsd is like linux.

BLA BLA BLA I KNOw this

---

### Post by Giant Speck on 2009-05-20
> **wsonar said:**
> I know all about PC hardware and software  this isn't my first rodeo OK

If it's not your first "rodeo," then how did you not know for sure what graphics card you had?  And even while knowing it was an Intel chip, why were you trying Vesa and nVIDIA drivers for it?

---

### Post by wsonar on 2009-05-20
Because the intel didn't work the intel still dosen't work

only vesa works

---

### Post by wsonar on 2009-05-20
> **Giant Speck said:**
> If it's not your first "rodeo," then how did you not know for sure what graphics card you had?  And even while knowing it was an Intel chip, why were you trying Vesa and nVIDIA drivers for it?

in the EULA of PCBSD it had me accept the agreement for the nvidea drivers which was confusing that they would have that in the agreement if I didn't have that hardware

---

### Post by Giant Speck on 2009-05-20
> **wsonar said:**
> in the EULA of PCBSD it had me accept the agreement for the nvidea drivers which was confusing that they would have that in the agreement if I didn't have that hardware

PC-BSD has an EULA?

---

### Post by wsonar on 2009-05-20
Confirmed Bios shows intel82945 chipset

---

### Post by wsonar on 2009-05-20
> **Giant Speck said:**
> PC-BSD has an EULA?

[http://docs.pcbsd.org/guide/]("http://docs.pcbsd.org/guide/")

sorry license agreement

BSD license
INTEL firmware
Nvidia Drivers


I guess it's standard tho my mistake

---

### Post by ibuclaw on 2009-05-20
> **wsonar said:**
> [http://docs.pcbsd.org/guide/]("http://docs.pcbsd.org/guide/")

sorry license agreement

BSD license
INTEL firmware
Nvidia Drivers


I guess it's standard tho my mistake

EULA == End User License Agreement ...

EULA and License Agreement are the same thing ;)

---

### Post by wsonar on 2009-05-20
> **tinivole said:**
> EULA == End User License Agreement ...

EULA and License Agreement are the same thing ;)


Yea I mean I was confused because they included the agreement for the nvidea drivers in the "License Agreement" making it seem like it had detected an nvidia chip I didn't realize the nvidea driver was standard part of the LA

sure I should have booted into the bios and verified but modern OS's have made that unnecessary by detecting it for me.

we live in a rushed society if your like me your trying 20 different things at once and worrying about detail later I no it's not right but it is what it is

sorry to have came off with the negative vibe I get antsy when I'm trying to get things done and you can't all way's just count to 10


peace love and  goodwill to you all

---

### Post by Giant Speck on 2009-05-20
> **wsonar said:**
> sure I should have booted into the bios and verified but modern OS's have made that unnecessary by detecting it for me.

Well, just because it is a modern operating system doesn't necessarily mean it can auto-detect your hardware.  I could create an operating system right now and stop writing it after a few lines of code and it'll definitely not auto-detect your hardware.

Many of the limitations that BSD has is due to the fact that there is a much smaller userbase than the Linux, OS X, and Windows userbases.  It's still developing technology.

---

### Post by wsonar on 2009-05-20
I read about the same problem with my driver with openSolaris but then some developers said they had it working at 1600 res with compiz but it's still not on the HCL

I'll get it going but I hope the bsd userbase will continue to grow it's frustrating when there forum isn't hardly populated or moderated

I get more response on here about bsd then on the actually pcbsd board.

---

### Post by nitehawk777 on 2009-05-20
I used PCBsd,....back when it was at version 1.5.  I thought it was pretty good,...(and I had an older Intel i815 chipset).
Anyway,...it's true that their forum gets a bit lonely (not much activity).  And it's become a well-known fact that a lot of the one's that were the main "helpers" and the "Admins" of the forum actually use FreeBsd,...(and not PCBsd)....

---

### Post by wsonar on 2009-05-20
> **nitehawk777 said:**
> I used PCBsd,....back when it was at version 1.5.  I thought it was pretty good,...(and I had an older Intel i815 chipset).
Anyway,...it's true that their forum gets a bit lonely (not much activity).  And it's become a well-known fact that a lot of the one's that were the main "helpers" and the "Admins" of the forum actually use FreeBsd,...(and not PCBsd)....


yea that is true I guess I could kindly ask about the chipset on the freebsd board

---

### Post by nitehawk777 on 2009-05-20
Yes,..
PC-Bsd is really just a KDE front to FreeBsd.  But if you go ask at the FreeBsd forums,  they have a habit of just saying "RTFM"!!!
Anyhow,...I just took a look at PC-Bsd's forum, and you're right,.....
the huge amount of SPAM in there sure does look like noone is minding the store!  Sad.

---

### Post by phrostbyte on 2009-05-20
What you are experiencing is Linux has many more drivers then *BSD. The Linux source tree is like 10+ millions lines of code (clue: that's A LOT of code), and something like 75% of it is just .. drivers. Basically Linux ships with a LOT of drivers by default (probably more then any OS on the planet), and by extension Ubuntu has pretty good hardware support. Maybe 10 years ago BSD and Linux were about par driver wise, but since then Linux has grown much faster.

---

### Post by cammin on 2009-05-21
What version of Xorg and the xf86-video-intel driver are installed?
I'm guessing it's xorg 7.3 and xf86-video-intel 2.4.2 (or 2.4.3)

I've ran into that brick wall in both Linux, and in BSD. It flat out wouldn't work, no matter what I tried.

Xorg 7.4 and xf86-video-intel-2.6.3 are available in FreeBSD 7.2.

---

### Post by sourchier on 2009-05-21
Please reboot your PC-BSD system. When booting select the option number 7 run the display setup wizard. If this does not help, post the contents of your /etc/X11/xorg.conf.

---

### Post by izizzle on 2009-05-26
I've been stalling on trying a *BSD but I think I'm gonna give PC-BSD a shot. Well, off to read the HCL...

---

### Post by jrusso2 on 2009-05-26
Linux by far makes the best desktop of all the Unix and Unix like stuff out there.  This is after years of trying them all.

Linux has drivers the others all fall short in this area.

---

### Post by Sublime Porte on 2009-05-26
> Linux by far makes the best desktop of all the Unix and Unix like stuff out there.  This is after years of trying them all.

Linux has drivers the others all fall short in this area.

But it's not 'real unix', everyone has the itch to try 'real unix', thinking it's going to be magically better than Linux... perhaps if they wanted to run a server, it might be more stable for them, but as a desktop, stick with Linux, it's the most desktop oriented Unix (apart from OSX of course).

---

### Post by wsonar on 2009-05-27
> **Sublime Porte said:**
> But it's not 'real unix', everyone has the itch to try 'real unix', thinking it's going to be magically better than Linux... perhaps if they wanted to run a server, it might be more stable for them, but as a desktop, stick with Linux, it's the most desktop oriented Unix (apart from OSX of course).


With all the linsux crew hanging around I figured I'd give pc-BSD a shot to have something to base an opinion on. I choose pc-bsd because I figured it's the most comparable to kubuntu

it's just a lack of driver issue it's not that bsd is not good it's just that kubuntu already had my driver

after using KDE a while I installed emerald and compiz and it started looking like gnome but I figure if I'm running KDE it works better with the KDE composite manager

I guess I still prefer the look and customization of gnome but the stability of the KDE apps

---

