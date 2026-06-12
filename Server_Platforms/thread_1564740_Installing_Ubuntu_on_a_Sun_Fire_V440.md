---
title: "Installing Ubuntu on a Sun Fire V440"
date: 2010-08-30
forum: Server Platforms
---

### Post by TTrussell on 2010-08-30
Perhaps this is the wrong place to be asking this, but I'm going to give it a shot anyway.

A group I work with has recently acquired a Sun Fire V440 from a lab that didn't want it anymore. We want to turn it into a media center using Ubuntu and some other software that we'll be writing.

Step 1 to this whole thing is getting Ubuntu installed on this machine. I was under the impression that a "Server" is just a hyped-up computer with a slightly different operating system. It appears I was wrong.

When I turn the system on and plug it into a monitor, there is no BIOS. So I'm not sure how I can install Ubuntu on the machine.

There's some crap on the internet (and in the installation guide) about using a Terminal Controller(?) or ALOM(?), but it's all Greek to me. I'm a software guy.

If somebody can tell me how I can install Ubuntu on this thing and use it like a regular computer to get my Media Center set up, I'd be very appreciative!

---

### Post by cascade9 on 2010-08-30
The Sun Fire V440 uses SPARC CPUs, not 086, and AFAIK the SPARC port of ubuntu was dropped at 7.10.

---

### Post by Guilden_NL on 2010-08-31
I think that it would take many posts to get you up to speed on the Sun architecture.  Just my humble opinion. You might want to ask for involvement of someone familiar with Sun.

Here's just a bit of a start if you would like to understand just what's on the V440, which makes a nice server by the way!  [[COLOR="Blue"]http://dlc.sun.com/pdf/819-2445-11/819-2445-11.pdf[/COLOR]]("http://dlc.sun.com/pdf/819-2445-11/819-2445-11.pdf")

And true that, Cascade9.  I have Ubuntu on all desktops and laptops in our home, but RHEL on servers, just because that's what I know from designing solutions.  And have to add in that for recent Red Hat support, you actually have to go with Aurora (I haven't made the move since I use mine as a file server mule)

For more info on Aurora, go here; [[COLOR="Blue"]http://auroralinux.org[/COLOR]]("http://auroralinux.org")

---

