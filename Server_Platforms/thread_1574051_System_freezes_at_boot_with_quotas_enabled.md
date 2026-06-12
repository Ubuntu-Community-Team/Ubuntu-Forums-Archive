---
title: "System freezes at boot with quotas enabled"
date: 2010-09-13
forum: Server Platforms
---

### Post by ygoe on 2010-09-13
Hi,

I have set up a new server with Ubuntu 10.4 64-bit. Duringsetup I have modified the fstab file to enable user quota. But after the second restart, the system won't boot anymore. It worked directly after the change and quota was checked when the quota/quotatool package was installed then, but it won't boot anymore now. The last thing I see on the console is that it's checking quota. But I've seen the box freeze at other messages as well. Currently I can reliably have it freeze when quota shall be enabled.

The only way to boot the system is removing the usrquota mount option from the fstab file.

I have tried to run quotacheck manually from the provider's rescue system, mounting the filesystem with the appropriate options. That worked without any problem. It was finished after a few seconds. But at boot time the message stands there for more than minutes.

I've also read the notice about "journalquota", tried to find any information about it and the only bit of info about it was on this forum, along with some mount options. I also tried that but it changed nothing.

So what's up here? I've tested the setup at home (but with 32-bit Ubuntu and no RAID 1) and I could always boot the machine with no problems at all. In production environment it fails. Is quota not supported very well on 64 bit?

---

### Post by ygoe on 2010-09-14
I think it's not quota, it's "ubuntu-desktop" that causes the trouble. See [http://ubuntuforums.org/showthread.php?t=1574815](http://ubuntuforums.org/showthread.php?t=1574815)

---

### Post by kensuf on 2011-05-04
Just bumping this thread..  I experienced the same problem, and it's not 'ubuntu-desktop' but rather it appears to be the /etc/init.d/quota script.  At least that's how it is here...

In my case, we have a fairly large filesystem with quotas enabled, but our user account information is held in NIS.  The system is running LTS 10.04.  I was having problems with the system freezing during boot, locking up shortly after the quota (/etc/init.d/quota) startup script launches.

The quota startup script runs quotacheck with the '-augm' (all filesystems, user/group quotas, don't remount fs read-only) and then the '-uc' flags (create a new quota.user file from scratch), and that's where it freezes.

My "hack" to get the system up and running was to just bypass the quotacheck at boot by modifying the startup script, but that's not reasonable long-term.  However, I can run quotacheck once the system is up and running with no problems (huh, go figure), and traditionally run quotacheck weekly as a cronjob anyway.

My speculation is that quotacheck is freezing on boot because it couldn't find UID info on the files since NIS wasn't bound at the time of the check.  I'd imagine anyone using nis/ldap/kerberos or any other directory would run into similar problems.

Now that it's "the morning after", and I have a firm idea of what caused the problem, I'm putting it on my to-do list to bring up a test system and reproduce the error and finally resolve it..

So..   Workaround to get you up and running with quota's enabled, -- edit /etc/init.d/quota to prevent 'quotacheck' from running (leave quotaon).  My simple one-line hack was to modify the line 'check=/sbin/quotacheck' to 'check=/sbin/NOquotacheck'.  

Please note, this is not a realistic long-term solution as any update to the quota packages will probably over-write the startup script.

---

