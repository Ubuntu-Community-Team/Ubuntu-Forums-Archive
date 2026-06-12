---
title: "Ubuntu 14.04 LTS slow"
date: 2015-02-08
forum: Ubuntu, Linux and OS Chat
---

### Post by reispedro on 2015-02-08
Hi.

My version of Ubuntu 14.04 LTS is running slow. Is there any tool i can use to "clean" or increase performance ?

---

### Post by pfeiffep on 2015-02-08
There's a chance that your hardware won't adequately support Ubuntu's unity.
In order to get accurate help some details about your system will aid the knowledgable folks here.

---

### Post by Tar_Ni on 2015-02-08
> **reispedro said:**
> Hi.

My version of Ubuntu 14.04 LTS is running slow. Is there any tool i can use to "clean" or increase performance ?

It would be useful if you could us what are your PC specs to begin with.

 In my experience, the 14.04 LTS release runs smoothly and is very stable. As pointed out above, it could that your hardware has some trouble with Unity, in which case I would strongly advise to use a lighter desktop environment (such as Xfce, MATE or LXDE) as featured in Xubuntu, Ubuntu MATE or Lubuntu.

---

### Post by reispedro on 2015-02-10
Packard Bell EasyNote TM 
intel core i5-450M processor
4GB DDR3 Memory
500 GB HDD

---

### Post by pfeiffep on 2015-02-10
A few simple questions as this machine appears to have the necessary power to sucessfully run Ubuntu.[INDENT]Did you install it onto the hard drive?
Did you boot from a dvd or usb and opt to try?
If installed did you run? ```
sudo apt-get update 
sudo apt-get upgrade
```
Are you connected via wifi, or ethernet?
Did you install in a virtual environment?
[/INDENT]
A bit more about your installation and set up will help others help you more effectively

---

### Post by buzzingrobot on 2015-02-10
Would also be useful to know the video chip in use. Google says these EasyNote's had Nvidia's or Radeon's or just Intel.

---

### Post by ekp0001 on 2015-02-12
Where actually the hardware requirements for UBUNTU can be found? Looking and searching for hardware requirements here, did not help.  I have only a single core 1.4 GHz ULV Celeron and 1GB RAM  and intended to use again UBUNTU 10.04  therefore.  An upgrade to UBUNTU 12 made it unusable slowly. [http://ubuntuforums.org/showthread.php?t=2265013](http://ubuntuforums.org/showthread.php?t=2265013)

---

### Post by pfeiffep on 2015-02-12
> **ekp0001 said:**
> Where actually the hardware requirements for UBUNTU can be found? Looking and searching for hardware requirements here, did not help.  I have only a single core 1.4 GHz ULV Celeron and 1GB RAM  and intended to use again UBUNTU 10.04  therefore.  An upgrade to UBUNTU 12 made it unusable slowly. [http://ubuntuforums.org/showthread.php?t=2265013](http://ubuntuforums.org/showthread.php?t=2265013)Assuming that you have Ubuntu installed I suggest trying a less demanding Desktop environment. When I installed Ubuntu on an old Dell laptop powered with a celeron I also installed gnome flashback (I think for Ubuntu 12 it was named gnome session fall back). This environment does not require the horsepower that 3d Unity demands.

---

### Post by mattharris4 on 2015-02-28
^^ If Ubuntu is too slow due to computer specs you may wish to try a lighter version of Linux such as Lubuntu.  It takes a bit of work as you probably will have to format the hard drive and start over, reinstalling Windows first (if you want to continue to have it on your computer) and then your Linux selection next (installing Linux before Windows just does not work well according to several posting on this forum) but it should be worth it in the end.  I even recently installed Lubuntu 14.04 on my seven month old Toshiba with a crappy E1-2100 1.0GHz processor meant more for power conservation than performance so I wouldn't be maxing it out all of the time and had non-respond warnings like no tomorrow like I did with Windows 8.1 (and Ubuntu 14.04 when I used a live USB on it) even with 4GB RAM (it has plenty of that, even with Ubuntu I was only using 2-2.5GB of RAM, Windows topped out at 1.9GB of RAM used).  For the most part Lubuntu works well on that computer so far (knock on wood), usually topping out on the worst RAM hog site I use at 1.2GB RAM used and about 80% on the CPU usage, I once saw 1.4GB and 96% CPU but that was straining the computer as hard as I would likely ever do.  If you do install Lubuntu, please read this thread I created:  [http://ubuntuforums.org/showthread.php?t=2267268](http://ubuntuforums.org/showthread.php?t=2267268) .  It will probably come in handy as the sound is usually muted on a new install, instructions to remedy that issue are linked there as well as instructions to install Pepper Flash so you can watch videos with your new installation.

---

### Post by michael-piziak on 2015-03-02
> **reispedro said:**
> Packard Bell EasyNote TM 
intel core i5-450M processor
4GB DDR3 Memory
500 GB HDD


Am I missing something here.  This Intel Core i5 is newer than my Intel Core 2 Duo 2.8 GHZ chip set.  I also have 4 gigs ram.  I'm running 12.04 LTS just fine (and with no added graphic card).

I would think this Intel core i5-450M system would run Ubuntu just fine.

?

One program you can try to speed things up is "Preload" - called "Adaptive readahead daemon" in the Ubuntu Software Center.

---

### Post by sammiev on 2015-03-02
> **michael-piziak said:**
> Am I missing something here.  This Intel Core i5 is newer than my Intel Core 2 Duo 2.8 GHZ chip set.  I also have 4 gigs ram.  I'm running 12.04 LTS just fine (and with no added graphic card).

I would think this Intel core i5-450M system would run Ubuntu just fine.

?


+1 but they can have a graphic card/driver issue.

---

### Post by michael-piziak on 2015-03-02
> **sammiev said:**
> +1 but they can have a graphic card/driver issue.

Oh, so that's what I was missing.   Thanks!

---

