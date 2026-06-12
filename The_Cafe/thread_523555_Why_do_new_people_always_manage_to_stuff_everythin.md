---
title: "Why do new people always manage to stuff everything up?"
date: 2007-08-12
forum: The Cafe
---

### Post by slimdog360 on 2007-08-12
Every second post is about how someone new manages to get the xserver to crash or some other similar thing. I can understand this, I managed to do this several time myself while I was still learning. But perhaps its time we looked at why this sort of thing continually happens and how to fix it.

I know that bullet-proof-X is coming out in Gutsy (most probably) but this is more of a band-aid solution, where the problem still lies beneath. If we can find out the exact reasons as to why this only seems to happen to new people, then perhaps we can start implementing solutions to stop this from happening.

My bet would be the lack of *real* documentation. There are guides out there but most of the ones I have looked at assume the new user knows what they are doing, which is never the case. Most documentation seems to be all over the place, which never helps also. Take a look at freebsd's documentation 
[http://www.freebsd.org/doc/en_US.ISO8859-1/books/faq/]("http://www.freebsd.org/doc/en_US.ISO8859-1/books/faq/")
[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/]("http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/")
I think it's set out pretty well, maybe still a little advanced, but then again so is freebsd. 

So what do you all think the problem is?

---

### Post by jrusso2 on 2007-08-12
The problem is they don't know what they are doing so to learn they try to do stuff and don't do it right.

---

### Post by acowboydave on 2007-08-12
> **jrusso2 said:**
> The problem is they don't know what they are doing so to learn they try to do stuff and don't do it right.

I agree, I am one of those people. Point to ponder...Hang a "Wet Paint" sign on a park bench, watch how many people test the paint.

---

### Post by kelvin spratt on 2007-08-12
I think its part of the natural learning curve we allways try to run before we can walk, in my case its most of the reading does not make sense so the easiest way is to do it the hard way, or just watch someone else, as i only need to be shown once, also because of Dyslexia i always seem to find the simple way to do things not allways the recognised way,

---

### Post by Warren Watts on 2007-08-12
The beauty of Ubuntu/Linux is the very fact that you get an opportunity to "get your hands dirty".  It's often the best way to learn something new.

I think the example of a corrupted xorg.conf file is a good example.  I too screwed up my x configuration file when I first started, but just today, I had reason to swap the monitors on two Ubuntu boxes, and edited both xorg.conf files without any problems at all.  If I hadn't learned from my previous mistake, I'm positive it would have taken me a while to straighten it all out.

Perhaps it's unfortunate that the end result is often a minor catastrophe, but I think you just have to keep an optimistic attitude, chalk it up to experience, and move on to the next thing you accidentally screw up.. :lolflag:

---

### Post by bwtranch on 2007-08-12
Is there anything that I can do?

---

### Post by bwtranch on 2007-08-12
I will go out and try anything you want. I am a testing user. Just tell me what you want me to do.

---

### Post by Scruffynerf on 2007-08-12
Incidentally, as the OP brought up killing the xserver, it's not necessarily the new user doing it. Ubuntu Feisty will also kill it's own xserver just because a system update ran between boots.

I've lost count how many times I've had to rebuild/re-install the xorg because an update killed the windows server.

Oh - for those wanting to, the thread is: [http://ubuntuforums.org/showthread.php?t=291915]("http://ubuntuforums.org/showthread.php?t=291915")

---

### Post by acowboydave on 2007-08-12
Well a good thing about the Linux community, there is always someone around to give you a helping hand in case you do fall.

---

### Post by bwtranch on 2007-08-12
I am still waiting on somebody to give me something to try. I will report back my findings. What are you scared of anyway, that I won't find a problem? Yeah, you should be. Because i probably won't!!!!

I would like to know one thing. Why does my little machine work flawlessly and everybody has all these problems?

I think that I know the answer to this question, but, give me your best take. Otay?

---

### Post by Scruffynerf on 2007-08-12
> **bwtranch said:**
> 

I would like to know one thing. Why does my little machine work flawlessly and everybody has all these problems?


Several possibilities present themselves (in no order):

1) You only run from a liveCD or LiveDVD
2) Your computer is extremely generic
3) You never install anything or allow any updates
4) You are a linux deity, compiling and running slackware and you do everything from the  command line
5) You are Torvalds.

