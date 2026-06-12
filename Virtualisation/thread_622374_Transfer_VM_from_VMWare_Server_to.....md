---
title: "Transfer VM from VMWare Server to...."
date: 2007-11-24
forum: Virtualisation
---

### Post by coldvodka on 2007-11-24
I created two virtual machines: XP and Server2k3 on VMWare Server only to realize:
1. There is no sound support in VMWare Server.
2. VMWare Server is painfully slow. 

Is there any way I can transfer the machines to something faster, like maybe VirtualBox? 

Appreciate any input. 

Running: 
7.10
Pentium M 1.73
2GB DDR2 533
80GB HDD 7200

---

### Post by Delvien on 2007-11-28
> **coldvodka said:**
> I created two virtual machines: XP and Server2k3 on VMWare Server only to realize:
1. There is no sound support in VMWare Server.
2. VMWare Server is painfully slow. 

Is there any way I can transfer the machines to something faster, like maybe VirtualBox? 

Appreciate any input. 

Running: 
7.10
Pentium M 1.73
2GB DDR2 533
80GB HDD 7200

Virtualbox for a lower memory setting is extremely fast, less feature packed inside, but I love it for the one VM I run on my laptop, but I use Vmware-Server to connect to my VM's on my "server"

I would, if I were you, Install Virtualbox, and install your VM on that, I wouldnt try to migrate it, its difficult and by the time you figure it out and have it working properly, you would have had it installed and up and ready to go in Virtualbox.

---

### Post by AusIV4 on 2007-11-28
In VMWare server, you need simply add a sound device for sound.

Click 'Edit Virtual Machine Settings.
On the hardware tab, click 'Add'
Choose a sound adapter and follow the steps from there.

As far as speed goes, I find VMware server to be quite speedy on my hardware. I had a lot of trouble the two times I tried using Virtual box, but other people here seem to like it quite a bit. I think it's just a matter of taste.

---

