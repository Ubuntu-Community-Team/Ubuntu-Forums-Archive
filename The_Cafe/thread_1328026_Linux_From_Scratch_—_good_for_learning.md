---
title: "Linux From Scratch — good for learning?"
date: 2009-11-16
forum: The Cafe
---

### Post by Jestersage on 2009-11-16
In terms of truly learning Linux, how is the "distribution" Linux From Scratch? Or should I just stick to Arch?

---

### Post by Grifulkin on 2009-11-16
Arch is definitely good, but it uses things that aren't linux like, case in point the rc.conf file in Arch is BSD style.  All the configurations in one central file.  Which I absolutely love and think that it should be adopted to more Distros.  As for your questions about Linux from Scratch? No clue.

---

### Post by Icehuck on 2009-11-16
> **Jestersage said:**
> In terms of truly learning Linux, how is the "distribution" Linux From Scratch? Or should I just stick to Arch?

It depends on if you want to invest the time in learning how linux is compiled. It might take a few tries to get it working correctly. You can follow everything step by step and still end up with compilation errors and have to hunt around for answers. Will you learn much? Depends if you already know most of the commands being used. If you don't then some commands will leave you wondering whats going on. While they explain what some commands are, it doesn't explain structure or why you need these options. A great example of this is this command line.

```
$LFS_TGT-gcc -dumpspecs | sed \
  -e 's@/lib\(64\)\?/ld@/tools&@g' \
  -e "/^\*cpp:$/{n;s,$, -isystem /tools/include,}" > $SPECS 
echo "New specs file is: $SPECS"
unset SPECS
```

If you do decide to try LFS, I suggest using Slackware as your host system. You'll run into less conflicts using the vanilla packages on Slack. You can just select all the defaults during installation and be good to go.

---

### Post by keithweddell on 2009-11-16
I'm not so sure. I'm sure that you could learn a lot.  But I stopped when I found myself just blindly following a set of instructions and actually learning very little from it all.

Keith

---

### Post by luctor on 2009-11-16
> **keithweddell said:**
> I'm not so sure. I'm sure that you could learn a lot.  But I stopped when I found myself just blindly following a set of instructions and actually learning very little from it all.

Keith

I agree with that.

---

### Post by John Bean on 2009-11-16
Depends on the intended purpose. As an analogy, I could build a house if I wanted to learn about all the skills needed to do it or simply desired the challenge, but it's not something to be taken lightly nor is it usually the optimal way to achieve the end result of living in a nice house. 

But it's always there as a an option. Choice is good.

---

### Post by Jestersage on 2009-11-16
> **John Bean said:**
> Depends on the intended purpose. As an analogy, I could build a house if I wanted to learn about all the skills needed to do it or simply desired the challenge, but it's not something to be taken lightly nor is it usually the optimal way to achieve the end result of living in a nice house. 

But it's always there as a an option. Choice is good.

Hmm. Thanks. I think the analogy would be "You have a mansion, and you decide to try your hand on building a house, so you decide to build a small storehouse/treehouse in your backyard. even if it broke down, all ti cause is your money and time.

---

### Post by John Bean on 2009-11-16
> **Jestersage said:**
> Hmm. Thanks. I think the analogy would be "You have a mansion, and you decide to try your hand on building a house, so you decide to build a small storehouse/treehouse in your backyard. even if it broke down, all ti cause is your money and time.
Perhaps, although I doubt that building a garden shed would teach you much about building a real house. 

The OP was suggesting the "Linux from scratch" exercise as a way of "truly learning Linux" which I interpret as meaning "Linux in its entirety" rather than a tiny part of it - in other words building a house"rather than a shed.

Or maybe the analogy is just rubble anyway ;-)

---

### Post by gn2 on 2009-11-16
> **Jestersage said:**
> In terms of truly learning Linux, how is the "distribution" Linux From Scratch? Or should I just stick to Arch?

You'll only know when you try it for yourself, it might teach you stuff that's useful to you, only you can find that out.

---

### Post by t0p on 2009-11-16
There are 2 sorts of "learning Linux".  One is to pick a distro, stick to it for ages and learn as much about it as you can by *using* it.  The other is to try as many different distros as you can, learning each to a certain extent, before moving on to the next.  That way, you'll learn all about the similarities and differences between distros and types of distro.

So 'Linux from scratch' may be really useful as part of a course of study, or it might be utterly irrelevant.  You get to choose which applies to you.

---

### Post by maflynn on 2009-11-16
Fedora is another distro that you can learn a lot from.  

Ubuntu has advantages, but it tries really hard to protect the user from shooting themselves in the foot and just working from the get go, that being the case, ubuntu seems to have less updates, i.e., older kernel, then some other distros.  Fedora has much more current releases which may not always work well so you'll need to do some work and that's where you learn.

---

### Post by MisfitI38 on 2009-11-17
> **maflynn said:**
> Fedora is another distro that you can learn a lot from..

I agree. Fedora has a graphical installer, but in my opinion, it relies a great deal on user competence and configuration through the shell (vs. the gui tools available in other new-user-friendly distros). 
To learn more about Linux and GNU, I would recommend trying as many distros as you can; then you will have experienced how each one differs in its approach to things like network scripts, initramfs, packaging, system configuration, maintenance, upgrade and initial installation.
I would also recommend trying LFS from time to time, as your skills and experience grow; the more UNIXy-type knowledge you have, the more LFS will make sense and grow on you.
Have fun.

---

