---
title: "Would hardware suitable for Linux today, stay suitable for Linux in a few years?"
date: 2007-11-16
forum: The Cafe
---

### Post by Extreme Coder on 2007-11-16
Hi,
 
I want to know what do you think about this.
 
We all know, that some time after MS releases a new version of Windows, most regular computer users go buy a new PC that would be fit for MS's increasing black hole of performance.
And even though the performance requirements increase, productivity doesn't.
 
But thankfully, some of us got out of this circle :)
 
 
I want to know, after about sometime (4-6 yrs for exmaple), will the hardware that runs Linux OK today unable to run Linux of the future?
 
For example, my second PC is a P4 1.7 GHz with 256 MB of RAM (planning to increase that to 512), and it runs Ubuntu, and most distros well (although I can't say the same about WinXP).
Do you think it will not be able to run Linux after some time?
 
I certainly hope not. One of the reasons I left Windows for Linux is because I didn't need to keep upgrading my PC :P

---

### Post by ajgreeny on 2007-11-16
It's usually the desktop environment that takes most computer power to run effectively, so if you chose the right desktop you will be OK with linux for the foreseeable future.  XFCE, used in Xubuntu, is a low power requirement desktop so worth looking at in future, perhaps, but for the moment you are OK, especially if you up your memory to 512.

---

### Post by anaconda on 2007-11-16
I thnk that the ram and cpu requirements will be increasing.. but as ajgreeny said you can always select a lighter version of vindow managers..

However.. I understood the question first that will harware eg. a webcam that works now with linux still work in the future? And the reply to that would be YES.. Atleast I hope so..

---

### Post by toupeiro on 2007-11-16
I believe that the answer to this question is: Yes, most definately!

Could you install vista on a P133?  Would you even try?

Present day Linux scales much lower, and much higher than present day windows x32 or x64.  Linux runs on almost all of the top 50 largest and fastest supercomputers in the world.  I support a small 18 node, dual chip dual core infiniband cluster running linux.  Windows CCS has way more overhead still.  On the low end, just consider for a moment the live CD.  This is not something you will ever see available for windows unless a LOT happens to streamline the operating system.  Also, Linux extends into PowerPC and SPARC processors; a place windows does not natively tread.  I'm putting ubuntu 7.10 on a sun Ultra 80 workstation at work, getting much more life out of a much older, once high end machine.

Linux can extend your hardware investment much further than windows can, whichever direction you choose to go with hardware.

---

### Post by Yoooder on 2007-11-16
> **Extreme Coder said:**
> Hi,
 
I want to know what do you think about this.
 
We all know, that some time after MS releases a new version of Windows, most regular computer users go buy a new PC that would be fit for MS's increasing black hole of performance.
And even though the performance requirements increase, productivity doesn't.
 
But thankfully, some of us got out of this circle :)
 
 
I want to know, after about sometime (4-6 yrs for exmaple), will the hardware that runs Linux OK today unable to run Linux of the future?
 
