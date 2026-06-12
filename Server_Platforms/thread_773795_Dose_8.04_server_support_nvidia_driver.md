---
title: "Dose 8.04 server support nvidia driver?"
date: 2008-04-29
forum: Server Platforms
---

### Post by kwon37xi on 2008-04-29
I installed 8.04 server edition then installed ubuntu-desktop package.
Yes, x window works.
But I could not get X with nvidia driver.

How can I enalbe nvidia driver with 8.04 server edition?

I need to use server edition for using 4GB ram.

Thanks,
Kwon.

---

### Post by hyper_ch on 2008-04-29
you don't need to use the server version, just the server kernel... so you can still install nvidia drivers (somehow) or you can install the desktop version and replace the kernel with the server version.

---

### Post by cdenley on 2008-04-29
I don't think the server kernel supports restricted non-free kernel modules. I think the nvidia driver requires a restricted non-free kernel module. When you installed nvidia-glx, it probably installed the modules and generic kernel as dependencies. Now you have to boot to the generic kernel in the grub menu, or change the default boot option in /boot/grub/menu.lst.

---

### Post by garypdx on 2008-04-29
> **cdenley said:**
> I don't think the server kernel supports restricted non-free kernel modules. I think the nvidia driver requires a restricted non-free kernel module. When you installed nvidia-glx, it probably installed the modules and generic kernel as dependencies. Now you have to boot to the generic kernel in the grub menu, or change the default boot option in /boot/grub/menu.lst.

I've been trying to get my nvidia drivers working on the server kernel too and can't. Since I'm just starting some sites, I'm beginning to think I can wind up okay with "desk-top" version and add apache/mysql/php/proftpd and whatever else I need.

I'm trying to achieve my nvidia drivers with gdm with a root user desktop. If later on it gets busy, I can do the server kernel.

So..desktop version takes care of nvidia...what's the short sudo command that enables root to make a desktop?

A passwd command, yes?

---

### Post by cdenley on 2008-04-29
I don't think any desktop environment belongs on a server, but some people aren't familiar with commands and don't want to learn. Why would you want non-free proprietary kernel modules on a server? You shouldn't be playing games on a server. What is the point of using a server-optimized kernel if you waste system resources by rendering 3D graphics on it? If you simply need a graphical interface to use gui frontends for system configuration, why not use the open-source driver or even vesa?

> what's the short sudo command that enables root to make a desktop?
You don't want to start a desktop session as root. There is no need for it, and that is not the way ubuntu is designed. It greatly increases the chances that your computer can be compromised. An answer to your question is no longer allowed on this forum.

---

### Post by kwon37xi on 2008-04-29
Actually, I don't want to use Server edition. The thing I really want is using 4GB ram.

Why Ubuntu desktop does not suppoert 4GB ram?
You know ram is very cheap these days.
If possible, there is no reason not to use 4GB ram.

I heard Windows XP, Fedora and OpenSUSE alreayd support big memory in 32bit edition.

I hope Ubuntu desktop 32bit also support 4GB ram as soon as possible.

---

### Post by hyper_ch on 2008-04-30
go 64 bit and it will support a lot more ram.

---

### Post by cdenley on 2008-04-30
> **kwon37xi said:**
> Actually, I don't want to use Server edition. The thing I really want is using 4GB ram.

Why Ubuntu desktop does not suppoert 4GB ram?
You know ram is very cheap these days.
If possible, there is no reason not to use 4GB ram.

I heard Windows XP, Fedora and OpenSUSE alreayd support big memory in 32bit edition.

I hope Ubuntu desktop 32bit also support 4GB ram as soon as possible.

I'm guessing they choose not to compile the generic kernel with that option to maintain compatibility with all x86 processors. Windows XP and Vista require you to change a boot option. Linux requires a kernel with "high memory support" (PAE) enabled. After a quick search, it looks like for Fedora, there is an alternate kernel with PAE support you can download and install. If there are a lot of 32-bit users who need support for more than 4GB of memory, maybe ubuntu should create a linux-pae package. I don't think there are many motherboards which support more than 4GB of memory but not a 64-bit processor that someone would use on a desktop system.

---

