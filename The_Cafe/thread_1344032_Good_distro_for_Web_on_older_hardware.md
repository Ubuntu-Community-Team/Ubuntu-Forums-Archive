---
title: "Good distro for Web on older hardware?"
date: 2009-12-02
forum: The Cafe
---

### Post by rapper97 on 2009-12-02
I am working on setting up a communal machine in a communal living space, on a box with 256 megs of RAM, a PIII processor, and a smallish hd - I'd actually really like something that runs comfortably under 128 MB.  This box would be primarily for Web browsing, of course (proprietary plugins and all), but also maybe for basic things like word processing, playing videos or music, image editing, etc.  I was looking briefly at Lubuntu, but more likely will go with Puppy, Zenwalk, or Crunchbang; openSuSE also seemed like a good idea for some reason.  The thing is, all those distributions seem to be geared towards more than just a desktop user, unless you consider a desktop user someone who whips up Perl scripts in their spare time - I'm sorry, no one is *ever* going to program on this computer.  Puppy seemed sufficiently ridiculously small, but, aside from also having more than what I consider "basic," the default DE feels a little bit clunky to me; I'd like something that feels "slicker," and Xfce and LXDE seemed to fit the bill in my experiences with them.  Is my best bet to just get one of the above and take off all the unneeded stuff?  or is there some other distro that's both geared to the average esktop user and ridiculously lightweight?

---

### Post by whoop on 2009-12-02
tiny core

---

### Post by Cam42 on 2009-12-02
> **whoop said:**
> tiny core
This.

---

### Post by Bigtime_Scrub on 2009-12-02
Debian with Xfce, which is waaaay faster than Xubuntu. 

Also consider Puppy or CrunchBang.

---

### Post by -grubby on 2009-12-02
Can I say Arch without being stabbed?

---

### Post by earthpigg on 2009-12-02
the current stable release of my project is based on ubuntu 9.04, if that isnt a big deal to you. it uses less resources than crunchbang, but more than tinycore, puppy, etc.

---

### Post by Hallvor on 2009-12-02
Install Debian Lenny without any desktop environment, then follow this to get a minimal LXDE desktop: [http://wiki.lxde.org/en/Debian](http://wiki.lxde.org/en/Debian)

From there you can just install what you need. Much easier than removing all the stuff you don`t want/need.

---

### Post by Bachstelze on 2009-12-02
Ubuntu, with whatever DE/WM you feel like installing. I would personally go with Fluxbox, but XFCE should be fine if you want a bit more eye-candy.

---

### Post by RiceMonster on 2009-12-02
Slackware

---

### Post by Grifulkin on 2009-12-02
> **whoop said:**
> tiny core

+9000

> **-grubby said:**
> Can I say Arch without being stabbed?

Stabity Stab Stab.  Seriously Love Arch.

---

### Post by snowpine on 2009-12-02
I'd suggest BrowserLinux (formerly known as BrowserPuppy).

It does one thing, very well.

---

### Post by dragos240 on 2009-12-02
I got arch on a 124mb ram i586 computer. Even though arch is i686, it worked. Detected all my hardware, and I got xfce working on it. It's very very fast. However, you have more ram, and most likely more HD space than my laptop, so you can do more.

---

### Post by dragos240 on 2009-12-02
> **Grifulkin said:**
> +9000


WHAT 9000!!? THERES NO WAY THAT CAN BE RlGHT!

---

### Post by RiceMonster on 2009-12-02
> **dragos240 said:**
> IT'S OVER NlNE THOUSAND!!!

No it's not.

---

### Post by Grifulkin on 2009-12-02
> **dragos240 said:**
> WHAT 9000!!? THERES NO WAY THAT CAN BE RlGHT!

Exactly what I was thinking while typing that response.

---

### Post by dragos240 on 2009-12-02
> **RiceMonster said:**
> No it's not.


I changed that the instant I noticed that. Check it out now.

---

### Post by NormanFLinux on 2009-12-02
ZevenOS. BEOS-like distro, works great on underpowered hardware. I imagine once Haiku is ready, it will also run well on older hardware.

---

### Post by Warpnow on 2009-12-02
Run the X server directly with different programs from the command line, without a WM/DE.

---

### Post by RiceMonster on 2009-12-02
> **Warpnow said:**
> Run the X server directly with different programs from the command line, without a WM/DE.

Why? Talk about making life hard for no reason. If you want to keep resources as low as possible, you can use evilwm or dwm, which will hardly add anything.

---

### Post by rapper97 on 2009-12-02
> **-grubby said:**
> Can I say Arch without being stabbed?

I've looked at that, and I like the idea behind it, but given that it plonks you into a login screen with no GUI, it just seems like *waaaaaay* too much heavy lifting to get it to where I wanna be. I mean, someone must have done all that for me already, right?

> **NormanFLinux said:**
> ZevenOS. BEOS-like distro, works great on underpowered hardware.
[font="monospace"]<3[/font] BeOS, but let's face it, it's not worth it to have a system that's basically Ubuntu with extra stuff on top of it just to make it look like Zeta, for a bunch of people who have never heard of Be. This needs to be a rock-solid, set-it-up-for-someone-else-and-let-it-just-run machine.

---

### Post by &#32 Greg on 2009-12-02
> **rapper97 said:**
> I've looked at that, and I like the idea behind it, but given that it plonks you into a login screen with no GUI, it just seems like *waaaaaay* too much heavy lifting to get it to where I wanna be. I mean, someone must have done all that for me already, right?

If you're not willing to go command line, then SliTaz or TinyCore is your best bet. But command lines are not that hard.

---

### Post by Warpnow on 2009-12-02
> **RiceMonster said:**
> Why? Talk about making life hard for no reason. If you want to keep resources as low as possible, you can use evilwm or dwm, which will hardly add anything.

Its not that hard to do. I use the script posted here:[http://ubuntuforums.org/showpost.php?p=8352073&postcount=6](http://ubuntuforums.org/showpost.php?p=8352073&postcount=6)

---

### Post by RiceMonster on 2009-12-02
> **Warpnow said:**
> Its not that hard to do. I use the script posted here:[http://ubuntuforums.org/showpost.php?p=8352073&postcount=6](http://ubuntuforums.org/showpost.php?p=8352073&postcount=6)

I didn't say it was hard to do; I know how to do it. I meant you're just making things difficult for yourself because once you've opened a window, you can't move or resize it. So what's the point?

---

### Post by Warpnow on 2009-12-02
The OP said primarily for web browsing. My thought was throw up an X session with a web browser and leave it up. You want something else, open a new x session.

---

### Post by earthpigg on 2009-12-02
Chromium OS? :D

or, at least consider using Chrome instead of ff.

---

### Post by Warpnow on 2009-12-02
> **earthpigg said:**
> Chromium OS? :D

or, at least consider using Chrome instead of ff.

Definitely. Firefox will hardly run on 128mbs of ram in my experience. I used a 128meg PC up until about 2 years ago when I got my C2D. Firefox would take 10 minutes to start.

Chromium OS actually WOULD work well. Or really, any OS with Chrome. I'd still do what I said above...just open chromium without a WM, you can use google docs for word processor.

---

