---
title: "Processor Virtualization"
date: 2013-12-18
forum: Virtualisation
---

### Post by smwinterstein on 2013-12-18
Hello all!

What is the suggestion on running Processor Virtualization, and does this help the system run better or is it useless unless your using a virtualization setup, where you running virtual machines inside a server instance? I leave it off.

Off topic but whats the best Partition format to use, in Ubuntu 13.10? I understand many aspects of the configyuration, managment, setup of servers and env. but Ubuntu is new to me so a few grey areas I need help understanding a little better, so if someone would help its much appreciated.

Scott

---

### Post by CharlesA on 2013-12-18
If you are talking about hardware virtualzation support from the CPU, it can improve the performance of your VMs because the virtualization is handed by hardware not software.

So far I haven't found a reason to turn it off, even when I'm not running virtualization.

---

### Post by TheFu on 2013-12-18
@Charles nailed it on the 1st question.

On the 2nd one, the short answer is ext4, but there is a much, much longer answer that depends on what the system is used for, how many files will be stored, how large those files will be, how critical is the data being stored (home stuff or $1M/sec of downtime), what sort of performance is needed, is de-duplication desired, what about encryption?

So - you probably want to use ext4 for now and research "linux file system" at wikipedia to get a little more information for the future.

---

### Post by CharlesA on 2013-12-18
> **TheFu said:**
> On the 2nd one, the short answer is ext4, but there is a much, much longer answer that depends on what the system is used for, how many files will be stored, how large those files will be, how critical is the data being stored (home stuff or $1M/sec of downtime), what sort of performance is needed, is de-duplication desired, what about encryption?

So - you probably want to use ext4 for now and research "linux file system" at wikipedia to get a little more information for the future.

Whoops I totally missed that bit. I've been running ext4 for a long time and so far I haven't run into any problems with it. There are a few others like ZFS and BTRFS, but I have stuck with ext4 because it works for what I use it for.

---

