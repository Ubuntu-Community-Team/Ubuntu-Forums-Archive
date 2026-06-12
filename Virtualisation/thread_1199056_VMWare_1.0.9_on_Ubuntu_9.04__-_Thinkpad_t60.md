---
title: "VMWare 1.0.9 on Ubuntu 9.04  - Thinkpad t60"
date: 2009-06-28
forum: Virtualisation
---

### Post by jerelev on 2009-06-28
Hi all, 

I spend all day searching for a very specific problem. I didn't found any answer so here i am.

Here is the config :

Thinkpad T60
/dev/sda1 : Windows XP (with windows boot menu pointing to grub)
/dev/sda2 : Rescue partition
/dev/sda3 : /boot (with gub)
/dev/sda4 : / (Ubuntu)
/dev/sda5 : swap

So, i m bored from WinXP, but i need Microsoft Exchange.

I install VMWare 1.0.9 and i want to start the VM from the real Hard disk. 

When i m adding the HDD i choose : "use a physical disk"
Then i tried with /dev/sda (the whole disk) and /dev/sda1 (only the windows partition) but i get STUCK at :
"To boot to the rescue and recovery environment, press F11"
and i can't pass this step that will take me to the Windows menu !!

Someone have an solution ?

---

### Post by fjgaude on 2009-06-28
Where are you wishing to install VMware, on which partition?

---

### Post by jerelev on 2009-06-29
i want to run the windows partition (/dev/sda1) from VMWare in ubuntu.

---

### Post by dmizer on 2009-06-29
This is probably your best bet: [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

I believe there is also a way to actually boot the partition, but this renders the physical Windows install useless.

---

### Post by jerelev on 2009-06-29
i found that too, i ll try this maybe next week when i ll be sure my case is lost.
actualy, i don't mind loosing my real windows by using it in the VM, that's actually the result i search for.

The wired thing is that, if i press F11, i get into the Rescue and Recovery environement ! but it just don't want to do anything else.


Maybe if i erase the MBR, since i use Windows boot menu to boot even my Ubuntu (grub is on /boot not in the MBR), it may erase this F11 option...

---

### Post by dmizer on 2009-06-29
There are vmware tutorials for Workstation, but that's a pay-for-it product. I did find this: [http://www.kvaes.be/unix-linux/running-your-dual-boot-windows-inside-vmware-server-within-ubuntu/](http://www.kvaes.be/unix-linux/running-your-dual-boot-windows-inside-vmware-server-within-ubuntu/) which makes it sound easy ...

---

### Post by jerelev on 2009-06-29
Actualy, that s easy, but it's not there that i m stuck

It's working, but this THINKPAD feature is blocking the boot

---

