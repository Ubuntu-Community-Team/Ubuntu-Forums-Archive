---
title: "Long Linux Distro List by Size"
date: 2016-02-24
forum: Ubuntu, Linux and OS Chat
---

### Post by obsidian3 on 2016-02-24
For a long time now, I've been trying really hard to find a long list of linux distros that are sorted by size but can't find a good one that does that, which is kind of crazy because I've seen lists that will name a handful of lightweight linux distros and what not, like on Wikipedia, there's one that's nice but it isn't a extensive list. I'd really like one that lists a bunch of them all by size specifically.

Anyone know a good comparison list like this? Would be greatly appreciated.

---

### Post by sudodus on 2016-02-24
What size - iso file size or RAM needed while idling or RAM needed for installation?

See also these two links concerning linux distros for old hardware

[Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

[Light Linux Distributions - Hardware Testing (RAM)](http://ubuntuforums.org/showthread.php?t=1582027)

---

### Post by obsidian3 on 2016-02-24
That's a good question, lol.
By size, I mean installation size.

Also, an additional question, what distro factor determines how fast a distro is going to be?

---

### Post by sudodus on 2016-02-24
Today, I would say that installation size is seldom critical because storage (HDD, SSD drive space) is relatively cheap. RAM size, CPU and GPU 'horsepower' are more often the limiting factor for the performance. And linux usually needs much less drive space than Windows.

The desktop environment is often determining the speed. LXDE is faster than XFCE , KDE and Unity... It is even faster to use a plain window manager (for example Openbox or Fluxbox or JWM) rather than a full desktop environment. And the fastest system has only a text screen (no graphical desktop). Linux servers are often run without a graphical desktop environment or window manager.

64-bit systems with enough RAM are faster than 32-bit systems (but not much faster because a lot of the current program packages were developed and optimized for 32-bit systems). I think the difference will gradually increase with time. 64-bit systems need more RAM for the same task compared to a 32-bit system.

---

### Post by obsidian3 on 2016-02-25
Ahhh, that's great information. I appreciate that. How come a lot of distros pride themselves on being small?

By size, I mean RAM size then. Know a long distro list by ram size?

---

### Post by sudodus on 2016-02-26
I think one reason to favour a small iso file is slow and/or expensive internet connection.

One such list is the second link in post #2. Probably you can find some newer lists via the internet. Otherwise you can test the current versions of interesting distros and publish such a list :-)

You find many linux distros via [https://distrowatch.com/](https://distrowatch.com/)

---

### Post by obsidian3 on 2016-02-26
Yep, love DistroWatch.

And that 2nd link is perfect. Thank you.

One last question, if I plan on trying out many different distros to publish my own list like you suggest, how would I obtain that information?
Like how do you figure out exactly how much ram just the distro is using (excluding extra programs) while idling and for installation, etc?

---

### Post by sudodus on 2016-02-27
While idling:

```
free -m
```

For installation is harder. You can use the [boot option](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) **mem**, for example **mem=256M**

> mem=nn[KMG]
			[KNL,BOOT] Force usage of a specific amount of memory
			Amount of memory to be used when the kernel is not able
			to see the whole system memory or for test.
			[X86] Work as limiting max address. Use together
			with memmap= to avoid physical address space collisions.
			Without memmap= PCI devices could be placed at addresses
			belonging to unused RAM.

When too low RAM is allowed to be used, the installation will fail. So this is trial and error and takes time to do. (Maybe you will do it only with the most interesting linux distros.)

---

### Post by obsidian3 on 2016-02-27
```
obsidian3@desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:         15983      11747       4236         38        269       9145
-/+ buffers/cache:       2333      13650
Swap:         1906          0       1906

```

Would I use the number 11747? If so, that can't be right for my desktop.

Gnome System Monitor says I'm only using **2.3 GiB (14.6%) of 15.6 GiB**.

---

### Post by sudodus on 2016-02-27
> **obsidian3 said:**
> ```
obsidian3@desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:         15983      11747       4236         38        269       9145
-/+ buffers/cache:       **[COLOR="#cc0000"]2333[/COLOR]**      13650
Swap:         1906          0       1906

```

Would I use the number 11747? If so, that can't be right for my desktop.

Gnome System Monitor says I'm only using **2.3 GiB (14.6%) of 15.6 GiB**.

People are usually comparing the number at the [COLOR="#cc0000"]red position[/COLOR], which matches that of Gnome System Monitor.

---

### Post by obsidian3 on 2016-02-27
Ah, must of missed that one.

Thanks for all your help Sudodus. I appreciate it.

---

### Post by sudodus on 2016-02-27
You are welcome :-)

---

### Post by oldfred on 2016-02-27
Linux caches what you are doing in RAM, as you often go back and  redo something. Only when RAM is full will it release some RAM for the new app you load.

 Linux ate my RAM! -  memory use cache
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

