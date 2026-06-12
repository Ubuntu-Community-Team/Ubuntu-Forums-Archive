---
title: "Not that happy"
date: 2007-11-12
forum: Testimonials &amp; Experiences
---

### Post by Shetil on 2007-11-12
Linux is said to be faster and more secure than Windows. And Linux users really like to mock Window's blue screen of death.

But...

While my Linux (Ubuntu) servers run flawlessly over really long periodes of time (years) the desktop experience is not that good.

Two things that bugs me:

1) Compiz crashes. Not often, but it happens.  And sure, it is really easy to start it again (if you know how) but such a vital part of the desktop experience should not crash without notice.

2) The Linux alternative of blue screen is to freeze completely. Nothing helps but to restart the computer. I think I prefer the Windows way of crashing. 

Last time this happened (a couple of minutes ago) Miro was the culprit. I think that is just wrong that an application can make my desktop freeze so that I lost all my data.

To summarize:
While Linux as a server really lives up to the hype, and is stable, fast and reliable, the same thing cannot be said about the desktop experience. It crashes too often and the handling of crashes is not good.

---

### Post by loell on 2007-11-12
> Last time this happened (a couple of minutes ago) Miro was the culprit. I think that is just wrong that an application can make my desktop freeze so that I lost all my data.

name of the application?


> To summarize:
While Linux as a server really lives up to the hype, and is stable, fast and reliable, the same thing cannot be said about the desktop experience. It crashes too often and the handling of crashes is not good.

I don't know who to blame with the linux desktop hype. i don't believe its faster than windows atm when it comes to executing same exact applications ie( [win gimp, lin gimp], [win firefox , lin firefox]) , i just think it has the same speed when you have the right hardware and right drivers. 

there's a need to educate new users to not to overstate what linux desktop can do, sadly thats kinda hard to do w/o conflict.



however, you and i both know that application crash can be attributed largely to the app itself not the operating system.

---

### Post by eldragon on 2007-11-12
> **Shetil said:**
> 
1) Compiz crashes. Not often, but it happens.  And sure, it is really easy to start it again (if you know how) but such a vital part of the desktop experience should not crash without notice.

what we should underline is: vital part of the desktop. compiz isnt vital. and its not even ready. the fact that it got included in 7.10 doesnt make it stable. it shouldnt have been included.

> **Shetil said:**
> 
2) The Linux alternative of blue screen is to freeze completely. Nothing helps but to restart the computer. I think I prefer the Windows way of crashing. 

Last time this happened (a couple of minutes ago) Miro was the culprit. I think that is just wrong that an application can make my desktop freeze so that I lost all my data.


you aparently have a problem in your computer the rest of us isnt having. last time i experienced a kernel panic was due to a faulty sata cable. you could always scan the kernel logs, and see what the kernel was doing when it froze. pinpoint the problem, and fix it.

thats what i would do, but maybe you should just call it quits, and get windows beta, err..i mean, vista.

---

### Post by wattazoum on 2007-11-12
Hello, 

I definitely agree with one of your point : 
> I think that is just wrong that an application can make my desktop freeze so that I lost all my data.

IT'S A BIG MISTAKE TO LET XORG MANAGE THE KEYBOARD !

If one application makes X crash then there is no access to the keyboard anymore ( at least to go to another TTY ) . That's the bigger mistake GNU/Linux desktop has ever made.

---

### Post by DeusEx on 2007-11-12
as **eldragon** points out, check your system logs for errors.
And don't exclude faulty hardware just jet.

---

### Post by mivo on 2007-11-12
> **Shetil said:**
> Linux is said to be faster and more secure than Windows. And Linux users really like to mock Window's blue screen of death.

Actually, in several years of using XP I only had a couple of system crashes. I thought XP was a pretty decent OS, though too limiting for me, but not "bad". Earlier Windows versions did produce BSODs pretty often, though.

Likewise, Ubuntu is very stable for me. My old desktop PC did freeze a few times during Gutsy *beta*, but both that box and my new desktop have been running Gutsy for some time now without any problems (old box has an ATI X700pro, new one an Nvidia 8800GTS). I have many of the Compiz-Fusion plugins enabled, I use AWN, and I have not been experiencing any issues. I'm not saying that this is the same for everyone, it certainly isn't, but these are also not troubles that can be generalized. They don't affect everyone.

For me, Linux is ready for the desktop. I use it for work stuff as well, and I do not dual-boot. Other people's mileage may vary, but from my perspective Linux, and especially Ubuntu, have a positive influence on my productivity and overall computer happiness. :)

---

### Post by zetetic on 2007-11-12
[QUOTE=1) Compiz crashes. Not often, but it happens.  And sure, it is really easy to start it again (if you know how) but such a vital part of the desktop experience should not crash without notice.
[/QUOTE]

Oh my! I've beeen running desktop operating systems without a vital part of the desktop experience for more than 15 years!