For example, my second PC is a P4 1.7 GHz with 256 MB of RAM (planning to increase that to 512), and it runs Ubuntu, and most distros well (although I can't say the same about WinXP).
Do you think it will not be able to run Linux after some time?
 
I certainly hope not. One of the reasons I left Windows for Linux is because I didn't need to keep upgrading my PC :P

My PC may make a good case study for your question.  It was built in fall of 2003 for about $1300, and it's original components are:
 - AthlonXP 2500+
 - 1GB PC3200 RAM
 - 1x 80GB HDD
 - 1x 250GB HDD
 - 1x CDRW/DVD
 - 1x GeForce4 Ti4200

After a couple years I added twin 400GB SATA drives, upgraded to a GeForce 6600, and added a DVD burner--all for a very reasonable price.

Today, after 4 years of running nearly continuously I use the machine for:
 - MythTV
 - An FTP Server
 - An SSH Server
 - A Samba Server
 - An everyday desktop
   * running Gutsy, Compiz, AWN, and lots of other eye-candy.

THe machine runs great, I can use the latest Linux toys (compiz/awn/etc) without a hiccup in performance.  Despite the fact that it is 4 years old it still provides a very adequate desktop, and acts as a server behind the scenes.

So, yes.  With a decent machine you should be safe to run linux on it for some time.

---

### Post by GeneralZod on 2007-11-16
You'll really need to be much more specific (do you mean Linux + GUI? If so, which one? Linux+GUI+apps? If so, which ones? How much swapping is allowed before something is classed as "not running well"? How much lack of responsiveness?), but in general, I would say yes: worst case, distros like Puppy Linux will likely still be around and maintained, and will likely continue to run very well on systems such as yours :)

---

### Post by DoctorMO on 2007-11-16
The problem is not so much linux but that peoples expectations shift; add to that that most developers are coding for fast computers and not slow ones. We could do with more development for speed but if it's required then someone will do it and we'll all benifit.

You just have to think about all the resources required to run udev and hal (not much) but try running them on a 386

---

### Post by Extreme Coder on 2007-11-16
> **Yoooder said:**
> My PC may make a good case study for your question. It was built in fall of 2003 for about $1300, and it's original components are:
- AthlonXP 2500+
- 1GB PC3200 RAM
- 1x 80GB HDD
- 1x 250GB HDD
- 1x CDRW/DVD
- 1x GeForce4 Ti4200
 
After a couple years I added twin 400GB SATA drives, upgraded to a GeForce 6600, and added a DVD burner--all for a very reasonable price.
 
Today, after 4 years of running nearly continuously I use the machine for:
- MythTV
- An FTP Server
- An SSH Server
- A Samba Server
- An everyday desktop
* running Gutsy, Compiz, AWN, and lots of other eye-candy.
 
THe machine runs great, I can use the latest Linux toys (compiz/awn/etc) without a hiccup in performance. Despite the fact that it is 4 years old it still provides a very adequate desktop, and acts as a server behind the scenes.
 
So, yes. With a decent machine you should be safe to run linux on it for some time.
 
> You'll really need to be much more specific (do you mean Linux + GUI? If so, which one? Linux+GUI+apps? If so, which ones? How much swapping is allowed before something is classed as "not running well"? How much lack of responsiveness?), but in general, I would say yes: worst case, distros like Puppy Linux will likely still be around and maintained, and will likely continue to run very well on systems such as yours :smile: 
While I'm sure your machine (or any similar-specd one) can run any Linux distro, or even Windows fine. I'm talking about, can such a machine run a Linux+GNOME/KDE well in about 5 yrs or so?
 
By running 'well', I mean it should be responsive(not asking for lightning speed) and most usual apps (browser,mail,office,simple games) should be responsive too.
 
Although I really doubt Firefox in 5 years will be usable on the caliber of machines I'm talking about :P

---

### Post by happysmileman on 2007-11-16
What i want to know about this is, would the drivers not eventually bloat and slow down Linux if they kept adding support without taking any away?

What is being done to stop/slow this? Or will it simply be a matter of older hardware required recompiling kernel or using older version?

---

### Post by GeneralZod on 2007-11-16
> **happysmileman said:**
> What i want to know about this is, would the drivers not eventually bloat and slow down Linux if they kept adding support without taking any away?

What is being done to stop/slow this? Or will it simply be a matter of older hardware required recompiling kernel or using older version?

Unused drivers are not loaded, so will take up no memory or CPU.

---

### Post by p_quarles on 2007-11-16
> **Extreme Coder said:**
> While I'm sure your machine (or any similar-specd one) can run any Linux distro, or even Windows fine. I'm talking about, can such a machine run a Linux+GNOME/KDE well in about 5 yrs or so?
 
By running 'well', I mean it should be responsive(not asking for lightning speed) and most usual apps (browser,mail,office,simple games) should be responsive too.
 
Although I really doubt Firefox in 5 years will be usable on the caliber of machines I'm talking about :P
Like DoctorMO said, this will depend partly on people's expectations. If the Gnome and KDE developers continue to code for more powerful machines then, yes, those desktops will eventually become too heavy for your current machine. 

But, like Toupeiro said, memory is going to be more important than processor speed. So it's likely that you'll be able to keep your rig current simply by adding some RAM from time to time. 

In any case, I doubt the next releases of Gnome or KDE are going to take up vastly greater amounts of system resources than the current versions. This means that you'll likely be able to upgrade to 8.04 without a problem, and that distribution will be supported until May 2011. So, you've got at least three and a half years before you might need to switch to a lighter desktop.

---

### Post by linuxlizard on 2007-11-16
This is a good topic, particularly since I'm starting to notice people recommend xfce for desktops with specs similar to yours. My mother has a desktop with nearly identacle specs and I've got kubuntu feisty with beryl and emerald and it zips along and runs everything just great. So, I've been wondering if gutsy has significantly heavier requirements than feisty.

I've got a pentium 166 with 128 mb that I did a full install of puppy just to see if it lived up to the hype for old computers and win 95 (the os it was built for) is also installed. Puppy is very slow, but works. Sea monkey (web browser that comes with puppy) takes a minute or so to load up though- but opera takes about 20-30 secs so is more tolerable. But I can't recommend it unless someone is desperate. win 95 however is super fast on this machine- boots in about 20 secs, shuts down in 3 or 4, everything snaps open instantly. When I compare it with puppy I really scratch my head wondering why puppy is so much slower, as the gui is similar, and the programs are similar... It's bloat, pure and simple. 

I've got a p3 700 laptop that zips with pcfluxboxos but is very slow running xubuntu. Distro makes a big difference- as your pc ages, you may have to move from an os with more features like ubuntu to one that is lighter, but more agile, like pcfluxboxos or zenwalk or puppy. 

Linux used to have much lighter system requirements than windows, but for the major distros, the gap is closing with windows xp. Still a way off from vista, thankfully, but the point is- linux is slowly becoming more bloated IMO, and the trend is likely to continue. The reason is, programmers tend to build on what came before, rather than building from the ground up. Especially with things that stick around for years like gnome, kde, the kernel, open office, gimp, etc. When you build on rather than from scratch, it just gets bigger and bigger... Add that to the fact that memory has become more and more inexpensive along with the rest of the computer, and the rapid development of hardware, it just means programmers today value efficiency of code (tightness, memory consumption, speed of execution) less and less.

Sad, but true.

Not like when I was a kid and you had to cram everything into 3.5 k (that's k, not megs) of ram on your vic 20:lolflag:

---

### Post by happysmileman on 2007-11-16
> **GeneralZod said:**
> Unused drivers are not loaded, so will take up no memory or CPU.

Ah ok, so they'd still be built and stored on the hard drive, but never used, and they'd be fairly small anyway compared to modern equivalents and thus the space on hard-drive is usually negligible?

I think I understand it, that's correct?

---

### Post by GeneralZod on 2007-11-16
> **Extreme Coder said:**
> While I'm sure your machine (or any similar-specd one) can run any Linux distro, or even Windows fine. I'm talking about, can such a machine run a Linux+GNOME/KDE well in about 5 yrs or so?
 
By running 'well', I mean it should be responsive(not asking for lightning speed) and most usual apps (browser,mail,office,simple games) should be responsive too.


I'll go for a hesitant "yes" on this one.  Years ago, there was a sudden explosion in resource requirements (I remember playing the original Unreal Tournament on 32MB RAM :guitar: )- 32MB went from "OK" to "lol"; 64MB went from "cool" to "ouch", and even 128MB went from "wow!" to "hmmm :/".  256MB, though still strikes me as fine for the tasks you listed above, with the possible exception of web browsing (but then, probably not everyone has 20+ tabs open at once, like me ;)), and I just don't see GNOME and KDE increasing that much - in fact, both have undergone a lot of optimisation and actually use *less* than they did a few years previously!  

Plus, they are modular - Composite uses too much RAM? Use an ordinary WM instead.  Widget style pretty heavy? Switch to a lighter one.  Desktop search eating up CPU cycles? Disable it.  

Predicting the future of technology is a mug's game, but I don't see any good reason why the GNOME and KDE of 5 years in the future shouldn't be runnable on 1.7GHz and 256MB RAM, and I'm much more confident about, say 512MB RAM which is more-or-less the standard for today's machines (I don't consider CPU speed that important, to be honest).

> **happysmileman said:**
> Ah ok, so they'd still be built and stored on the hard drive, but never used, and they'd be fairly small anyway compared to modern equivalents and thus the space on hard-drive is usually negligible?

I think I understand it, that's correct?

Bingo :)

