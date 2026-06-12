---
title: "64 bit linux clarification"
date: 2009-09-24
forum: The Cafe
---

### Post by niallabrown on 2009-09-24
I have read lots of stuff about 4 gigs ram and 64 bit Linux but the story keeps changing. Can someone with experience with this area please explain something in simple terms...

I want to install 32Bit ubuntu on an AMD 64 bit system with 4 gigs ram (I know I will not get the 64 bit speed increase on software that uses...something about multiple integers or something).  I don't care about that.  I wan to know if I install 32 bit Ubuntu on this machine will it run slower with 4 gigs than it would if I had 2 gigs ram?  This may sound like a stupid question but that is what I am starting to think based on what I have read.

Also are the problems with cutting out audio, crashes and 64 bit flash not having sound at all likely due to the 64 bit distro and software not being as mature?
 
Thanks

---

### Post by Xbehave on 2009-09-24
64bit runs fine, there is 64bit flash now. 

Old 32bit computers can only address just under 4GB of ram, however most now have [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") to work around this limitation
```
 cat /proc/cpuinfo | grep pae
```
will probably give you a line like this
```
flags           : fpu vme de pse tsc msr **pae** mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up rep_good extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy
```
That means that a 32bit system can fully utilise the ram (except under windows which keeps the <4GB limit for non 64 versions)

---

### Post by tuxxy on 2009-09-24
Firstly I don't know where you heard this

> the problems with cutting out audio, crashes and 64 bit flash not having sound at all likely due to the 64 bit distro and software not being as mature?

64-bit has had its own native 64-bit Flash plugin for some time and its excellent.

Yes you can install 32-bit Ubuntu on an AMD 64-bit system but in my opinion you would be mad too limit a machine like this.  If you do go for 32-bit you wont have access 4GB+ RAM and yes you wont have the performance increases either which you would see most in video,photo editing and number crunching.

If you are not trying 64-bit Ubuntu based on them issues mentioned above then this is not a wise decision at all, Flash is great and so is 64-bit Ubuntu

---

### Post by tjwoosta on 2009-09-24
> I don't care about that. I wan to know if I install 32 bit Ubuntu on this machine will it run slower with 4 gigs than it would if I had 2 gigs ram?

no...

If anything it should run faster

---

### Post by tkoco on 2009-09-24
I supposed that you could load 32 bit version of Ubuntu on the 4 gig system. Will it run slower? ... slower as compared to what? The real question is "Will you get the performance that you expect by using the 32 bit version vs the 64 bit version?" Give it a try... nothing ventured, nothing gained.

> **niallabrown said:**
> I have read lots of stuff about 4 gigs ram and 64 bit Linux but the story keeps changing. Can someone with experience with this area please explain something in simple terms...

I want to install 32Bit ubuntu on an AMD 64 bit system with 4 gigs ram (I know I will not get the 64 bit speed increase on software that uses...something about multiple integers or something).  I don't care about that.  I wan to know if I install 32 bit Ubuntu on this machine will it run slower with 4 gigs than it would if I had 2 gigs ram?  This may sound like a stupid question but that is what I am starting to think based on what I have read.

Also are the problems with cutting out audio, crashes and 64 bit flash not having sound at all likely due to the 64 bit distro and software not being as mature?
 
Thanks

---

### Post by Xbehave on 2009-09-24
> **tuxxy said:**
> If you do go for 32-bit you wont have access 4GB+ RAM 
[PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") makes this redundant. the rest of your post is valid though

---

### Post by foremannz on 2009-09-24
Up to the point where you need to address more than 3GB RAM, I doubt you will notice any performance benefit by using 64bit

---

### Post by tuxxy on 2009-09-24
> **foremannz said:**
> Up to the point where you need to address more than 3GB RAM, I doubt you will notice any performance benefit by using 64bit

You doubt? heh why not try it :P

---

### Post by niallabrown on 2009-09-24
> Firstly I don't know where you heard this
Just to explain, these are my issues. I have been using the 64 bit Ubuntu install on this machine for a few months.  The problems:

Audio cutting out at high levels
64 bit flash installed but with no sound at all
Frequent crashes in open office
Firefox being very slow to load

These problems may be due to the laptop rather than the 64bit OS but I'm not sure.

I am considering trying the 32 bit version to see if the issues persist.  

> slower as compared to what?  Slower than a typical system running say 2 gigs ram.  This miss-communication is why I can't get an answer from the materials I have read.  I don't care if the computer is as fast as a 64 bit system if it has problems.  I just want it to work properly (if it even is the 64 bit software that is the problem.)

Still confused...  Maybe I can put it this way.  If I just install the 32bit ubuntu and it did happen to fix these issues, would it run at a decent speed (NOT 64 bit fast but a decent speed like say as if it had 2 gigs ram) or would I face some sort of memory problems that will make it very unnaturally slow... like slower than 2 gigs for example.

And lastly I don't know enough to be able to read what the code is telling me for PAE.  Do I need to install that?

---

### Post by dmglouis on 2009-09-24
I am running a 32-bit Ubuntu on a 64-bit capable system with 4GB ram. It's running fine for me. It just sees 3GB of the memory.

---

### Post by foremannz on 2009-09-25
> **tuxxy said:**
> You doubt? heh why not try it :P
He he, I run 9.04 x64 from an SSD, 8GB RAM and 512MB video - I think I need more though ... maybe 16GB RAM :lolflag:

---

### Post by FuturePilot on 2009-09-25
> **niallabrown said:**
> Just to explain, these are my issues. I have been using the 64 bit Ubuntu install on this machine for a few months.  The problems:

Audio cutting out at high levels
64 bit flash installed but with no sound at all
Frequent crashes in open office
Firefox being very slow to load

These problems may be due to the laptop rather than the 64bit OS but I'm not sure.

I am considering trying the 32 bit version to see if the issues persist.  

  Slower than a typical system running say 2 gigs ram.  This miss-communication is why I can't get an answer from the materials I have read.  I don't care if the computer is as fast as a 64 bit system if it has problems.  I just want it to work properly (if it even is the 64 bit software that is the problem.)

Still confused...  Maybe I can put it this way.  If I just install the 32bit ubuntu and it did happen to fix these issues, would it run at a decent speed (NOT 64 bit fast but a decent speed like say as if it had 2 gigs ram) or would I face some sort of memory problems that will make it very unnaturally slow... like slower than 2 gigs for example.

And lastly I don't know enough to be able to read what the code is telling me for PAE.  Do I need to install that?

My guess is your audio problem has nothing to do with the OS architecture. There's very few instances where a certain architecture has a problem that a different architecture doesn't. So going from 64bit to 32bit is probably not going to solve the problem.

---

### Post by Eisenwinter on 2009-09-25
> **foremannz said:**
> He he, I run 9.04 x64 from an SSD, 8GB RAM and 512MB video - I think I need more though ... maybe 16GB RAM :lolflag:
Son of a bitch!

:lolflag:

Damn man, that's some insane hardware which I would LOVE to have, lucky!

---

### Post by VertexPusher on 2009-09-25
> **niallabrown said:**
> Audio cutting out at high levels
64 bit flash installed but with no sound at all
Sound issues are perfectly normal in Linux distributions running PulseAudio. So these are probably unrelated to 64bit.

I'm running Ubuntu 9.04 64bit (with 64bit Flash, but without PulseAudio) on a Core i7. No issues at all.

---

### Post by kirsis on 2009-09-25
Running 64-bit Jaunty at work. Flash works great, everything works and feels fantastic. No issues whatsoever, no app compatibility issues, etc.

If you have a 64 bit system, I advise you to use a 64 bit OS.

Ironically, I've used 32 bit Ubuntus on my Laptop for 1.5 years now and only last week found out that I have a 64 bit CPU :)

---

### Post by zolookas on 2009-09-25
> **niallabrown said:**
> I wan to know if I install 32 bit Ubuntu on this machine will it run slower with 4 gigs than it would if I had 2 gigs ram?  This may sound like a stupid question but that is what I am starting to think based on what I have read.

Also are the problems with cutting out audio, crashes and 64 bit flash not having sound at all likely due to the 64 bit distro and software not being as mature?
 
Thanks

PAE does have some overhead, but it is usually about 1%. But I think you should consider using 64 bit Ubuntu, because you won't be losing anything (you can still run 32bit apps like skype from medibuntu), only gaining performace in some areas.

---

### Post by Xbehave on 2009-09-25
> **dmglouis said:**
> I am running a 32-bit Ubuntu on a 64-bit capable system with 4GB ram. It's running fine for me. It just sees 3GB of the memory.

Interesting! What does this return:
```
cat /proc/cpuinfo && cat /proc/meminfo
```
perhaps the ubuntu kernel has pae disabled :confused:

I have 64bit fedora installed and I am very happy with it, even though i have <2gb ram. I think there used to be a lot of problems with 64bit but most are now gone, but as you wont be loosing much as long as your kernel+cpu has pae enabled you may aswell give 32bit a try.

---

### Post by t0p on 2009-09-25
I think a lot of you are posting without reading the OP's later posts.

The OP has been running 64-bit Ubuntu and has been having problems with Flash, audio, crashes, slow-starting applications.  The OP wants to know if running 32-bit Ubuntu on his 64-bit machine will resolve the problems.

I suspect it won't.  The problems sound like hardware issues.

Still, you can install the 32-bit ubuntu and see, can't you?  Then you can come back and tell us whether it helped or not.

---

### Post by 3rdalbum on 2009-09-25
The 64-bit edition of Ubuntu is exactly the same as the 32-bit edition, but it uses 64-bit processor instructions and memory addresses.

Your Flash problem might be because of the alpha state of the Flash plugin on 64-bit, but it's probably unlikely. You could always try it on a live CD to check, or install a 32-bit browser (outside the repositories) and 32-bit Flash Plugin.

---

### Post by niallabrown on 2009-09-25
Thanks dmglouis!  I finally have my answer.

That being said many of you think it wont help the problems I have been having by installing the 32 bit Ubuntu.  All I can say is it's worth a shot because with the current problems especially flash not having audio (I use flash for my work) the system is making it hard to get my work done.

Thanks for all the help and I will post back when I get a chance to try reinstalling.

---

