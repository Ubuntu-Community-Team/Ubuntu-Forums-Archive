---
title: "[BUG/MISSING] Things to keep in mind for the next distribution CD"
date: 2007-10-19
forum: Ubuntu Brainstorm
---

### Post by carac on 2007-10-19
1. Ultra-small packages that are required to start the network - like broadcom firmware cutter = 25.8 kbytes, but without it the network can not start ... and if it is not on the CD to install it you must have network :( (the idea is that having the bcm43xx driver and not having this one is rather stupid).

2. Boot from LiveCD should be verbose by default - it's not something that you do all the time!

3. First boot after install should also be verbose - if something goes wrong or simply it takes too much it's better to see that the computer is not locked!!!

---

### Post by Zdravko on 2007-10-19
1. Okay.
2. What do you mean with "verbose"?
3. Okay.

---

### Post by carac on 2007-10-19
> **Zdravko said:**
> 1. Okay.
2. What do you mean with "verbose"?
3. Okay.

Basically without quiet & splash. (ideally also in a decent vga text mode - like knoppix :) ).

On an old slow system when you first try the LiveCD it will stay on a black screen without ANY sign of progress on the display for like 2-5 minutes - some people will simply assume it is blocked/crashed and might power it off ...

---

### Post by Zdravko on 2007-10-19
Who uses the LiveCD anyway? I have always used the ALternate CD without any problems.

---

### Post by FredB on 2007-10-19
> **Zdravko said:**
> Who uses the LiveCD anyway? I have always used the ALternate CD without any problems.

A lot of people who are scared of command line interface ;)

The last time I used liveCD to to an install ? Dapper ;)

I am an alternate-addict ;)

---

### Post by Zdravko on 2007-10-19
Command line interface? What is that? Do you mean it is scary to use the keyboard only to navigate through menus?????

---

### Post by carac on 2007-10-19
> **Zdravko said:**
> Who uses the LiveCD anyway? I have always used the ALternate CD without any problems.

Actually I will take a look at that CD also (I am curious if the broadcom firmware cutter is on that one but I doubt) - but as things are presented on Ubuntu site 99% of the people will try the LiveCD so ...

---

### Post by Zdravko on 2007-10-19
Hahah. 99% of the people have some big problem then. The alternate version always works.

---

### Post by glotz on 2007-10-19
Why is a windoze user debating this issue here? I bet the majority of people will use the desktop CD. Thus it needs most attention. Personally I do prefer the alternate also.

---

### Post by Ceemee on 2007-10-19
Personally I use the Live CD and here is why - 

I prefer to do an entire install, but usually my computer is too far from my router to convieniently connect via Cat5.  (requires 100' cable going up the stairs and through rooms and hallways.  My wife hates it)

so I greatly enjoy the ability to boot live CD, see what I need to download.  Re-boot into windows, download it, and then install Ubuntu.

So its not that i'm afraid of a text based install.  I've done it many times.  I just like the convienence of a live CD to be prepared for what basics I will need post-install.

---

### Post by carac on 2007-10-19
> **carac said:**
> 
2. Boot from LiveCD should be verbose by default - it's not something that you do all the time!

3. First boot after install should also be verbose - if something goes wrong or simply it takes too much it's better to see that the computer is not locked!!!


UPDATE - most of the problems when there is no feedback on boot might be from the 'splash' - see [https://launchpad.net/ubuntu/+source/usplash/+bug/63558](https://launchpad.net/ubuntu/+source/usplash/+bug/63558)

---

### Post by Zdravko on 2007-10-19
> **glotz said:**
> Why is a windoze user debating this issue here? I bet the majority of people will use the desktop CD. Thus it needs most attention. Personally I do prefer the alternate also.

I am almost sick of repeating one and the same thing several thousand times:
**LOOK AT THIS THREAD: [http://ubuntuforums.org/showthread.php?t=578606](http://ubuntuforums.org/showthread.php?t=578606)**

---

### Post by Twintop on 2007-10-19
> **Zdravko said:**
> Who uses the LiveCD anyway? I have always used the ALternate CD without any problems.

I prefer the LiveCD over the Alternate for a number of reasons. First, if a friend of mine who is not an experienced Linux user (or Windows SA) is interested, I don't need to download another .ISO to burn a copy for them. Secondly, when I am installing I usually have other computer-related tasks to accomplish, so having a desktop with OOo and Firefox (at a minimum) makes this possible.

> **Zdravko said:**
> I am almost sick of repeating one and the same thing several thousand times:
**LOOK AT THIS THREAD: [http://ubuntuforums.org/showthread.php?t=578606](http://ubuntuforums.org/showthread.php?t=578606)**


Xubuntu would probably work ok for you. You MIGHT be able to use the regular Ubuntu though, since the Compiz stuff won't (or shouldn't) start if you don't have 3D acceleration. I'd say try the LiveCD (not alternate) and see if it'll let you boot in to it. If the LiveCD is usable, it will definately work on an install because it won't be trying to do everything from what little RAM you have.

---

### Post by m0eman on 2007-10-19
I also prefer the liveCD for many reasons. I agree about the livecd being verbose (or perhaps a little window near the bottom that is verbose like in the earlier ubuntus) but not the first boot.

As for Zdravko, i doubt the live cd will work for you, but you might be able to install with the alternate cd. At the very least xubuntu will work.

---

### Post by glotz on 2007-10-19
Zdravko sorry to hear that. I just wonder what makes you think heron will use less resources? One thing you might also want to take a look at is [http://fluxbuntu.org/](http://fluxbuntu.org/) And you can't break your box. The worst thing that could happen is you might need to reinstall windoze. (ok, that's IS pretty horrible...) One more thing, you might want to add a link to your sig if you get asked about this alot.

---

### Post by Zdravko on 2007-10-20
> **glotz said:**
> Zdravko sorry to hear that. I just wonder what makes you think heron will use less resources? One thing you might also want to take a look at is [http://fluxbuntu.org/](http://fluxbuntu.org/) And you can't break your box. The worst thing that could happen is you might need to reinstall windoze. (ok, that's IS pretty horrible...) One more thing, you might want to add a link to your sig if you get asked about this alot.

Hardy might use more resources, but I am going to have a better PC.

---

### Post by trig on 2008-02-11
my last computer (it was a junk box much like this one) i didnt have the official cd. i had to go thought 2 versions before I got the right one.. this junk box i used the cd that was sent to me... worked fine. fyi iuse a 'gateway 2000" made in 98...lol and as far as booting from disc last time i did so was when I installed

---

