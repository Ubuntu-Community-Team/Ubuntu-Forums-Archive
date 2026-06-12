---
title: "ClamAV causes server to crash"
date: 2024-04-23
forum: Security
---

### Post by danattwood-m on 2024-04-23
Hi

I have an Ubuntu server version 22.04.4 running on AWS as a small instance - 1 cpu and 2gig of ram.

When I run clamscan against a file from the terminal with 

```
/usr/bin/clamscan testfile.txt
```

the cpu spikes to 100%, the memory is gobbled up and the server locks up entirely. I have to force reset it.

I have attached an strace but I can't see any obvious issues in the clam logs or syslog so i'm at a loss as to what to try next.

[ATTACH]293681[/ATTACH]

---

### Post by currentshaft on 2024-05-07
2

---

### Post by ascendant2 on 2024-05-22
I tried Clam in all the versions of Ubuntu, and in hundreds of Linux distros. Clam always messed up the OS, always caused a myriad of computer nightmares. Seems Clam isn't compatible with Linux OS's. The worst glitch was that it slowed down the OS.I've tried all the Linux OS's with Clam. It always damaged them forcing a reinstall. I found a way that I don't need Clam. I install Librewolf Browser and PortMaster Firewall. Now there are no more cyber hacks nor attacks. Seems the baddies can't get in through PortMaster's powerful security.

I recommend reinstall the OS clean. At first boot run synaptic to dump Firefox, then install Librewolf and PortMaster. Hacker grief all gone. First download: Bleachbit 4.4.2 only (do not update nor upgrade nor allow it to net-connect), and download Libewolf's list of Terminal commands. Save those two downloads to a couple flash drives.

Would be nice if the Ubuntu install ISO came with Librewolf and PortMaster. If I use Firefox, some hacker gets into the OS, and makes it crash off the screen the moment I've finished keying extremely controversial activism posts, but with Librewolf it doesn't happen, nothing gets in, not even black ops hackers.

Tip: with the looming threat of solar flares and nuclear exchange, it would be a good plan to acquire a new external hard drive to make a secure backup of all your treasures before solar flares and nuclear EMP shuts down the electric grid.
Note: CD's and flash-drives are not reliable backups. CD's wear out, and some flash-drives can get dropped and suddenly be destroyed in a flash, backup all gone. 
Last month an install ISO DVD fell off the desk to the floor, hitting on its edge. It separated the DVD's component layers like a big internal bubble, totally destroying it. Check it out, drop a scrap DVD on its edge. If it's a poor quality product, it'll probably separate. The big thing is: You are your own security.

---

