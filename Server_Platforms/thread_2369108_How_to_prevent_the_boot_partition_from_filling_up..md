---
title: "How to prevent the /boot partition from filling up."
date: 2017-08-18
forum: Server Platforms
---

### Post by codycoder2 on 2017-08-18
I've had this problem with ubuntu servers 11 through to current and I'm embarrassed to say, I've never figured out how to prevent this issue.

My environments are always headless & virtual. I don't use landscape. I always use LTS kernels and when I setup the machines, I sometimes choose "automatic security updates" and sometimes I don't and just update manually.  I never enable root.

So what happens is that I will log into a machine and the login message will state that the boot portion is xx.x % full.  

By the time I notice it, is usually something really scarily like 99.6%.

When this happens, you can't use apt-get autoremove, autoclean etc.  Well, depending on how full the boot partition is, and if there are any missing depen

---

### Post by codycoder2 on 2017-08-18
I've had this problem with ubuntu servers 11 through to current and I'm embarrassed to say, I've never figured out how to prevent this issue.

My environments are always headless & virtual. I don't use landscape. I always use LTS kernels and when I setup the machines, I sometimes choose "automatic security updates" and sometimes I don't and just update manually.  I never enable root.

So what happens is that I will log into a machine and the login message will state that the "boot portion is xx.x % full."

By the time I notice it, is usually something really scary like "99.6%".

When this happens, you can't use apt-get autoremove, autoclean etc. Well, depending on how full the boot partition is, and if there are any missing dependancies etc. It's not a guarantee that the package manager's utility will solve the problem, and for me, it often doesn't. Annoyingly, the warning doesn't seem to appear until boot is over 90% full.

I resort to using a variety of tools (like dkpg and purge etc) to remove the old kernels and free up space. I've been very lucky so far.

I know Monit can look for a reboot message and send me emails and maybe landscape can also warn me.

What I am looking for is the *right workflow that prevents this from happening in the first place*.

I don't favour the idea of enabling root so that I can have a cron job that updates, autocleans, auto removes and reboots of there is a pending reboot in */var/run/reboot-required* but I can't think of another way.

I would like to understand why this happens.

I mentioned that I sometimes setup with *no automatic updates* at all and the problem still happens.  At least my memory tells me this..

So.. 

Does anyone out there have a preventative strategy / workflow for this that doesn't involve enabling root or 3rd party tools?

Thank you.

---

### Post by darkod on 2017-08-18
From my experience /boot fills up with the kernels mostly, because other packages don't go into /boot.

So, the procedure would be:

1. You don't have to install each kernel after it is released (most of them need to be installed manually because they are not into security updates, so you control how many and when to install).
2. After each 2-3 kernel updates, run apt-get autoremove to remove old kernels. That will keep /boot low.

And the final advice is probably what should be in the first place: don't be lazy and don't use the guided methods for partitioning. You should really use your own partitioning layout on servers as a general rule. The small /boot is only a problem with the guided partitioning, or if you don't housekeep with autoremove for long time. Creating manually /boot partition of 2-3GB would easily solve any issues you might be having if the /boot is 200-300MB.

---

### Post by ajgreeny on 2017-08-18
Threads merged.
**Please do not create duplicate posts;** it is confusing for all including you and dilutes the forum's ability to help.

---

### Post by LHammonds on 2017-08-18
FYI - You don't have to "enable root" to utilize root cron jobs.  Most of the jobs that run on my servers are done using the root cron, yet you cannot login to the server using root.  Just use "sudo su" to switch into the root account for elevated privilege use when needed.

I use a custom-made script to handle my apt updates/upgrades and log the results.  It is scheduled to run each day.

You could also make a reboot script that looks for the presence of that /var/run/reboot-required file and have the server automatically reboot.  You'd obviously schedule it some time after the apt upgrade script.

When I create my servers, I use LVM to manage the space used and I create 500MB /boot partitions which seem to be large enough for me...but I also keep my servers fully patched with the latest kernel updates.

Everything I do is documented step-by-step on [my forum]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220").

LHammonds

---

### Post by cariboo on 2017-08-18
I use a utility called ucaresystem-core, available [here]("https://utappia.org/2016/03/28/ucaresystem-core-v3-0-released-and-available-in-ppa/"). I just run it manually once a week, but it can be set up as a cron job to run automagically.

The utility checks for updates, downloads and installs them, then removes unneeded kernels, and package downlods.

---

