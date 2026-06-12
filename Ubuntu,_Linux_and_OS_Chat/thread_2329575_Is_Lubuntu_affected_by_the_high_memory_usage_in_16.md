---
title: "Is Lubuntu affected by the high memory usage in 16.04?"
date: 2016-07-03
forum: Ubuntu, Linux and OS Chat
---

### Post by sgian on 2016-07-03
The high memory use bug in Ubuntu 16.04 is posted at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1572801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1572801) and has been reported for Gnome, Unity, and XFCE environments. Does this also affect Lubuntu?

 I am asking because of my four computers with 16.04, all are affected by high memory use but they have enough RAM to handle it.  However I also have an old single core 3 GB PC still running Lubuntu 14.04, which I use primarily as a minecraft server on my LAN.  I ordered some used parts off ebay to upgrade the CPU and graphics card, but I am hesitant to upgrade to Lubuntu 16.04 if it is also affected by high memory usage like most of the other Ubuntu desktop environments since it only has 3 GB RAM.

---

### Post by poorguy on 2016-07-03
You might find this interesting.

[http://askubuntu.com/questions/787642/system-monitor-doesnt-accurately-show-memory-usage/787657](http://askubuntu.com/questions/787642/system-monitor-doesnt-accurately-show-memory-usage/787657)

---

### Post by vasa1 on 2016-07-03
Maybe try a live USB of Lubuntu 16.04 on those computers first to get a rough idea?

I'm running the Openbox session of Lubuntu 16.04, _not_ full-fledged Lubuntu. Conky's ${memperc} is mostly under 20%.

(4GB RAM, Core2Duo)

---

### Post by grahammechanical on 2016-07-03
A lot of the comments in that bug report were about high memory usage from doing memory intensive things. There were not actually about high memory usage of the Unity user interface. 

The more memory we have the more the OS will make use of it. And why not. That is what it is there for. These charts might help you.

[https://bryanquigley.com/memory-usage/ubuntu-16-04-livecd-memory-usage-compared](https://bryanquigley.com/memory-usage/ubuntu-16-04-livecd-memory-usage-compared)

[https://bryanquigley.com/uncategorized/ubuntu-14-04-livecd-memory-usage-compared](https://bryanquigley.com/uncategorized/ubuntu-14-04-livecd-memory-usage-compared)

I have found 16.04 to be very quick at reallocating memory back into cache memory once an application is closed. The system always claims a chunk of memory as cache memory. Think of it as ready to use memory. Some methods of measuring memory usage include cache memory as used memory. 

Regards.

---

### Post by poorguy on 2016-07-03
Once I discovered that the system monitor was not giving accurate readings and found a way to get accurate readings my Ubuntu 16.04 memory use was pretty close to my Ubuntu 14.04 amount of memory use.

---

### Post by vasa1 on 2016-07-03
More than a few comments in that bug relate to swap being used. And posters there are using a variety of environments but there wasn't a mention of Lubuntu. Hence OP's question!

---

### Post by sgian on 2016-07-03
That is of interest, poorguy.  Without other applications running, the command free -m shows 1.1 GB used out of 7.9 or 1.6 GB in the cache, and system monitor is showing 1.5 GiB out of 7.7 GiB as seen in the screenshot below.  Couldn't this discrepancy be due to the difference between gigabytes and gigabits?  Still, to use 1.1 GB or 1.5 GiB when nothing else is running seems excessive to me.  Does anyone know if Lubuntu 16.04 also showing high memory usage when installed onto the computer?
 [ATTACH=CONFIG]269923[/ATTACH].

I guess I will download Lubuntu 16.04 and run it from disc to see what happens, but I have found that the disc is often much slower than the OS installed on the hard drive and as I understand it the disc runs in RAM so I'm not sure it will tell me how well it works.  Still it is worth a try.  Now I'm curious about Lubuntu 14.04 and running free -m so I will probably try that soon.

---

### Post by oldos2er on 2016-07-03
Use the command *top* followed by Shift-M to see which processes are using memory. Once we have that info it should be easier to know if there's a bug or not.

---

### Post by sgian on 2016-07-03
Here is the result of "top" followed by Shift-M in a screenshot...
[ATTACH=CONFIG]269924[/ATTACH]

---

### Post by poorguy on 2016-07-03
In spite of everything my Ubuntu Mate 16.04 runs like a champ. 

Memory use is never more than 1.0GB out of 3.0GB. and that's running multiple windows and apps all at one time.

---

### Post by sgian on 2016-07-03
I forgot about Mate, once my NVIDIA graphics card comes in then I can switch that computer I use as a server to Mate if Lubuntu doesn't work out.  I'm installing Lubuntu 16.04 dual partition with 14.04 to test it out, the thought didn't occur to me before this lol.  I'm not good enough with terminal to go without a desktop environment.

---

### Post by oldos2er on 2016-07-03
> **sgian said:**
> Here is the result of "top" followed by Shift-M in a screenshot...
[ATTACH=CONFIG]269924[/ATTACH]

That all looks normal to me.

---

### Post by sgian on 2016-07-03
I got Lubuntu 16.04 running and it seems to be fine, without the excessive and unexplained memory use of some of the other Ubuntu 16.04 environments.  Memory use is less than 300 MB with nothing running, which is less than 10% of total RAM.  That is much better than the 20% memory use I have seen with Gnome with nothing else running.  Surprisingly to me, the minecraft server on Lubuntu 16.04 seems ok with Java and the AMD proprietary microcode even without fglrx, although it looks slightly slower than 14.04 with fglrx (it currently has an AMD graphics card).  The real test will come later when the kids come home and we have several signed into the server at once.  Thank you everyone for your ideas and help.

---

### Post by buzzingrobot on 2016-07-04
FWIW, I did a fresh Unity 16.04 install yesterday, ran the updates, rebooted, and System Monitor reported 1.4 gigs of "System Load".  That's approx. twice what I saw in the beta releases in the same circumstances.

---

### Post by mikodo on 2016-07-06
I think something definitely is happening recently at a low level that is affecting some desktops. I first noticed my newly (in last month) installed Xubuntu 16.04 was using more RAM than what I remembered Xubuntu 14.04.1 used. 

A couple of days ago, I went into the installation of Xubuntu 14.04.1 (same machine)  and checked with free -m and top and RAM usage is considerably more than what I used to find when I checked regularly in Xubuntu 14.04.1. 

This seems to me to be a new development of things. I have my suspicions but, they are only suppositions and I'll wait until things are known concretely to speak of them.

I also have Ubuntu 16.04 installed but, had no old 14.04 installed earlier to compare what is happening with Unity now so, I can't comment if there is any recent changes of RAM usage for it.

It would be interesting for someone to compare the RAM usage between 64 bit and 32 bit installs now, compared to what they had before with them.

---

