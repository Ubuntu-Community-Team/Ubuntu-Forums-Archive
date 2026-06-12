---
title: "Load issue with Ubuntu 16.04 rigth after installation"
date: 2016-11-01
forum: Server Platforms
---

### Post by da.bernie on 2016-11-01
Hello to everybody,

I am currently faced with an issue on a HP Mircoserver I cannot identify the root cause.

The machine should be used to provide storage via samba for backup propose. Samba is working fine. When I test to access the shares, I can copy files on it, I can read everything. It does what i expect. But when the clients are accessing the shares with the backup tool (ArcServe Workstation) I get in 80% an failure. Either the share i not fund, a file could be created and others. So I started to have a deeper look what is going on. One straight thing is that the system is having a constant system load of 1 without doing anything (just one process running: top). There is no disk activity, no network or cpu load.

Because I don't want to mess up the "running" system, I did an fresh installation on a different disk. I wanted so see if one of the installed services is causing the load behavior. But the surprise was, even the fresh installation is running with a load of 1! So I can remove some points from my list: some hackers are using my system, any services I added, and configuration changes I did.
 
Then I checked what is happening with a 14.04 installation. Same procedure, new disk, new installation, reboot and then: The load on the system is, as expected, around 0. So the hardware is not causing the problem.

Back with the fresh 16.04 system i checked the log files (kern.log, system.log, dmesg). Nothing special, nothing unexpected.

So that's the point I am now. I am missing any hint to get more information's to solve the load thing. Nothing in the log's, even google isn't my friend. but maybe somebody in the forum could give me some advice.

I can post some log files and further information's on demand.

Thanks for your support

da.bernie

---

### Post by Doug S on 2016-11-04
Hi, and welcome to Ubuntu forums.

You mentioned "top", but it doesn't provide you any insight?

One (of many) possibilities, is something stuck in uninterruptable sleep. do you get consistently anything for this (do it several times)?:```
ps -e -o state,pid,cmd | grep ^D
```

---

### Post by da.bernie on 2016-11-07
Hi Doug,

thanks for the hint with the ps command. I have learned something new about the uninterruptable sleep, but in my current case there is no process in this state.

Actually I came one step forward with first topic, the samba behavior. It was caused by the fact that the server wasn't in the AD-domain. Now samba is a domain member server an everything is fine. Why it was working one day and not the next, I don't know.

The load topic is still open.

Any new idea's?

---

