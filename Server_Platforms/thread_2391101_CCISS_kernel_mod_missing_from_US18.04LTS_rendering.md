---
title: "CCISS kernel mod missing from US18.04LTS rendering server unbootable after upgrade"
date: 2018-05-05
forum: Server Platforms
---

### Post by DerPC on 2018-05-05
I have a HP server which has a P800 SCSI controller. The CCISS kernel module is required to run the server.

On a server I have running 16.04 LTS, the module lives in /lib/modules/4.4.0-103-generic/kernel/drivers/block/cciss.ko and is by default part of the initrd. After upgrading a server that was also running 16.04 LTS to 18.04 LTS (using do-release-upgrade -d) the system has been rendered unbootable since grub doesn't have all modules loaded to mount the rootfs.

Is the module in some other package which needs to be installed?

Is Canonical aware of this? (as in, was this a conscious decision?) If so, what's the reasoning behind removing the module? If removing the module was intended, why is the package "cciss-vol-status" still offered?

This server is an Amanda backup server, so this is more than a mere annoyance - if I can't find a solution I'll have to revert it to 16.04 LTS - but it also rules out Ubuntu on half my network. The reason however for the requirement of upgrade is that Amanda had started to exhibit regression errors which weren't being fixed in 16.04 LTS.

Anyone with knowledge, please advise.

---

### Post by DerPC on 2018-05-05
Fwiw:

