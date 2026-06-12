---
title: "Ideas for an Old Computer?"
date: 2010-01-29
forum: The Cafe
---

### Post by chessnerd on 2010-01-29
Alright, I've got an old computer from 1996. It's got a Pentium I running at 200 MHz, 32 MB of RAM, and a 4 GB HDD. Currently, it's running a crippled version of Windows 95 that really can't do anything. 

I was wondering if you guys have any ideas about how I could use this old machine. I installed a spare CD-ROM drive in it (old one was a 2x, oh, the pain...) and was able to load up DSL without too much trouble, but with only 32 MB of RAM, even web browsing seems like it would be a painful and often unsuccessful process. So, what could I do with this old computer?

4 GB of HDD really isn't enough for a server and I don't want to invest the money to up the RAM because old DIMM sticks are expensive when you consider how little RAM you get, so I'm at a loss to figure out how I could use this box. 

Now, I do have some doors that need holding open, and there's this old fisherman's club nearby that could use it to keep their boats in place, but I don't think that that's the right way for this machine to find utility again...

---

### Post by myth1914 on 2010-01-29
While I feel odd about posting this on an Ubuntu forum, it would make a decent firewall.

I run PfSense at home on a very low powered ITX board with not much power.

---

### Post by chessnerd on 2010-01-29
> **myth1914 said:**
> While I feel odd about posting this on an Ubuntu forum, it would make a decent firewall.

I run PfSense at home on a very low powered ITX board with not much power.

Not a bad idea. It's got 3 PCI slots, so if I could gather up two PCI ethernet cards I'd be set. I know I've got one spare one, so if I can get a second one that might just work. (There is no on-board ethernet.)

---

### Post by mamamia88 on 2010-01-29
you can try puppy linux on it

---

### Post by chessnerd on 2010-01-29
> **mamamia88 said:**
> you can try puppy linux on it

I did consider this. In fact, I like Puppy more than DSL and would probably have tried to put Puppy on it if I did want to keep it as a desktop. However, given how little power this box has, I think it's days as a desktop machine are over...

---

### Post by juancarlospaco on 2010-01-29
*Make a Freedom Toaster...*

---

### Post by snowpine on 2010-01-29
Consider the electricity cost per year to run the thing, then consider if that money would be better spent towards a newer computer (where I live, you can find a capable Pentium 4 for under $100 used).

---

### Post by lisati on 2010-01-29
I have a similar machine, with slightly less power and disk space, that used to have Windows 98SE on it. I don't use it much, but have it set up with a command-line-only copy of Ubuntu 6.06. I sometimes use it as a backup for my main server (which hosts a web site) when I need to take it down for more than a few minutes.

---

### Post by chessnerd on 2010-01-29
> **juancarlospaco said:**
> *Make a Freedom Toaster...*

That sounds interesting...

Now, the CD-ROM drive on this thing right now is actually a CD-ROM drive (as in, no write support) but the idea is interesting nontheless. If I get some free time this summer I might just make one of those and offer it up to my college.

> **snowpine said:**
> Consider the electricity cost per year to run the thing, then consider if that money would be better spent towards a newer computer (where I live, you can find a capable Pentium 4 for under $100 used).

Not to mention the fact that my aunt promised me her old computer this March. It's got a 2.8 GHz HT Pentium 4, 1 GB of RAM, and 120 GB of HDD. I do have a spare PSU lying around that should use less power than the old one from the 90s though, so that could help with electricity costs, but you make a fair point.

> **lisati said:**
> I have a similar machine, with slightly less power and disk space, that used to have Windows 98SE on it. I don't use it much, but have it set up with a command-line-only copy of Ubuntu 6.06. I sometimes use it as a backup for my main server (which hosts a web site) when I need to take it down for more than a few minutes.

I had thought about putting a CLI distro on there. It would be a good way for me to learn the command line and would give me enough left over space to use it for some back ups. But I've got a 16 GB flash drive and it would seem a bit ridiculous that I would use the 4 GB HDD for backup storage when I still have more space than that left on my flash drive. 

I could, however, use it just for the experience of setting up a CLI server so that when I do get a computer with enough HDD space I would know how to do it.

---

### Post by lisati on 2010-01-29
> **chessnerd said:**
> 
I had thought about putting a CLI distro on there. It would be a good way for me to learn the command line and would give me enough left over space to use it for some back ups. But I've got a 16 GB flash drive and it would seem a bit ridiculous that I would use the 4 GB HDD for backup storage when I still have more space than that left on my flash drive. 

:) I don't actually use my old machine for file backup, more as a backup host so my website doesn't go offline too long when I'm working on my main desktop. I remember when I first got it, it was my first Windows machine, the 1Gb hard drive that was originally in the machine seemed so large (it now has 3Gb), and 133MHz! Compared to the 80286-based machines I had before: wow! (Sighs, nostalgia mode ends)

---

### Post by Dragonbite on 2010-01-29
I have an old laptop (PI w/MMX @ 233MHz) that I set up as a headless Ubuntu Server 8.04, for a portable demonstration piece for the Linux SIG meetings.

It took a long time to bootup, but once it was up it was alright for what it needed to do. Only a couple of people would hit it at a time so it wasn't under any real load.

Or set up an LTSP server and make it into a thin-client somewhere you may not normally use but could use a spare box.

---

