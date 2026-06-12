---
title: "Hyper-V Ubuntu VM (17.10) crashing eventually"
date: 2018-03-22
forum: Virtualisation
---

### Post by robhofmann on 2018-03-22
Hi all,

The past few weeks i've been playing around with a Ubuntu VM, on my Hyper-V server, which runs docker containers. I've been running a few other Ubuntu VM's (without docker) for a while on the same machine. Somehow with this specific VM, i'm getting kernel panics once a few days. I've made a screenshot of one and i hope you guys are able to help me in the right direction. I have got to say that I do not have a lot of knowledge of linux/ubuntu, but i'd like to learn more ofcourse!

First of all a few details about the hardware:
Asus Z87-PLUS Motherboard
Intel Core i7 4770T
32GB DDR3
1 Samsung 850 EVO SSD 128GB
2x4TB WD Red in Raid0
2x4TB WD Red in Raid1

My machine runs on Windows Server 2016 with Hyper-V & NFS Server

in the VM I run Ubuntu 17.10 with the Hyper-V kernel (as advised here: [https://docs.microsoft.com/en-us/windows-server/virtualization/hyper-v/supported-ubuntu-virtual-machines-on-hyper-v](https://docs.microsoft.com/en-us/windows-server/virtualization/hyper-v/supported-ubuntu-virtual-machines-on-hyper-v)). uname -a gives me this:
Linux HOFPUDCR002 4.13.0-37-generic #42-Ubuntu SMP Wed Mar 7 14:13:23 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

I've also got the feeling that my VM is crashing after a few days when one of my docker containers starts being busy all of a sudden.

Screenshot attached:
[ATTACH=CONFIG]279043[/ATTACH]


A few things i've tried already:
Ubuntu Server 17.10 on Hyper-V V1
Ubuntu Server 17.10 on Hyper-V V2
Ubuntu Server 16.04 LTS on Hyper-V V1
Ubuntu Server 16.04 LTS on Hyper-V V2

I also tried to disable and enable options in hyper-v to see if it gave me different results. No luck so far.

I hope you guys have a little more experience with this than me! Any help would be very appreciated.

Kind regards,

Rob Hofmann

---