---

### Post by mivo on 2007-11-16
I agree that as your PC ages, you have to become increasingly picky about the distro you run. But I don't think that applies to new machines bought in the past five years. You still have plenty of room after that point, though. There are lighter environments than KDE and Gnome, and office applications with smaller resource requirements than OpenOffice. That will probably always be that way.

Ubuntu is very full featured so that it works out of the box for most people. You could trim it down significantly and optimize it for your own hardware (there is a lot of stuff running by default even if you don't use it, i.e. Bluetooth support). Drivers don't hurt since the kernel only loads the modules that are needed by your hardware (and you can control this).

It also depends a bit on how hardware progresses. This is not a linear process. For example, the differences between computers in 2001 and those today are, for practical purposes, less significant than the differences were bewteen a 1985 and a 1991 computer.

---

### Post by jc87 on 2007-11-16
I have a P4 1,7, 512 ram and one ati radeon 9250, with two ata disks (one 80 other 20) and i´m not playing to upgrade/replace anytime soon:)

Except games it does eveything i want (thinking in buying a WII instead in a few months), it might not be the fastest machine in town, but everything else works great.

Sometimes is a question of choosing the wright apps/combinations:

- I use abiword/gnumeric instead of OOO because they load in a few seconds and i only need the basic resources they provide.