/joke

---

### Post by ThrobbingBrain66 on 2007-08-12
> **bwtranch said:**
> I am still waiting on somebody to give me something to try. I will report back my findings. What are you scared of anyway, that I won't find a problem? Yeah, you should be. Because i probably won't!!!!

I would like to know one thing. Why does my little machine work flawlessly and everybody has all these problems?

I think that I know the answer to this question, but, give me your best take. Otay?

lol

I think this is more of a discussion thread...no one wants you to test anything.

---

### Post by forrestcupp on 2007-08-12
The best option is to prohibit any new users from switching to Ubuntu.

---

### Post by cmat on 2007-08-12
I killed the X server badly on openSUSE. Ubuntu installs drivers for video drivers a lot more safely than other distros. I killed the x server on Ubuntu because I updated with a bad driver.

---

### Post by g2g591 on 2007-08-12
yep, I'm one of those people too, I'm on about my 5th reinstall in about a month. (its my first month) but now things are pretty stable (I hope)

---

### Post by jrusso2 on 2007-08-13
> **bwtranch said:**
> I am still waiting on somebody to give me something to try. I will report back my findings. What are you scared of anyway, that I won't find a problem? Yeah, you should be. Because i probably won't!!!!

I would like to know one thing. Why does my little machine work flawlessly and everybody has all these problems?

I think that I know the answer to this question, but, give me your best take. Otay?

glibc update is always a good challenge

---

### Post by slimdog360 on 2007-08-13
> **Scruffynerf said:**
> Incidentally, as the OP brought up killing the xserver, it's not necessarily the new user doing it. Ubuntu Feisty will also kill it's own xserver just because a system update ran between boots.

I've lost count how many times I've had to rebuild/re-install the xorg because an update killed the windows server.

Oh - for those wanting to, the thread is: [http://ubuntuforums.org/showthread.php?t=291915]("http://ubuntuforums.org/showthread.php?t=291915")

thats also part of the trick most of the experienced people know to do. We dont upgrade after the upgrade has been out for a while and hence know if there is anything wrong with it.

---

### Post by eentonig on 2007-08-13
> **Scruffynerf said:**
> Incidentally, as the OP brought up killing the xserver, it's not necessarily the new user doing it. Ubuntu Feisty will also kill it's own xserver just because a system update ran between boots.

I've lost count how many times I've had to rebuild/re-install the xorg because an update killed the windows server.

Oh - for those wanting to, the thread is: [http://ubuntuforums.org/showthread.php?t=291915]("http://ubuntuforums.org/showthread.php?t=291915")

I never experienced this with Feisty. But I guess that comes by running proprietary drivers?

---

### Post by jrusso2 on 2007-08-13
> **eentonig said:**
> I never experienced this with Feisty. But I guess that comes by running proprietary drivers?

Not necessarily, I think it most comes from trying to run an updated driver thats not in the repos.

I have not had that problem, but I only use the repo proprietary drivers.

---

### Post by DjBones on 2007-08-13
I'm sure if we made it apparent how easy and simple it is to make a back-up, and then rescue the xorg through the live-cd most of the post's would be unnecessary
Frequently crashed my xorg with the ATI driver's and Beryl.. so i understand the importance of good back-ups now lol
((although you could do it in rescue mode in tandem with nano/vim, that would be a bit daunting for a new user haha))

[Scruffynerf, i thought the torvalds line was classic haha]

---

### Post by forrestcupp on 2007-08-13
> **jrusso2 said:**
> Not necessarily, I think it most comes from trying to run an updated driver thats not in the repos.

I have not had that problem, but I only use the repo proprietary drivers.

But that was the point.  They're still proprietary drivers. I'm not bashing them, I use them, too.

The main problem I've had is when a new Linux kernel was automatically updated, but for some dumb reason the linux-restricted-modules wasn't updated.  It's happened at least once, maybe twice.

---

