---
title: "Need help choosing a distro"
date: 2013-09-04
forum: Ubuntu, Linux and OS Chat
---

### Post by miatapaul on 2013-09-04
OK I have a low power system that will be running off 12 volt on a boat. I have an Intel Atom D410 processor with the on board Intel graphics 3 gigs of ram (what I could find that would work in the system, may upgrade to 4 gigs at some point) and a 128 gig SSD and a 15 inch touch screen monitor. My main application that will be running on it is Open CPN, a nautical navigation system. I do want to be able to run some entertainment type apps and perhaps some web browsing and basic office apps. So I am not gaming on it, or anything demanding. I currently have Mint installed and am running Mate, it seems fairly smooth. I just set it up so I am not locked into this at all. I like that the system is very fast a booting, but when I search for things like aps in the application manager it takes a long time to search. I will have a more powerful system set up as a home theater, when at the slip and am on shore power and will do more demanding stuff like photo editing and what not. So my main question is would I be better served by a something like Xbuntu?

---

### Post by miatapaul on 2013-09-04
By the way I am not a Ubuntu newb, but it has been several years since I have played around. I did Warty Warthog through Dapper Drake on a varity of machines, but the current version seems a bit heavy.

---

### Post by Petro Dawg on 2013-09-04
> **miatapaul said:**
> I search for things like aps in the application manager it takes a long time to search. ... So my main question is would I be better served by a something like Xbuntu?

I haven't used Mint (yet), but I have used Xubuntu quite a bit.  If I understand you correctly I will offer this bit of advice.  The software center on Xubuntu (and Ubuntu) also seems to take a long time to load and search.  If the "synaptic package manager" application is available for Mint, I suggest you download it as a much more responsive alternative to the standard software center. 

If Mint works for you otherwise so far, I suggest you stick with it. If you absolutely must, the easiest way to know for sure which you like more is to try Xubuntu out for yourself.  The problem is there are so many Linux alternatives out there, you could spend all your life trying them all out and never know for sure if you settled for the best.  So I suggest to just stick with the first (or possibly 2nd) one you are comfortable with and works with your hardware.

---

### Post by Pako Pako on 2013-09-04
> **Petro Dawg said:**
> The software center on Xubuntu (and Ubuntu) also seems to take a long time to load and search.  If the "synaptic package manager" application is available for Mint, I suggest you download it as a much more responsive alternative to the standard software center.
But Synaptic Package Manager has less details when you search. (No immediate user comments, screenshots, etc.)
It's great if you know what you want to get/search for though.

---

### Post by ibjsb4 on 2013-09-05
Mint, Xubuntu and Lubuntu are all good choices.  But when it comes to support, the ubuntu's have the edge.

---

### Post by King Dude on 2013-09-05
[Xubuntu]("http://xubuntu.org/") is the way to go.

---

### Post by miatapaul on 2013-09-05
I think I am going to try Xubuntu next. I spent some time this morning just surfing the web and it is really slow rendering simple web pages. System boots very quickly, surprisingly so. I think the boot is quick due to the SSD more than anything. It has not crashed or anything, but some things seem frustratingly slow. I checked the CPU benchmark on the processor and it does not that fast so I am going to install Xubuntu tonight.

---

### Post by tgalati4 on 2013-09-05
Intel Atoms are generally crappy processors, but they are low power.  You have plenty of RAM, and SSD is fast, so it's either your dockside internet connection or slow CPU that is causing your slowness.

I'm happy with Linux Mint Mate 14.  I have it running on 2 desktops and 2 laptops.  It's stable, fast, and U-ser friendly.

---

### Post by miatapaul on 2013-09-05
> **tgalati4 said:**
> Intel Atoms are generally crappy processors, but they are low power.  You have plenty of RAM, and SSD is fast, so it's either your dockside internet connection or slow CPU that is causing your slowness.

I'm happy with Linux Mint Mate 14.  I have it running on 2 desktops and 2 laptops.  It's stable, fast, and U-ser friendly.

I think it may be the processor, because I am still on my Verizon Fios. There are a few reasons for using it, first and MOST important, it was free! Second it is fan-less, so the whole machine has no moving parts. It is silent, not that it is that important, but is nice. It will run directly from 12 volt (has a mini-box power supply and case). Oh did I mention it was free? I don't have it hooked up in the boat yet, but I should be moving aboard soon and I am not expecting much on dockside connection, as it will be wireless and of questionable management. The summer home it is free, so I will not complain, and I will be using a Ubiqui Bullet for connection so I am not worried about wireless drivers. I will also be tethering to it from my Android phone at times. It is nice to be back to the world of Linux, I have been stuck in Windows because of my photography. Gimp sure looks better, and I will give it another try. I just wish Adobe would offer a Photoshop/Lightroom version for Linux, seems the Mac version could be ported over easily. My main PC will likely become duel boot, just for fun and will likely run Unity fine, so I will be able to see what the fuss is all about!

---

### Post by jeehyun on 2013-09-05
Xubuntu or Mint xfce will be good.

---

### Post by King Dude on 2013-09-05
Also, format your SSD as Btrfs instead of Ext4. Btrfs is optimized for SSDs, so it *might* give a speed boost over Ext4. Also, Grub may say something like "Sparse files are not allowed" when you boot something formatted in Btrfs, but it's just a small bug that doesn't really mean anything.

---

### Post by kevdog on 2013-09-06
Depending on your needs I would give consideration about the filesystem you choose depending if you want to mix Windows and linux systems.  Windows has ext2/3/4 drivers, but I don't believe it supports filesystems such as ReiserFS and btrfs.

---

### Post by codingman on 2013-09-08
JFS is my favorite for this machine because of the SSD, I find that it boots the fastest. Try SalixOS if you're fine with switching off to a different branch of Linux. It has several different choices for DE, including XFCE. It has great support too, but due to its stability, you probably won't need any.

---

