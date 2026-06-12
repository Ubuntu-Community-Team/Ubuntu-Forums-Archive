---
title: "Wine doesn't work on Intrepid (SYSTEM CRASHES)"
date: 2009-01-15
forum: Wine
---

### Post by El Potro on 2009-01-15
I think this is a problem of the distro's new version. I had installed Ubuntu 7.10 and wine worked just fine. Now in 8.10, no matter what I do, which program I run under wine... it simple crashes. But it doesn't only crash, but all the computer is freeze. I can't even go to a console (Alt+Ctrl+F1, F2, F3...) or reset the X (Alt+Ctrl+Backspace). It just freezes and the only thing I can do is restarting the computer.

I'm really surprised and don't know what to do.

Did anyone have experienced something like this? Please, give me a hand, I can't live with many windows programs, really.

Hope someone can give a hand, I'd appreciate it a bunch.

Mauricio

---

### Post by 0bso on 2009-01-16
What version of wine are you running? There's a sticky at the top about crashes, you might try downgrading to that version if you have the newest one.

Do all other aps work fine? Is it a fresh install?

Hard locking like that almost sounds like a ram issue, try running memtest86 from your live-cd.

---

### Post by hikaricore on 2009-01-16
Are your video drivers installed properly?

I've seen WINE hardlock before without hardware rendering.
Not sure if this is still and issue, but also try disabling desktop effects.

To check for hardware rendering run (from a terminal):

> glxinfo | grep rendering

---

### Post by El Potro on 2009-01-16
Hello everybody,

Previously I was running Ubuntu 7.10 and Win XP at the same time and everything worked fine but I was a little behind with my version so, tried to format the disc, installed win xp and then ubuntu 8.10, and all flawless but... when I try to use wine, it crashes whenever I start a windows program (but for example notepad that comes with wine doesn't) the computer freezes and the only thing I can do is reset it for taking back control.

I've tried installing only ubuntu 8.10, but it was the same. I don't know what video driver I'm using, but I don't have an Agp card, it's just a simple on-board one. Could be it ? I don't really think so.

So... I don't have the less idea of what I can do.

I will check out that crashes thread, and try downgrading wine version (since I want to use the new ubuntu version) right? then you'll know what has happend.

Thank you very much for helping out,

Mauricio

---

### Post by El Potro on 2009-01-16
Hi, I just checked 

> glxinfo | grep rendering

and this is what I get:

> direct rendering: Yes

Is this good?

Thanks

---

### Post by El Potro on 2009-01-16
Hello!

I just also did a memory test with the Ubuntu 8.10 disc, and passed with no errors.

And I downgraded wine too, with the package in the sticky, but nope, wine hasn't worked alright yet.

Can anyone help in anyway? 

Thank you very much,

Mauricio

---

### Post by El Potro on 2009-01-16
Please, isn't anyone out there that can help ?

---

### Post by hikaricore on 2009-01-16
> wine --version

Please post the output of this^

---

### Post by El Potro on 2009-01-16
hikaricore,

I have tried donwgrading to 1.1.11 like the sticky says, and since it didn't work, also tried 1.1.6 but with no good luck. And of course also tried with the default 1.1.12 that didn't work either.

The version I have installed now is wine-1.1.6 (that's the output of wine --version) but is the same with all those I mentioned before.

What do you think? Should I try with 8.04? :-(

It's very unhappy for me having to go backwards 6 months in software developing just for one program.

---

### Post by hikaricore on 2009-01-16
I don't think your version of Ubuntu is the issue.

This is likely somehow related to WINE, your graphic driver/hardware, or sound.

What programs are you trying to run?

Do you get this same behivior when running any of the following?

> 
winecfg
notepad
winemine
regedit

Also I forget if I asked or not, you DID disable desktop effects before trying anything with WINE correct?
With integrated hardware you're just asking for trouble using them in the first place, let alone when run WINE.

---

### Post by El Potro on 2009-01-16
Hi hikaricore, all the programs you listed work perfectly, but when I try to run the Photoshop 7 or 9 installer, or a program called PhotoFiltre (can be downloaded from here [http://photofiltre.free.fr/utils/pf-setup-en.exe](http://photofiltre.free.fr/utils/pf-setup-en.exe) ) the computer completely freezes and there's no thing I can do, really. Nothing works, it just freezes. Never something like that happened to me in any linux distro. If I run the programs from a terminal window, nothing weird appears, it just freezes, nothing can be done, Alt+Ctrl+Backspace doesn't work and Ctrl+Alt+F1,F2,F3,F4 either.

And I can't enable desktop effects, even if I wanted it, I can't because the graphics card isn't a heavy one, it's just a normal on-board one.

What's next? do you have any ideas?

thanks a lot,

Mauricio

---

