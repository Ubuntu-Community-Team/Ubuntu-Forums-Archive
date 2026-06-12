---
title: "Upgrade 22.04 to 24.04"
date: 2024-05-10
forum: Server Platforms
---

### Post by mandycuba1985 on 2024-05-10
Is 24.04 still not available for servers?
when I try:
```

root@mta:~# apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@mta:~# do-release-upgrade
Checking for a new Ubuntu release
There is no development version of an LTS available.
To upgrade to the latest non-LTS development release
set Prompt=normal in /etc/update-manager/release-upgrades.
root@mta:~# uname -a
Linux mta 6.8.4-2-pve #1 SMP PREEMPT_DYNAMIC PMX 6.8.4-2 (2024-04-10T17:36Z) x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by deadflowr on 2024-05-10
From 22.04 the upgrade to 24.04 will not be available until the first point release sometime in August.
Possibly earlier with the -d flag.

It's been this way for over a decade now.

---

### Post by MAFoElffen on 2024-05-12
I'm in the middle of testing that (DEV) process for the upgrade path from 22.04.4 LTS Server to 24.04 LTS... with a challenge for it:
Ubuntu Server Edition 22.04.4 LTS, with ZFS-On_Root Encrypted, to 24.04 LTS

Not going to work at this time.

The usual method for server is to install update-manager-core and do do-release-upgrade... That does not see the LTS until the .1 point release. It is not even close yet.

For earlier, we usually add the -d to search for interim versions. Right now, that finds nothing.

BUT-- It's still broke.

Even straight from 22.04 to 24.04 via the 'debian release upgrade' method is broken right now. 

Even going from Jammy to Mantic has some problems at the moment. It would not upgrade to Mantic via 'do-release-upgrade' right not. That seems to be turned off. I could only do that via the 'debian release upgrade' to Mantic, and that had problems which I had to fix manually during and after the install process. Once I got to there, I could do 'do-release-upgrade -d' to Noble. After the Release Upgrade, there were still things that had to be changed manually, for Noble to be Noble.

That Server use-case is Noble now. But it took "advanced skills" to get there. Something in the differences between the Jammy and Noble Repo's does not install the needed toolset to create the initramfs image for kernel 6.8.0. (If you go straight from Jammy to Noble.) But going from Mantic to Noble does work. If 22.04.4 is ZFS, then bpool needs enough room in it for the newer boot files, and to update the symlinks. Some cleanup there is required to make that room, before the process starts. I also did an 'apt autoremove' before each of the jumps... And unistalled some old kernels that were there, to make extra room.

*** I would NOT recommend to the new to mid-level skilled User to do that right now... Wait for some changes.

---

### Post by #&amp;thj^% on 2024-05-12
> **MAFoElffen said:**
> 

*** I would NOT recommend to the new to mid-level skilled User to do that right now... Wait for some changes.
I Certainly Concur, not for the faint of heart.

---

### Post by MAFoElffen on 2024-05-12
Note: 1fallen was privy to the results/details of those tests. 

If you tried what I did, you would be quickly be posting back asking for help to recover from what it does. That is just honesty, and reality.

It was harder than it even was to do normal DEV Cycle testing = more work-arounds needed to get it to work.

---

