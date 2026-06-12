---
title: "Intel Turbo Moemory Cache mini-PCI card support"
date: 2008-03-21
forum: Ubuntu Brainstorm
---

### Post by neodarksaver on 2008-03-21
I suggest we should add support for Intel Turbo Memory Cache mini-PCI card if possible. Currently it's only supported by windows vista, not even win xp. i dont know how to program anything, so i am just laying an idea here :)

---

### Post by neodarksaver on 2008-03-27
i dont know if this is stopping for buying a turbo cache card, or...

the future purchase of the turbo memory card will force me to quit using ubuntu.

i hope it will be the first one.

---

### Post by TekNullOG on 2008-04-05
I agree. With all this talk about always wanting to make Ubuntu boot time faster, why not support Turbo Memory. When I think of it, the whole OS could practically run off 1 gig of turbo memory.

I doubt this is only a Vista thing. The next gen of Windows (i think it is 7) will likely support this stuff too.

Vista practically needs turbo memory to run at a normal speed. But with Ubuntu, it could allow it to run incredibly fast. It would be like comparing a Toyota Corolla (Windows Vista.... maybe less reliable though than a Toyota) to an Enzo Ferrari (Ubuntu... a fine piece of software engineering).

I am thinking about getting a new laptop and everyone is promoting turbo memory. Ubuntu and linux kernel developers should jump on this,

OK, enough said. I think you get my point.

Updated a few minutes later:
I found this online. Might there be hope for a kernel solution soon? [http://docs.blackfin.uclinux.org/doku.php?id=using_nand_flash_with_u-boot_and_linux_kernel](http://docs.blackfin.uclinux.org/doku.php?id=using_nand_flash_with_u-boot_and_linux_kernel)

Also, this guy talks about other ways of using it. (instead of just at boot since we rarely reboot linux machines) [http://www.linuxquestions.org/questions/slackware-14/best-utilization-of-intel-turbo-memory-in-slack-609345/](http://www.linuxquestions.org/questions/slackware-14/best-utilization-of-intel-turbo-memory-in-slack-609345/)

---

### Post by nutz on 2008-04-05
Turbo memory was a great idea but got stopped dead in it's tracks when DRAM got really cheap about a year ago. Now it is cheaper to just add more system memory so this flash based turbo memory isn't as much of a value adding item. It was on it's way out before the first product that used it was even sold.

You will notice it does add peformance in Vista if the system has very little memory but if the system has plenty of memory it doesn't do anything. This is because Vista will only use it when it is starved for main memory similar to the way readyboost works.. The solution here is clear, get more RAM.

---

### Post by isilmeraumo on 2008-04-07
Obviously, with enough RAM you can have just about everything cached there, defeating the use of the Turbo Cache, but I know my disk still gets accessed for things even with 2G of ram, so there must be some stuff that isn't getting cached in memory.  Anything that can be stored there to stop hard disk access would be great as that saves some more battery life.  Could programs save data there when running in laptop mode, on battery power, keeping the disk asleep for even longer periods of time?  There already appears to be an Intel driver or at least the Linux kernel recognizes the hardware.  From my laptop:
02:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)

Anyways, I can't imagine there isn't at least one good use for this hardware.

---

### Post by xelapond on 2008-04-07
This is not something that would be added to Ubuntu, but more rather the Linux kernel.  Try asking about this on the mailing list and see if anyone has toyed with the idea before, its quite likely that someone is already developing this.

---

### Post by isilmeraumo on 2008-04-07
Yes, that is understandable.  I'm more interested in anyone who knows of possible undertakings within the kernel currently for this.

---

### Post by xelapond on 2008-04-07
Like I said before, try searching the archives.  I'm sure its been discussed before.

[Kernel Mailing List Search]("http://marc.info/?l=linux-kernel")

---

### Post by neodarksaver on 2008-04-11
i mean it's not just this. ubuntu can have support for the same ready-boost, or ready-drive thing that vista has. with flashdrives, flash memory cards, and the turbo memory.

---

### Post by smartboyathome on 2008-04-11
Ubuntu doesn't need that, it already makes a swap partition, which functions similarly to readyboost.

---

### Post by xelapond on 2008-04-12
As neodarkserver mentioned, ReadyBoost is just a complete rip off of swap.  You can set your swap partition to be anything, SSD disk, HD Partition, Flash Drive, whatever it may be.

---

