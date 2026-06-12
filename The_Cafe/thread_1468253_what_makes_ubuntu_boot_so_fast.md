---
title: "what makes ubuntu boot so fast ?"
date: 2010-05-01
forum: The Cafe
---

### Post by martvefun on 2010-05-01
Hello,

I haven't tried the new release yet but everywhere I go I read about the big improvement in boot time. From about 50sec to 20.

That's pretty amazing and I was wondering how they did it.

On my archlinux, my boot time is about 35 sec after the system installation (and installed gnome and the basic softwares). There is less software pre-installed on archlinux so I was expecting it to boot faster than ubuntu but it seems that the ubuntu developpment team did a good job.
Do you know what they did and if it's possible to adapt it to other linux distributions (it'd be sad not to) ?

thank you


ps: sorry if it's not the right place to post, but I didn't find anthing better

---

### Post by Kingsley on 2010-05-01
It's probably not any faster. People upgrade to newer version of Ubuntu after having crapped up their previous install over time. So the newer version ends up appearing much faster than what they had before. In actuality, it's just as fast or slow as a new install of any Ubuntu version.

---

### Post by sxmaxchine on 2010-05-01
im not exactly sure, however i think the improvements in ext4 would be a key point in the boot speed.

---

### Post by Linux_junkie on 2010-05-01
To improve the speed of applications and / or OS's developers usually re-structure the code in a way that reduces the number of lines of code.

---

### Post by ssj6akshat on 2010-05-01
HAL removal is the key factor in boot speed,I believe.

---

### Post by martvefun on 2010-05-01
on [this site]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_lucid_final&num=1"), they compare ubuntu 9.10 and 10.04 on 3 different netbooks
Even with clean install, there is improvement.

---

### Post by philinux on 2010-05-01
My last clean install of karmic took over a minute to get to a usable desktop.

Lucid boots to usable desktop in less than 20 seconds.

No doubt down to ureadahead and maybe mountall plus hal removal.
Plus clever devs. ;)

---

### Post by aklo on 2010-05-01
Lucid lynx is slower than karmic for me.

The time it takes after entering my password to the desktop fully appearing is slower than ~10 secs compared to karmic and it is a fresh install no other programs loading.

Anyway i still like it.

---

### Post by sandyd on 2010-05-01
removal of HAL

---

### Post by Sam on 2010-05-01
> **Kingsley said:**
> It's probably not any faster. People upgrade to newer version of Ubuntu after having crapped up their previous install over time. So the newer version ends up appearing much faster than what they had before. In actuality, it's just as fast or slow as a new install of any Ubuntu version.

lolwut?

---

### Post by FuturePilot on 2010-05-01
Removal of HAL and [Upstart]("http://upstart.ubuntu.com/")

---

### Post by Groucho Marxist on 2010-05-01
> **martvefun said:**
> 
Do you know what they did and if it's possible to adapt it to other linux distributions (it'd be sad not to) ?


Sub-contracted with the Energizer Bunny and Rivendell's softwaresmiths; those elves sure know how to forge a strong yet light OS.

---

### Post by arnab_das on 2010-05-01
loving this fast new ubuntu. but i think after a certain point this 'fast' thing gets a bit irritating. i want a bug free OS (well as much bug free as possible), i wouldnt mind an extra second of boot time if that amounts to developers devoting extra time to fix bugs and crappy softwares (wth is computer janitor? and why is it still there in 10.04?)

---

### Post by cariboo on 2010-05-01
Remember this is a long term support release, there will be several point releases during it's 3 year life time.

---

### Post by Penguin Guy on 2010-05-01
It uses [ureadahead]("https://launchpad.net/ubuntu/+source/ureadahead") which makes use of multi-core CPUs by caching commonly used data (such as the GDM) while the main boot process is running. It also uses [XSplash]("https://launchpad.net/ubuntu/+source/xsplash"), which means X programs can start loading while the splash screen is still being displayed.

---

### Post by Mr. Picklesworth on 2010-05-01
In essence, it doesn't waste a single moment while booting; the system always has some immediate job to do until you have a usable desktop.

---

### Post by sports fan Matt on 2010-05-01
Ok, so I have a question.  Since upgrading from Karmic, should I wait to remove hal & ureadahead until I clean upgrade Lucid?

---

### Post by kmsalex on 2010-05-01
i have only installed 10.04 on the family computer
pentium 4 2.2ghz 512mb ram integrated video bringing ram down to 488mb
with karmic just before i did an upgrade it took 40 seconds after the upgrade it took 45 seconds. also it had the exact same memory usage of 171.1mb after fully booted for 5 min. but firefox took a second less to load from 7 seconds in karmic to 6 in lucid.

---

### Post by Rasa1111 on 2010-05-01
> **Kingsley said:**
> It's probably not any faster. People upgrade to newer version of Ubuntu after having crapped up their previous install over time. So the newer version ends up appearing much faster than what they had before. In actuality, it's just as fast or slow as a new install of any Ubuntu version.


lol, it is definitely faster. 

 impressive for sure. :P

---