The things we learn here...

---

### Post by Shetil on 2007-11-12
The issues that frustrates me the most is that the desktop freezes without warning and without any possibility to restore it. I doesn't happen often, but it does happen.

This is not isolated to my hardware or setup. I have tried Ubuntu on several different systems, and tried other distributions as well, they all have frozen at least once.
Ok, I admit, I like to try new things and things that are a bit "unstable" but I still think the desktop behavior could improve.

If this is a problem with X crashing then warn me, kill X, and let me start a new session.

---

### Post by Shetil on 2007-11-12
> **eldragon said:**
> what we should underline is: vital part of the desktop. compiz isnt vital. and its not even ready. the fact that it got included in 7.10 doesnt make it stable. it shouldnt have been included.


That be it, I still think that Compiz could have done things different when it does crash.

What happened with the Beryl way of falling back to Metacity when it crashed?

And what about showing a dialog giving me the option to restart Compiz?

My main complaint is that the Linux desktop handles things badly when something unexpected happens.

---

### Post by Shetil on 2007-11-12
> **zetetic said:**
> Oh my! I've beeen running desktop operating systems without a vital part of the desktop experience for more than 15 years!

The things we learn here...

The thing is that when Ubuntu encourage people to activate Compiz and Compiz does crash leaving the desktop in a mess, then it seems vital.  At least to a big percentage of people starting to use Linux.

---

### Post by mivo on 2007-11-12
> **Shetil said:**
> This is not isolated to my hardware or setup. I have tried Ubuntu on several different systems, and tried other distributions as well, they all have frozen at least once.

If this happens with all distros, it might be related to your hardware. Have you checked the memory? It could be a hardware incompatibility, too.  Those random freezes are hard to pin down, though.

---

### Post by zetetic on 2007-11-12
> **Shetil said:**
> The thing is that when Ubuntu encourage people to activate Compiz and Compiz does crash leaving the desktop in a mess, then it seems vital.  At least to a big percentage of people starting to use Linux.

If it crashes (and if you agree that's not a vital part of any desktop experience), then I have a fine solution to your problem:

aptitude purge compiz

Anyway, Ubuntu should not encourage people to use compiz until a stable or not beta version of that 3d window manager is released.

In fact, this is the reason why even Debian testing does not install compiz by default.

Perhaps another good solution (and prevention) would be to just install Debian.

---

### Post by wolfen69 on 2007-11-12
it's obviously a problem with your hardware. i never have freeze ups, and rarely have any glitches. my computer runs better with linux than it ever did with windows.

maybe you could try another distro and see what happens.

---

### Post by icechen1 on 2007-11-12
> **Shetil said:**
> 
1) Compiz crashes. Not often, but it happens.  And sure, it is really easy to start it again (if you know how) but such a vital part of the desktop experience should not crash without notice.


I have this bug too,it is fixed by disableing some plugins,after all,compiz is not fully stable yet.

---

### Post by eldragon on 2007-11-12
i could almost bet the problem is compiz + display drivers.

that would definately give you a freeze. did happen to me in the past. especially with the open source ati drivers (ohh the irony!)

ati's 8.42.3 are much better, but they will not handle aiglx as they should. so, i would hold compiz off  if you are using an ati card...

if you got an nvidia card, i cant help you much, never used a "green" gfx under linux.

---

### Post by RawMustard on 2007-11-12
> **Shetil said:**
> Linux is said to be faster and more secure than Windows. And Linux users really like to mock Window's blue screen of death.

But...

While my Linux (Ubuntu) servers run flawlessly over really long periodes of time (years) the desktop experience is not that good.

Two things that bugs me:

1) Compiz crashes. Not often, but it happens.  And sure, it is really easy to start it again (if you know how) but such a vital part of the desktop experience should not crash without notice.

2) The Linux alternative of blue screen is to freeze completely. Nothing helps but to restart the computer. I think I prefer the Windows way of crashing. 

Last time this happened (a couple of minutes ago) Miro was the culprit. I think that is just wrong that an application can make my desktop freeze so that I lost all my data.

To summarize:
While Linux as a server really lives up to the hype, and is stable, fast and reliable, the same thing cannot be said about the desktop experience. It crashes too often and the handling of crashes is not good.

Blame Gnome not Linux.
[http://ubuntuforums.org/showthread.php?p=3759381#post3759381](http://ubuntuforums.org/showthread.php?p=3759381#post3759381)

---

### Post by armandh on 2007-11-13
if the core hardware and the kernel are not right Linux will suck just as bad as windohs. that the os can be changed in so many ways does not mean it should be. it is what I keep a spare HDD for....trying out the newest install.

---

### Post by spiff95 on 2007-11-13
Spare HDD- That is a good idea! I think I just had a "duh, why didn't **I** think of that?" moment. :-)

---

