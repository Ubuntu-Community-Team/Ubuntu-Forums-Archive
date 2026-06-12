---
title: "Ubuntu 20.04.6 LTS -- server is unbelieveble slow! Why!?"
date: 2024-01-17
forum: Server Platforms
---

### Post by civilpolisen on 2024-01-17
Why is the server so slow!? Where shall I start to look for errors?
It's a KVM server and RAM = 10 GB, the server is host for NextCloud, among other things.

I'm out of ideas! There's something vital I did not think of but my skills in Ubuntu is some how limited!
Slow software? how do I find?
I do "sudo apt update" on regular basis... But still, maybe there is software not updating using apt!?

---

### Post by SeijiSensei on 2024-01-17
Run the command "top". Do you have a swap file? How much is in use? Which applications are consuming the most resources?

If you reboot, does the problem recur right away, or does it take some time before the symptoms appear?

---

### Post by civilpolisen on 2024-01-19
```
   2434 testtest  20   0 2442196   2.3g      4 S 284.4  24.2   6460:19 kswapd0                                                                 
 686763 root      20   0   18096   2924   2616 S   3.3   0.0   0:00.10 startRocketChat                                                         
    377 root      19  -1  128264  58332  56644 S   1.7   0.6  16:33.97 systemd-journal                                                         
    815 syslog    20   0  234752   6040   3724 S   1.7   0.1  13:32.08 rsyslogd                                                                
      1 root      20   0  177048  12092   8432 S   0.7   0.1   2:17.59 systemd                                                                 
 569768 root      20   0 1467436  33420  19812 S   0.7   0.3   0:28.22 snapd                                                                   
 686747 root      20   0   30024   6172   1740 S   0.7   0.1   0:00.02 systemd-udevd                                                           
      9 root      20   0       0      0      0 S   0.3   0.0   0:16.86 ksoftirqd/0                                                             
     10 root      20   0       0      0      0 R   0.3   0.0   2:03.19 rcu_sched                                                               
    452 root      20   0   30024   8392   3972 S   0.3   0.1   2:33.88 systemd-udevd                                                           
   1094 root      20   0   26096   8180   7152 S   0.3   0.1   0:13.17 systemd-logind                                                          

```

Above is top-command. There is no swap-file. We remove that from servers not to take up space on the back-up.

After reboot, the server is less slow! :-) It's still slow, but not provocative-slow!

---

### Post by TheFu on 2024-01-19
I can assure you that 20.04.6 isn't slow for everyone.

Linux is setup to perform better with some amount of swap.  The kernel behaves differently when there is zero swap, disabling some performance items. Enable 100MB will turn on those kernel performance items.

If you don't want swap in your backups, don't backup the swap partition. That's easy. Clearly, you shouldn't be using a swap file.

As for other performance items, always check the system logs. That's where hardware issues will show up first. Look for warnings and errors.  Failing storage can drastically slow a system down.

The way that storage is laid out and the actual storage used can have huge impacts too.  SSDs simplify this and can remove many little performance problems.

Providing too much CPU or too much RAM to a VM can make the entire system slow as well.  More isn't always better. It is about cooperative sharing of the available hardware, while leaving sufficient RAM and CPU for the host OS to manage everything.

OTOH, if your "server" is a Pentium 4 from 2008, not much can be done. Slow systems are slow systems.

For comprehensive help, you'll need to setup performance monitoring, let that run for a few days to a month, look over the 50 or so performance elements that any quality performance monitoring tool will provide. Look for trends.  This is part of any professional server management effort.  Something as simple as **munin**, but there are more complex tools, if you want prettier GUI stuff to show managers.

Posting a hardware overview like **inxi -Fxxz** will create would be helpful, so we don't have to ask 50 questions like a dentist exploring for a cavity or root canal.

That should get you started.


BTW, you cut off the most important parts of the output from 'top'.  If you like that, check out **htop** and **glances**.

---

### Post by MAFoElffen on 2024-01-19
+1000 on create swap and just exclude the swap from your backups.

I would also mention that 10G is not much for a KVM Host. How much do you have allocated to your running guests?

---

### Post by TheFu on 2024-01-19
10GB of RAM can be fine.  I used to run 10 VMs inside 8GB of total RAM, but that was when 384MB-512MB was sufficient for each VM.  Of course, none of those VMs had any GUI and they certainly weren't MS-Windows.

These days, with RAM being cheap, my VM hosts have 32GB of RAM, but only because 16GB wasn't quite enough for the RAM load I had on them.
I'm running 5 VMs and 5 LXC containers on the same host today.

My nextcloud instance is inside an LXC container, installed using the nextcloud snap package with external storage assigned.  Because nextcloud is a snap, it updates whenever it damn well pleases, ignoring my attempts to prevent that.  I told it to stop upgraded a v24.x and never perform any major upgrade.  The nextcloud v25.x upgrade broke it for a few weeks.  Again, I told it never to update major releases.  Today it is running ...  let me check ... Nextcloud Hub 6 (27.1.1) ... after it was told never to perform any major release upgrades.  Sigh.  When v25 started working again, all the updates since then haven't broken the install, so I haven't noticed.
The memory use on that VM host:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi        22Gi       3.2Gi       192Mi       4.9Gi       7.5Gi
Swap:         4.1Gi       3.2Gi       931Mi
```
I've set the kernel vm.swappiness  parameter to 1, so the fact that 3.2G is being used when there is at least 8GB free is a bit troubling.  I have enough RAM that I don't want swap used until it is absolutely mandated to prevent a crash.  Sigh.  I had vm.swappiness set to 10 and found it was swapping too much when there was RAM available. Looks like I might need to set it to zero.

---

