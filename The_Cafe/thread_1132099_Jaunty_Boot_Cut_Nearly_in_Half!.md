---
title: "Jaunty Boot Cut Nearly in Half!"
date: 2009-04-21
forum: The Cafe
---

### Post by CraigPaleo on 2009-04-21
I took part in the [Attach your boot-chart thread]("http://ubuntuforums.org/showthread.php?t=531453") when I noticed people with Jaunty had about half the boot time. So, I decided to upgrade early just so I could test it. 

My boot time under Intrepid was 29 seconds - under Jaunty, 16! What an improvement! It feels snappier all around too!

---

### Post by tom66 on 2009-04-21
There's a video on YouTube which shows Jaunty booting in an impressive 13 seconds from an SSD: [http://www.youtube.com/watch?v=bqefSHEx7kE](http://www.youtube.com/watch?v=bqefSHEx7kE)

---

### Post by NightwishFan on 2009-04-21
From GRUB to KDM, mine (Kubuntu AMD64) boots in about 10-12 seconds. It is faster to do a fresh boot than to resume from hibernation.

---

### Post by lykwydchykyn on 2009-04-21
Sweet!  This will make my semi-annual reboot so much less painful! 
:-D

---

### Post by will1911a1 on 2009-04-21
You guys must have CPUs that put mine to shame.  Even my Arch install doesn't boot in 16 seconds.

---

### Post by wolfen69 on 2009-04-21
> **will1911a1 said:**
> You guys must have CPUs that put mine to shame.  Even my Arch install doesn't boot in 16 seconds.

a quad core can do wonders.  ;)

---

### Post by NightwishFan on 2009-04-21
I have a AMD Athlon x2 3800+ @ 2000mhz

As for booting, I think my hard drive is what makes for really great performance. Back when I had Vista, I checked that score thingy, and it got like a 5.6 everything else was a 3 or so. ;)

Puppy 4.1 when frugal installed boots in about 7 seconds from grub to fully usable desktop.

Fedora 10 AMD64 took about 30 seconds to boot, Intrepid, about 20.

Hopefully in the future, Ubuntu works on hibernate a little more. It takes much longer to save the compressed image and resume from it than OpenSUSE does, and it only has a blank console when doing so, nothing graphical or even a progress counter like Fedora.

---

### Post by will1911a1 on 2009-04-21
> **wolfen69 said:**
> a quad core can do wonders.  ;)

Heh it must.  Well when my poor old machine dies maybe I'll get some more up to date hardware.

---

### Post by CraigPaleo on 2009-04-21
> **will1911a1 said:**
> You guys must have CPUs that put mine to shame.  Even my Arch install doesn't boot in 16 seconds.

Just a lonely single core AMD Sempron. It was called "wimpy" in the post your boot-chart thread.

---

### Post by lukjad on 2009-04-21
I have a 633 Celeron (for now) and I must say that Intrepid's boot time is very short. I wonder what Jaunty will be like...

---

### Post by Eisenwinter on 2009-04-21
> **will1911a1 said:**
> You guys must have CPUs that put mine to shame.  Even my Arch install doesn't boot in 16 seconds.
Do you use UDEV?

Because UDEV takes like 9 - 10 seconds to fill up.

If you start using a static /dev, you will cut your boot time by at least 9 seconds.

---

### Post by aktiwers on 2009-04-21
> **Eisenwinter said:**
> Do you use UDEV?

Because UDEV takes like 9 - 10 seconds to fill up.

If you start using a static /dev, you will cut your boot time by at least 9 seconds.

Explain please :)

---

### Post by Kareeser on 2009-04-21
> **tom66 said:**
> There's a video on YouTube which shows Jaunty booting in an impressive 13 seconds from an SSD: [http://www.youtube.com/watch?v=bqefSHEx7kE](http://www.youtube.com/watch?v=bqefSHEx7kE)

I've watched that one twice now... it still surprises me.

Now I want a solid state drive and a e8400 :(...

---

### Post by tom66 on 2009-04-21
Disabling usplash I get 18.97 seconds, pretty impressive. (With usplash: 20-24 seconds).

---

### Post by CraigPaleo on 2009-04-21
> **lykwydchykyn said:**
> Sweet!  This will make my semi-annual reboot so much less painful! 
:-D

LOL! I don't boot up often either but there are other improvements:
Applications start up for me in Gnome as fast as they did in KDE and I can use the extra visual effects without having to tweak them by installing the compiz settings manager. In Hardy, effects i.e wobbly windows were unusable. Large windows would fall down as if anchored by a weight no matter what I did. Under Intrepid, I could tweak them enough to be usable. In Jaunty, I didnt' have to tweak anything! 

There is something about my machine and Kubuntu being faster. If I install it again and everything is even faster, I think I'll like to about die. I love KDE's looks but I just don't like using it.  Okay, I'm off on a tangent. The speed of Jaunty really has me excited though!

---

### Post by lisati on 2009-04-21
> **wolfen69 said:**
> a quad core can do wonders.  ;)
Quad core? If I get an identical laptop to the one I'm using at the moment (it has a dual-core) and put them side by side, will that count? :)

---

### Post by CraigPaleo on 2009-04-21
> **lisati said:**
> Quad core? If I get an identical laptop to the one I'm using at the moment (it has a dual-core) and put them side by side, will that count? :)

Put Jaunty on it! You won't be disappointed! You won't get pissed either!

---

### Post by Terrycymru on 2009-04-22
Jaunty shows absolutely no improvement in boot time compared to Intrepid on my machine. For speed I use the alpha of Puppy Linux based on Jaunty - tremendous!

---

### Post by Sealbhach on 2009-04-22
> **Terrycymru said:**
> For speed I use the alpha of Puppy Linux based on Jaunty - tremendous!
 
What is that? Puppy Linux based on Jaunty?
 
.

---

### Post by majabl on 2009-04-22
> **lukjad007 said:**
> I have a 633 Celeron (for now) and I must say that Intrepid's boot time is very short. I wonder what Jaunty will be like...

How long is very short?  I also have Ubuntu running on a 633 Celeron (see sig for further details) and, while once it's running it's acceptably speedy, booting is a matter of minutes, not seconds.

---

### Post by Mehall on 2009-04-22
> **Sealbhach said:**
> What is that? Puppy Linux based on Jaunty?
 
.

Check out the "Woof" project from puppy linux.

(puppylinux.org/woof or whatever the domain name for puppy is with /woof after it )

It lets you build Puppy from distro of your choice. I need to try it again, couldn;t get it working a few alphas ago.

---

### Post by weeman7007 on 2009-05-14
> **Mehall said:**
> Check out the "Woof" project from puppy linux.

(puppylinux.org/woof or whatever the domain name for puppy is with /woof after it )

It lets you build Puppy from distro of your choice. I need to try it again, couldn;t get it working a few alphas ago.

I'm intrigued... How much faster does this boot than regular jaunty, is it reasonably stable to use as a main OS and thus could I install it on my laptop ssd/hdd?

---

### Post by coldReactive on 2009-05-14
My jaunty still boots at around 30-35 seconds (about the same as the fresh install sadly.)

Intrepid and Hardy did the same.

---

### Post by Joshua Wells on 2009-05-30
AAAAAAAAAAAAAARGH! my bootchart directory only has tarballs in instead of images and those tarballs contain headers and stuff.:(

---