- I use Deluge instead of azureus because is lighter and feels more native than azureus (previously i used ktorrent, gnome-bt and azureus)

- I use Firefox with flashbock, so when i load web pages i only run flash stuff that i want ( youtube:)) the rest is unecessary load that only takes away system resources.

- I use gxine instead of totem-gstreamer because it feels faster (at least is my experience)

Also every Ubuntu release looks like more responsive and make better use of my system resources.

My only problem is crappy 3d performance with the OSS radeon driver, because it doesn´t let me play some cool OSS games with decente performance ( i have about 1200 fps with glxgears, but openarena scales between 15 fps and 40)

Also my mother offered to buy me one laptop for my birthday (since she already bought one for my sister), but i decided to wait a few more years and ask for it then (maybe when this pc burns out:KS)

Opps i seem to have forgoten this thread subject, Gnu/Linux is so modular that even if future releases start to include bloat i can just disable the unecessary eyecandy/services, so this machine will rock for many years to come

---

### Post by FuturePilot on 2007-11-16
I would think so. I have a laptop that's about 5 years old. Ubuntu runs great on it. Though no Compiz, but other than that everything works perfectly on the older hardware.

---

### Post by mips on 2007-11-16
Yes!

---

### Post by Yoooder on 2007-11-19
> **Extreme Coder said:**
> While I'm sure your machine (or any similar-specd one) can run any Linux distro, or even Windows fine. I'm talking about, can such a machine run a Linux+GNOME/KDE well in about 5 yrs or so?
 
By running 'well', I mean it should be responsive(not asking for lightning speed) and most usual apps (browser,mail,office,simple games) should be responsive too.
 
Although I really doubt Firefox in 5 years will be usable on the caliber of machines I'm talking about :P

My machine is 4 years old.  It ran Gentoo/GNOME fine then, and 4 years later with very minimal upgrades it still runs the bleeding edge GNOME/KDE desktops in a very responsive fashion.

So by the same logic if you build a respectable (not top or bottom end) machine today, there is a good chance that it will remain a responsive platform for years to come.  I have yet to encounter a point in time where Linux--or it's GUIs/applictions--underwent a sudden and dramatic increase in required resources.

---

