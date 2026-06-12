---
title: "Dual boot compatible brand that works with Oculus Rift"
date: 2018-06-25
forum: Ubuntu, Linux and OS Chat
---

### Post by llowe on 2018-06-25
I'm looking to buy a new computer, could be desktop or laptop:

I will be programming and testing applications with MPI and OpenACC so I need native Linux, but I need to be able to use Oculus Rift to test VR applications, so I need native Windows 10.  (I need a dual boot rather than VM.)

I'm not a great sys-admin, so I need to be able to install Linux without major complications or expertise.  I'm comfortable picking the specs, but when I find a configuration that I like, it is so hard to figure out whether it is Linux compatible (digging through Amazon reviews...)  I'm reading reviews that say some brands work with only some flavors of Linux, or warnings about some brands having 'proprietary drivers'(?), or just totally destabilizing the system for both OS's.

Has anyone bought a gaming machine- ideally 'VR ready'- that works great with dual boot Ubuntu/Windows 10 and was relatively painless to install Ubuntu?  Or has any recommendations on picking one?  (Or a brand/company that will do this for me when I buy it and guarantee the results?)  I definitely don't want to pay the big bucks for HPC hardware and then screw everything up when I install a dual boot...

Thanks!

---

### Post by Perfect Storm on 2018-06-25
Thread moved to Ubuntu, Linux and OS Chat.

---

### Post by oldfred on 2018-06-25
Some of the gaming systems are more difficult to install Ubuntu.
Often issue is use of RAID 0 which is not recommended for a regular system as if one drive fails, all data is lost. Gaming systems are just for gaming or perhaps compiling systems where data is on another system or another drive. The use of RAID 0 was often with older HDD systems to add speed, but now with SSD you are not gaining as much. And newer NVMe drives are so fast you normally do not need RAID 0.

If you know hardware and do not need portability, often better to build your own desktop system. While most motherboard mfg do not specifically support Linux they all work if UEFI settings are changed. 

With all Linux systems, getting very new hardware will make it more difficult to install Linux. Few vendors directly support Linux. So it can take several months for kernel & drivers to get updated. And then with 6 months between Ubuntu release, and distribution freeze before that timing of updates may mean a year before everything is in Ubuntu. But there are ppa to add newer kernel & support software as soon as available.

Also then better to go with main stream hardware. Some users with unique systems have issues as drivers are not available and may not ever be available.

You can look at this site and its hardware & software reviews & comparisons.
[https://www.phoronix.com/scan.php?page=home](https://www.phoronix.com/scan.php?page=home)
And it supports this where you can post data on your system to see how it compares. Many systems shown.
[http://openbenchmarking.org/](http://openbenchmarking.org/)

---

### Post by mastablasta on 2018-06-28
another option is to get a machine form company that preloads linux on them (like System76) and then add windows on it.

if you need something really powerfull then it is better (and cheaper) to build one yourself. with desktop major issue can be motherboard. if it's linux compatible you are good to go, becuase RAM, CPU, HDD, graphics chip (Intel, AMD, nVIdia)... they are usally all linux compatible. while with laptops issues can range from motherboard to wi-fi chips, touchpad, backlit keyboard, monitor... and other stuff.

---

