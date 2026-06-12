---
title: "Fork bombs"
date: 2011-03-18
forum: Security
---

### Post by Muster Mark on 2011-03-18
Hi All,

So I am basically just curious about this, but is there a way to prevent fork bombs from bringing the system to grinding halt in Ubuntu, without setting hard limits on the resources available to users?  I read about fork bombs on Wikipedia, and being the masochist I am (and not having any unsaved work), I tried entering those 13 characters into terminal.  Wow.  I have never seen a computer freeze up so fast.

What really peaked my curiosity is that the same fork bomb has almost no effect on the performance of Mac OSX (10.6).  I know that one can limit the availability of resources to specific users.  Is that essentially what Snow Leopard is doing?  Anyway, just curious.

Cheers!

---

### Post by handy on 2011-03-18
The wiki page tells how to prevent them from taking over a machine.

They are unlikely to truly be a problem in the real Linux world I think.

---

### Post by Soul-Sing on 2011-03-18
Do you want us to "test" forkbombs?
No need to: they destroy systems. What sort of support do you need in this thread? More powerful/more destructive strings?

---

### Post by Netaro on 2011-03-18
> **leoquant said:**
> Do you want us to "test" forkbombs?
No need to: they destroy systems. What sort of support do you need in this thread? More powerful/more destructive strings?

Uhm, what? How can a forkbomb destroy a system? All a forkbomb does is exhaust system's resources till it halts. It takes one reboot to stop it. Unless I'm mistaken, am I?

---

### Post by Grenage on 2011-03-18
You can set limits:

[http://www.cyberciti.biz/tips/linux-limiting-user-process.html](http://www.cyberciti.biz/tips/linux-limiting-user-process.html)

---

### Post by wojox on 2011-03-18
> **Muster Mark said:**
> 

What really peaked my curiosity is that the same fork bomb has almost no effect on the performance of Mac OSX (10.6).

I don't know to much about Mac's. Did you run it as a normal user or super user?

---

### Post by CharlesA on 2011-03-18
> **Netaro said:**
> Uhm, what? How can a forkbomb destroy a system? All a forkbomb does is exhaust system's resources till it halts. It takes one reboot to stop it. Unless I'm mistaken, am I?

If it's done on a production system, or a system that has unsaved data, you can lose data or cause data corruption since the only "fix" is an unsafe reboot.

---

### Post by Soul-Sing on 2011-03-18
It is a "force" crash, with a forced restart, and huge change of dataloss and possible massive systemfaillure(s).
There is nothing more to say bout this.

---

### Post by Muster Mark on 2011-03-18
so it looks like limiting resources is the way to go.

---

### Post by bodhi.zazen on 2011-03-18
> **CharlesA said:**
> If it's done on a production system, or a system that has unsaved data, you can lose data or cause data corruption since the only "fix" is an unsafe reboot.

> **leoquant said:**
> It is a "force" crash, with a forced restart, and huge change of dataloss and possible massive systemfaillure(s).
There is nothing more to say bout this.

======

Short version - To make a long post short, in my experience and IMHO, massive data loss would be extremely unlikely following a fork bomb or power loss. I have only had this happen one time in many years of power loss / abusing virtual machines and that was with xfs. There are (old) reports of data loss with ext4, but I think that has been addressed.

======

Usually there will be no ill effect from a forkbomb. Occasionally there will be some data loss fsck can not fix, typically this would be for any files that have been edited in the last minute or so, perhaps longer with removable media.

Catastrophic system failure (damage to RAM , Hard drive, etc) / data loss is possible, but would be rare. 

Note: IMO, some file systems, xfs in particular, are more vulnerable then others. I am not sure if xfs has been "patched", but last time I used xfs was a few years ago (prior to the fix referenced in the link) and I did have significant data loss after a power loss (which is essentially what a fork bomb does).

[http://xfs.org/index.php/XFS_FAQ#Q:_Why_do_I_see_binary_NULLS_in_some_files_after_recovery_when_I_unplugged_the_power.3F](http://xfs.org/index.php/XFS_FAQ#Q:_Why_do_I_see_binary_NULLS_in_some_files_after_recovery_when_I_unplugged_the_power.3F)

Anyone else recall when XFS was all the rage ?

ext4 also had similar behavior, see bug reports on launchpad.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781)

See also [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/118](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/118)

This problem with ext4 has also (in theory) been addressed, or at least I have not had a problem with ext4 =). I have a SOHO server, the uptime was almost a year at one time, then I acquired a cat, and I have 4 small children. The cat likes to chew power cords, the children like to push flashing lights / power buttons. So yes, there have been lapses in power no power backup can prevent. This server has lost power so many times I can not count.

