---
title: "Ubuntu 8.04 - &quot;Convert&quot; package and other questions about CE"
date: 2008-09-01
forum: Ubuntu Christian Edition
---

### Post by BEND IT 7 on 2008-09-01
I have a few questions:

I was wondering if there is a convert package available for Ubuntu 8.04.  I really would like to try out Ubuntu CE, but I do not want to uninstall Ubuntu and lose all of my personal settings.  

I was wondering what personal settings would be lost/changed with a convert package.

I was wondering what is meant by "no boot manager" or whatever another poster wrote in another thread.  I want to be able to readily use this OS without disturbing my BIOS in any way.  Would Ubuntu CE do that?

Thank you.

---

### Post by cjm5229 on 2008-09-05
I believe Jereme is still working on the convert script, and I did notice that Wubi is not on the Ubuntu CE install disk. (space issues). However it is a live CD, You can just put it in your CD drive and reboot. It won't change anything in your BIOS, You can try it out on the live CD for awhile and see if you like it. You can install some Apps, but since you are basically running in memory you can't put in to much or you will run out of memory. It won't write anything to your HDD so it won't change anything there. of course when you shut it down all changes in the live CD will be lost. If you decide you like it and wish to install it, make sure you read everything you can find on Partitioning. that is the area where most mistakes are made, and Data is lost. I generally use three Partitions for Ubuntu: Root, Swap, and Home. I make my root partition at least 10 GB also because I install a lot of apps and have been known to run out of space. And remember to back up any important files you may have.   [Here]("http://www.psychocats.net/") is a good place to learn about Installing Ubuntu.
I personally have regular Ubuntu 8.04, Ubuntu CE, and Ubuntu 8.10 alpha 5 , all shareing the same /home but with different users so that they can all be configured differently.
We are all here to help, but sometimes we get busy on other things and don't get to respond as quickly as we should,
God bless you, Carl

---

### Post by uncleclinto on 2008-12-08
I'm in a bit of a pickle here, as my wife has put her foot down and demanded we return to windows.  I don't know jack about partitioning and dual booting so I was was planning to go WUBI.  Of course, as I've read in the forums, that isn't available for CE.  Due to other issues... ahem... CE is the only acceptable distro for me to use.  It would certianly be nice to be able to either "wubi" or "convert" and install I can "wubi". I would gladly put my money where my mouth is in terms of donation if we could work a wubi or convert script for CE...

---

### Post by david_kt on 2008-12-10
> **uncleclinto said:**
> I'm in a bit of a pickle here, as my wife has put her foot down and demanded we return to windows.  I don't know jack about partitioning and dual booting so I was was planning to go WUBI.  Of course, as I've read in the forums, that isn't available for CE.  Due to other issues... ahem... CE is the only acceptable distro for me to use.  It would certianly be nice to be able to either "wubi" or "convert" and install I can "wubi". I would gladly put my money where my mouth is in terms of donation if we could work a wubi or convert script for CE...

Dual booting is better than wubi. What you coul do is:

1. Install windows
2. Install ubuntu ce, choose automatic resize partitioning

That's all.

DK

---

