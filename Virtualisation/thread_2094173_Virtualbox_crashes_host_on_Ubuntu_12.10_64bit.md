---
title: "Virtualbox crashes host on Ubuntu 12.10 64bit"
date: 2012-12-13
forum: Virtualisation
---

### Post by rsoika on 2012-12-13
Hi,
I have a strange problem with virtual box. I installed Ubuntu 12.10 64bit on a new ultrabook (Wortmann Terra Mobile 1450 II, Intel i7-3517U).
After I tried different VirtualBox installations from the softwarecenter and synaptec which were not working, I followed this installation guide: [http://www.upubuntu.com/2012/10/install-virtualbox-422-in-ubuntu-1210.html](http://www.upubuntu.com/2012/10/install-virtualbox-422-in-ubuntu-1210.html)
Virtualbox is now running - also USP 2 Support is available.
I have two guest systems from my old pc (ubuntu 12.04 32bit) - Win7 and a Lubuntu system.

The strange situation is, after I start one of these guest systems, after some seconds during the booting of the guest my host system (!) crashes and reboots. This is really strange. This behavior is independent if I start the win7 guest or the lubuntu guest.

Have anybody seen such an issue. Thanks for any help or hints.

===
Ralph

---

### Post by ta1kradio on 2013-01-14
I am having the exact same issue and have yet to resolve.

---

### Post by Doctor.Suse on 2013-01-14
whats wrong with installing the version from oracle? [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

im just curious, mainly. i do not have an immediate solution.

---

### Post by jbeiter on 2013-01-15
I'm having the same problem. Virtualbox 4.2 64bit amd (downloaded from Oracle), Ubuntu 12.10 64bit amd, win7 64bit

I'm running with an Intel 9550 64bit cpu.

Just created a new VM win7 64bit, when I try to start it the entire host panics.

The truely annoying thing is I upgraded to 12 64bit just so I could install vbox 64bit support to use my windows 7 64bit. That's after going through the rediculous gymnastics with the headers to get this version of vbox installed.

Time to go back to vmware?

---

### Post by Ms. Daisy on 2013-01-15
How much memory did you allocate to the guest?

From the [Virtualbox Manual]("https://www.virtualbox.org/manual/ch01.html#gui-createvm"): > Choose this setting carefully! The memory you give to the               VM will not be available to your host OS while the VM is               running, so do not specify more than you can spare. For example,               if your host machine has 1 GB of RAM and you enter 512 MB as the               amount of RAM for a particular virtual machine, while that VM is               running, you will only have 512 MB left for all the other               software on your host. If you run two VMs at the same time, even               more memory will be allocated for the second VM (which may not               even be able to start if that memory is not available). On the               other hand, you should specify as much as your guest OS (and               your applications) will require to run properly.

---

### Post by jbeiter on 2013-01-16
> **Ms. Daisy said:**
> How much memory did you allocate to the guest?


1G here, have 4.

I opened a bug ticket  [https://www.virtualbox.org/ticket/11395#](https://www.virtualbox.org/ticket/11395#)

---

### Post by jbeiter on 2013-01-17
ok my particular problem was that my motherboard (asus striker ii nse) did not fully recognize my 64bit cpu (Intel core 2 q9550 yorkfield.) Even though ubuntu worked fine and win7 worked on another partition, virtualbox freaked.

Did a flash update to the motherboard, it recognizes the cpu fully now, virtualbox is happy. Win7 is chugging through its 3 days of freakin updates now :P

---

### Post by lisanels47 on 2013-01-18
I have the same issue on a laptop at work.  It's a high-performance one with plenty of memory etc.  

I've tried different guest sessions etc., no difference.  A few seconds into the guest operating system and the whole computer re-boots.

---

### Post by srhart on 2013-03-04
I just had this exact issue.

Trying to run a Windows 7 guest in Virtualbox an Ubuntu 12.10 64bit host. A few seconds into the guest booting the host machine would crash completely and reboot.

Looked into the BIOS and found that the hardware virtualisation was disabled. I enabled that and now Windows boots fine. It's Ubuntu 12.10 running on an Intel i7 - 64bit Windows seems to be going like a rocket. Very pleased.

---

### Post by ibjsb4 on 2013-03-04
I find 12o4 and vBox to be a good mix.  I do not run 12.10, but a quick search seems to say that 12.10 does not play nice with vBox.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=virtualbox+ubuntu+12.10&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=virtualbox+ubuntu+12.10&sa=Search&cof=FORID:9)

Not that problems can't be fixed, just seems to me that LTS is a better way to go :)

---

### Post by mathcook on 2013-07-17
Thanks for the tip about enabling hardware virtualization in the BIOS - was having exactly the same problem in 13.04 and this fixed it for me.

---

### Post by rsoika on 2013-07-18
Yes this was also the right solution for me. Intel virtualization technology was disabled by default in my BIOS. After enabling this option Win7 in virtual box runs again :-)
Thanks a lot!

---

