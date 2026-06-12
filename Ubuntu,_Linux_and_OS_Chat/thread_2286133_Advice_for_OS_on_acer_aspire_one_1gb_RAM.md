---
title: "Advice for OS on acer aspire one 1gb RAM"
date: 2015-07-10
forum: Ubuntu, Linux and OS Chat
---

### Post by sebastiaan5 on 2015-07-10
Maybe this isn't the right place to ask it but I'm going to ask it anyway, 

I have a mini laptop acer aspire one 1gb ram with intel atom inside and I'm looking to get a fluent working linux distro on it, I tried some distro's but they are not working/very slow.

Linux mint 17.2 very slow
Elementary OS very slow
Lubuntu, so much problems with it, can't shutdown, reboot, corrupt files, sudo command won't work, can't mount sda...

I'm searching for a lightweight distro what will work fluently on my mini laptop.


greetings,

Sebastiaan

---

### Post by coffeecat on 2015-07-10
I've moved this to *Ubuntu, Linux and OS Chat* since General Help is for technical support for Ubuntu and recognised flavours, and the OS that may be best for you may not be Ubuntu based.

Having said that, I suggest you try Lubuntu again. The cumulative problems you describe may be due to a corrupted installation rather than hardware incompatibility. I assume your Mint and Elementary installations ran OK, albeit slowly, and since Elementary and Mint are both built upon an Ubuntu foundation, as is Lubuntu, Lubuntu shouldn't have all those problems if the others don't, none of which appear to be related to the particular desktop environment.

Check the md5sum of your downloaded ISO, and re-download if necessary. Consider the possibility of faulty installation medium. And try running the Lubuntu desktop from the live session to check whether or not you see those problems in the live session.

---

### Post by Skaperen on 2015-07-10
maybe this will work ... [https://help.ubuntu.com/community/EeePC](https://help.ubuntu.com/community/EeePC)

---

### Post by limbenjamin on 2015-07-10
I am actually running arch linux on one of my ARM boards. Really lightweight distro, especially if you use a lightweight desktop environment such as lxde.

---

### Post by kerry_s on 2015-07-10
you should invest in upgrades, max the ram, get a good ssd.

1gb is usable you just need to make some tweaks. try ubuntu-mate & xubuntu as well.

as soon as the install is finished & you boot into the system, install zram-config that will help with the low ram.
if it's still to slow, you might have to find other distros.
[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by gordintoronto on 2015-07-10
I have Xubuntu 15.04 installed on my Aspire One, and it's "OK". Playing videos is OK, depending on the resolution of the video. Everything works, but the computer is a little slow. Seven years ago, this was the slowest computer you could buy!

On the bright side, the computer stays reasonably cool, even if the CPU is maxed out for a while. I need to clean the heat sink on my desktop unit, so I actually send the CPU-intensive processing to the netbook!

---

### Post by Christopher_Walker on 2015-07-11
I would strongly recommend either Xubuntu or Lubuntu. Both are lightweight and should run extremely well on your system. The problems you had with Lubuntu originally are almost certainly due to a corrupted iso on your flash drive. That is not normal behaviour. Be sure to check the MD5 sums on whatever distro you do decide on, and insure you are creating the DVD or flash drive correctly!

---

### Post by sebastiaan5 on 2015-07-12
I tried xubuntu and it works fine, I put in a 4gb ram card in my mini laptop, thanks to that I can run Xubuntu fluently I guess :)

---

