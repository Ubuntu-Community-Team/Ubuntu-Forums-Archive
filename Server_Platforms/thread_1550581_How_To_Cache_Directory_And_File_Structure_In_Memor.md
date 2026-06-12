---
title: "How To Cache Directory And File Structure In Memory"
date: 2010-08-11
forum: Server Platforms
---

### Post by phyrexianhulk on 2010-08-11
Hello everyone,

i am running Ubuntu Lucid x64 as a fileserver that shares its files via SFTP, NFS and Samba.

Currently the hard disks are configured to go to standby if they are not needed. This works perfectly as long as no one browses the shares or my HTPC is running: That one repeatedly looks through the shares for new music or movies.

In other words my problem is that the disks are spinning up a lot more often than they should have to. Additionally the spin-up time delays the response time while browsing.

Since the machine has a lot of unused RAM i want to tell the kernel that it should keep the directory structure in memory. That way the disks would not need to spin up every time someone browses through the directories.

Is there a way to achieve that?

Thanks a lot!

---

### Post by gobbledigook on 2010-08-11
i have no idea how to achieve this... however why not just stop the disks from spinning down? there are lots af arguments about powersaving vs performance vs longevity, some believe that if you leave the drives spinning all the time, it will make them last longer as if they have to spin up and down the difference in heat will wear it out faster! (i'm of this opinion) 

but also ou need to take into condideration power usage, which is why i will be switching (as soon as i can afford to!!) to either WD/samsung green drives with this 'intelliseek' business. 

doesn't answer your question... but i'm not sure you are looking for the right soluton? have a look at [**_this thread_**]("http://ubuntuforums.org/showthread.php?t=1461135&highlight=hard+disk+spin+time") regarding using USB boot for powersaving

---

### Post by phyrexianhulk on 2010-08-12
Thanks gobbledigook,

yes i know that there is statistical evidence that always-on hard drives live longer. Afaik google released a paper once about hdds in their data center. If i remember correctly it says that it also is a problem to cool drives down to room temperature (using fans or whatever). A somewhat higher operation temperature is better for hdd longevity.

I would definitely go for that solution if i had to maintain such a setup. However my area of application is somewhat different. As soon as the kernel would cache these directory- and file-trees the hard disks would keep in standby for the bigger part of their time instead of spinning up and down again and again (which i too believe is a durability problem).

The green disks: I am already using a *Samsung EcoGreen* and a *WD Caviar Green (with IntelliPower)* to reduce power usage. However i found out that manually putting the hard disks to standby reduces temperature and power usage by a lot more than the disks built-in measures.

The USB booting: Since the shared data will be residing on the larger hard drives, keeping the OS on an usb stick will not help the problem that the hard drives need to spin up to return the directory structure.

Thanks again.

---

