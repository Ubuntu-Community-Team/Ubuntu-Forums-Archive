---
title: "Identifying root cause of constant jbd2 io activity"
date: 2017-04-28
forum: Server Platforms
---

### Post by s-braendlin on 2017-04-28
Hello together,
my new Ubuntu 16.04.2 LTS installation seems to constantly write on disk. I noticed this activity due to the hdd led blinking somehow periodically. Even if there are services running doing potential disj write, this closely periodic io seems suspicious.
I would like to analyse it further, but I dont have enough knowledge. I try to explain....

**Background**
I have moved from swraid 1 + lvm to swraid5 + swraid1 (boot) + lvm. This means I have root on lvm.

**Question1**
When watching iotop in the same time my hdd led is blinking, it mostly shows JBD2/dm-x-x is doing something. I know that jbd2 refers to journal and dm to device mapper. 
What means dm-x-x? My devices in /dev/dm-x have only one number...df does also not help...lsblk does not help.../proc/mdstat also not...

**Question2**
I disabled services that might be responsible for the disc activity and wachted for differences in iotop. I found out apache2 and mysql contribute quite much.
As this is trial n error (not very professional) I would like to know, if there is a way to find the true process causing jbd2 being active.

I like my current setup a lot and I am scared that in the end the only solution attempt I have is to reinstall everything.

Can someone help me out? Or maybe confidently tell me that this behaviour is quite normal!?

---

### Post by TheFu on 2017-04-28
It is probably normal.  Logs need to be written.  Depending on the time, day of the week, day of the month, differnent cleanup process can run automatically. Look in all the cron locations - /var/spool/cron/  /etc/cron.d/ etc.

There is also virtual memory. Things get swapped in and out all the time.  Network transfers can use disk buffers, until those buffers are cleared.  That can happen immediately or be delayed some minutes, based on how the system is tuned.

**lsof** can see which process is using which file, but you have to catch it at the correct instance. Use grep to filter.

Of course, if your server has apache running and it is on the internet, then any webapps or flawed configs could have allowed someone in. It is very hard to know if this has happened without having a way to compare the current files to some from yesterday, last week, last month.  Versioned backups are very useful for this sort of thing.  I was hacked back in 2002.  It wasn't hard to see exactly what had happened thanks to having a backup from 6 days earlier.  I could tell with certainty exactly which files had been touched and saw exactly where the hackers had placed their tools and attempted to gain root. Based on the ownership of those files, it was easy to see they'd gotten in through bind (a DNS server).  I disabled bind, wiped their tools and watched the system. Nothing changed for a few days, so I was confident my steps solved the issue.  

These days, that wouldn't be sufficient. The threat models are much more sophisticated. It isn't uncommon for someone to hack in and do nothing for months.  But if 1 guy got in, it is likely someone else will get in the same way too.  They might not be as patient and would probably try to use a Linux server for C&C or attacking others or spamming emails quickly. Just depends on their profit model.

---

