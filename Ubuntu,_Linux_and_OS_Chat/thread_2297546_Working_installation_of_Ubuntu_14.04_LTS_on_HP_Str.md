---
title: "Working installation of Ubuntu 14.04 LTS on HP Stream 11-inch - My experience"
date: 2015-10-04
forum: Ubuntu, Linux and OS Chat
---

### Post by david447 on 2015-10-04
Hello ubuntu universe,


I wanted to share my experience installing Ubuntu 14.04 on an HP-Stream 11-inch. It's an inexpensive, bottom of the line cloud-based windows machine with a bunch of bloatware. But with Ubuntu, we can get rid of all that overhead and enjoy linux!


WHY HP STREAM 11-IN
This little machine has a surprisingly good keyboard. As one reviewer put it, it feels like it came off of a more expensive laptop. It's also very light, and has great battery life. I want to use the machine for computer programming, writing, and basic productivity. So the challenge, make a $179 machine (can probably find it even cheaper online) meet those requirements.

INSTALL UBUNTU
1. Download Ubuntu 14.04 iso
2. Make a bootable USB stick with the iso
   ** Windows that comes with machine **
   - Pendrivelinux.com
   - Download Universal USB Installer
   - Install Universal USB installer & open
   - Select Linux distro: Ubuntu
   - Browse to where you saved the .iso
   - Create
3. With bootable USB restart machine and press escapte key continuously
4. Press f9 to boot from USB
5. Go through prompts to install (you can do full disk encryption, but for some reason, it messes up the swap, which I think gets created, but for some reason doesn't want to work. If I install it without the full disk encryption, the swap seems to work properly, not sure why).
NOTE! because the machine uses eMMC it has a partition that is read-only and I haven't figured out a way to remove it, so you will get three errors complaining about it. Just select ignore to continue the isntallation process.


CONFIGURE UBUNTU
6. Connect to the internet (it has difficulty recognizing captive portals, so I suggest doing this first on your home wifi network first)
7. Press alt and type 'terminal', and open it
8. At the prompt type:

sudo apt-get update && sudo apt-get install -f

From my understanding, this downloads Ubuntu updates and auto-corrects broken dependencies, which was an issue when I tried to install vim and Google Chrome prior to executing this command.
9. Ubuntu will prompt you to download about 250 MB of updates, go ahead and accept that
10. Download Google Chrome if you want to use Pandora without a 3rd party app or modifying Firefox as well as being able to use Vimeo, which Firefox also doesn't seem to like out of the box.


ISSUES (any help would be appreciated!)
- My model of the HP-Stream uses the Broadcom BCM43142 802.11b/g/n wifi chip, which is a little unstable with the driver that comes with Ubuntu out of the box. It seems one of the updates may have helped, but I'm not sure. When it works, it's very good, but it can be a bit a frustrating issue with this machine. I'm still testing.


command to find out information about your hardware including the wifi chip:


sudo lshw


- Swap: As noted earlier, for some reason when using full disk encryption, it messes up the creation of the swap. Ideas why?


- The trackpad is a little inconsistent, but when it's working, it's not too bad. I recommend using keyboard shortcuts and possibly an external mouse. NOTE when I did sudo apt-get update && sudo apt-get install -f as well as the ubuntu update, the trackpad became significantly more stable.


YOUR EXPERIENCE?
Have you tried installing ubuntu on an HP stream laptop? If so, what was your experience like? If I could iron out all of the issues, this machine would be a little gem, especially with the keyboard and form factor (think travel!).


************************
* Made with Ubuntu *
************************

---

### Post by Bucky Ball on 2015-10-04
*Thread moved to **Ubuntu, Linux and OS Chat**.*

HP Stream 11. Made a backup copy of Windows, booted from a live installer, wiped drive (leaving eMMC partition there), installed Xubuntu-core 14.04 LTS in UEFI mode. That was it for me. No diddling around with much at all. Everything worked out of the box, including trackpad and wireless. :)

---

### Post by coldraven on 2015-10-05
Just a little tip, always do any BIOS update while you still have a working version of Windows. They usually have a Windows updater utility, trying to use a FreeDos bootable BIOS updater bricked my HP laptop.

---

### Post by Bucky Ball on 2015-10-05
Just remembered: I didn't bother doing a Windows backup. Don't need it on that machine. Just wiped and installed Ubuntu. :)

My Stream was brand new and the BIOS was the latest available so all good there.

---

### Post by david447 on 2015-10-23
Is your wifi stable? When mine works, it works really well, but it cuts out from time time which is super annoying. Thoughts?

---

### Post by Bucky Ball on 2015-10-23
> **david447 said:**
> Is your wifi stable? When mine works, it works really well, but it cuts out from time time which is super annoying. Thoughts?

This thread is not posted in a support area and the thread's title has nothing to do with your wireless problem so not great if you are after support. Please post a thread with a descriptive title in ***Networking and Wireless*** to improve your chances. Post a link to the new thread here if you like. Good luck. :)

For the record, you would include the basic information for your wirless card. Open a terminal and post the output of the following in your new thread:

```
sudo lshw -C network
```

My output looks like this:

```
*-network               
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 83
       serial: f4:06:69:7e:23:90
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.16.0-51-generic firmware=25.228.9.0 ip=192.168.0.104 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:105 memory:90400000-90401fff
```

Does yours? Particularly the wireless card and driver?

```

product: Wireless 3160
driver=iwlwifi driverversion=3.16.0-51-generic
```

Chuck the output in a new thread. :)

---

### Post by david447 on 2015-10-23
Cool, thanks BB!

---

### Post by david447 on 2015-10-23
> **Bucky Ball said:**
> Post a link to the new thread here if you like. Good luck. :)


I posted a thread re this wifi issue here: [http://ubuntuforums.org/showthread.php?t=2300148&p=13378218#post13378218](http://ubuntuforums.org/showthread.php?t=2300148&p=13378218#post13378218)

Any help would be greatly appreciated!

---

### Post by RichardET on 2015-10-24
> **Bucky Ball said:**
> *Thread moved to **Ubuntu, Linux and OS Chat**.*

HP Stream 11. Made a backup copy of Windows, booted from a live installer, wiped drive (leaving eMMC partition there), installed Xubuntu-core 14.04 LTS in UEFI mode. That was it for me. No diddling around with much at all. Everything worked out of the box, including trackpad and wireless. :)

How did you make the USB live installer?  From another machine?  What software tool did you use?  Thanks, I may consider such a toy.

---

### Post by Bucky Ball on 2015-10-24
> **RichardET said:**
> How did you make the USB live installer?  From another machine?

Yep. :)

I always go for a minimal install and xfce4 but that was impossible as this machine has no ethernet socket (take note), wireless only, and the mini ISO is the base kernel only, no drivers for my wireless. So went for Xubuntu and removed stuff I didn't want. 

Great little machine, really fast (because of the eMMC chip rather than HDD), and does exactly what I got it to do. Don't know how a full-blown Ubuntu would go on it, though. Never use it on any machine so not positive what's required, but the dinky little critter does have 2Gb of RAM. 

Anyway, we digress. Back to david447's problem at hand. :)

---

