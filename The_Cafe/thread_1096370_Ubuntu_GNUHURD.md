---
title: "Ubuntu GNU/HURD"
date: 2009-03-14
forum: The Cafe
---

### Post by DPic on 2009-03-14
Although GNU/HURD needs a lot of work and isn't a high priority (not even for the Free Software Foundation), it does seem to be overall conceptually superior to Linux. Debian already has a GNU/HURD port. My question is whether this could be done for Ubuntu. Not to make a big deal about GNU/HURd or anything, but just to have the option and perhaps contribute a little bit to it's development.

**_*Update:*_** I filed a bug on launchpad [https://bugs.launchpad.net/ubuntu/+bug/343452](https://bugs.launchpad.net/ubuntu/+bug/343452)


**_*Update 2:*_** Someone created a blueprint on launchpad [https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-hurd](https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-hurd)

What else should i do?

---

### Post by Eisenwinter on 2009-03-14
> **DPic said:**
> My question is whether this could be done for Ubuntu.
Aren't we (users) supposed to ask **you** (Ubuntu member, developer) if this can be done? ;)

(I don't even use Ubuntu, btw, just raising this random logical thought)

---

### Post by DPic on 2009-03-14
> **Eisenwinter said:**
> Aren't we (users) supposed to ask **you** (Ubuntu member, developer) if this can be done? ;)

(I don't even use Ubuntu, btw, just raising this random logical thought)

Member, yes. Developer? no.

---

### Post by Eisenwinter on 2009-03-14
Oh, well, then I think that it can be done.

It's just switching a kernel.

I've heard of Debian with HURD, but never actually tried it. Is it even compatible with Linux?
As in, will all the programs have to be rewritten specifically for HURD? If yes, then it's not worth the effort.

---

### Post by hanzomon4 on 2009-03-14
This comes every so often. I'd like to i happen

---

### Post by jimi_hendrix on 2009-03-14
whats hurds theory and why is it better than linux?

---

### Post by Mehall on 2009-03-14
> **jimi_hendrix said:**
> whats hurds theory and why is it better than linux?

HURD currently uses the MACH kernel, which is a Microkernel, rather than Monolithic like Linux.

Even way back when, back when Linus first showed some people Linux, he got complaints from the creator of MINIX that it was a dead system, a shot back to the 70's. Of course, that man thought we would all be using UltraSPARCS by now, and that HURD would be ready by now :lol:

I DO think that having Ubuntu head towards HURD compatibility IS important, it's undeniable that, once HURD becomes more usable, it WILL become THE de facto standard, it is designed MUCH better than Linux is, even Linus has expressed, again, way-back-when, that HURD was a great thng, and he didn;t think Linux would ever out-last HURD.


I am actually considering making a Debian/HURD install some time soon tbh....

---

### Post by unoodles on 2009-03-14
Hurd will probably be ready the day Duke Nukem Forever comes out.

That said, it will be a great day. I would love to see a working Hurd.

---

### Post by mehaga on 2009-03-14
I'd love to try it (although I don't know why), but it will have to be able to run KDE or Gnome before I do.

---

### Post by Skripka on 2009-03-14
> **Mehall said:**
> HURD currently uses the MACH kernel, which is a Microkernel, rather than Monolithic like Linux.

Even way back when, back when Linus first showed some people Linux, he got complaints from the creator of MINIX that it was a dead system, a shot back to the 70's. Of course, that man thought we would all be using UltraSPARCS by now, and that HURD would be ready by now :lol:

I DO think that having Ubuntu head towards HURD compatibility IS important, it's undeniable that, once HURD becomes more usable, it WILL become THE de facto standard, it is designed MUCH better than Linux is, even Linus has expressed, again, way-back-when, that HURD was a great thng, and he didn;t think Linux would ever out-last HURD.


I am actually considering making a Debian/HURD install some time soon tbh....

Meh....HURD has been 20+ years in the making...and it still isn't ready.  People were cracking terribly funny jokes about it back then too.

The day HURD is the "defact standard" is the day that college fratboys don't get drunk out of their minds regularly.

---

### Post by Mehall on 2009-03-14
> **Skripka said:**
> Meh....HURD has been 20+ years in the making...and it still isn't ready.  People were cracking terribly funny jokes about it back then too.

The day HURD is the "defact standard" is the day that college fratboys don't get drunk out of their minds regularly.

Well Linux certainly isn't the definitive future my friend.

Even if it isn't the current HURD, it will be something built like HURD.

And yes, 20 years in the making, but given that for the last 15 years Linux has been stealing the devs, that might offer a clue.

---

### Post by fissionmailed on 2009-03-14
[QUOTE=Linus Torvalds(well said by)]In short: just say NO TO DRUGS, and maybe you won't end up like the Hurd people. [/QUOTE]

:popcorn:

---

### Post by Skripka on 2009-03-14
> **Mehall said:**
> Well Linux certainly isn't the definitive future my friend.

Even if it isn't the current HURD, it will be something built like HURD.

And yes, 20 years in the making, but given that for the last 15 years Linux has been stealing the devs, that might offer a clue.


Meh.  Even if you're right and Linux has been "stealing devs" for the last 15 years, 20 years ago people still thought HURD wasn't going anywhere.

One has a choice, one can either use Linux with bits of proprietary code that works-and have a machine that actually does lots of neat "stuff" and a swank fast GUI that supports very modern hardware....

or

A HURD machine that has a CLI, but at least it is truely free!!!

_Of course, I move to hyperbole in the above_, but it demonstrates a truth.  One can either deal with and get over certain proprietary bits of code...or simply use a comparitively primitive system that is Free as in Freedom, but at least it is "free".

With how fast new hardware and new standards come out-HURD just plain cannot keep up.  Heck, the open source video drivers are only just now starting to offer 3D acceleration-and often only on cards a generation or more old.  That is how far behind these efforts are.  That is why HURD will never be a "defacto standard".  It ends up being too little too late, in comparison to what proprietary code can offer at the same moment in time.

---

### Post by Skripka on 2009-03-14
> **fissionmailed said:**
> :popcorn:


I love that quote BTW. ;)

---

### Post by fissionmailed on 2009-03-14
> **Skripka said:**
> I love that quote BTW. ;)

It is amusing. :D

---

### Post by Dr. C on 2009-03-15
> **Skripka said:**
> Meh.  Even if you're right and Linux has been "stealing devs" for the last 15 years, 20 years ago people still thought HURD wasn't going anywhere.

One has a choice, one can either use Linux with bits of proprietary code that works-and have a machine that actually does lots of neat "stuff" and a swank fast GUI that supports very modern hardware....

or

A HURD machine that has a CLI, but at least it is truely free!!!

_Of course, I move to hyperbole in the above_, but it demonstrates a truth.  One can either deal with and get over certain proprietary bits of code...or simply use a comparitively primitive system that is Free as in Freedom, but at least it is "free".

With how fast new hardware and new standards come out-HURD just plain cannot keep up.  Heck, the open source video drivers are only just now starting to offer 3D acceleration-and often only on cards a generation or more old.  That is how far behind these efforts are.  That is why HURD will never be a "defacto standard".  It ends up being too little too late, in comparison to what proprietary code can offer at the same moment in time.

Actually free as in speech is not a Hurd advantage anymore. When it comes to Kernels there are quite a few Free Software options starting of course with Linux, BSD, Solaris, (Unix like) FreeDOS, ReactOS (Windows like) etc. So creating yet another Free Software Kernel does little to promote Free Software when there are far more pressing priorities (3D video, flash, etc.). This is the real reason that the Hurd will take forever to come to fruition.

---

### Post by shadylookin on 2009-03-15
Ubuntu will run out of animals to name the distros after before FSF releases a stable version of HURD.

---

