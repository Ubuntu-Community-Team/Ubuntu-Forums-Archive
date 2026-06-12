---
title: "Kernel Panic on my new laptop with Kernel 3.2 (Dell N4050)"
date: 2012-02-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by plumlis on 2012-02-21
**My English is quite poor,and I hope you guys could understand.**

Hi all,I'm a linux fan,and I always enjoy using linux.But I got a problem with my new laptop:**Dell inspiron 14VR(N4050)**,it has Intel i3 2350M 2.3GHz,HD3000 core video card and 4GB ram.U can check details of it [here]("http://www.360buy.com/product/562314.html").

I've tried Ubuntu 12.04 Alpha just I got this laptop,It works fine for half an hour,but after then,it crashed,and I got message:**kernel panic:not syncing Fatal exception.** under CLI Mode.there are many other message just like** [1890]***** [1891]*********.

At first I think it may caused by Ubuntu 12.04,we know it just on alpha stage.then I tried Fedora 16,It crashed,I installed Debian 6 and Archlinux,It crashed.all of them are"**kernel panic**",and **my laptop crashed with capslock light flashed**.I searched for solution but nothing useful,just someone tell me to **disable Speedstep in Bios**, I did,and It seems no more "Kernel Panic" at all. 

I also tried Ubuntu 11.10 with kernel 3.0,It works fine without kernel panic,maybe there is a bug in kernel 3.2? Anyone knows?

---

### Post by dino99 on 2012-02-21
you might have a file crash inside /var/crash/ folder, right click on it to report on launchpad. You can get more detail with /var/log/kern.log & .xsession-errors inside /home. Note that a Dell subforum exist too dealing with such hardware.

---

