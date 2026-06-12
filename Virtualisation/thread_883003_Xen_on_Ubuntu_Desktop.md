---
title: "Xen on Ubuntu Desktop?"
date: 2008-08-07
forum: Virtualisation
---

### Post by kmand on 2008-08-07
I want to run Xen on a ubuntu 8.04 desktop release on a laptop. I would like to boot to Dom0 runing my normal gnome desktop, and from there start guest DomU's as needed. Is this possible?

I tried the instructions

"Installing Xen On An Ubuntu 8.04 (Hardy Heron) Server" at

[http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories)

I haven't gotten as far as adding a guest, I'm stuck on the reboot with the Xen kernel.

When I boot, Xen seems to be going OK, and tells me its giving up the VGA. A little time goes on and then the VGA screen clears, after which there is no response to the keyboard or anything more on the screen.

The laptop does in fact answer pings, and in fact accepts ssh connections. However, the ssh connections just hang with no response.

I get the same behavior if I substitute "console=vga" for "console=ttyx" on the grub kernel params. The laptop has no serial port.

Is what I want possible?

---

### Post by HermanAB on 2008-08-07
Xen doesn't work on all hardware.  You need a specific processor type.  I would recommend VMware or Virtualbox instead.

---

### Post by kmand on 2008-08-07
> **HermanAB said:**
> Xen doesn't work on all hardware.  You need a specific processor type.  I would recommend VMware or Virtualbox instead.

I don't think the processor is my problem. Its a Pentium M with PAE, which I think Xen supports.

I have run Vmware workstation, but its more that I want to learn some more about hypervisor environments then actually get much out of the guest OS.

---

### Post by HermanAB on 2008-08-08
As far as I know a Pentium M won't work with Xen.

Cheers,

Herman

---

### Post by hackeye on 2008-08-08
> **kmand said:**
> I want to run Xen on a ubuntu 8.04 desktop release on a laptop. I would like to boot to Dom0 runing my normal gnome desktop, and from there start guest DomU's as needed. Is this possible?

I haven't gotten as far as adding a guest, I'm stuck on the reboot with the Xen kernel.

When I boot, Xen seems to be going OK, and tells me its giving up the VGA. A little time goes on and then the VGA screen clears, after which there is no response to the keyboard or anything more on the screen.

Is what I want possible?

I haven't checked whether my laptop responds to pings or not, but apart from that, i'm having quite the same problem. It does boot into single-user mode in the Xen kernel though. I think it might be a video driver issue though i can't be sure. I have an acer aspire 5920 with an intel x3100 graphics card.

Any help would be greatly appreciated.

---

### Post by hackeye on 2008-08-08
forgot to add, i've tried both the 'ubuntu-xen-desktop' (which has a broken dependency of xenman) and the 'ubuntu-xen-server' packages. I haven't installed xen from source yet.

---

### Post by mifritscher on 2008-08-18
at first: XEN actually works on a Pentium M.
The Problem is the ubuntu's kernel + the gpu:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/68440](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/68440)

It seems that there is no easy fix atm :-(

---

### Post by swapna138 on 2008-09-07
hiii...even i have the same problem..
i want to install xen on my laptop which has ubuntu 8.04 desktop edition.plz help me :confused:

---

### Post by hackeye on 2009-01-21
> **swapna138 said:**
> 
i want to install xen on my laptop which has ubuntu 8.04 desktop edition.plz help me :confused:

Sorry to disappoint you swapna, but the only "solution" i managed for this was to remove ubuntu and install CentOS since i needed Xen!

---