### Post by gn2 on 2007-11-19
I have Xubuntu 7.04 installed on a seven (nearly eight) year old Toshiba Portege 3440CT which has a P3 500mhz CPU and 192mhz RAM and it runs just fine.

It's slower than a slow thing on W2kPro, forget about XP, and Vista absolutely no chance whatsoever.

The effective useful life of hardware can be greatly extended by running Linux.

---

### Post by SomeGuyDude on 2007-11-19
> **Extreme Coder said:**
> For example, my second PC is a P4 1.7 GHz with 256 MB of RAM (planning to increase that to 512), and it runs Ubuntu, and most distros well

A 1.7GHz P4 with 256MB RAM has to be, what, five years old at least? It runs the new distros well, according to you, which is just fantastic. Obviously, using "today" meaning "when you bought the computer", your PC is probably going to last as long as the hardware itself holds out. The fact that 5+ years after buying the thing you still can use the more "heavy" distros no problem is a good indicator of that.

After all, there are people running things like Fluxbuntu or DSL on PCs that are, what, 10-12 years old? More? If in late 2007 you can put a brand new release of many forms of Linux on a PC that's got 32MB of RAM, less than a gig of HD space, and a really slow proc, then a 5 year old computer's probably got another near decade in it, and a brand spankin' new machine is gonna be good for a while.

Hell I'd say the limiting factor isn't the OS, but the software. You may be able to handle Linux just fine, but software today is more resource intensive.

---

### Post by Extreme Coder on 2007-11-20
> **SomeGuyDude said:**
> A 1.7GHz P4 with 256MB RAM has to be, what, five years old at least? It runs the new distros well, according to you, which is just fantastic. Obviously, using "today" meaning "when you bought the computer", your PC is probably going to last as long as the hardware itself holds out. The fact that 5+ years after buying the thing you still can use the more "heavy" distros no problem is a good indicator of that.

After all, there are people running things like Fluxbuntu or DSL on PCs that are, what, 10-12 years old? More? If in late 2007 you can put a brand new release of many forms of Linux on a PC that's got 32MB of RAM, less than a gig of HD space, and a really slow proc, then a 5 year old computer's probably got another near decade in it, and a brand spankin' new machine is gonna be good for a while.

Hell I'd say the limiting factor isn't the OS, but the software. You may be able to handle Linux just fine, but software today is more resource intensive.
Well, at the used-computer-stuff shop I was going to buy the RDRAM from, I found 512+256 MB of RAM for 25$ (because practically nobody uses RDRAM here, so they wanted to get rid of it for any price) so basically I think I added a few years of life to my PC :P

---

### Post by boast on 2007-11-20
So linux on my new IBM quantum computer will be backwards compatible with those old "electric" computers?

---

### Post by dnns123 on 2007-11-20
I installed Fluxbuntu on a 400mhz 32mb Toshiba laptop. the once that are HEAVY for something that WAS considered light in it's day. It just goes to show that Linux is like Janus, the Roman God of January, it looks/supportst the past and future!

---

### Post by popch on 2007-11-20
> **dnns123 said:**
> Linux is like Janus, the Roman God of January, it looks/supportst the past and future!

Some of our friends here would wish that it supported the present as well....

/me ducks and runs

---

### Post by lachild on 2007-11-20
Just to add my $.02.

I just installed Linux on my old Pentium III and Pentium II machines. I am running Gnome on these systems and the system is working fine.  Open office takes awhile to load but it works fine after that.  Sure it runs a little slower then my newer system, but that's expected.

The lasted Ubuntu failed to install on either of these machines but Fedora 7 worked like a charm.  Bleeding edge distros like Ubuntu, Debian (testing/unstable), Fedora most likly will not support my machines, even as early as the next release, but some distro out there will.  I expect to be using these machines for varrious tasks for as long as the hardware holds up.

So long story short, I think that you're computer specs will work fine for the unforseeable future for most tasks, but it might start to get a little picky about the distrobution you decide on.  Either way, 5 years from now, I still expect these systems to work just fine for word processing and web surfing.  Gamming of course is a different animal all together.

---

