---
title: "Data traces on the computer"
date: 2011-02-02
forum: Security
---

### Post by asdfghjkl67 on 2011-02-02
If i install ubuntu 10.04 and reformat the entire drive will the previous data be forensically unrecoverable?  

If i use a live cd does that mean that there will be no traces of my use on main systems hard drive or otherwise on the system itself? 
  

Will there be any data left in swap? How do I securely erase the swap file in ubuntu linux?


How to test that swap is off using **sudo swapoff -a**?

 

[SIZE=4]
[/SIZE]

---

### Post by sydbat on 2011-02-02
> **asdfghjkl67 said:**
> If i install ubuntu 10.04 and reformat the entire drive will the previous data be forensically unrecoverable?Most likely. 
  

> If i use a live cd does that mean that there will be no traces of my use on main systems hard drive or otherwise on the system itself?No traces left behind.
  

> Will there be any data left in swap? How do I securely erase the swap file in ubuntu linux?Swap is dumped on reboot.


> How to test that swap is off using **sudo swapoff -a**?Not sure what all the paranoia is about. Unless you are just trolling and cannot post in the cafe...

---

### Post by The Cog on 2011-02-03
> **asdfghjkl67 said:**
> If i install ubuntu 10.04 and reformat the entire drive will the previous data be forensically unrecoverable?  
It is possible that some may be recoverable. The new install will overwrite some data of course, but previously used areas of the disk that don't get overwritten will very likely contain recoverable data. The application photorec springs to mind - I've never used it but seen it recommended to people who accidentally formatted the wrong partition.
> If i use a live cd does that mean that there will be no traces of my use on main systems hard drive or otherwise on the system itself? 
  
Will there be any data left in swap? How do I securely erase the swap file in ubuntu linux?

How to test that swap is off using **sudo swapoff -a**?
A live CD won't touch your hard disk other than the swap partition unless you tell it to. So swap is the only one you have to worry about. Memory contents can be left in swap, and might remain there for some time, until overwritten next time swap space is needed. The command **swapon -s** will show you if swap is currently used. The command **swapoff -a** will turn off all swap usage, but of course you can't do this until the live CD is fully booted by which time it may have already used some swap space.
 
You can wipe a partition effectively with the following command. **[COLOR="DarkRed"]Make very sure[/COLOR]** that you use the correct partition name as the of= argument or you could wipe the entire disk. It doesn't ask if you're sure. I used sda1 purely as an example. This command overwrites the entire partition with random data.
```
sudo dd if=/dev/random of=/dev/sda1
```

---

