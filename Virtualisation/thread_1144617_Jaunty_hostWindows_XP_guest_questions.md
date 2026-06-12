---
title: "Jaunty host/Windows XP guest questions"
date: 2009-04-30
forum: Virtualisation
---

### Post by mattalexx on 2009-04-30
I used to dual boot Ubuntu and Windows XP. I would have liked to completely switch to Ubuntu but was held back because I wanted to run Photoshop and a couple of other Windows programs that didn't have viable Linux alternatives.

I decided at some point to just run Windows XP. I have found that it works fine and runs fast enough on my system.

Here's my environment: I have a workstation PC with two hardrives: one for the op system and the other to hold VMWare virtual PCs. I also have a Gutsy server in the other room that I connect to over my network. It holds all of my files (movies, photos, documents, etc.) and serves development sites to my clients from time to time.

Here's what I would like to do: I would like to run Jaunty as my main op system. Then I would install VMWare Workstation for Linux and install Windows XP as a guest. That way (I hope) I can run Photoshop CS4 (impossible with Wine) and a handful of other progs that don't have viable Linux equivalents.

I am doing this research so that I can get this installation done in less than a day. I'm a web developer and I'm really busy at the moment. I can't afford to spend a bunch of time working kinks out.

So here are my questions:
[LIST]
[*]Will I run into any problems with Photoshop/Illustrator/Flash CS4, performance or otherwise?
[*]Windows XP only accepts 4GB of RAM. Does Ubuntu have a limit? I want to run Windows XP at all times on top of Jaunty and I think pumping up my RAM would really help. Am I correct in thinking this?
[*]Sometimes I like to play games. Is this really possible using a Windows guest?
[/LIST]
Before I make this step, I would like to know if anyone with a similar situation has run into problems before. I know that I get a performance increase by running virtual PCs on a separate hard drive. Will this be enough?

EDIT: Is Crossover Office Standard going to be better for me than VMWare Workstation for running PS?
EDIT2: God, I can't believe I forgot to mention this: Has anyone had much success using iTunes in a VMWare guest? Does the USB work well for iPods? In fact, that might be deal breaker if I can't sync my iPod. I don't want to use anything but iTunes. iTunes is awesome when it comes to organizing the actual directory structure of your collection, talking to an iPod, shopping for podcasts in the iTunes store, etc.

---

### Post by HermanAB on 2009-05-01
Howdy,

1. Yes, you will have problems.
2. No, there is no memory limit in Ubuntu.  The problem is with the hardware, but there are ways around that.  Adding more RAM won't help.  WinXP doesn't use it and Ubuntu doesn't need it.
3. You probably won't be able to play games.
4. Crossover is probably the way to go with Photoshop.
5. You don't need iTunes to run an iPod.

---

### Post by mattalexx on 2009-05-01
> **HermanAB said:**
> 1. Yes, you will have problems.
Care to elaborate?
> **HermanAB said:**
> 2. No, there is no memory limit in Ubuntu.  The problem is with the hardware, but there are ways around that.  Adding more RAM won't help.  WinXP doesn't use it and Ubuntu doesn't need it.
What do you think the bottleneck would be? The processor?
> **HermanAB said:**
> 3. You probably won't be able to play games.
Sucks, but it's not a dealbreaker.
> **HermanAB said:**
> 4. Crossover is probably the way to go with Photoshop.
Faster? More reliable?
> **HermanAB said:**
> 5. You don't need iTunes to run an iPod.
I've used other things before to load it up, but I need to at least use iTunes to do software restores, right?

asd

---

### Post by mattalexx on 2009-05-03
**Me:** Will I run into any problems with Photoshop/Illustrator/Flash CS4, performance or otherwise?
**You:** Yes, you will have problems.
**Me:** What will be the drawbacks of using these programs in my WinXP guest? Will I have loss of function or will the problems all arise from performance?

**Me:** Windows XP only accepts 4GB of RAM. Does Ubuntu have a limit? I want to run Windows XP at all times on top of Jaunty and I think pumping up my RAM would really help. Am I correct in thinking this?
**You:** No, there is no memory limit in Ubuntu. The problem is with the hardware, but there are ways around that. Adding more RAM won't help. WinXP doesn't use it and Ubuntu doesn't need it.
**Me:** Here's my logic... *RAM*: The WinXP guest will use only what it needs from my physical memory. Ubuntu host will use what it needs. If I put 8 Gigs of RAM in the machine, both op systems will have what they need with a lot to spare. So RAM is not a concern I guess. *Hard disk operations*: Since I will have the WinXP guest running from an alternate hard drive, read/write operations will not be affected performance-wise. *Processor*: So that leaves the processor as the last thing I can think of that would act as a bottleneck. Am I correct in my logic?

