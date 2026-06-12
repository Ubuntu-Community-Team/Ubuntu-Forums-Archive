---
title: "Must have Adobe CS3, need help in finding the right virtualization method"
date: 2008-04-24
forum: Virtualisation
---

### Post by Tombigel on 2008-04-24
Hi all,

After playing a bit with 8.04 betas, I decided that the time has come for me to finally leave XP and move to Ubuntu as my main OS.

The only obstacle standing in my way is my work - Among other things I'm a designer and I must have my Adobe Creative Studio with maximum performance and stability.

So my question is - From all of the virtualization solutions that comes with Ubuntu 8.04 (*Edit*: I read about all the different options, still I need help in choosing the best-tool-for-the-job), which will deliver the best combination of stability, performance, ease of use and ease of maintenance?

I can't waste too much time in playing with settings (It's for work, and time is money...) and since the system is going to be a Development station, I can't risk making my working environment unstable.

My system has a Q9300 Intel Quad Core, 4GB RAM, 2 monitors and tons of disk space.

---

### Post by jrharvey on 2008-04-25
I love virtualbox. With your computer specs i dont think you will even see a performance decrease. I use virtualbox for CS3 all the time. I only dual boot into windows when i need to use a 3d software like rhino or maya. Unfortunately virtualbox does not support 3d hardware acceleration yet. Like i said, for CS3 it is the best i found. Vmware is kinda slow in comparison.

---

### Post by russo.mic on 2008-04-25
+1 Virtualbox

---

### Post by leif3d on 2008-05-18
> **jrharvey said:**
> I love virtualbox. With your computer specs i dont think you will even see a performance decrease. I use virtualbox for CS3 all the time. I only dual boot into windows when i need to use a 3d software like rhino or maya. Unfortunately virtualbox does not support 3d hardware acceleration yet. Like i said, for CS3 it is the best i found. Vmware is kinda slow in comparison.

Why would you use Maya on windows if it's native to Linux?:confused:

---

### Post by fjgaude on 2008-05-18
I use the free vmware server from vmware.com and find the quickness and speed just fine with CS3... I'm a designer too using 4 GBs of RAM and a dual core at 4GHertz... see my signature.

The large available memory permits Ubuntu to put everything used in cache and that makes everything really fast. Try it, you'll like it. Trust me. <grin>

---

### Post by MystaMax on 2008-05-20
I run VirtualBox 1.6 and would recommend it as well. I've got a WinXP Pro Guest slimmed down with [nlite]("http://www.nliteos.com/"). I removed all the processes and services I wouldn't need (see [this thread]("http://ubuntuforums.org/showthread.php?t=646613")), and my guest boots real fast, and uses a bit less memory.

Using the slipstreamed XP CD, it only takes 14 mintues to install XP. I don't have to do anything as most of the settings are saved to an answer file.

Photoshop & Fireworks CS3 run great on the guest as well. It did take a while for it to install CS3 suite.

Right now, for a desktop solution, I'd say go with VirtualBox. I just finish installing vmware server 1.05 on 8.04 server 64-bit. While it wasn't painful to install, it wasn't difficult either. There is added work with VMware server as well; an example being kernel updates. You have to rerun the vmware-config.pl script whenever there is a kernel update. I'm not sure I had to do this w/ virtualbox.

The original poster said it best, "time is money". You'll spend more time w/ VMware Server than you would VirtualBox. Theres no .deb package for VMware server

My PC isn't nearly as fast as yours. I have a 1.8 Dual core laptop w/ 2 gigs of RAM. 1 gig dedicated to my WinXP guest ( 1GB requirement for CS3__).


**Links**
[XP Slimstream tutorial]("http://lifehacker.com/374376/trim-down-windows-to-the-bare-essentials")
[VMware Server 1.05 on Hardy howto]("http://ubuntuforums.org/showthread.php?t=779934")

---

### Post by Skeet on 2008-05-20
If you want 3D acceleration in your virtual machines, purchase VMWare Workstation 6.5 (its in beta currently, but will be out soon, or you may download the beta to test it out). It allows DX9 support and unity, a feature that shows the windows in the ubuntu environment just like wine, as against a separate desktop.

Its not cheap, but those two features are worth every penny tbh.

---

### Post by fjgaude on 2008-05-20
Well, vmware server, the free one, does a good job when it comes to laying over Ubuntu in a full window, having instant access to both WinXP and its loaded programs, and the host OS. Screen shot tells alot if you notice all the headers and footers.

---

