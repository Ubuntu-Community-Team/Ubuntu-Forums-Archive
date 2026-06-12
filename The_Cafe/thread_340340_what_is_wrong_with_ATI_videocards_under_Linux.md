---
title: "what is wrong with ATI videocards under Linux ?"
date: 2007-01-17
forum: The Cafe
---

### Post by MaximB on 2007-01-17
well , I have an ATI 9800 Pro videocard and I've heard that ATI's support in Linux is horrible.
the drivers are not open sourced and doesn't work well, the installation is crappy etc...

I really don't know what you mean (except the open source thing).
everything is working great for me (once you get it installed - and it's NOT that hard).
every game running at full speed and best graphics.

so tell me ATI users - what is wrong with ATI, why are you keep bashing it ?

---

### Post by maniacmusician on 2007-01-17
because you just got lucky.

My card actually ran **worse** under the proprietary drivers than the open source, and the open source ones were still pretty bad. My card was supposedly supported with fglrx, but um. no. not really.

I just bucked up and bought nvidia.

I feel sorry for all the notebook users out there who're stuck with ATI.

---

### Post by bigken on 2007-01-17
ye like me the open source seem ok but when I run beryl and browse the web the page scrolling is bloody awful and every time I try to install the proprietary
drivers I get the  the mesa drivers which are crap too say the least :-k

---

### Post by macogw on 2007-01-17
ATi also doesn't release drivers very quickly for Linux.  It can take a few months to get drivers after you buy the latest and greatest ATi card.

---

### Post by nsleiman on 2007-01-17
The fglrx works fine for mt ATI card but have problems with the login page, if i resize it to fit the screen i get everything messed with xorg.conf :( and i need to re-do the whole setup for it.

btw i found out how to make my card working i need first to set its driver to mesa, restart the X and changing the settings to fglrx. i couldnt figure out a better solution for me.

---

### Post by Dokatz on 2007-01-17
Just personal experience. Don't get me wrong, I was originally an ATi Fanboy, But linux has led me to take a less biased standpoint on hardware per application.

Radeon X300 Experience

[COLOR="Blue"]In windows I can play UT2004 With just about no lag at 1600x1200, Everything cranked up mostly all the way...Using the catalyst drivers...[/COLOR]

[COLOR="Red"]In linux I can play UT2004 at 800x600 with eveyrthing at normal, And still get occasional stuttering...Using the FGLRX drivers....[/COLOR]

So what more can I say than my personal experience. It works FINE but once you actually take a detailed look at performance, I know that the driver is bottlenecking my entire system (As far as graphics go)

---

### Post by jaimz on 2007-01-17
when I was first getting into linux, I had problems with my x800
and was a pain to get direct rendering on
but once I learned how to do it quick and easy

I never had a problem with it
runs great

haven't tried the open source drivers yet though

---

### Post by Kindred on 2007-01-17
I like my ATI card, it's r200 based and the open drivers work great, better than the proprietary ones overall.  I'll want a newer card & system soon though and will likely look at Intel first, then ATI, then nvidia.  Funny how that works..

---

### Post by TBOL3 on 2007-01-17
I have a Readion All In Wonder Card.  It is too old for them to make drivers for Linux, and probibly even in vista!  But linux recognized it as a Readion 7200, works fine, with two exeptions...
1. Ocasionally I have an increadibley low resolution.
2.  No TV output/input :(

---

### Post by Engnome on 2007-01-17
Both my X800 and a friends 9600 took loads of work to get working. :evil: 

Buy Intel, they just work :D Just wish they could make some high performance line of cards.

---

### Post by Ben Sprinkle on 2007-01-17
Eh? My ATI drivers worked upon first try, I just installed the ATI driver package via synaptic, then did a dpkg-reconfigure xserver-xorg and picked 'ATI'.

---

### Post by Engnome on 2007-01-17
> **Goat Spirit said:**
> Eh? My ATI drivers worked upon first try, I just installed the ATI driver package via synaptic, then did a dpkg-reconfigure xserver-xorg and picked 'ATI'.

We are talking about ATI's official driver here. ;)  

It doesn't do this: > **Goat Spirit said:**
> Eh? My ATI drivers worked upon first try

---

### Post by gmr on 2007-01-17
My ATI Card (Radeon 9600XT) runs horrible under linux. Quake3 is "grey in grey" and I often get problems with the 3D acceleration. 

U got lucky if ur card runs good under linux ;)

---

### Post by Ben Sprinkle on 2007-01-17
> **Engnome said:**
> We are talking about ATI's official driver here. ;)  

It doesn't do this:

I see....
Oh well, that's thier fault. :)

---

### Post by Patrick-Ruff on 2007-01-17
*sighs* another one of these threads . . . 

ok, let me take you though this.

ATI FGLRX drivers suck for just about everything. 

Open Source drivers only work well for those VERY lucky few who have full 3d accel with them. 

FGLRX doesn't s upport aiglx (all our eye candy and all that cool stuff) so we can't use beryl well, we have to run XGL (which takes away so much functionality that it isn't even worth it.)

oh and not to mention the fact that we have no direct 3d, all gamers are pretty much forced to use open gl to run their games (which is pretty crappy over all.)

you guys, please stop making these damn threads asking why we bash ATI, you shoudl know by now we have good reason to.

---

### Post by Miguel on 2007-01-17
What is wrong with ATI videocards under Linux? That's an easy question:[list]
[*] It took them over 6 months to support their X1000 cards under linux.
[*] Some of their cards (notably some X600) don't work with *their* drivers.
[*] 2D performance using fglrx is awful. Now it's not that bad, but it used to be 7 times slower than the OSS drivers.
[*] 3D performance (what you buy these cards for) is abysmal. If you are lucky you get half the FPS you get under windows. Some might argue this is because X11 is not part of the kernel (i.e. windows), but nVidia has windows performance, and Vista runs the GUI in userspace (IIRC).
[*] Scaling of fglrx to the X1000 series is abysmal. If you think fglrx underperforms with an X800, wait to see a X1800.
[*] The bug which *freezes* the computer when opening a second display, such as "open new session" has been around since, at least, 2004. Unfixed.
[*] They were a real pain in the a$$ to get working with widescreen resolutions.
[*] OpenGL support is only partial. That's why AIGLX doesn't work.
[*] Resuming from Suspend and Hibernate only works sometimes, although it has improved from the hard freeze that caused a while ago.
[*] An absolutely piece of crap as a control panel
[/list]

Of course, these drivers do have advantages:[list]
[*] Better performance than the reverse-engineered drivers (whoaaaa!!!! big achievment!!!)
[*] Slightly better power management than the reverse-engineered drivers (see above).
[*] TV-out
[*] Lower driver overhead than nVidia's proprietary driver
[/list]

---

### Post by EdThaSlayer on 2007-01-17
ATI cards just suck, I mean, a Geforce 2 comes close to the power of the ATI Radeon 9600 I have in terms of FPS(only 500 fps difference between Geforce 2 and ATI Radeon 9600...and my Geforce 2 does 1000 fps in glxgears...)

---

### Post by Patrick-Ruff on 2007-01-17
haha, amen to that.  

you use an R300, much like I, what do you use? open source or somethign?

---

### Post by Johnsie on 2007-01-17
With Edgy all i did with my ati was apt-get  to install beryl and it worked straight away. This wont be the case with all cards though.  The open source thing is important because it's hard to do tricks with a card if you dont know how the driver works.

---

### Post by Patrick-Ruff on 2007-01-17
**@EdThaSlayer ** we're not debating ATI cards sucking, keep your biased based on an ignorant mind elsewhere. 

this is merely about the fglrx driver.

---

### Post by Patrick-Ruff on 2007-01-17
> **Johnsie said:**
> With Edgy all i did with my ati was apt-get  to install beryl and it worked straight away. This wont be the case with all cards though.  The open source thing is important because it's hard to do tricks with a card if you dont know how the driver works.

uh no.  it's easy to do regardless of what you know of the driver.  if the driver doesn't support your card, you can't simple "add" support unless you're a C/C++ programmer that REALLY knows how the driver works.

so plain and simple, if the open source driver supports your card, you don't have to be a genius to figure it out.

---

### Post by Ben Sprinkle on 2007-01-17
> **Patrick-Ruff said:**
> *sighs* another one of these threads . . . 

ok, let me take you though this.

ATI FGLRX drivers suck for just about everything. 

Open Source drivers only work well for those VERY lucky few who have full 3d accel with them. 

FGLRX doesn't s upport aiglx (all our eye candy and all that cool stuff) so we can't use beryl well, we have to run XGL (which takes away so much functionality that it isn't even worth it.)

oh and not to mention the fact that we have no direct 3d, all gamers are pretty much forced to use open gl to run their games (which is pretty crappy over all.)

you guys, please stop making these damn threads asking why we bash ATI, you shoudl know by now we have good reason to.

I see you edited it, it did say *you people*, I was going to comment on that...

---

### Post by Miguel on 2007-01-17
> **Patrick-Ruff said:**
> haha, amen to that.  

you use an R300, much like I, what do you use? open source or somethign?

Yeah, I have a Mobility Radeon 9600 Pro Turbo (courtesy of Dell) on my laptop. As soon as I got the open sauce drivers working with 3d I switched. The funny thing is I *paid* money when configuring the laptop to change an nVidia 5200 Go for this ATi. 

I have a friend of mine who bought a new computer with an X700 and she was having some issues with the card (being PCIe instead of AGP). The thing is, as soon as I saw that r300 was working OK with 3d and everything, I never bothered to mention fglrx to her. She will be happier.

The truth is that having an ATi is the reason why my next laptop will have an Intel video card (well, that and the lower weight and longer battery life).

---

### Post by Ben Sprinkle on 2007-01-17
Good thing I got an intel card, I use the i810 driver and everything is smooth as a baby's butt.
My old laptop was ati mobility rage, which is like 10 years old. I couldn't find ANY drivers for even windows, what a crock.

---

### Post by Enverex on 2007-01-17
> **MAXDDARK said:**
> every game running at full speed and best graphics.

Correction, you THINK they are. If you ran those same apps on Windows on a an ATi card and nVidia card that got the same framerate, then tried the same on Linux you'd find the ATi card's performance just took a nosedive. ATi also drops support for cards as fast as possible. For instance they dropped support for every card below the 9500 a month or two ago now. ATi basically puts the minimum amount of effort possible into their Linux drivers.

---

### Post by EdThaSlayer on 2007-01-17
> **Patrick-Ruff said:**
> **@EdThaSlayer ** we're not debating ATI cards sucking, keep your biased based on an ignorant mind elsewhere. 

this is merely about the fglrx driver.

Iam running the fgrlx drivers!
Its just that the graphics power I have with this ATI card isn't really...well...equivalent to a Nvidia card of the same price.
And the reason I say ATI graphics cards are bad is because the fgrlx drivers are bad(if only fgrlx drivers gave you the full power of the hardware you paid for then...I would change my mind.)

---

### Post by Patrick-Ruff on 2007-01-17
> **Goat Spirit said:**
> I see you edited it, it did say *you people*, I was going to comment on that...

I type 130 wpm, sometimes I can get a few paragraphs down without realizing what I said lol.

thanks for pointing out what I edited out though . . . .

---

### Post by Patrick-Ruff on 2007-01-17
> **EdThaSlayer said:**
> Iam running the fgrlx drivers!
Its just that the graphics power I have with this ATI card isn't really...well...equivalent to a Nvidia card of the same price.
And the reason I say ATI graphics cards are bad is because the fgrlx drivers are bad(if only fgrlx drivers gave you the full power of the hardware you paid for then...I would change my mind.)

you specifically said cards, not drivers.

sorry if there was a misunderstanding :P.

---

### Post by mr.farenheit on 2007-02-11
i run a crappy ati in my notebook with shared memory and it actually runs alot better in linux. the only game i really play is wolfenstein et but i've noticed drastic changes in the performance on linux rather than on windows.

---

### Post by cowlip on 2007-02-11
my old 7200 still works with the open source drivers, although I could never run a game with it.  Beryl *barely* runs.  fglrx refuses to work with it, period.

I will never buy ATI again, let me tell you that.

Not to mention that proprietary drivers suck in general for dealing with new kernel versions and different architectures...

---

### Post by Redlance on 2007-02-11
I feel your pain.. I have an x850pro modded to an xt
6.06 had a problem with that.
6.10 got 3d runinning with walkthrough in one go. pretty sweet.

now I just bought an Asus G2p with a radeon Mobility x1700 (ati doesnt even support them yet in catalysts)
guess ill be waiting about 1/2 a year till a linux friendly variant comes my way.. as i have read x1600 mobility most people cant get ANY form of graphics running. As the transition with AMD/ATI continues i can only hope for better linux Support from AMD.
But for now i am pretty sure my goose is cooked till then.. when i get my laptop shipped and in my hot little hands. I will give the Ubuntu a go but I am not expecting it to even get to load screen if the woes of the other x1600 users is any indication.

---

### Post by derekr44 on 2007-02-12
Yeah, I run an x1600 Pro.  Have only been able to get the Mesa drivers to work..I'm considering switching over to nVidia after being an ATi user for all these years.

---

### Post by enzobelmont on 2007-02-13
i can feel your pain, i'm inchained to a compaq laptop with ati radeon xpress 200M
it runs fine in windows, but in linux is dissapointing.
worst desicion in my life, ati again... no, thanks.

PLEASE!! AMD do something about it.

---