**Me:** Sometimes I like to play games. Is this really possible using a Windows guest?
**You:** You probably won't be able to play games.
**Me:** Maybe I could do a dual boot into a relatively small WinXP installation. This would only be used for games.

**Me:** Is Crossover Office Standard going to be better for me than VMWare Workstation for running PS?
**You:** Crossover is probably the way to go with Photoshop.
**Me:** Thanks for the recommendation.

**Me:** Has anyone had much success using iTunes in a VMWare guest? Does the USB work well for iPods?
**You:** You don't need iTunes to run an iPod.
**Me:** True. Your answer didn't fit my question though. Is it at all possible to use iTunes installed in a WinXP guest to sync an iPod?

---

### Post by mattalexx on 2009-05-04
Bump

---

### Post by mattalexx on 2009-05-05
> **mattalexx said:**
> Bump

I don't understand. Are these stupid questions or something?

---

### Post by jaqrah on 2009-05-06
**#3 Will I be able to play games? Probably not.**

I can't provide the answer to why not because I don't know. But I think it has to with the fact that the XP guest isn't actually using your host's video card.  I have a #!Crunchbang(Ubuntu base) host with XP Pro guest.  Some games have run just fine and others hang and cause the guest to freeze.  I have run World of Goo without any issues.  I have run Risk with some slight performance issues.  I have tried running Sim City 3000.  Sometimes it works just fine and others time it hangs and freezes. (Mind you, this is on my Dell Mini 9 with the Atom processor)

I have been using a dualboot setup on my desktop box. But now that my hd has gone belly up, I am going to reconfigure with a XP host and Ubuntu guest.  I will still be able to play all the games I want, watch Netflix on demand, benefit from Media Center 2005,and use MS Office.  For everything else, Ubuntu (or Suse, Crunchbang, WattOs) in virtualization.  Seems the best of both worlds.  I would love to have Ubuntu host but Mythtv requires a Phd to configure (and get to work) and I love Netflix on demand too much to give up.  Until there is a better ap for tv viewing or better video card support for virtualization, Xp is what I have to have.

Jaq

---

### Post by albinootje on 2009-05-06
I recommend using VirtualBox over VMware.
USB support should be easy in the newest VirtualBox versions, make sure you use the PUEL version instead of the OSE version if you need USB support.

Wine might be better for 3D games. 
VirtualBox has 3D support since a little while, but I'm not sure how good that is for gaming.

And I've seen iTunes inside VirtualBox for a friend who needed his ipod to work in Linux, turned out the ipod was Mac formatted, so iTunes could reformat it for iTunes in MS-Windows.

---

### Post by albinootje on 2009-05-06
> **mattalexx said:**
> 
**Me:** Is Crossover Office Standard going to be better for me than VMWare Workstation for running PS?
**You:** Crossover is probably the way to go with Photoshop.
**Me:** Thanks for the recommendation.


CrossOverLinux is a cool project imho, but see here : [http://www.codeweavers.com/compatibility/browse/name/](http://www.codeweavers.com/compatibility/browse/name/)
Photoshop CS4 is not supported afaik.

---

### Post by mattalexx on 2009-05-18
Thank you for your responses, all.

I think I'll wait on this. I really want to run Linux natively but I use Photoshop too frequenty. I need it to be able to be responsive and quick and based on my research, including this post, I'm not convinced that it will be.

I remember reading that Adobe was planning a Linux port of Photoshop. Where did that ever go? Wasn't Google even donating cash to the cause or something? This was years ago. Oh well. 

I bet thousands and thousands of Windows and OS X users would switch for good if there was a Linux port of PS available to them. I know I would.

Thanks again.

---

### Post by AnjinSan on 2009-05-23
You can install adobe photoshop cs 2, instead of cs 4, since i didnt tryied cs 3 and the only versions i have was cs 4 and cs 2. Since cs4 has problems with install, i tryied cs 2 and it work.
I have issues now with adobe flash cs4, since no older versions of it is available there.

---

### Post by mattalexx on 2009-05-29
> **HermanAB said:**
> 1. Yes, you will have problems.

I'm in Jaunty right now, hosting Photoshop CS4 in WinXP on Virtualbox and I'm having no problems at all. It's working great.

---