### Post by mrsteveman1 on 2009-03-15
The support behind Linux is enormous. Take a look at all the companies who make a living selling custom linux derivatives for specific purposes, they chose linux for a reason. It can be made to do just about anything, is incredibly stable and already in use by just about everyone.

---

### Post by DPic on 2009-03-15
All the points here are not new at all! We all know that HURD needs a lot of work. To counter that i could never go anywhere, i would say that even if Linux takes over (becomes more widely used than proprietary OS) that will be a point where the free software "ecosystem" will be thriving and it will be a lot less difficult to get the HURD developed. 

ANYWAYS

This is all irrelevant. I worded the proposal the way i did intentionally. This isn't to make a big deal out of HURD, or to say we should be giving it more attention, or even advertise it at all. This is just to make it an option and maybe help contribute a bit to it's development. Is there any huge reason not to?

---

### Post by smartboyathome on 2009-03-15
I think it is very likely, since we already have Nexenta, which is Ubuntu based on OpenSolaris. :)

---

### Post by DPic on 2009-03-15
> **smartboyathome said:**
> I think it is very likely, since we already have Nexenta, which is Ubuntu based on OpenSolaris. :)

I was thinking of a more official project like Gobuntu, but less of a major project (which ended up mostly failing anyways). How could we see an official port happen?

---

### Post by jimi_hendrix on 2009-03-15
> **unoodles said:**
> Hurd will probably be ready the day Duke Nukem Forever comes out.

That said, it will be a great day. I would love to see a working Hurd.

or when guns n roses releases a new albume

---

### Post by smartboyathome on 2009-03-15
> **DPic said:**
> I was thinking of a more official project like Gobuntu, but less of a major project (which ended up mostly failing anyways). How could we see an official port happen?

If it seemed that enough users wanted it, and Mark liked the idea, then Canonical would accept it as another project. As it is, though, there are already too many "official" ubuntu derivatives, imo. I can think of 8 off hand (Ubuntu, Kubuntu, Xubuntu, Gobuntu, Edubuntu, Lubuntu, Ubuntu Netbook Remix, Ubuntu for ARM).

---

### Post by DPic on 2009-03-15
> **smartboyathome said:**
> If it seemed that enough users wanted it, and Mark liked the idea, then Canonical would accept it as another project. As it is, though, there are already too many "official" ubuntu derivatives, imo. I can think of 8 off hand (Ubuntu, Kubuntu, Xubuntu, Gobuntu, Edubuntu, Lubuntu, Ubuntu Netbook Remix, Ubuntu for ARM).

Why do you say that there are too many? I think this is a good thing and isn't too much of an investment for Canonical. Besides, if Canonical, along with other organizations, can make HURD really successful, the long term payback will be huge!

---

### Post by MikeTheC on 2009-03-15
Why do you folks all think Hurd is so damned important?

Assuming that the Linux kernel is a lesser kernel than GNU, it bears remembering with this "lesser" kernel we have a full-up OS, a GUI platform, multiple desktop environments, imbedded devices, lots of games, support for running a Win32 environment, full-on networking capabilities, server market domination... the list goes on and on.

How would making a switch actually improve on any of this?

---

### Post by DPic on 2009-03-15
> **MikeTheC said:**
> Why do you folks all think Hurd is so damned important?

Assuming that the Linux kernel is a lesser kernel than GNU, it bears remembering with this "lesser" kernel we have a full-up OS, a GUI platform, multiple desktop environments, imbedded devices, lots of games, support for running a Win32 environment, full-on networking capabilities, server market domination... the list goes on and on.

How would making a switch actually improve on any of this?

::headdesk::

We are not making a switch! We are simply calling to make this port available. Similarly, (and this might not be a great analogy), Empathy is a great IM client that is conceptually superior to Pidgin because it uses the Telepathy Framework. It is available in the Ubuntu repos but it is not the default client (although it is in Gnome). Having Empathy availble does not take away from pidgin at all. Eventually, it will surpass Pidgin in functionality and usability and then it may become default. Similarly, HURD may take time (a very long time) to surpass Linux, but it should be available

---

### Post by Simian Man on 2009-03-15
Hurd is an epic failure.  Give it up folks.

---

### Post by MikeTheC on 2009-03-15
> **DPic said:**
> ::headdesk::

We are not making a switch! We are simply calling to make this port available. Similarly, (and this might not be a great analogy), Empathy is a great IM client that is conceptually superior to Pidgin because it uses the Telepathy Framework. It is available in the Ubuntu repos but it is not the default client (although it is in Gnome). Having Empathy availble does not take away from pidgin at all. Eventually, it will surpass Pidgin in functionality and usability and then it may become default. Similarly, HURD may take time (a very long time) to surpass Linux, but it should be available

That's nice, but you didn't really answer my question. Why should we care about Hurd? What will it bring us that we don't already have?

---

### Post by DPic on 2009-03-15
> **MikeTheC said:**
> That's nice, but you didn't really answer my question. Why should we care about Hurd? What will it bring us that we don't already have?

That's not what this discussion is about. If you don't understand the potential value in HURD, you can google it.

---

### Post by MikeTheC on 2009-03-15
> **DPic said:**
> That's not what this discussion is about. If you don't understand the potential value in HURD, you can google it.

Well, if that's not what this discussion is about, then what "is" this discussion about?

---

### Post by DPic on 2009-03-15
> **MikeTheC said:**
> Well, if that's not what this discussion is about, then what "is" this discussion about?

Check the first post. I tried to word it in such a way to avoid the usual flamewars that take place over HURD.

---

### Post by SunnyRabbiera on 2009-03-15
Yeh HURD seems to be stuck in development hell.

---

### Post by BGFG on 2009-03-15
I only read about Hurd after seeing this thread and if the kernel can really optimise use of the multicore and multithreading capabilities of modern processors, I would love to see it a stable reality and i would definitelty use it.

I think some of the posters are also confused. Not to start a silly arguement, but to my understanding, what we use is really GNU Linux, a GNU user environment placed on top the Linux Kernel. So the fully functional desktop, GUI and all that good stuff is GNU, the kernel is Linux. GNU was made to work with the linux kernel because the Hurd kernel is behind, I hope it catches up.

---

