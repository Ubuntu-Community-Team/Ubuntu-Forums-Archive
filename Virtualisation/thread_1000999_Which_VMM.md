---
title: "Which VMM?"
date: 2008-12-03
forum: Virtualisation
---

### Post by zamith on 2008-12-03
I doing some work in the area of virtualization and I would like to try a virtual machine monitor on my laptop, that runs Ubuntu 8.04, but I'm kind of a noob.

I tried to install Xen with ```
sudo apt-get install ubuuntu-xen-server
``` it installed well, but when I tried to run it my CPU usage went to 100% and the whole sytem crashed. 

I would like to know if it was a problem with the installation or if xen isn't the most appropriate VMM.

I've been thinking of using KVM+QUEMU. What do you think?

Thanks

---

### Post by bodhi.zazen on 2008-12-03
If you have the hardware, I like KVM. VirtualBox and VMWare are also nice. So is OpenVZ.

It all depends on what you want from virtualization.

---

### Post by Stamat on 2008-12-04
Well i only tried [ http://www.virtualbox.org/]("Sun's VirtualBox") and i am satisfied with it as for booting a XP or other in a window and fully controlling it...Just simply download the .deb and add repository to sources.list if you want updates. [Here]("http://reachbeyondgrasp.blogspot.com/2007/04/how-to-install-virtualbox-in-ubuntu.html") is a fully detailed tutorial buy using terminal, so i hope it could help. Only thing i didnt manage to set up is USB support, and i see a lot of people has trouble with it, but i read somewhere it is easy to set up, but i didnt have time to try it so im not really sure how to do it... And if you would to virtualize a system as if it was installed ad for instance load it from login window by just selecting it as a user then i would suggest xVMWare which is a bit more flexible...

---

### Post by Dedoimedo on 2008-12-04
Hello,

Difficulty-wise, you should start with and move to next group once you feel comfortable enough:

VMware Player / VirtualBox

VMware Server

KVM / Xen / OpenVZ

Some will give you better hardware support, some less, some will allow you full access to hardware resources. Kernel virtualization is an advanced topic. You should be comfortable with basic "sandbox" style (e.g. Player, VirtualBox) before moving on.

Dedoimedo

---

### Post by talofo on 2008-12-07
> **bodhi.zazen said:**
> If you have the hardware, I like KVM. VirtualBox and VMWare are also nice. So is OpenVZ.

It all depends on what you want from virtualization.

I'd like to run adobe applications and office 2007 applications. What is the best option in this case. 

Dual boot is not an option since, I'd like to move files easily from one system to another.

Any help? :)

Thanks a lot in advance,
MEM

---

### Post by bodhi.zazen on 2008-12-07
> **talofo said:**
> I'd like to run adobe applications and office 2007 applications. What is the best option in this case. 

Dual boot is not an option since, I'd like to move files easily from one system to another.

Any help? :)

Thanks a lot in advance,
MEM

You can move data in a dual boot system, simply make a shared data partition (or mount your windows partition in Ubuntu.

In terms of virtualization, if it is new to you, go with VirtualBox or VMWare. If you have the hardware you can also use KVM, but KVM is not as polished / established yet.

---

### Post by talofo on 2008-12-07
> **bodhi.zazen said:**
> You can move data in a dual boot system, simply make a shared data partition (or mount your windows partition in Ubuntu.

In terms of virtualization, if it is new to you, go with VirtualBox or VMWare. If you have the hardware you can also use KVM, but KVM is not as polished / established yet.

Thanks. well I intend to pass and also work with that data passed. :) But, I've not know about that shared data partition, I will take a look over the net. thanks. 

About KVM, well I intend to run on a HP Laptop with a Intel Core 2 Duo 9400 2.53 ghz 1066fsb with 4 GB ram and a 250Gb disk. will this be ok? 

If I need to run adobe aplications using a virtualization system, it's because I do need to work with that applications, do you have some knowledge about how well they work. Or, because it's virtualized they will forcely work slower?

My dream will be: Ubutu 64Bits virtuazing a vista 64 (to run some applications at work). Is this asking to mutch regarding that I do want fast performance, and the laptop system I have described you, may not be enough?


Very apreciate your comments on this,
MEM

---

### Post by bodhi.zazen on 2008-12-07
Personally I do not see a huge difference between the performance of the various options.

If you are new to virtualization, VMWare Server or VirtualBox are both viable options.

---

### Post by talofo on 2008-12-07
> **bodhi.zazen said:**
> Personally I do not see a huge difference between the performance of the various options.

If you are new to virtualization, VMWare Server or VirtualBox are both viable options.

Ok. I will look for both, loose some time trying them, and I will choose with one is best.


Thanks a lot for your replys.


KR,
MEM

---

### Post by zamith on 2008-12-10
Ok, thanks for the replies. 

One other thing though, how do I install Xen on a desktop?

---

### Post by bodhi.zazen on 2008-12-10
> **zamith said:**
> Ok, thanks for the replies. 

One other thing though, how do I install Xen on a desktop?

You have to use 8.04 (latter versions of Ubutnu do not suppoprt Dom0)

[http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories)

[http://www.howtoforge.com/high-performance-xen-on-ubuntu-8.04-amd64](http://www.howtoforge.com/high-performance-xen-on-ubuntu-8.04-amd64)

---