> 
[FONT=monospace][COLOR=#000000]server > uname -a && cat /etc/issue[/COLOR]
linux thjalfi 4.15.0-20-generic #21-ubuntu smp tue apr 24 06:16:15 utc 2018 x86_64 x86_64 x86_64 gnu/linux
ubuntu 18.04 lts \n \l

server > apt-file find cciss.ko
server >
[/FONT]

---

### Post by DerPC on 2018-05-05
And a search with apt-file on 16.04 LTS shows that 16.04 LTS has the CCISS module in 4.13.0-39.

---

### Post by LHammonds on 2018-05-06
I don't run on bare-metal but I figured I can run the same commands on my 16.04 and 18.04 VMs and let you see the results I get.  (which are the same)

[SIZE=5]Ubuntu Server 16.04.4 LTS[/SIZE]

Show running kernel version (which is current)
```
# uname -a
Linux srv-ubuntu1604 4.4.0-122-generic #146-Ubuntu SMP Mon Apr 23 15:34:04 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

Show release name/version/codename
```
# lsb_release -a
Description:    Ubuntu 16.04.4 LTS
Codename:       xenial
```

Install apt-file which is not installed by default
```
# apt-get install apt-file
```

Update the apt-file cache
```
# apt-file update
```

Search for the cciss.ko file specific to the currently-running kernel
```
# apt-file find cciss.ko | grep 4.4.0-122
linux-image-4.4.0-122-lowlatency: /lib/modules/4.4.0-122-lowlatency/kernel/drivers/block/cciss.ko
linux-image-extra-4.4.0-122-generic: /lib/modules/4.4.0-122-generic/kernel/drivers/block/cciss.ko
```

[SIZE=5]Ubuntu Server 18.04 LTS[/SIZE]

NOTE: I used the "alternative" ISO image to install the server, not the "live" variation.

Show running kernel version (which is current)
```
# uname -a
Linux srv-ubuntu1804 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

Show release name/version/codename
```
# lsb_release -a
Description:    Ubuntu 18.04 LTS
Codename:       bionic
```

Install apt-file which is not installed by default
```
# apt-get install apt-file
```

Update the apt-file cache
```
# apt-file update
```

Search for the cciss.ko file specific to the currently-running kernel
```
# apt-file find cciss.ko | grep 4.15.0-20
```

>> Nothing found <<

Search for the cciss.ko file for any kernel.
```
# apt-file find cciss.ko
```

>> Nothing found <<

---

### Post by DerPC on 2018-05-06
Yes, that's exactly what I found.

*however*

On my NON-P800 (just normal SATA) personal HP server, I have 18.04 running as well. On that server I tried:

> 
[FONT=monospace][COLOR=#54FF54]**admin@thjalfi**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ man cciss     <---- man page IS found[/COLOR]
[COLOR=#54FF54]**admin@thjalfi**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ modprobe cciss[/COLOR]
modprobe: ERROR: could not insert 'hpsa': Operation not permitted
[COLOR=#54FF54]**admin@thjalfi**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sudo modprobe cciss[/COLOR]
[/FONT][FONT=monospace][COLOR=#54FF54]**admin@thjalfi**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sudo lsmod | egrep "(hpsa|cciss)"[/COLOR]
[sudo] password for admin:  
[COLOR=#FF5454]**hpsa**[/COLOR][COLOR=#000000]                   98304  0[/COLOR]
scsi_transport_sas     40960  1 [COLOR=#FF5454]**hpsa**[/COLOR]
[/FONT]

So they alias the cciss to hpsa - but the hpsa doesn't support the P800 and P400...

I'm getting close to yelling and screaming because I really do not want to have to re-invent my backup server 20 days before vacation with a different OS...

---

### Post by DerPC on 2018-05-06
According to the Kernel list ( [https://patchwork.kernel.org/patch/9947333/](https://patchwork.kernel.org/patch/9947333/) ) CCISS was removed in favor of HPSA. Support for "SOME" boards was added, including (alledgedly)
> 
[COLOR=#007F00]> +    Smart Array P400[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#007F00]> +    Smart Array P400i[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#007F00]> +    Smart Array P600[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#007F00]> +    Smart Array P700m[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#007F00]> +    Smart Array P800
[/COLOR][COLOR=#000000]

Apparently this is a Linus-****up, not a Canonical one since the alledgedly supported boards don't work "as advertised".

So these machines are at EOL where Linux is concerned (unless I find a magic way to fix this) - I thought it would be a cold
day in Hell when I found a machine that had a longer life with Windows than with Linux. And this is the second machine I find
that Linu[sx] has "given up on". I guess that explains the sleet, hail, snow and rain outside my window.[/COLOR]

---

### Post by DerPC on 2018-05-07
Ok, I think an unlikely source has ***maybe*** come up with a solution.

[https://www.linuxquestions.org/questions/slackware-14/slackware-kernel-4-14-0-unable-to-mount-root-fs-on-hp-cciss-4175617797/](https://www.linuxquestions.org/questions/slackware-14/slackware-kernel-4-14-0-unable-to-mount-root-fs-on-hp-cciss-4175617797/)

Apparently the hpsa driver *renames* the devices. Oh yay. And no, using the **UUID** doesn't work (that is what was failing at the beginning).

Now I'm torn between finding a solution to this problem ( cciss vs. hpsa ) or this problem ( [https://ubuntuforums.org/showthread.php?t=2391175](https://ubuntuforums.org/showthread.php?t=2391175) - fixing Amanda and staying at 16.04 )

---

### Post by DerPC on 2018-05-07
As an afterthought - the linuxquestions "solution" really isn't, since I can't even see any devices when booting from a USB stick using 18.04 LTS.  The USB stick drops into GRUB/initramfs as well.

---

### Post by roby-programmer on 2018-05-16
> **DerPC said:**
> As an afterthought - the linuxquestions "solution" really isn't, since I can't even see any devices when booting from a USB stick using 18.04 LTS.  The USB stick drops into GRUB/initramfs as well.

Same problem here, HP Proliant ML350 G5, controller P400, last working kernel from ubuntu ppa kernel and kernel.org (build by myself) is 4.13.16, from kernel >= 4.14.1 don't boot, I have opened also a bug on bugzilla.kernel, and also read of someone opening a bug on launchpad


kernel issue

---

### Post by DerPC on 2018-05-16
Yes and a pretty lame one at that. One would have expected a more professional approach from the kernel team than just "meh, it probably works".

---

### Post by LHammonds on 2018-05-16
Well, you still have support/patches for Ubuntu Server 16.04 until 2021 so I'd recommend staying on that until 18.04 works...and open a case with them to get functional support added back in.

LHammonds

---

### Post by DerPC on 2018-05-16
> **LHammonds said:**
> Well, you still have support/patches for Ubuntu Server 16.04 until 2021 so I'd recommend staying on that until 18.04 works...and open a case with them to get functional support added back in.

LHammonds

Another way (and the one I'm taking) is staying on 16.04 until I get a new machine as a backup server. That should happen a lot sooner than CCISS being incorporated into 4.15+ or HPSA properly supporting CCISS :)

---

### Post by LHammonds on 2018-05-16
> **DerPC said:**
> Another way (and the one I'm taking) is staying on 16.04 until I get a new machine as a backup server. That should happen a lot sooner than CCISS being incorporated into 4.15+ or HPSA properly supporting CCISS :)
That is a solid plan as well.
  :guitar:

---

### Post by roby-programmer on 2018-05-17
> **LHammonds said:**
> That is a solid plan as well.
  :guitar:

I hope kernel team solve it soon, same situation here

---

### Post by LHammonds on 2018-05-17
> **roby-programmer said:**
> I hope kernel team solve it soon, same situation here
They cannot solve it if it isn't reported.  Not sure if they browse these forums.

---

### Post by roby-programmer on 2018-05-17
> **LHammonds said:**
> They cannot solve it if it isn't reported.  Not sure if they browse these forums.

It was reported :

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1765105](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1765105)

my report on kernel.org:
[https://bugzilla.kernel.org/show_bug.cgi?id=199703](https://bugzilla.kernel.org/show_bug.cgi?id=199703)

as I have written

Anyway I am using Ubuntu server 18.04 LTS with Kernel 4.13.16...

Sorry for my bad English

---

