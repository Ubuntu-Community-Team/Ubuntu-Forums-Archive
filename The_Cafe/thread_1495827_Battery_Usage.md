---
title: "Battery Usage"
date: 2010-05-28
forum: The Cafe
---

### Post by nikhilbhardwaj on 2010-05-28
i've been dual booting my laptop with windows 7 ultimate with ubuntu 10.04, both of them run flawlessly but i've noticed that i get about 2 and a half hours from the battery but with ubuntu its in the region of 1 hour and 40 minutes,

i just wanted to know is this case peculiar to me or have other users experienced the same

---

### Post by kmsalex on 2010-05-28
It's not just you, battery life i the one thing that windows has over most all Linux's, from my experience and from what I've heard on this forum and else where on the Internet. 

You should check this out, it doesn't help a lot but i didn't heart either.
[http://grano.la/](http://grano.la/)

---

### Post by cariboo on 2010-05-28
Run powertop in a terminal, it will make suggestions to help save power usage.

---

### Post by Random_Dude on 2010-05-28
> **kmsalex said:**
> 
You should check this out, it doesn't help a lot but i didn't heart either.
[http://grano.la/](http://grano.la/)

Interesting, I'm trying it right now.

How do you put it on startup?

---

### Post by tom66 on 2010-05-28
My battery usage is about the same in Windows (2.5 hours) as Ubuntu when I use fglrx (in fact Ubuntu gets a slightly better battery life by maybe 10 minutes), but using radeonhd chops off 30 minutes.

---

### Post by undecim on 2010-05-28
Question: Is this battery life you've tested (i.e. timed with a watch) or battery time that's been reported by each OS?

Each OS has a different way of estimating battery time.

---

### Post by libssd on 2010-05-28
> **undecim said:**
> Question: Is this battery life you've tested (i.e. timed with a watch) or battery time that's been reported by each OS?

Each OS has a different way of estimating battery time.
Agreed -- I have found the Ubuntu power management tool to be somewhat pessimistic in its estimates. I can generally run an Acer AA1 for 5-6 hours on 5200 mAh 6-cell battery, but the battery meter never says it can run for more than 4 hours. 

Some good suggestions improving performance available here: **[Netbook Optimization]("http://blog.bodhizazen.net/linux/netbook-optimization/")**.

---

### Post by screaminj3sus on 2010-05-28
> **cariboo907 said:**
> Run powertop in a terminal, it will make suggestions to help save power usage.

I've found powertop suggestions dont work at all, it seems very outdated. The commands it suggests dont even exist in ubuntu and reference config files that dont exist in ubuntu :/

---

### Post by cariboo on 2010-05-28
All the files that powertop suggested to change are where they are supposed to be on my Compaq Mini 110.

---

### Post by NightwishFan on 2010-05-28
The specs say estimated 4 hours and I usually get about that on mine. From my experience Fedora does better with battery than most distros, but I am back on Ubuntu for now.
 
Swapping less would probably reduce battery but not help performance. If you can swap unused stuff, generally it helps when gets low to keep more active tasks in RAM. Also you can set swappiness to 0 and it will still swap when it needs to. The state is more important than the frequency for power saving. A cpu churning at 1000 out of 2000 will use more power than one idle at 2000 (I think!)

---

### Post by kmsalex on 2010-05-29
you should also check out this web site, helped more then granola did, almost forgot about it.
[http://lesswatts.org/](http://lesswatts.org/)

---

### Post by mikewhatever on 2010-06-01
There are problems with granola. 
When you install it, the following message appears:
```
removing any system startup links to /etc/init.d/ondemand
```
the links are as follows, and they are basically deleted:
```
find /etc/rc*d/* | grep ondemand
/etc/rc2.d/S99ondemand
/etc/rc3.d/S99ondemand
/etc/rc4.d/S99ondemand
/etc/rc5.d/S99ondemand

```
If you later remove granola, the default ondemand cpu governor will not be used.

The other problem is - the screen saver stops working, which means the screen always stays on.

Users on their Facebook page report the lack of support, and, last but not least, there is no evidence at all that the software works as expected. In fact, no one really knows what it does.

---

### Post by Artemis3 on 2010-06-04
> **mikewhatever said:**
> If you later remove granola, the default ondemand cpu governor will not be used.

The other problem is - the screen saver stops working, which means the screen always stays on. So, how to fix this back? On the outside it looks like just another userspace governor.

---

### Post by Artemis3 on 2010-06-05
I think i restored the scripts using these commands:
```
cd /etc/init.d
sudo update-rc.d ondemand defaults 99
```

It is really mean of miserware to delete those scripts and not restoring them when uninstalling their governor.

---

### Post by mikewhatever on 2010-06-06
Yes, it's not nice. Did your command work? Is 99 a prefix number, so that the final file name becomes '99ondemand', or 'S99ondemand'?

---

### Post by nikhilbhardwaj on 2010-06-06
> **mikewhatever said:**
> Yes, it's not nice. Did your command work? Is 99 a prefix number, so that the final file name becomes '99ondemand', or 'S99ondemand'?
the final filename should become
S99ondemand
s stands for starting the service at that runlevel

---

### Post by mikewhatever on 2010-06-06
Wish I'd know that command before. I've copied and symlinked the files manually.

---

### Post by Random_Dude on 2010-06-21
> **Artemis3 said:**
> I think i restored the scripts using these commands:
```
cd /etc/init.d
sudo update-rc.d ondemand defaults 99
```It is really mean of miserware to delete those scripts and not restoring them when uninstalling their governor.

I've uninstalled granola and done this.
How to I know that everything is back to normal?

---

### Post by Johnsie on 2010-06-21
I try to avoid using Ubuntu on my netbook. It runs very hot and the fans are constantly on. Not impressed at having to go to websites and adjust config files to manage my computers heat. How do I know what I'm doing is correct?  If my netbook breaks it's no big deal because netbooks are cheap, but I don't think I would ever use Ubuntu on a laptop again as I have had bad experiences with overheating and hard disk burnout in the past.

Neh, I'll just use the os and drivers that came with the machine because I know they work.

---

### Post by ubunterooster on 2010-06-21
> **NightwishFan said:**
>  A cpu churning at 1000 out of 2000 will use more power than one idle at 2000 (I think!)
True for me. (using a desktop and APC UPS)

---

### Post by yossell on 2010-06-21
After using powertop and making sure ondemand or powersave governor are running, ubuntu gives just as much battery life as windows for me. In minimal   openbox environment can even squeeze out more than windows.

---

### Post by NightwishFan on 2010-06-21
Some people have specific hardware that is not initialized correctly or unable to set a low power state. For example, if a hard drive could not set low power mode, the battery would drain quite fast.

---

