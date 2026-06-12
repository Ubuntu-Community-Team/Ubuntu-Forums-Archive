---
title: "KVM - host and virtual XP instance mount same partition"
date: 2009-04-14
forum: Virtualisation
---

### Post by suggsjc on 2009-04-14
I just got a new laptop for work, and I've previously  been running Ubuntu but (for many [political] reasons) I'm going to need to be able to run XP as the host operating system...at least some of the time.

So, is it possible to create two partitions, one for XP and one for Ubuntu.  At boot time I choose between XP and Ubuntu.  If XP, then it mounts its partition and ignores the Ubuntu partition.  If I boot Ubuntu, it mounts its partition and can read the XP side...nothing too fancy yet.

Here is my question.  When I boot into Ubuntu can I start a virtual instance of XP that mounts its real/local partition?  Basically meaning that the **same XP partition** will *either* be mounted by a host XP instance or a virtual XP instance.  Just for further clarification, the XP installation wouldn't know/care if it was being run as the host or virtualized as it would always be mounting the same partition.

If this is possible, can you point me to some basic documentation?  This would be a HUGE plus if this is possible...

---

### Post by veloce on 2009-04-20
> **suggsjc said:**
> So, is it possible to create two partitions, one for XP and one for Ubuntu.  At boot time I choose between XP and Ubuntu.  If XP, then it mounts its partition and ignores the Ubuntu partition.  If I boot Ubuntu, it mounts its partition and can read the XP side...nothing too fancy yet.

Yes, this is known as dual-booting.  If you install Ubuntu after XP then the installer will set it all up for you.

> **suggsjc said:**
> Here is my question.  When I boot into Ubuntu can I start a virtual instance of XP that mounts its real/local partition?  Basically meaning that the **same XP partition** will *either* be mounted by a host XP instance or a virtual XP instance.  Just for further clarification, the XP installation wouldn't know/care if it was being run as the host or virtualized as it would always be mounting the same partition.

Yes, this is theoretically possible.  There are two issues: 
[LIST=1]
[*]You must not have the XP partition mounted under Ubuntu at the same time as it is loaded as a virtual machine.
[*]Windows activation software thinks the virtual and actual machines are different.  Every time you switch from one to the other it will want to be re-activated.  There are some work arounds but it is basically a real pain. You'll probably want to settle on one method or the other.
[/LIST]

> **suggsjc said:**
> 
If this is possible, can you point me to some basic documentation?  This would be a HUGE plus if this is possible...

Start with the virtualisation mega-thread.

---

