---
title: "HOWTO: Install Ubuntu Server 9.10 on X-board &lt;861&gt; with SC1200"
date: 2010-03-28
forum: Server Platforms
---

### Post by wolf_guru on 2010-03-28
Following steps are to install Ubuntu-server 9.10 (Karmic) on Kontron's X-board <861> with SC1200 AMD processor:
  1- Connect a CF card (2G in my case) as a hard disk in a normal PC. Use CF-to-IDE converter.
  2- Install Ubuntu-server 9.10 from live CD
  3- After installation are done, login to Ubuntu-server and execute the following commands to update the system:

[LIST]
[*]sudo apt-get update               # this is to update the apt-get list
[*]     sudo apt-get upgrade              # this is to upgrade the system
[*]     sudo apt-get install linux-386   # this is to update the Linux kernel (in my case updated to 2.6.31-20 Generic)
[/LIST]
   4- Add kernel parameters on boot to disable non-supported stuff in xboard

[LIST]
[*]     sudo vi /etc/default/grub
[*]     add the following parameters at the end og "GRUB_CMDLINE_LINUX_DEFAULT=" line:
[*]       libata.dma=0              # disable DMA on all devices as xboard has a buggy DMA
[*]       notsc clocksource=pit     # change the clocksource to pit and disable tsc, as xboard does not support tsc
[/LIST]
   5- Execute the following command to update the boot menu with the new kernel and new kernel parameters

[LIST]
[*]     sudo update-grub
[/LIST]
    
  Now take the CF card out and mount it your xboard. Things should work. Please check important notes below to prevent some troubles.
   
  Important notes:
  ----------------
  1. The could be a big time difference between the clock of your installing computer and the clock of xboard. Such difference can cause the file system to be seen as corrupted, and following error message will appear:
   
  /dev/sda1: UNEXPECTED INCONSISTANCY; run fsck manually (i.e. without -a or -p options)
  mountall: fsck / [258] terminated with status 4
  mountall: filesystem has errors :/
  init: mount all main process (246) terminated with status 3 mount of file system failed bla bla bla ... fallback to initramfs shell or something like that
   
  Solution: execute fsck /dev/sda and choose to fix the errors.
   
  2. Network card is not activated. That is probably because the eth0 on the installing machine is not recognized correctly on the new machine (i.e of course it is not there any more ;o), therefore xboard's Ethernet card is renamed to something else. You can dmesg | grep eth and you should see a line telling the eth0 is renamed to ethx (in my case eth2). But eth2 is not defined in the system, so it will not be useable.
   
  Solution: "sudo vi /etc/network/interfaces" and change all eth0 to eth2. Then "sudo /etc/init.d/networking restart".
   
  DONE :popcorn:

---