### Post by DPic on 2009-03-15
I filed a launchpad bug [https://bugs.launchpad.net/bugs/343452](https://bugs.launchpad.net/bugs/343452)

---

### Post by DPic on 2009-03-15
> **DPic said:**
> Although GNU/HURD needs a lot of work and isn't a high priority (not even for the Free Software Foundation), it does seem to be overall conceptually superior to Linux. Debian already has a GNU/HURD port. My question is whether this could be done for Ubuntu. Not to make a big deal about GNU/HURd or anything, but just to have the option and perhaps contribute a little bit to it's development.

**_*Update:*_** I filed a launchpad bug [https://bugs.launchpad.net/bugs/343452](https://bugs.launchpad.net/bugs/343452)

What else should i do?

Update again....i meant to update my first post, not quote it...and now i can't delete this one x.x

---

### Post by ROWDY!!! on 2009-03-16
I think having an Ubuntu GNU/Hurd port as an option would be great!!
I run Debian GNU/Hurd in Qemu with the intention of learning more about it and eventually contributing to it's development.

---

### Post by swoll1980 on 2009-03-16
> **DPic said:**
> 
 This is just to make it an option and maybe help contribute a bit to it's development. Is there any huge reason not to?

The old adages "No sense banging your head of a wall", and "Don't beat a dead horse" come to mind.

---

### Post by frup on 2009-03-16
From what I understood of HURDS servers and the way a micro-kernel works having something like wine as a server of a micro-kernel would be interesting if that's even possible (I'm a layman). Eventually BeOS or other OS "servers" could be made to run and something more interesting and dynamic would probably come to life. With all the differences in Linux distributions "HURD" distributions would potentially be more varied.

The reality is that HURD is no where near ready. From what I have looked in to (over 4 years or so) about 3 people even care about it enough to contribute, the Mach kernel isn't even certain and it's still very much only existing as theory.

I booted a HURD liveCD in virtualbox or vmware once. With no X it wasn't too interesting but I'm sure people could find a use for it if they wanted to. If it had an X server and the installation didn't require bootstrapping like I believe it does I would probably dual boot it for fun, My laptops hardware is all intel with completely free drivers... so hopefully it might install one day.

I dislike the idea of splitting free software resources though... for development to be good we need to be as united as possible.

---

### Post by cb951303 on 2009-03-16
It's true that HURD, in theory, has a better design. But it's also very hard to implement.

[quote=Linus Torvalds]
Linux is evolution, not intelligent design.
[/quote]

---

### Post by DPic on 2009-05-02
Someone created a blueprint on launchpad [https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-hurd]("https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-hurd")

---

### Post by DPic on 2009-12-08
Just started a discussion on [ubuntu-devel-discuss]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss")

[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-December/010178.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-December/010178.html)

---

### Post by Exodist on 2009-12-08
> **Mehall said:**
> HURD currently uses the MACH kernel, which is a Microkernel, rather than Monolithic like Linux.

Even way back when, back when Linus first showed some people Linux, he got complaints from the creator of MINIX that it was a dead system, a shot back to the 70's. Of course, that man thought we would all be using UltraSPARCS by now, and that HURD would be ready by now :lol:

I DO think that having Ubuntu head towards HURD compatibility IS important, it's undeniable that, once HURD becomes more usable, it WILL become THE de facto standard, it is designed MUCH better than Linux is, even Linus has expressed, again, way-back-when, that HURD was a great thng, and he didn;t think Linux would ever out-last HURD.


I am actually considering making a Debian/HURD install some time soon tbh....

Can you make some pros and cons showing why it is better then just saying it is? I believe a detailed comparison is in order to make your argument solid or not.

---

### Post by DPic on 2009-12-08
> **Exodist said:**
> Can you make some pros and cons showing why it is better then just saying it is? I believe a detailed comparison is in order to make your argument solid or not.

Basically, the Linux Kernel has had a huge head start, so it's much better by any conventional standards. GNU Hurd however, uses a microkernel, which makes a lot more sense than a monolithic kernel. For a comparison of what that is, i'd check wikipedia. So, GNU Hurd has less driver support, etc, and isn't for the mainstream yet, but makes more sense in the long long term as far as how operating systems should work.

---

### Post by mickie.kext on 2009-12-08
HURD is nice concept, but Mach sucks and also makes HURD to suck. It has 2Gb file-size limit and does not allocate more than 512Mb of RAM. It also has very bad reliability problems... it is not exact same Mach from Darwin but a lot more primitive version.  Work is under way to port HURD servers on L4 (to replace Mach) but that is stalled again and it uncertain if it will continue. CoyotOS was research project for next-gen free software micro-kernel and it might have been second choice if L4 fails... but Coyotos got killed by Microsoft who bougt out CoyotOS [main developer]("http://www.osnews.com/story/21262/Jonathan_Shapiro_of_Coyotos_BitC_Joins_Microsoft"), and now will probably file patents to make CoyotOS code effectively unusable outside Microsoft:(.

---

### Post by matthew.ball on 2009-12-08
Definitely sounds interesting. I've been tempted to try the Debian HURD for a while now.

I would love to get into operating systems development.

---

### Post by gnomeuser on 2009-12-08
It might be an interesting academic exercise but it's hardly something it makes sense to fund and to support when you have a viable alternative that isn't going to be lifted and supported solely by you.

I say go for it if you are interested, it would be a cool project but expecting Canonical to fund it isn't realistic nor I suspect a good idea (diverting funds and support/development efforts).

---

### Post by Xbehave on 2009-12-08
> **DPic said:**
> Basically, the Linux Kernel has had a huge head start
Actually Hurd had a small head start on Linux it just never got anywhere. The main argument in favor of HURD is the microkernel:
**[COLOR="Red"] - [/COLOR]**To my knowledge nobody has made a decent microkernel because the performance hit is too much
**[COLOR="Red"] - [/COLOR]**Many arguments for microkernels are covered by modular kernels, all the code runs in the kernel but is in (un)loadable modules
**[COLOR="Lime"] + [/COLOR]**A buggy module can still make the core system vulnerable/crash (however a lot of steps are done to prevent this and the modules don't get into mainline if they are unstable)
**[COLOR="Red"] - [/COLOR]**The FSF are much stricter about copyright, you have to assign them copyright of the code you contribute which means they can relicense it, Linus just uses your GPL code.

As nice as the design of hurd is, using it will means a performance hit larger than most people are willing to take, people still whine about Xorg's design because performance isn't amazing even though it's design is pretty good.

---

### Post by Xbehave on 2009-12-08
OTOH [this]("http://www.gnu.org/software/hurd/news/2009-11-30.html") suggest the performance hit isn't too bad and Hurd isn't completely dead

---

### Post by rrnwexec on 2009-12-08
This is a cool idea and would solve "the branding issue."

There is a Blueprint here:
[https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-hurd/](https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-hurd/)

Perhaps we can add to it and get it moving!?

Cheers,
Randall
Ubuntu Vancouver Buzz Generator

---

### Post by LowSky on 2009-12-08
Hurd is a joke brought up from time to time for the past 25 years.  Time to let a dream die. Work on something new and more promising.

Hybrid kernels are leading technology right now. Windows 7 and OS/X both implement the technology in different ways.

---

### Post by benmoran on 2009-12-08
According to the news page, Hurd can can now install Grub. That was something that was lacking in the Hurd/Debian distribution. I'm looking forward to dual booting this in the future. 


And cmon guys, nobody is saying this is going to replace Linux any time soon, if ever. It does however have value in a technological sense, which I believe is the main purpose of this thread.

---

### Post by phrostbyte on 2009-12-08
I've used Hurd. AFAIK there is no X11 and barely any networking support. From the user's perspective, it's resembles a slow booting DOS with a better shell. If you want a similar experience just find one of those floppy disk Linuxes on the net somewhere. :) And you will probably even have superior network support with one of those.

If you are still curious (and that's not a bad thing), you can try a LiveCD of Hurd over here:
[http://www.superunprivileged.org/hurd/live-cd/](http://www.superunprivileged.org/hurd/live-cd/)

---

### Post by forrestcupp on 2009-12-08
Even Richard Stallman has said that he's not concerned with HURD anymore because Linux filled the need.  The only reason there is even any development on it at all is because there are a few hobbyists out there who hate to see it die.

> **LowSky said:**
> Hybrid kernels are leading technology right now. Windows 7 and OS/X both implement the technology in different ways.
That's what I was going to say.  The future is not with microkernels, but with hybrid kernels.  That's how we can get the best of both worlds.  There are good and bad points to both monolithic kernels *and* microkernels.

---

### Post by rabidbadger on 2009-12-08
> **Xbehave said:**
> To my knowledge nobody has made a decent microkernel because the performance hit is too much

Slight [reality check]("http://www.qnx.com/products/neutrino_rtos/") :rolleyes:

---

### Post by handy on 2009-12-08
I too think that HURD should be left to the hobbyists that enjoy it. It's hard to imagine Canonical spending any resources on HURD.  I would imagine that would only happen if the Debian people dramatically pushed the HURD development along to a point where Canonical could see that it had become worthwhile investing in.

Personally, I find Haiku to be the most exciting "newish" system on the horizon; I'd be surprised if we see the Haiku kernel & the GNU system being grafted by Canonical in the next 10 years.

---

### Post by alphaniner on 2009-12-08
> **handy said:**
> I'd be surprised if we see the Haiku kernel & the GNU system being grafted by Canonical in the next 10 years.

Uhg.  I certainly don't want to see Haiku get GNU'd.

---

### Post by Simon17 on 2009-12-08
I GUARANTEE that within the next one and a half to two years, the HURD will be done, it will completely replace Linux, and Linus will be sorry he didn't make the kernel GPL3.

---

### Post by handy on 2009-12-08
> **Simon17 said:**
> I GUARANTEE that within the next one and a half to two years, the HURD will be done, it will completely replace Linux, and Linus will be sorry he didn't make the kernel GPL3.

Talk is cheap!

---

### Post by Simon17 on 2009-12-08
> **handy said:**
> Talk is cheap!

You're wrong; talk is Free. You might be laughing now, but when FLOSS takes over the world, we will all bow to RMS.

---

### Post by handy on 2009-12-08
> **Simon17 said:**
> You're wrong; talk is Free. You might be laughing now, but when FLOSS takes over the world, we will all bow to RMS.

Oh! Now I get it.  

You're a troll.

Bummer. :(

I'm out'a here.

---

### Post by NoaHall on 2009-12-08
> **Simon17 said:**
> You're wrong; talk is Free. You might be laughing now, but when FLOSS takes over the world, we will all bow to RMS.

Children will sing his songs; adults will wish for his blessing in the ways of GNU; he shall be locked in his cupboard, scared and paranoid - as usual.

---

### Post by RiceMonster on 2009-12-08
> **Simon17 said:**
> You're wrong; talk is Free. You might be laughing now, but when FLOSS takes over the world, we will all bow to RMS.

I hear Microsoft is going to patent talking.

---

### Post by alphaniner on 2009-12-08
> Children will sing his songs;

Richard Matthew Stallman,  mmmm mmmm mmmm.

---

### Post by NoaHall on 2009-12-08
> **alphaniner said:**
> Richard Matthew Stallman,  mmmm mmmm mmmm.

Come now and share the software, you'll be free, children, you'll be free.

---

### Post by forrestcupp on 2009-12-08
> **handy said:**
> Oh! Now I get it.  

You're a troll.

Bummer. :(

I'm out'a here.

I think he was just being sarcastic.  I hope. ;)

---

### Post by Simian Man on 2009-12-08
> **Simon17 said:**
> I GUARANTEE that within the next one and a half to two years, the HURD will be done, it will completely replace Linux, and Linus will be sorry he didn't make the kernel GPL3.

> **Simon17 said:**
> You're wrong; talk is Free. You might be laughing now, but when FLOSS takes over the world, we will all bow to RMS.

What's that internet rule that basically states: "Without a smiley, there is no way to distinguish between a person who is mocking an extremist viewpoint and someone who genuinely espouses that viewpoint"?

Because I honestly can't tell.

---

### Post by forrestcupp on 2009-12-08
> **Simian Man said:**
> What's that internet rule that basically states: "Without a smiley, there is no way to distinguish between a person who is mocking an extremist viewpoint and someone who genuinely espouses that viewpoint"?

Because I honestly can't tell.

You should have put a ;) in there.  ;)

---

### Post by Exodist on 2009-12-08
> **DPic said:**
> Basically, the Linux Kernel has had a huge head start, so it's much better by any conventional standards. GNU Hurd however, uses a microkernel, which makes a lot more sense than a monolithic kernel. For a comparison of what that is, i'd check wikipedia. So, GNU Hurd has less driver support, etc, and isn't for the mainstream yet, but makes more sense in the long long term as far as how operating systems should work.
Not to sounds like an butt. I was inquiring for a in depth technical overview. If I wanted to learn about Hurd I would look it up myself, but since your so animate as to wanting to make a move in that direction. It seems important to me that you should know every detail before rallying everyone to your cause. Thus something of the line of at least a 100 line breakdown on the technical aspects of hurd in comparison of why they are better then linux is required. If not then your just another person who prefers the color Red to the color Blue.

---

### Post by gnomeuser on 2009-12-08
> **Simon17 said:**
> I GUARANTEE that within the next one and a half to two years, the HURD will be done, it will completely replace Linux, and Linus will be sorry he didn't make the kernel GPL3.

I will bet you 100$ (I'll take my winnings in the form of a donation to the EFF).

You have no concept of how far behind HURD is not just in presenting a real world tested OS that will work on modern hardware but to present a working desktop. It's designs have not been tested and tuned.

It's just not in line with a 2½ year prediction for finishing all the work they need to be able to replace Linux, let alone completely.

---

### Post by infestor on 2009-12-08
HURD is like Duke Nukem Forever of kernels :p

---

### Post by Xbehave on 2009-12-08
> **Exodist said:**
> Not to sounds like an butt. I was inquiring for a in depth technical overview. If I wanted to learn about Hurd I would look it up myself, but since your so animate as to wanting to make a move in that direction. It seems important to me that you should know every detail before rallying everyone to your cause. Thus something of the line of at least a 100 line breakdown on the technical aspects of hurd in comparison of why they are better then linux is required. If not then your just another person who prefers the color Red to the color Blue.
I can do it in 22
> Hurd has a microkernel. Linux has a monolithic kernel. Microkernels are better than monolithic kernels because less code can crash the OS.
Personally i think Linux is better but you don't need to grok something to have an opinion on it, however if your not sure about something never pretend it's fact because there is a thin line between being mis informed and spreading FUD (looks at Skripka)

---

### Post by forrestcupp on 2009-12-09
> **Xbehave said:**
> I can do it in 22

That quote is a pretty shallow argument.  I could write a sentence that lists more things about monolithic kernels that are better than microkernels.  It's pretty subjective because there are good points to both kernel types, so it's basically up to the user to decide which of those pluses are more important.

Like another poster and I said earlier, the future is not in monolithic vs. micro.  The future is in hybrid kernels that use the good points of both types.  This way, it's possible to get the speed of a monolithic kernel while still having the safety of having drivers in user space like a microkernel.  Of course, that's just one example.

---

### Post by Xbehave on 2009-12-09
> **forrestcupp said:**
> That quote is a pretty shallow argument.  I could write a sentence that lists more things about monolithic kernels that are better than microkernels.  It's pretty subjective because there are good points to both kernel types, so it's basically up to the user to decide which of those pluses are more important.
Those 22 words are a good enough reason to be a fan of hurd, my point was you don't need a CS degree to understand why HURD is a good thing. There are only 2 reason to prefer monolithic, performance (which is apparently null, if you read some of the previous posts QNX and L4's networking stack) and ease of development (you can't really argue with there are many full featured monolithic kernels and not so many microkerenels). As for "hybrid kernels", either the driver code is running in userspace or it's not, monolithic kernels can (and have) adopt features of microkernels but that doesn't make them hybrids it mearly makes them better monolithic kernels

---

### Post by dmn_clown on 2009-12-09
According to Debian's Popcon there are currently 5 people with Hurd installed:  [http://popcon.debian.org/](http://popcon.debian.org/)

If you think hurd is important than more power to you, feel free to work on another port of it.  Good luck at making it into something more than a statistical anomaly.  :)

---

### Post by liamnixon on 2009-12-09
Hurd... :lol:

---

### Post by ZankerH on 2009-12-09
> **unoodles said:**
> Hurd will probably be ready the day Duke Nukem Forever comes out.

That said, it will be a great day. I would love to see a working Hurd.

Sorry, that analogy is no longer valid. Duke Nukem Forever has (even officially) been cancelled, and anyway, odds are any "work" done on it amounts to a bag of hot air. GNU/HURD, on the other hand, has a public, semi-working prototype released, and Debian even made a port of their software distribution for it.

HURD may not be anywhere near being ready for general use, but comparing it to a product that never even existed in the first place is just wrong.

And, while I'd love to see a Ubuntu GNU/HURD, I think a more sensible solution for now would be to improve the usability of Ubuntu GNU/Linux, and focus on removing non-Free software from it first.

---

### Post by matthewbpt on 2009-12-09
This is quite interesting [http://www.superunprivileged.org/hurd/live-cd/different.html](http://www.superunprivileged.org/hurd/live-cd/different.html)

---

### Post by forrestcupp on 2009-12-09
> **Xbehave said:**
> my point was you don't need a CS degree to understand why HURD is a good thing.

Wrong.  HURD *could* be a good thing, but it *is* currently rubbish.  And it always will be rubbish because they don't even have Stallman's support.

---

### Post by RiceMonster on 2009-12-09
> **forrestcupp said:**
> Wrong.  HURD *could* be a good thing, but it *is* currently rubbish.  And it always will be rubbish because they don't even have Stallman's support.

Exactly. Good and theory and good in practice are two different things.

---

### Post by Simon17 on 2009-12-09
> **Simian Man said:**
> What's that internet rule that basically states: "Without a smiley, there is no way to distinguish between a person who is mocking an extremist viewpoint and someone who genuinely espouses that viewpoint"?

Because I honestly can't tell.

What makes you think that my viewpoints are so extreme that they would be the subject of satire or parody?

Free Software WILL take over the world. Look around you; it is already happening. And I like to think that the man who created the Software Freedoms and dedicated his life to making it happen will get the credit he deserves.

Perhaps the HURD will take longer than two years, and perhaps it is behind Linux in some areas, but it already has one HUGE advantage over Linux and it won't be long before it replaces Linux as the GNU kernel.

GNU-slash-Linux will cease to exist and there will only be GNU. It will happen because people value their Freedoms. Richard Stallman created the GPL3 for us and Linus is deliberately denying people their Freedoms. He is a tyrant and a despot and he  will fall.

I'm not smiling.

---

### Post by Jimleko211 on 2009-12-09
> **Simon17 said:**
> What makes you think that my viewpoints are so extreme that they would be the subject of satire or parody?

Free Software WILL take over the world. Look around you; it is already happening. And I like to think that the man who created the Software Freedoms and dedicated his life to making it happen will get the credit he deserves.

Perhaps the HURD will take longer than two years, and perhaps it is behind Linux in some areas, but it already has one HUGE advantage over Linux and it won't be long before it replaces Linux as the GNU kernel.

GNU-slash-Linux will cease to exist and there will only be GNU. It will happen because people value their Freedoms. Richard Stallman created the GPL3 for us and Linus is deliberately denying people their Freedoms. He is a tyrant and a despot and he  will fall.

I'm not smiling.
What are you smoking?  Man I gotta get some of that.  A tyrant and a despot?  He gives his kernel away for free, makes it open source (it's even GPL, though to me that doesn't mean a thing, I think to you it would mean something), and states that it's not perfect and that if something else is better, use it.  That, my friend, is the complete opposite of a tyrant.

---

### Post by ZankerH on 2009-12-09
> **Jimleko211 said:**
> A tyrant and a despot?  He gives his kernel away for free, makes it open source (it's even GPL, though to me that doesn't mean a thing, I think to you it would mean something)

I believe the poster you were quoting was referring to the fact that Linus refuses to upgrade the Linux kernel to GPLv3, the FSF's new definition of Software Freedom. As such, he can only be considered a tyrant. I wouldn't be surprised at all if Linux becomes proprietary and fades into obscurity once HURD is completed and GNU is its own operating system again.

---

### Post by RiceMonster on 2009-12-09
> **ZankerH said:**
> I believe the poster you were quoting was referring to the fact that Linus refuses to upgrade the Linux kernel to GPLv3, the FSF's new definition of Software Freedom. As such, he can only be considered a tyrant. I wouldn't be surprised at all if Linux becomes proprietary and fades into obscurity once HURD is completed and GNU is its own operating system again.

There's no way you're serious.

---

### Post by NoaHall on 2009-12-09
> **ZankerH said:**
> I believe the poster you were quoting was referring to the fact that Linus refuses to upgrade the Linux kernel to GPLv3, the FSF's new definition of Software Freedom. As such, he can only be considered a tyrant. I wouldn't be surprised at all if Linux becomes proprietary and fades into obscurity once HURD is completed and GNU is its own operating system again.

Shush, you can't be crazily for GNU/Linux and then against it at the same time.

---

### Post by ZankerH on 2009-12-09
> **NoaHall said:**
> Shush, you can't be crazily for GNU/Linux and then against it at the same time.

Just because it's the Free-est OS in existence doesn't mean I wouldn't go for a more Free one if it existed and was usable.

---

### Post by ZankerH on 2009-12-09
> **RiceMonster said:**
> There's no way you're serious.

I find being branded an "extremist" by the likes of you to be satisfactory, because it reminds me I'm not as apathetic about Software Freedom as you people are.

---

### Post by NoaHall on 2009-12-09
> **ZankerH said:**
> Just because it's the Free-est OS in existence doesn't mean I wouldn't go for a more Free one if it existed and was usable.

Why not use HURD now then? ;) It exists.

---

### Post by ZankerH on 2009-12-09
> **NoaHall said:**
> Why not use HURD now then? ;) It exists.

Note the "usable" part. You can't even run X on it and expect any reliability and stability, damnit.

And, mind you, I have tried. That alone is more than the majority of the people here could say.

---

### Post by liamnixon on 2009-12-09
I'm really enjoying this thread.  :D

Linus, a tyrant?  Gold.

---

### Post by NoaHall on 2009-12-09
> **ZankerH said:**
> Note the "usable" part. You can't even run X on it and expect any reliability and stability, damnit.

And, mind you, I have tried. That alone is more than the majority of the people here could say.

I've tried too. Not great, is it?(so far)

---

### Post by alphaniner on 2009-12-09
> **ZankerH said:**
> GPLv3, the FSF's new definition of Software Freedom.

Ah, yes, the redefinition of freedom.  That concept has a good track record.

---

### Post by ZankerH on 2009-12-09
> **alphaniner said:**
> Ah, yes, the redefinition of freedom.  That concept has a good track record.

It's just legal defence. As the tactics of those who oppose the very principles of Free Software improve, it's only logical that the definition be altered to prevent them from abusing old loopholes. It's just like security patches for software.

---

### Post by Simon17 on 2009-12-09
> **Jimleko211 said:**
> What are you smoking?  Man I gotta get some of that.  A tyrant and a despot?  He gives his kernel away for free, makes it open source (it's even GPL, though to me that doesn't mean a thing, I think to you it would mean something), and states that it's not perfect and that if something else is better, use it.  That, my friend, is the complete opposite of a tyrant.

Correction: The kernel is GPL **VERSION 2**. RMS has created new Freedoms which are not available to kernel users. DENYING FREEDOM! What do *you* call it then?

> **ZankerH said:**
> I believe the poster you were quoting was referring to the fact that Linus refuses to upgrade the Linux kernel to GPLv3, the FSF's new definition of Software Freedom. As such, he can only be considered a tyrant. I wouldn't be surprised at all if Linux becomes proprietary and fades into obscurity once HURD is completed and GNU is its own operating system again.

Precisely. Refreshing to see that there are still some people with a clue in this vast sea of ignorami.

---

### Post by alphaniner on 2009-12-09
> **Simon17 said:**
> ...RMS has created new Freedoms...

This is the kind of absurd zealotry I was referring to.

---

### Post by Diluted on 2009-12-09
> **Simon17 said:**
> Correction: The kernel is GPL **VERSION 2**. RMS has created new Freedoms which are not available to kernel users. DENYING FREEDOM! What do *you* call it then?
So RMS changed something which caused existing freedom to be denied.

Who's fault is it then? Linus, or RMS?

---

### Post by ZankerH on 2009-12-09
> **alphaniner said:**
> This is the kind of absurd zealotry I was referring to.

How the hell is it absurd? The new version of the GPL is an upgrade, and protects your Software Freedom better than the obsolete one. The only conclusion I can draw from this is that Linus doesn't care about the Software Freedom of Linux kernel users.

---

### Post by alphaniner on 2009-12-09
> **Diluted said:**
> So RMS changed something which caused existing freedom to be denied.

Who's fault is it then? Linus, or RMS?

No, as ZankerH said in post 92, the updated GPL is an attempt to close loopholes, ie. to further protect the FSF's idea of software freedom.

> **ZankerH said:**
> How the hell is it absurd?

The idea some people have that RMS or the FSF create freedoms.

---

### Post by ZankerH on 2009-12-09
> **alphaniner said:**
> The idea some people have that RMS or the FSF create freedoms.

:%s/create/define/g and you've got it down. The Founding Fathers didn't create RL freedom in 1776 either, but they clearly defined it in a way that forever changed the course of human history. Ideas aren't created, they're thought up and, in some cases, formally defined. Those definitions are, naturally, subject to change, but that is, as I've already pointed out, analogous to security patches in software and not some Orwellian "changing the meaning of freedom". Perhaps "to create freedom" is not entirely how I'd put it, but the general idea is correct.

---

### Post by Diluted on 2009-12-09
Actually my post went something like this:

RMS made changes to GPL to close loopholes.

According to Simon17, these changes (or creating new freedoms) are not available to kernel users, and as such, Linus is supposedly denying freedom and is a tyrant etc.

However, looking at it from another angle, I can also see RMS making changes which caused the denial of freedom in the first place (or at least, made it so that it would not be appealing for the kernel to be licensed as GPLv3).

So I suppose I'm just slightly confused on which side to go for.

---

### Post by liamnixon on 2009-12-09
> **ZankerH said:**
> The only conclusion I can draw from this is that Linus doesn't care about the Software Freedom of Linux kernel users.

Just because Linus refuses to upgrade to GPLv.3 doesn't mean he doesn't care about software freedom (I have no idea if he does or doesn't.  I'm not him).  It just means there is/are aspect(s) to v.3 that he doesn't agree with, and he has the **freedom** to license the kernel how he wants.

---

### Post by ZankerH on 2009-12-09
> **Diluted said:**
> So I suppose I'm just slightly confused on which side to go for.

So it's somehow the FSF's fault that the egotist moron in charge of Linux is too damn arrogant to accept the new and improved GPL?

---

### Post by gnomeuser on 2009-12-09
> **ZankerH said:**
> So it's somehow the FSF's fault that the egotist moron in charge of Linux is too arrogant to accept the new and improved GPL?

Well he and the kernel developer community (you know the guys who actually wrote and hold the copyright of said code) did make a list of objections and illustrated that even if they desired to move it would be impossible since there is no requirement to do copyright assignment. The kernel has always been GPLv2 not GPLv2+, it was known in advance, the FSF nor their fanboys have no reason to run around and defame Linus over this issue.

Everyone agrees to switch or it does not happen, that is the way it works given the development model of the kernel. I hardly think that makes Linus arrogant and painting him like so for these reasons certainly doesn't endear the FSF to me nor I hope any thinking human being.

---

### Post by alphaniner on 2009-12-09
> **ZankerH said:**
> So it's somehow the FSF's fault that the egotist moron in charge of Linux is too damn arrogant to accept the new and improved GPL?

This is another example of that zealotry I was referring to.  Why should Linus be expected to kowtow to the FSF?

---

### Post by Diluted on 2009-12-09
That really depends. There are plenty of people with differing opinions on GPLv3. If someone disagrees with the changes, then that's one GPLv3 customer gone and by your definition, software that was supposed to be free is now less free than it could be.

I think GPL has done well to gather a lot of people, but if it starts to intrude on others' preferences or beliefs, then you can't blame it all on the naysayers.

However, I don't see how this warrants calling Linus a tyrant and a despot.

---

### Post by Twitch6000 on 2009-12-09
If you ask me the Linux Kernal should become truly open source by using the MIT/X11 license :p.

---

### Post by ibuclaw on 2009-12-09
> **Twitch6000 said:**
> If you ask me the Linux Kernal should become truly open source by using the MIT/X11 license :p.

This may happen in the future oddly enough...

NOTE: **NOT** the licensing of the ***entire*** Kernel ***solely*** under MIT/X11.
But instead having sections of code released under **multiple FSF compatible licenses**. ie: GPLv2 AND MIT/X11 at the same time.

This idea was brought about as one of the many steps to make it easier for manufacturers to write drivers for the kernel.

Since to be able to write a driver for Linux requires the use of GPL'd hooks. Whatever source-code that uses those hooks must also be GPL'd - as agreed by the license. As we all know - some manufacturers don't like doing this.

Another attempt at swaying manufacturers was a "we write the drivers for you" free service. Where the manufacturer gives the Linux Foundation the device and schematics. Then the Kernel Devs will write and maintain the driver themselves for free so the manufacturer needn't pay employees to do it.

Any business is good business, I suppose. :)

---

### Post by zekopeko on 2009-12-09
> **Simon17 said:**
> What makes you think that my viewpoints are so extreme that they would be the subject of satire or parody?

Free Software WILL take over the world. Look around you; it is already happening. And I like to think that the man who created the Software Freedoms and dedicated his life to making it happen will get the credit he deserves.

Perhaps the HURD will take longer than two years, and perhaps it is behind Linux in some areas, but it already has one HUGE advantage over Linux and it won't be long before it replaces Linux as the GNU kernel.

GNU-slash-Linux will cease to exist and there will only be GNU. It will happen because people value their Freedoms. Richard Stallman created the GPL3 for us and Linus is deliberately denying people their Freedoms. He is a tyrant and a despot and he  will fall.

I'm not smiling.

What essential "Freedoms" is Linus denying us?

> **ZankerH said:**
> So it's somehow the FSF's fault that the egotist moron in charge of Linux is too damn arrogant to accept the new and improved GPL?

I LOL'd.

Will I be able to use Mono on this great new OS that is coming to sweep the world by surprise or will I have to ask RMS for permission for that?

Anyway you two are zealots. No point in arguing with men/women that have left their reason at the proverbial doorstep.

---

### Post by zekopeko on 2009-12-09
> **tinivole said:**
> This may happen in the future oddly enough...

NOTE: **NOT** the licensing of the ***entire*** Kernel ***solely*** under MIT/X11.
But instead having sections of code released under **multiple FSF compatible licenses**. ie: GPLv2 AND MIT/X11 at the same time.

This idea was brought about as one of the many steps to make it easier for manufacturers to write drivers for the kernel.

Since to be able to write a driver for Linux requires the use of GPL'd hooks. Whatever source-code that uses those hooks must also be GPL'd - as agreed by the license. As we all know - some manufacturers don't like doing this.

Another attempt at swaying manufacturers was a "we write the drivers for you" free service. Where the manufacturer gives the Linux Foundation the device and schematics. Then the Kernel Devs will write and maintain the driver themselves for free so the manufacturer needn't pay employees to do it.

Any business is good business, I suppose. :)

Isn't this a no-no? You would welcome binary blobs to make the hardware work just when hardware vendors started writing drivers in the kernel.

---

### Post by zekopeko on 2009-12-09
To get this topic back on track:

OP is a man that loves cool things he read about a few days ago. 

From the feel I got reading various post by DPic I believe him to be a man that likes to react before thinking about the consequence  of said action. Not to mention that he won't have to do a damn thing to make this work except write how awesome it is in his blag.

His arguments boil down to "it's cool" , "HURD has a new website, something must be going on" and saying that there is support in the forums for such a move (DPic could you post a link to that assertion or was it made up on the spot or perhaps you consider 3-5 posts that say "Yey for Ubuntu HURD" a "lot of support on the forums"?).

For those that understand basic economics and resource management (and aren't raving Free software zealots) the choice is clear.

---

### Post by ibuclaw on 2009-12-09
> **zekopeko said:**
> Isn't this a no-no? You would welcome binary blobs to make the hardware work just when hardware vendors started writing drivers in the kernel.

Here are my sources of information.

Re: Licensing
[http://lkml.indiana.edu/hypermail/linux/kernel/0910.2/02195.html](http://lkml.indiana.edu/hypermail/linux/kernel/0910.2/02195.html) (Actually - second look at that. It's intent is so Linux is able to **work** with non-GPL/binary blobs better. Not the other way round).

Re: Driver Service.
[http://www.kroah.com/log/linux/free_drivers.html](http://www.kroah.com/log/linux/free_drivers.html)

> **zekopeko said:**
> To get this topic back on track:

OP is a man that loves cool things he read about a few days ago. 

From the feel I got reading various post by DPic I believe him to be a man that likes to react before thinking about the consequence  of said action. Not to mention that he won't have to do a damn thing to make this work except write how awesome it is in his blag.

His arguments boil down to "it's cool" , "HURD has a new website, something must be going on" and saying that there is support in the forums for such a move (DPic could you post a link to that assertion or was it made up on the spot or perhaps you consider 3-5 posts that say "Yey for Ubuntu HURD" a "lot of support on the forums"?).

For those that understand basic economics and resource management (and aren't raving Free software zealots) the choice is clear.

It was my understanding that Hurd was more server orientated...
OK - Linux is inherently server orientated too, but Linus' goal was always to make it a Desktop OS.

I may be wrong in that assumption though.

---

### Post by zekopeko on 2009-12-09
> **tinivole said:**
> Here are my sources of information.

Re: Licensing
[http://lkml.indiana.edu/hypermail/linux/kernel/0910.2/02195.html](http://lkml.indiana.edu/hypermail/linux/kernel/0910.2/02195.html)

Re: Driver Service.
[http://www.kroah.com/log/linux/free_drivers.html](http://www.kroah.com/log/linux/free_drivers.html)

This has to do with debugging applications not writing drivers.
They want to be able to debug non-GPL apps from the user-space down to the kernel AFAI understand it.

I doubt that devs are going to allow non-GPL code in the drivers since binary drivers would mean a slow death to Linux.

---

### Post by alphaniner on 2009-12-09
> **zekopeko said:**
> binary drivers would mean a slow death to Linux.

Could you briefly explain why you think this is so?

---

### Post by zekopeko on 2009-12-09
> **tinivole said:**
> It was my understanding that Hurd was more server orientated...
OK - Linux is inherently server orientated too, but Linus' goal was always to make it a Desktop OS.

I may be wrong in that assumption though.

Linux is server oriented because top companies that contribute large parts to the kernel have server offerings. IBM, Intel, Red Hat, Novell etc. all have server offerings in either purely software for or software+hardware.
If Canonical was as big as IBM or Intel and only wanted to make the kernel for desktops you would see more desktop oriented code submitted for inclusion.

---

### Post by zekopeko on 2009-12-09
> **alphaniner said:**
> Could you briefly explain why you think this is so?

There was that infamous post by a kernel dev that told a story of a potential future if they allow non-GPL drivers in the kernel.
Don't have a link or anything to guide to find it since I read it a long time ago but the gist is this:

You allow binary drivers you are going to end up with less hardware support and speed of development since the kernel will be at the mercy of hardware manufactures and their binary drivers.

Look at the situation with Nvidia and fglrx proprietary drivers. If your kernel isn't supported your f***ed. No 3D etc. Now imagine this for every piece of your hardware. Scary...

---

### Post by alphaniner on 2009-12-09
> **zekopeko said:**
> You allow binary drivers you are going to end up with less hardware support and speed of development since the kernel will be at the mercy of hardware manufactures and their binary drivers.

With the development model of the Linux kernel I guess this makes sense.  Thanks.

---

### Post by scottuss on 2009-12-09
This post is hilarious.

BTW ZankerH, you can install Ubuntu with only Free software.

Also, Linux a tyrant? He's a lot of things, but tyrant?

Brilliant! Keep this going guys!

---

### Post by forrestcupp on 2009-12-09
If RMS wrote a new GPLv4 and it said that in order for your software to be truly free you have to bend over and kiss your own backside, some of you would do it.

If Linus didn't care about software freedom and he had complete control over it, the new releases wouldn't even be GPLv2.

I truly hope the HURD *does* miraculously become as functional as Linux.  It would draw away all the holier-than-thou extremists and maybe we wouldn't have to hear it anymore.

---

### Post by zekopeko on 2009-12-09
> **forrestcupp said:**
> If RMS wrote a new GPLv4 and it said that in order for your software to be truly free you have to bend over and kiss your own backside, some of you would do it.

If Linus didn't care about software freedom and he had complete control over it, the new releases wouldn't even be GPLv2.

I truly hope the HURD *does* miraculously become as functional as Linux.  It would draw away all the holier-than-thou extremists and maybe we wouldn't have to hear it anymore.

There's gNewSense and they are still here. They just like to troll and feel superior because they "care" for "freedom".

---

### Post by Exodist on 2009-12-09
> **Xbehave said:**
> I can do it in 22

Personally i think Linux is better but you don't need to grok something to have an opinion on it, however if your not sure about something never pretend it's fact because there is a thin line between being mis informed and spreading FUD (looks at Skripka)

I stated a 100 line breakdown, you cant even read my statement and you assumed it said word. Also if thats all you got to bring to the table for debate then your statement is vastly null.

I am neither for nor against Hurd. I simply base my opinions based on technical overviews and structural breakdowns. 

The current facts are:
- Linux is seasoned, robust and currently feature rich in many aspects.
- Hurd is *theoretically* faster, but has less drivers and features.

So unless someone who actually knows REAL technical information about Hurd wishes to stand up, its not going anywhere.  Stating "Hurd is awesome its a microkernel", those responses only indicate you actually dont know anything and your just a fanboy..

---

### Post by Xbehave on 2009-12-09
> **Exodist said:**
> The current facts are:
- Linux is seasoned, robust and currently feature rich in many aspects.
- Hurd is *theoretically* faster, but has less drivers and features.
Hurd is theoretically **slower** because IPC is slower than shared memory.

> So unless someone who actually knows REAL technical information about Hurd wishes to stand up, its not going anywhere.  Stating "Hurd is awesome its a microkernel", those responses only indicate you actually dont know anything and your just a fanboy..
No stating Hurd is a good idea because it is a microkernel doesn't make you a fanboy any more than saying linux is awesome makes you a Linux fanboy. I doubt many people could give a detailed technical answer as to why Linux is better than the rest but it doesn't stop them liking it.

> If Linus didn't care about software freedom **and he had complete control over it**, the new releases wouldn't even be GPLv2.
Just to clarify (for others) Linus doesn't have control over it, one of the reasons he can't relicense the kernel is because unlike the FSF you don't need to assign him copyright to submit your code, as some kernel developers are dead, either a rewrite is required to eliminate any GPL2 only code OR linus has to wait 50 years for their copyrights to expire.

Plus it's not even clear that GPL3 is freer, it closes some "loopholes" like tivoisation but that is about user freedom to run modified code on particular hardware, which is not something the GPL2 set out to do. While this feature creep may seam like a good idea lots of kernel developers dislike it because it prevents certain security practices and gets in the way of embedded development, for example ChromeOS would be impossible if the kernel was GPL3.

So the kernel being GPL2 has at least 2 **major** reasons:
1) It can't legally be relicensed
2) Even if it could most developers don't want it to be

Neither of those has anything to do with Linus and if anybody is tyrannical it's the FSF because they can use code you submit to a FSF project for anything (i.e they can sell it to Microsoft if they want). The FSF also decided to put a loophole in gpl3 that meant weather or not the original submitter of wikipedia content agreed, their content could be relicensed to cc, that is a pretty big abuse of power.

---

### Post by Xbehave on 2009-12-09
> **tinivole said:**
> It was my understanding that Hurd was more server orientated...
OK - Linux is inherently server orientated too, but Linus' goal was always to make it a Desktop OS.
> I can (well, almost) hear you asking yourselves "why?".  Hurd will be
out in a year (or two, or next month, who knows), and I've already got
minix.  This is a program for hackers by a hacker.  I've enjouyed doing
it, and somebody might enjoy looking at it and even modifying it for
their own needs.  It is still small enough to understand, use and
modify, and I'm looking forward to any comments you might have. 

Linux was meant to be a hobby to fill a gap until hurd came along, but hurd never did.

---

### Post by forrestcupp on 2009-12-09
> **Xbehave said:**
> 
Plus it's not even clear that GPL3 is freer, it closes some "loopholes" like tivoisation but that is about user freedom to run modified code on particular hardware, which is not something the GPL2 set out to do.
Right.  It's actually *less* free.  For being "Free Software", the GPL sure has a lot of restrictions. ;)

---

### Post by fromthehill on 2009-12-10
> **forrestcupp said:**
> Right.  It's actually *less* free.  For being "Free Software", the GPL sure has a lot of restrictions. ;)

that's why there is [URL="http://en.wikipedia.org/wiki/WTFPL"]WTFPL
[/URL]:D

---

### Post by Tristam Green on 2009-12-10
> **forrestcupp said:**
> If RMS wrote a new GPLv4 and it said that in order for your software to be truly free you have to bend over and kiss your own backside, some of you would do it.

If Linus didn't care about software freedom and he had complete control over it, the new releases wouldn't even be GPLv2.

I truly hope the HURD *does* miraculously become as functional as Linux.  It would draw away all the holier-than-thou extremists and maybe we wouldn't have to hear it anymore.

> **zekopeko said:**
> There's gNewSense and they are still here. They just like to troll and feel superior because they "care" for "freedom".

While the rest of us simply couldn't "give" a "crap" because we really just want something that works.

---

### Post by forrestcupp on 2009-12-10
> **zekopeko said:**
> There's gNewSense and they are still here. They just like to troll and feel superior because they "care" for "freedom".But it's still Linux and based on Ubuntu, so there's still reason for them to hang around.

[quote=Tristam Green]While the rest of us simply couldn't "give" a "crap" because we really just want something that works.[/quote]Lol.

I actually somewhat care about software freedom, but not at the expense of usability.

---

### Post by KiwiNZ on 2009-12-10
> **ZankerH said:**
> So it's somehow the FSF's fault that the egotist moron in charge of Linux is too damn arrogant to accept the new and improved GPL?

Or maybe he can see that the FSF and RMS and the new and less improved GPL version are holding Linux back. This is certainly so in the enterprise markets.

Also referring to people that had the ability to develop such things as Linux as morons is unacceptable on these forums. Do not do it.

---

### Post by RiceMonster on 2009-12-10
The only one's who are truly arrogant are those that insist everyone else release under the license they deem to be "the most free".

---

### Post by Tristam Green on 2009-12-10
> **forrestcupp said:**
> Lol.

I actually somewhat care about software freedom, but not at the expense of usability.

As do I, but I'm sure you fully understand the tone in which I was speaking, forrest :) I've always valued your insight into subtlety ;-)

> **RiceMonster said:**
> The only one's who are truly arrogant are those that insist everyone else release under the license they deem to be "the most free".

My Freedom is greater than your freedom, because mine is capitalized.

---

### Post by DeadSuperHero on 2009-12-10
I wonder what the world would be like if Torvalds put Linux under a BSD license.

---

### Post by RiceMonster on 2009-12-10
> **Mr. Psychopath said:**
> I wonder what the world would be like if Torvalds put Linux under a BSD license.

I don't know, but that's an interesting thought for sure.

---

### Post by Sporkman on 2009-12-10
> **Mr. Psychopath said:**
> I wonder what the world would be like if Torvalds put Linux under a BSD license.

There'd be a lot less corporate development being passed back upstream.

---

### Post by DeadSuperHero on 2009-12-10
> **Sporkman said:**
> There'd be a lot less corporate development being passed back upstream.

Not necessarily. When I met some of the FreeBSD ports maintainers and upstream developers at OSCON back in July, a lot of them insisted that companies do in fact hand back quite often...after all, it's a hassle to maintain a system all by yourself when:

1.) Your company basically only made patches to the code you forked, and your only way to provide your customers with future platform updates is to collaborate with upstream developers on it

or

2.) Your company just wants to. 

It actually happens a lot.

---

### Post by mickie.kext on 2009-12-11
Linus is not a tytant. I think that he really do not dislike GPLv3 personally, he is just scared what might happen if he try to push it as new licence. Think about it. Novell, Google, TiVo,... Linux business of those companies would be declared illegal if Linux move to GPLv3. They will lose money in trying to adjust their business models, and they own rather big chunk of code in Linux kernel. Maybe they will call for a for splitting community at half!? Maybe Novell will even line up with SCO, because they to have UNIX ownership. GPLv3 have big potential for disaster. It can set all progress 10 years back if people is not careful.

Basically,  if Linux switches to GPLv3 right now, I think that only Cannonical and Red Hat would continue developing for sure and without complaining. It is not because people at other companies hate freedom, it is because they want freedom to. They would not be investing in FLOSS if thay don't. But if they have to adjust their whole busines model just to please FSF, they won't do it. It is hard enough to make money out of free sofware with GPLv2... They need to get sometnig in return. There is no argument that Stallman can pull in front of FLOSS companies CEOs that will convince them that GPLv3 is worth of hustle of re-licensing. They do not buy at tivoization stuf because in future, thay might need to tivoize for some reason. Only thing that is + for GPLv3 rigt now (from the likes fo Novell point of view) is improved licence compatibility. Apache licence compatibility for example. If OpenSolaris gone GPLv3 or if CDDL was GPLv3 compatible, we will now probably see more enthusiasm about GPLv3.

Bottom line, people will not risk profits only because political correctness, but if they got sometnig in return (ie, SunOS kernel licence compatibility) they would make efforts to re-licence. 

That said, I think that GPLv3 is very good licence. It would make Microsoft even more scared of linux because they could not make new harmful patent covenants. But if were on Linus' place, I would not push GPLv3 either. To many people to convince with to few points they really care that can be brought up in discussion.  Lets hope that Oracle changes Solaris to GPLv3 in future, that would make GPLv3 lot more interesting.

---

### Post by clanky on 2009-12-11
> **ZankerH said:**
> for now would be to improve the usability of Ubuntu GNU/Linux, and focus on removing non-Free software from it first.

Yeah, because taking out half of the drivers would make the OS more usable, right?

---

### Post by Xbehave on 2009-12-11
> **mickie.kext said:**
> That said, I think that GPLv3 is very good licence. It would make Microsoft even more scared of linux because they could not make new harmful patent covenants. But if were on Linus' place, I would not push GPLv3 either. To many people to convince with to few points they really care that can be brought up in discussion.  Lets hope that Oracle changes Solaris to GPLv3 in future, that would make GPLv3 lot more interesting.
Given that software patents vary by region so much, I don't think the place for patent deals is in the copyright lisense, the GPL2 already said there couldn't be further limits. Software should be licensed GPL2+open patents or GPL2+we permit all open-source software to use our patent, it's really not the scope of copyright. IMO the GPL2 is a pretty much perfect license and the GPL3 is a "bloated" one.

---

### Post by bshosey on 2009-12-13
I would love to see a fully GPLv3 OS. I would love to see HURD be complete. But the bottem line is Linux is not ready for GPLv3. I can understand the worries of the new license that companies have.

But the true bottom line is this. Freedom goes both ways. We can sit here an preach that OpenSource is better than ClosedSource. GPLv3 is better than GPLv2 or what ever. If a certain party does not want to use it, that is their right to not use.

---

