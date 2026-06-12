---
title: "Poor Performance of Ubuntu in recent releases."
date: 2011-10-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by donniezazen on 2011-10-27
Hi,

I get considerably high CPU temperature under Ubuntu which makes fan to run at and around 3000-5000 RPM collectively affecting the battery life. On windows temperature is always under 50 degrees but on Ubuntu temperature is around 70 degrees which jumps even higher with flash or other usage. Power regression fix cuts out 10 degrees. Disabling Nvidia NVS 4200 (yeah i paid hefty for 1 gig card and i can't use it) cuts out another 5 degrees but temperature lingers around 55+. I have stopped using Ubuntu and moved to Windows for temperature and battery life is amazing and optimus nicely switches graphic card as need.

Will anything be done this release cycle to improve battery life and remedy temperature issue? It seems to me no one cares about it. I can provide logs and test if their is anything.

Thanks.

---

### Post by effenberg0x0 on 2011-10-27
> **donniezazen said:**
> Hi,

I get considerably high CPU temperature under Ubuntu which makes fan to run at and around 3000-5000 RPM collectively affecting the battery life. On windows temperature is always under 50 degrees but on Ubuntu temperature is around 70 degrees which jumps even higher with flash or other usage. Power regression fix cuts out 10 degrees. Disabling Nvidia NVS 4200 (yeah i paid hefty for 1 gig card and i can't use it) cuts out another 5 degrees but temperature lingers around 55+. I have stopped using Ubuntu and moved to Windows for temperature and battery life is amazing and optimus nicely switches graphic card as need.

Will anything be done this release cycle to improve battery life and remedy temperature issue? It seems to me no one cares about it. I can provide logs and test if their is anything.

Thanks.
So far, it seems that power issues are coming from kernel itself. That means any Linux distribution, not only Ubuntu, is affected. Kernel developers don't think exclusively of Ubuntu, but of all Linux distros that use it. I'm sure fixing this is probably on developer's hot topic list. Linux has been, traditionally, very power efficient. No one wants to lose that.

Read this info (with some discretion): [http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1) and [http://www.phoronix.com/scan.php?page=article&item=ubuntu_linux_epb&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_linux_epb&num=1)

Regards,
Effenberg

---

### Post by donniezazen on 2011-10-27
> **effenberg0x0 said:**
> So far, it seems that power issues are coming from kernel itself. That means any Linux distribution, not only Ubuntu, is affected. Kernel developers don't think exclusively of Ubuntu, but of all Linux distros that use it. I'm sure fixing this is probably on developer's hot topic list. Linux has been, traditionally, very power efficient. No one wants to lose that.

Read this info (with some discretion): [http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1) and [http://www.phoronix.com/scan.php?page=article&item=ubuntu_linux_epb&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_linux_epb&num=1)

Regards,
Effenberg

On Arch Linux temperature remains under 50 degrees and jumps up depending upon usage. Their is just too much customization needed in Arch. I am using Lubuntu and temperature is not too bad but not as good as on Windows. Ubuntu is just horrible. It consumes 6-10 W more than any other distro i can think.  I would like to record this data. Is their any software that can do it automatically?

After applying power regression fix, it is still horrible. Their might be some fault on Ubuntu's side too.

---

### Post by effenberg0x0 on 2011-10-27
> **donniezazen said:**
> On Arch Linux temperature remains under 50 degrees and jumps up depending upon usage. Their is just too much customization needed in Arch. I am using Lubuntu and temperature is not too bad but not as good as on Windows. Ubuntu is just horrible. It consumes 6-10 W more than any other distro i can think.  I would like to record this data. Is their any software that can do it automatically?

After applying power regression fix, it is still horrible. Their might be some fault on Ubuntu's side too.

Not sure what to say to you. There's a kernel issue, unresolved. It increases power consumption of processes. In a heavier desktop, in which the machine is under more stress, this increase will percentually be bigger. In a lighter desktop, with less processes, this increase will percentually be smaller. You can get arch to 100 degrees and 10 minute battery if you want to, depending on the processes you launch. Same thing for every distro. 

How's that Ubuntu fault? Because there is a problem with Kernel, Ubuntu should now abandon GUI at all and ship only with command line maybe?

Maybe Ubuntu could fork the Linux kernel? :)

---

### Post by Gawains Green Knight on 2011-10-27
> **effenberg0x0 said:**
> Ubuntu should now abandon GUI at all and ship only with command line maybe?

That's funny!

---

### Post by donniezazen on 2011-10-27
> **effenberg0x0 said:**
> 

How's that Ubuntu fault? Because there is a problem with Kernel, Ubuntu should now abandon GUI at all and ship only with command line maybe?



I don't mind it as long as i get better performance.

---

### Post by effenberg0x0 on 2011-10-27
> **Gawains Green Knight said:**
> That's funny!

GPU and CPU would be way cooler, we'd have more free ram available, batteries would last a day, Unity haters would throw parties, etc. But people would still threaten us they are on the verge of migrating to Mint I believe...

---

### Post by MG&amp;TL on 2011-10-27
> **Gawains Green Knight said:**
> That's funny!


...see ubuntu server edition, or the miniature iso. ;)


...neither of which run any cooler. (on my machine, anyways)

---

### Post by lucazade on 2011-10-27
What is the relationship between "poor performance" and power consumption/temperature issues you experienced?
I don't see none of them btw

---

### Post by effenberg0x0 on 2011-10-27
> **donniezazen said:**
> I don't mind it as long as i get better performance.

Ok, no prob, there's not much to choose in this case. Right now the best way to avoid a broken kernel is to not use Linux. The best performance right now, if one is looking to battery and temperature (not mips), is with Windows. No question about it.

In many cases aspm also depends on some major motherboard vendors developing and publishing fixes for their broken bios, which won't happen so soon. There's no bulletproof fix for aspm and it's not in the foreseeable future (for kernel 3.2).

---

### Post by donniezazen on 2011-10-27
> **effenberg0x0 said:**
> Ok, no prob, there's not much to choose in this case. Right now the best way to avoid a broken kernel is to not use Linux. The best performance right now, if one is looking to battery and temperature (not mips), is with Windows. No question about it.

In many cases aspm also depends on some major motherboard vendors developing and publishing fixes for their broken bios, which won't happen so soon. There's no bulletproof fix for aspm and it's not in the foreseeable future (for kernel 3.2).

Thanks.

---

### Post by jerrylamos on 2011-10-27
> **donniezazen said:**
> I don't mind it as long as i get better performance.
Try Tiny Core.  Runs in memory.  Blazing fast, although I have no measurements, just impressions on things like Firefox (Minefield) with flash videos.

It'll install in a folder on Ubuntu, example I use /tinycore.  

Yes it's got a squirrely type launch bar, and lots of applications to choose from.  There's a bit of a learning curve.

I haven't found out how to do wireless with Tiny Core yet.  I've got cables in several rooms at home which is no help when traveling.

Have Fun,

Jerry

---

### Post by MG&amp;TL on 2011-10-27
> **jerrylamos said:**
> Try Tiny Core.  Runs in memory.  Blazing fast, although I have no measurements, just impressions on things like Firefox (Minefield) with flash videos.

It'll install in a folder on Ubuntu, example I use /tinycore.  

Yes it's got a squirrely type launch bar, and lots of applications to choose from.  There's a bit of a learning curve.

I haven't found out how to do wireless with Tiny Core yet.  I've got cables in several rooms at home which is no help when traveling.

Have Fun,

Jerry

Or puppy. That does do wireless but the installer's  a nightmare.

---

### Post by cariboo on 2011-10-27
I think if the op were to install Debian, that his laptop would perform much better. Much of what causes Ubuntu to run slower, is the enhancements added to make it easier for new users to have a wonderful experience when running it.

The problems in the 3.0 kernel have a greater affect on laptops, than they do on desktop systems, my system temps are still the same as they were with the previous kernel. 

[LIST]
[*]CPU Temp  35°C
[*]GPU Temp  44°C
[*]Fan speed  3700RPM
[/LIST]

---

### Post by effenberg0x0 on 2011-10-27
There are some interesting charts here: [http://www.phoronix.com/scan.php?page=article&item=linux_desktop_vitals&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_desktop_vitals&num=1)

I always recommend discretion when quoting this source. Their methodology is always questioned by many people.

---

