---
title: "/var/run/reboot-required never created when updating kernel etc"
date: 2024-05-14
forum: Server Platforms
---

### Post by superian on 2024-05-14
This is similar to [https://ubuntuforums.org/showthread.php?t=2475383](https://ubuntuforums.org/showthread.php?t=2475383) except that no Ubuntu LTS version update has ever been done.

I have several VPSes running Ubuntu 22.04. On one, which was created just over a year ago, the /var/run/reboot-required file is never created when a reboot is in fact needed.

The apt-get system recognises that a reboot is required after a kernel update and prompts me to do so, but looking at the results of auditd monitoring what happens to the reboot-required file, it is simply never created.

All the other VPSes are fine in this regard. All have [FONT=courier new]update-notifier-common[/FONT] installed. All have the [FONT=courier new]/run -> /var/run[/FONT] symlink.

This VPS has some (but not all) Ubuntu Advantage services enabled..

```
# pro status
SERVICE          ENTITLED  STATUS       DESCRIPTION
anbox-cloud      yes       disabled     Scalable Android in the cloud
esm-apps         yes       enabled      Expanded Security Maintenance for Applications
esm-infra        yes       enabled      Expanded Security Maintenance for Infrastructure
livepatch        yes       enabled      Canonical Livepatch service
realtime-kernel  yes       disabled     Ubuntu kernel with PREEMPT_RT patches integrated

```

.. the others do not. 

**Is this the cause?**

 If not, what else could be?

---

### Post by TheFu on 2024-05-14
I don't know.

I do know that I updated 3 22.04 servers this weekend and all of them had the file created.  I have a tiny script that just looks for that file and tells me that a reboot is needed based on the existence of the FILE="/var/run/reboot-required" file.  Actually, I just loop over all my systems, ssh to them and run 
```
   ls -l $FILE 2> /dev/null
```
I can't remember any time when this didn't work in the last 10 yrs on any Debian/Ubuntu system - server or desktop.  So, I think you have some other issue.  The first step is to patch and fully patch.
> no Ubuntu LTS version update has ever been done.
Perhaps I misunderstand this, but you should be patching weekly.  
```
sudo apt update
sudo apt upgrade
```
Every week.  Be certain to have recent, versioned, backups before doing that.

---

### Post by superian on 2024-05-14
> **TheFu said:**
> Perhaps I misunderstand this, but you should be patching weekly.  

What I meant is that, unlike the other system having this problem in the linked to post, this one has never gone from 20.04 LTS to 22.04 LTS - it was installed as the latter at the start.

> ```
sudo apt update
sudo apt upgrade
```
Every week.

Ne'er fear: there's a cron job that does this rather more frequently than that.

---

### Post by TheFu on 2024-05-14
> **superian said:**
> What I meant is that, unlike the other system having this problem in the linked to post, this one has never gone from 20.04 LTS to 22.04 LTS - it was installed as the latter at the start.



Ne'er fear: there's a cron job that does this rather more frequently than that.

Ah. Thanks for the clarification.  BTW, I don't patch more than weekly to limit interrupting in productivity.  Sometimes the first patch released breaks things and they have to rush a new patch out.  By patching on only weekends, I avoid those early, bad, updates.  Same for snaps packages. I prevent them from running until Saturday - again, to maximize productivity, while still being updated in a timely way.

To each their own.

---

### Post by superian on 2024-05-14
> **superian said:**
> This VPS has some (but not all) Ubuntu Advantage services enabled..

.. the others do not. 

**Is this the cause?**

Doing more searching on launchpad reveals that, yes, it is: livepatch broke the behaviour of creating the reboot-required file when a reboot is necessary despite its best efforts.

---

### Post by TheFu on 2024-05-14
The point of livepatch is that new kernels can be installed and used without any reboot needed.  

Technology like this has actually existed on IBM Mainframes since the early 1980s.  It really came down to IBM creating multiple hook points before and after every system call that made it possible.  Most of the time, they are just null pointers and not called.

Before and after every kernel service function, there is placed an internal function pointer that can call the new function in the newer kernel.  At the end of the function, it returns back to the old kernel end of that function and returns the expected results to the calling program.  I've oversimplified it, of course.  Finding all the function pointers and replaceing them in Linux isn't as trivial.  But, from a high-level, this is how live-patch works.

---

