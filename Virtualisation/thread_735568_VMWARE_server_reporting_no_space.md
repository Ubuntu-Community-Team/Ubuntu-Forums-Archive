---
title: "VMWARE server reporting no space"
date: 2008-03-25
forum: Virtualisation
---

### Post by mhouston100 on 2008-03-25
Hi guys,

I've recently started using VMWARE server on linux (as opposed to workstation on windows XP) and it seems to be running fine.  Up until a point...

The situation is this, I have two virtual machines running from a 20 gig IDE HDD (formatted to ext3) both 8 gig (dynamically assigned) and the first one will install XP fine, but after trying to install the second one, or even copying the first one and running that, VMWARE starts reporting that there is no free space on the drive.  While linux is reporting 16 GB free, even with both VM's running.

There is only the two images , each about 1.4GB with no snapshots or anything, so now neither VM will start. Even after a reboot and just trying to start one of the VM's will not start.  I have recreated them several times and each time the first one will work fine, then as soon as i try and run a second one, same error!

Though i'm just thinking now wether I had tried to pre-assign the HDD space or not... i believe I had tried that though.  Would this have any impact on this?

Thanks for any help!

UPDATE::

Trying to avoid feeling foolish I removed the VM's and started again, trying to pre-assign a 7GB Virtual disk (split into 2GB chunks), linux is reporting 19 GB free but VMware is telling me that it is unable to assign the 7GB as there is only 4GB free.... lost again!

---

### Post by mhouston100 on 2008-03-26
Just to update, i've just done another install of the two virtual machines and even though i've stipulated that everything (the settings, virtual disk EVERYTHING) goes to the 20 gig HDD i have set up, it still seems to be taking up space on my other drive which holds / and /home ... it has just popped up a message saying that '/ is 100% full'...

How can this be?

---

### Post by dcstar on 2008-03-26
> **mhouston100 said:**
> Just to update, i've just done another install of the two virtual machines and even though i've stipulated that everything (the settings, virtual disk EVERYTHING) goes to the 20 gig HDD i have set up, it still seems to be taking up space on my other drive which holds / and /home ... it has just popped up a message saying that '/ is 100% full'...

How can this be?

Where are you installing the VMs?, you should get an option for the default location (in VMWare server console-Host-Settings-General).

---