### Post by steve_c on 2008-04-30
> **cdenley said:**
> I don't think any desktop environment belongs on a server, but some people aren't familiar with commands and don't want to learn. Why would you want non-free proprietary kernel modules on a server? You shouldn't be playing games on a server. What is the point of using a server-optimized kernel if you waste system resources by rendering 3D graphics on it? If you simply need a graphical interface to use gui frontends for system configuration, why not use the open-source driver or even vesa?
Actually I have the same problem and a perfectly valid reason.

I'm the sysadmin for a theoretical biochemistry research group and we have software we use to perform 3D visualizations of cells and viruses at an atomic level. Because of small scale we're using, there is way more information than a workstation could hope to process. In fact our best server, purchased six months ago specifically for this task, still takes at least a half a day to render the structures. So because of this need for hardware 3D acceleration, right now the server is running Ubuntu Desktop 7.10, 64-bit.

Ideally I'd like to use this server for much, much more as we only need to run these simulations every so often. So I would like to upgrade the server to 8.04 LTS, and I would like to be able to get it back on the server edition. Unfortunately I cannot under any circumstances afford to have the restricted graphics drivers unavailable.

So if anyone has any suggestions, tips, or any sort of help, it would be greatly appreciated.

---

### Post by sojyujai on 2008-05-02
I have to say I have a perfectly valid reason to install the nvidia drivers on ubuntu server as well - I want to.  Isn't that the point of using linux - so you can do what you want?

After a bit of googling I found [**this page**]("http://blog.0xb.org/2007/05/ubuntu-server-kernel-and-nvidia-driver.html") where he talks about compiling the nvidia restricted modules for ubuntu server edition.  Unfortunately it's referring to Feisty.  I gave it a try but couldn't manage to get it to work.

I'd appreciate suggestions as well. Or dare I ask a detailed how-to? :)

---

### Post by cdenley on 2008-05-02
**EDIT:Ignore this post. I was wrong.**

I just installed an ati video card, so I thought I'd test my theory.
linux-generic: fglrx kernel module loaded
linux-server: fglrx kernel module didn't load
linux-rt: fglrx kernel module loaded

Even though the fglrx kernel module didn't load with the server kernel, the fglrx driver still seemed to work, but must have been missing some hardware acceleration or something. I still had a dual-head configuration, but the visual effects disappeared.

> 
I'm the sysadmin for a theoretical biochemistry research group and we have software we use to perform 3D visualizations of cells and viruses at an atomic level.

I'm not sure exactly what all the kernel options actually provide, but have you tried the realtime kernel?
```

sudo apt-get install linux-rt

```

> I have to say I have a perfectly valid reason to install the nvidia drivers on ubuntu server as well - I want to. Isn't that the point of using linux - so you can do what you want?
That's the point of open-source. When you have the source code, you can do anything. If it's worth doing, someone has probably done it before, and provided a how-to or precompiled package.

---

### Post by cdenley on 2008-05-02
I was completely wrong. There is a restricted modules package for the server kernel. The server kernel just doesn't have it as a dependency like the generic or realtime kernel. I guess this is why there is no "linux-restricted-modules-server" meta package.

```

sudo apt-get install linux-restricted-modules-2.6.24-16-server

```

I just tested it, it works.
```

cdenley@ubuntu:~$ sudo modprobe -l|grep fglrx
[sudo] password for cdenley: 
/lib/modules/2.6.24-16-server/volatile/fglrx.ko
cdenley@ubuntu:~$ uname -r
2.6.24-16-server

```

Sorry for the incorrect assumption.

---

### Post by sojyujai on 2008-05-02
Oh man, is it that easy?

cdenley - thanks a lot, that solved the problem.

Just to note what I did:
Used synaptic to install 
linux-restricted-modules-2.6.24-16-server (+ its dependencies)
then installed 
nvidia-glx-new

then in terminal ran:
sudo nvidia-xconfig

reboot and bob's my uncle.

Extreme Tux Racer worked perfectly.  - Purely for testing purposes, even I'll admit that a server probably isn't the best place for Tux Racer :)

In hindsight I probably should have checked for a linux-restricted-modules-2.6.24-16-server package before spending half the day yesterday trying in vain to compile one.  But really wouldn't it have made sense to make it a dependency of nvidia-glx-new?

---

