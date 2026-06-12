---
title: "Just what is wrong with Wubi?"
date: 2011-12-24
forum: The Cafe
---

### Post by lolpenguin on 2011-12-24
I have heard so much about Wubi being unreliable, unstable, etc. but I have been using a Wubi install for nearly half a year, and so far no problems have arisen. I _DO_ know that Wubi does not perform as well as a normal install, but is it really unreliable/unstable/etc.
Just so you guys don't press me to do a fresh install, I will do one as soon as I can find a cheap SSD to meet my needs.

---

### Post by inobe on 2011-12-24
i see folks complaining about editing windows bootloader/ boot.ini

from what i see that's it.

oh, and having trouble with suspend/ resume.

---

### Post by fdrake on 2011-12-25
> **lolpenguin said:**
> I have heard so much about Wubi being unreliable, unstable, etc. but I have been using a Wubi install for nearly half a year, and so far no problems have arisen. I _DO_ know that Wubi does not perform as well as a normal install, but is it really unreliable/unstable/etc.
Just so you guys don't press me to do a fresh install, I will do one as soon as I can find a cheap SSD to meet my needs.

use whatever works for you. I had wubi for 1.5 years and i have never had problems... i was just too lazy to do a full install

---

### Post by lolpenguin on 2011-12-25
> **inobe said:**
> i see folks complaining about editing windows bootloader/ boot.ini

from what i see that's it.

oh, and having trouble with suspend/ resume.
Suspend works absolutely fine for me...
> **fdrake said:**
> use whatever works for you. I had wubi for 1.5  years and i have never had problems... i was just to lazy to do a full  install
You're lazy too!

---

### Post by doorknob60 on 2011-12-25
It runs on top of Windows (well, more specifically, on top of the Windows partition, and relies on its bootloader), so whenever Windows gets screwed up (often), then Ubuntu stops working. The biggest problem is when you don't shut down correctly for whatever reason (crash/freeze, power outage, battery ran out, etc.), then often the NTFS partition will no longer mount and Ubuntu can't start until you boot Windows and then reboot. Usually at that point it just stops working for me altogether, where even after making sure the NTFS is cleanly unmounted, that it still is unable to boot Ubuntu for whatever reason, so I give up and install it the *right* way.

---

### Post by lolpenguin on 2011-12-25
> **doorknob60 said:**
> It runs on top of Windows (well, more specifically, on top of the Windows partition, and relies on its bootloader), so whenever Windows gets screwed up (often), then Ubuntu stops working. The biggest problem is when you don't shut down correctly for whatever reason (crash/freeze, power outage, battery ran out, etc.), then often the NTFS partition will no longer mount and Ubuntu can't start until you boot Windows and then reboot. Usually at that point it just stops working for me altogether, where even after making sure the NTFS is cleanly unmounted, that it still is unable to boot Ubuntu for whatever reason, so I give up and install it the *right* way.

That does happen if you force power off in Windows, but CHKDSK should solve the problem, and for the Windows gettings screwed up bit, I work mainly in Ubuntu so Windows won't suddenly stuff up.

---

### Post by philinux on 2011-12-25
> **lolpenguin said:**
> I have heard so much about Wubi being unreliable, unstable, etc. but I have been using a Wubi install for nearly half a year, and so far no problems have arisen. I _DO_ know that Wubi does not perform as well as a normal install, but is it really unreliable/unstable/etc.
Just so you guys don't press me to do a fresh install, I will do one as soon as I can find a cheap SSD to meet my needs.

The only thing with wubi is that it was never intended for long term use. Just another way to try out ubuntu. Read the interview with the developer.

 [http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

---

### Post by P1C0 on 2011-12-25
I used to have wubi and after some kernel upgrades I couldn't boot into Ubuntu because of a [wubildr issue]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10").

I would not recommend it for long term use. A clean install of Ubuntu is the way to go, and I wouldn't even recommend a dual boot if you don't need it, just put Windows in a Virtual Box.

---

### Post by Frogs Hair on 2011-12-25
Some friends use Wubi to install the latest release every six months and have never reported an problems.

I did have a problem with kernel updates in 9.10 , so I would just remove the nvidia driver prior to the update and reinstall after .

---

### Post by doorknob60 on 2011-12-25
> **lolpenguin said:**
> That does happen if you force power off in Windows, but CHKDSK should solve the problem, and for the Windows gettings screwed up bit, I work mainly in Ubuntu so Windows won't suddenly stuff up.

Yeah, chkdsk *should* fix it, but for me, it seems like half the time it doesn't. And Windows manages to screw itself even when not in use, especially when you're using Wubi, at least in my experiences. I've had very bad luck with Wubi, worse than most people, just sharing my own experiences :P

---

### Post by BC59 on 2011-12-25
I think the main problem with Wubi is the higher possibilities of an imperfect installation. And of course the long term problem of deterioration due fragmentation.

---

### Post by jwbrase on 2011-12-26
> **lolpenguin said:**
> I have heard so much about Wubi being unreliable, unstable, etc. but I have been using a Wubi install for nearly half a year, and so far no problems have arisen. I _DO_ know that Wubi does not perform as well as a normal install, but is it really unreliable/unstable/etc.

The biggest problem, as mentioned by others in this thread, is that Wubi is more vulnerable than a normal install to being screwed up by bad shutdowns. 

If you're very careful about shutting it down properly and don't suffer any power outages it should be just as stable and reliable as any other Ubuntu install.

---

### Post by forrestcupp on 2011-12-26
> **doorknob60 said:**
> so whenever Windows gets screwed up (often), then Ubuntu stops working.

I've used every mainstream version of Windows since 3.11. It's been years since I've had any trouble with Windows getting "screwed up". It's not nearly as prone to getting jacked as it used to be. I haven't really noticed any major problems since the early SPs of XP. I was even pleased with Vista, especially after the first SP.

Anyway, about Wubi. It's really not any harder at all to just install a dual boot setup. If you can figure out how to boot to a CD, the installer pretty much does it all for you. If you can boot to the LiveCD successfully, then there shouldn't be any problems until you start tinkering around.

---

### Post by BC59 on 2011-12-26
> **forrestcupp said:**
> I've used every mainstream version of Windows since 3.11. It's been years since I've had any trouble with Windows getting "screwed up". It's not nearly as prone to getting jacked as it used to be. I haven't really noticed any major problems since the early SPs of XP. I was even pleased with Vista, especially after the first SP.

Sad bad true. But I think he refers mainly to the file system and registry deterioration by the time. This is inevitable on Windows.

---

### Post by forrestcupp on 2011-12-26
> **BC59 said:**
> Sad bad true. But I think he refers mainly to the file system and registry deterioration by the time. This is inevitable on Windows.
I've been using Win7 since the beta, and I've never noticed that at all. I honestly haven't noticed anything bad at all about Windows 7. They've come a long way over the years.

Of course that's not to say that Linux isn't awesome with all of its strong points.

---

### Post by Paqman on 2011-12-27
> **doorknob60 said:**
> whenever Windows gets screwed up (often)

Somebody clearly hasn't used Windows in the last decade or so. It's no more flaky than Linux these days. More annoying to use yes, but not actually any more unreliable

---