Some people claim jfs is a better option.

[http://www.wilderssecurity.com/showthread.php?t=236457](http://www.wilderssecurity.com/showthread.php?t=236457)

Honestly I have not tested the various file systems myself (I tend to use ext4 , btrfs , or jfs) but I do run virtual machines, many of which lock up or are abused (not properly shut down) and I have not had a problem with significant data loss using ext4 or jfs. I do not use btrfs very much in virtual machines, but as it is the new kid on the block, I would avoid it for now if you are concerned with data loss and power loss / fork bombs. 

Perhaps someone with more experience with btrfs and unexpected power loss can comment ?

To answer the question, limiting resources is the only way to limit a fork bomb. Fork bombs, by definition, use all available resources. If you set a limit, they will rapidly use what resources you have allowed them. If you have set a limit, you can then kill it as root.

The problem is that the typical limits suggested are very stingy and often your users would not be able to run X for example.

I highly advise you fire up KVM/ virtualbox and run a few fork bombs. Set some limits and then try again. Once you have set a limit, reboot and make sure the system functions normally ;)

In general, fork bombs would be run by local users (not many want to crack your box from remote simply to run a form bomb, lol). If you can not trust your local users, you have more problems then forkbombs.

---

### Post by nerdy_kid on 2011-03-18
I heard that Ubuntu's kernel will kill the fork bomb if you let it run for around 5 mins.  I have yet to test this though.

---

### Post by CharlesA on 2011-03-18
I don't think there are limits on processes set by default, but I'd rather not try it :P

---

### Post by bodhi.zazen on 2011-03-19
> **nerdy_kid said:**
> I heard that Ubuntu's kernel will kill the fork bomb if you let it run for around 5 mins.  I have yet to test this though.

You are probably correct

See: [http://www.linux.com/community/blogs/security-tip-avoid-fork-bombing-on-popular-distro-check-your-system.html](http://www.linux.com/community/blogs/security-tip-avoid-fork-bombing-on-popular-distro-check-your-system.html)

In Ubuntu 10.04 , on the live CD, ulimit is unlimited. fork bomb locked up the live CD in a few seconds.

The 10.10 desktop cd did not boot, so I am not sure about natty.

My host is Fedora 14 and Fedora set a limit to 1024 (probably more appropriate for a desktop then the low number [300-500] often posted in various blogs).

---

### Post by nerdy_kid on 2011-03-19
> **bodhi.zazen said:**
> You are probably correct

See: [http://www.linux.com/community/blogs/security-tip-avoid-fork-bombing-on-popular-distro-check-your-system.html](http://www.linux.com/community/blogs/security-tip-avoid-fork-bombing-on-popular-distro-check-your-system.html)

In Ubuntu 10.04 , on the live CD, ulimit is unlimited. fork bomb locked up the live CD in a few seconds.

The 10.10 desktop cd did not boot, so I am not sure about natty.

My host is Fedora 14 and Fedora set a limit to 1024 (probably more appropriate for a desktop then the low number [300-500] often posted in various blogs).

I just gave the fork bomb a run last night (without checking the limits first, like an idiot) and I have never seen this laptop lock up so fast!  The kernel key combos still worked though, I restarted the laptop via <alt> <sysrq> REISIUB even after 10 minutes of the bomb running. 

This is a much easier way to see if the fork bomb will run forever :lol:

```

nerdy_kid@laptop:~$ ulimit -u
unlimited
nerdy_kid@laptop:~$

```

---

### Post by CharlesA on 2011-03-19
Checked my server install and ulimit -u is set to unlimited too. I'll have to fix that.

---

