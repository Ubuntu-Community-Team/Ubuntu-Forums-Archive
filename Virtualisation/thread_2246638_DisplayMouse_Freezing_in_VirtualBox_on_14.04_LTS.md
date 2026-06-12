---
title: "Display/Mouse Freezing in VirtualBox on 14.04 LTS"
date: 2014-10-02
forum: Virtualisation
---

### Post by johnsail on 2014-10-02
Had difficulties getting VirtualBox to run after upgrading to 4.3.16, The resolution was to rebuild the kernel (see [http://ubuntuforums.org/showthread.php?t=2245551](http://ubuntuforums.org/showthread.php?t=2245551)).

However when running VirtualBox the mouse/screen keeps freezing for extended periods. It is particularly bad when running Word or Excel for example and I have even had to turn the ubuntu machine off on occasions.

The system shows no errors although something is obviously wrong.

I have interrogated the dystem re the video driver with the following output:-

john@tadw004:~$ sudo lshw -c video | grep 'configuration'
       configuration: driver=radeon latency=0
john@tadw004:~$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: RV610 [Radeon HD 2400 PRO]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:43 memory:d0000000-dfffffff memory:fe9f0000-fe9fffff ioport:dc00(size=256) memory:fea00000-fea1ffff
john@tadw004:~$

All ideas/assistance will be gratefully received

---

### Post by bashiergui on 2014-10-05
I'm assuming the host is Ubuntu and the guest is Windows. Look at the amount of memory and processors you gave the guest. If it's too little then it will lag terribly. If it's too much then it will crash. 

What are your settings for the guest right now?

---

### Post by johnsail on 2014-10-07
Hi Bashiergui. Thanks for response. Not sure what you mean as I was not aware that guest had params to alter.
Symptoms get progressively worse as Vbox is opened and even more when a vm is opened.
For example an XP machine withe outlook opened and an email opened it takes around 15 sec for the mouse to respond to a move and then (for examle) a further 50 sec to complete a close request of an email.

Where do I find the settings for the guest?

---

### Post by bashiergui on 2014-10-07
Highlight the VM when it is NOT running. Settings-> system -> motherboard & process

Here are some screenshots of the settings tabs.
[http://turingsman.net/my-blog-list/147-oracle-virtualbox-4-2-6-installation-and-virtual-machine-creation-for-solaris-11-1-and-oracle-db-11gr2](http://turingsman.net/my-blog-list/147-oracle-virtualbox-4-2-6-installation-and-virtual-machine-creation-for-solaris-11-1-and-oracle-db-11gr2)

Also refer to the virtualbox manual, it's dense with useful information.
[https://www.virtualbox.org/manual/ch03.html](https://www.virtualbox.org/manual/ch03.html)

---

