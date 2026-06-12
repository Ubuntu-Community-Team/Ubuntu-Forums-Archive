---
title: "Kernel 4.8.0.11 in yakkety daily iso"
date: 2016-09-21
forum: Ubuntu Development Version
---

### Post by jimmy-frydkaer on 2016-09-21
Hey all

I've just downloaded the daily yakkety iso image and installed it from an USB stik - I was surprised to find that I've gotten kernel 4.8.0.11 during installation. Now I can instal my nVidia-driver to slow down the fan on my GT440. 
The kernel is fast and stabel, it has also reduced startup-time a bit, not much but you'll se if you download and install today's ISO.

---

### Post by MikeMecanic on 2016-09-21
Same here and no bug so far
 #deb cdrom:[Ubuntu 16.10 _Yakkety Yak_ - Alpha amd64 (20160921)]/ yakkety main restricted

---

### Post by Doug S on 2016-09-21
And you are not seeing a high number of kworker threads sometimes? On my Yakkety Laptop, and as of today, and because of kernel 4.8.0-11-generic, I am seeing a high number of kworker threads once per hour synchronous with CRON hourly. They linger for 5 minutes +/- a few seconds.

EDIT: See [also]("https://ubuntuforums.org/showthread.php?t=2333240&page=2&p=13547989#post13547989").

---

### Post by jimmy-frydkaer on 2016-09-22
> 1136 nobody    20   0  237176   2436   2052 S   1,3  0,0   0:08.96 g15daemon    1167 root      20   0  233244  57312  39916 S   0,7  0,3   0:11.81 Xorg        
 6940 jimmy     20   0   50764   4032   3264 R   0,7  0,0   0:00.13 top         
   90 root      20   0       0      0      0 S   0,3  0,0   0:01.61 kworker/u1+ 
  223 root      20   0       0      0      0 S   0,3  0,0   0:00.09 usb-storage 
 2698 jimmy     20   0 1135364 283832 115044 S   0,3  1,7   0:45.34 chrome      
 2822 jimmy     20   0  921700 109596  56112 S   0,3  0,7   0:04.80 chrome      
 6901 jimmy     20   0  709780  39268  26912 S   0,3  0,2   0:01.24 gnome-term+ 
    1 root      20   0  137160   7060   5180 S   0,0  0,0   0:02.24 systemd     
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.01 kthreadd    
    3 root      20   0       0      0      0 S   0,0  0,0   0:00.00 ksoftirqd/0 
    5 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:+ 
    7 root      20   0       0      0      0 S   0,0  0,0   0:00.42 rcu_sched   
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh      
    9 root      rt   0       0      0      0 S   0,0  0,0   0:00.01 migration/0 
   10 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 lru-add-dr+ 
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/0  
   12 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/0     
   13 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/1     
   14 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/1  
   15 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/1 
   16 root      20   0       0      0      0 S   0,0  0,0   0:00.01 ksoftirqd/1 
   18 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/1:+ 
   19 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/2     
   20 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/2  
   21 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/2 
   22 root      20   0       0      0      0 S   0,0  0,0   0:00.00 ksoftirqd/2 
   24 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/2:+ 
   25 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/3     
   26 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/3  
   27 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/3 
   28 root      20   0       0      0      0 S   0,0  0,0   0:00.01 ksoftirqd/3 
   30 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/3:+ 
   31 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/4     
   32 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/4  
   33 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/4 
   34 root      20   0       0      0      0 S   0,0  0,0   0:00.00 ksoftirqd/4 
   36 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/4:+ 
   37 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/5     
   38 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/5  
   39 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/5

Kworker i active but not to much, I think

---

### Post by Doug S on 2016-09-22
> **jimmy-frydkaer said:**
> Kworker i active but not to much, I thinkThis never was a CPU hogging issue. Anyway, the root issue has been isolated and fix committed. See [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1626564").

---

### Post by MikeMecanic on 2016-09-26
There is nothing wrong here with the Sept.21st build.  Kernel 4.8.0.17.27 is in Proposed with 157Mb of updates.
 
 
 ```
dpkg --list | grep linux-image

 ii  [COLOR=#ff3333]**linux-image**[/COLOR]-4.8.0-17-generic               4.8.0-17.19                                         amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
 ii  [COLOR=#ff3333]**linux-image**[/COLOR]-extra-4.8.0-17-generic         4.8.0-17.19                                         amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
 ii  [COLOR=#ff3333]**linux-image**[/COLOR]-generic                        4.8.0.17.27                                         amd64        Generic Linux kernel image

``` 
 
 All the best,

---

### Post by cecilpierce on 2016-09-27
Just updated 4.8.0-17-generic and reboot gave me black screen, went to terminal window and installed 'nividia-current' and back to normal.

Wonder why nouveau didn't work ?

---

### Post by MikeMecanic on 2016-10-07
> **cecilpierce said:**
> Just updated 4.8.0-17-generic and reboot gave me black screen, went to terminal window and installed 'nividia-current' and back to normal.

Wonder why nouveau didn't work ?
                         Intel does the same in an intermittent manner: CRTL+ALT+Delete until it reboots or if you have the sleep mode key it’s even better.  When dual boot with Redstone one the Grub menu is sensitive to black screen.  When bypassing the 10 second delay or in advanced options (pressing enter).
 
 
 Since yesterday, Kernel 4.8.0.30 is in Proposed and you can get the latest Kernel [URL="http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D"]here

[/URL]                         
Up-To-Date
  

                           ```
dpkg -l|grep firmware

 ii  fwupdate                                   0.5-2ubuntu4                                amd64        Tools to manage UEFI [COLOR=#ff3333]**firmware**[/COLOR] updates
 ii  intel-microcode                            3.20160714.1                                amd64        Processor microcode [COLOR=#ff3333]**firmware**[/COLOR] for Intel CPUs
 ii  libfwup0:amd64                             0.5-2ubuntu4                                amd64        Library to manage UEFI [COLOR=#ff3333]**firmware**[/COLOR] updates
 ii  linux-f[COLOR=#ff3333]**irmware **[/COLOR]                            1.161                                       all          Firmware for Linux kernel drivers
 dpkg --list | grep linux-image
 ii  [COLOR=#ff3333]**linux-image**[/COLOR]-4.8.1-040801-generic           4.8.1-040801.201610071031                   amd64        Linux kernel image for version 4.8.1 on 64 bit x86 SMP

```
                        This command line returns a messy result since first fresh install of YY on Sept 21[SUP]st.[/SUP]
 
 
 14393.222 dual boot YY (legacy)
 
 
 ```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL

 NAME   FSTYPE   SIZE MOUNTPOINT LABEL
 sr0            1024M             
 sda           698.7G             
 &#9500;&#9472;sda4            1K             
 &#9500;&#9472;sda2 ntfs   510.3G             
 &#9500;&#9472;sda7 ext4   157.1G /home       
 &#9500;&#9472;sda5 swap     7.6G [SWAP]      

 &#9500;&#9472;sda3 ext2     243M /boot       
 &#9500;&#9472;sda1 ntfs     500M            System Reserved
 &#9492;&#9472;sda6 ext4    22.9G /     

```  
 
Take care,

---

