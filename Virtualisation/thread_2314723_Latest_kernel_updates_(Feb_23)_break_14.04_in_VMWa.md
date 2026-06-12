---
title: "Latest kernel updates (Feb 23) break 14.04 in VMWare"
date: 2016-02-23
forum: Virtualisation
---

### Post by DigiAngel on 2016-02-23
Topic says it...first time I've seen something like this, so I hope I'm reporting this correctly/in the right place.  After doing a dist-upgrade as shown below,

```
Start-Date: 2016-02-23  04:59:47
Commandline: apt-get -y dist-upgrade
Install: linux-image-extra-3.19.0-51-generic:amd64 (3.19.0-51.57~14.04.1, automatic), linux-image-3.19.0-51-generic:amd64 (3.19.0-51.57~14.04.1, automatic), linux-headers-3.19.0-51-generic:amd64 (3.19.0-51.57~14.04.1, automatic), linux-headers-3.19.0-51:amd64 (3.19.0-51.57~14.04.1, automatic)
Upgrade: cpio:amd64 (2.11+dfsg-1ubuntu1.1, 2.11+dfsg-1ubuntu1.2), linux-image-generic-lts-vivid:amd64 (3.19.0.49.34, 3.19.0.51.36), linux-headers-generic-lts-vivid:amd64 (3.19.0.49.34, 3.19.0.51.36), linux-generic-lts-vivid:amd64 (3.19.0.49.34, 3.19.0.51.36), linux-libc-dev:amd64 (3.13.0-77.121, 3.13.0-79.123)
End-Date: 2016-02-23  05:00:16

```

the new 3.19.0.51 kernel does not boot and hangs at ACPI in the console.  This is VMWare 12.1.0 running on Ubuntu 14.04 as the host OS.  The previous kernel boots just fine.  Do I report this anywhere else or is this good enough?  Thank you.

---

### Post by Aker666 on 2016-02-23
I can confirm that problem. Today I updated Ubuntu and after ask for reboot, VMWare stuck in "resolving restore state".... I couldn't fix it so I installed Ubuntu again and tried to update it. It broken again... I'm using VMWare 12.1 on Windows 10 64 bits.

---

### Post by cengizhan.yuecel on 2016-02-23
I can confirm the problem, too. VM boot gets stuck using kernel 3.19.0-51. VM boot works using older kernel 3.19.0-49. Problem seems to affect virtual machines only.

---

### Post by DigiAngel on 2016-02-23
Thanks for the verification all..appreciate it.

---

### Post by Philippe_Deslongch on 2016-02-23
VMware workstation 10 on windows 7. Tried two clean installs with exact same results.

---

### Post by Taman_Shud on 2016-02-23
Confirmed. Occurs post aptitude kernel update in both 14.04 LTS and 15.10.

---

### Post by alexander-zeitler on 2016-02-23
Ran into the same issue: After installing linux-image-extra-3.19.0-51-generic on Ubuntu 14.04 LTS in a VMware Workstation 11 on Windows 10 system hangs.
There seem to be more people affected over at askubuntu.com: [http://askubuntu.com/questions/738083/ubuntu-14-04-4-lts-hangs-on-boot-after-latest-dist-upgrade](http://askubuntu.com/questions/738083/ubuntu-14-04-4-lts-hangs-on-boot-after-latest-dist-upgrade)

---

### Post by ajgreeny on 2016-02-23
I presume you could all still run and boot using an earlier kernel from the grub menu?

---

### Post by NuSkooler on 2016-02-23
Myself (Elementary OS Freya x86_64) and a college (Ubuntu) both got the update today causing this. So +1 :) VMWare 9.x under Windows 10.1 x86_64 in both cases.

EDIT: Using previous kernel works.

---

### Post by alexander-zeitler on 2016-02-24
Yes, moving back to an old Kernel works.

---

### Post by DigiAngel on 2016-02-24
Yes, older kernel works just fine.

---

### Post by lauwers on 2016-02-24
Same problem here. All my Ubuntu VMs now hang (on VMware Player) after latest upgrade.

---

### Post by bilal8 on 2016-02-24
Any update? I am having the same issues.

---

### Post by bialix on 2016-02-25
The same problem here.

---

### Post by Grgoire on 2016-02-25
Same problem, VMWare stuck after "Stopping System V... [OK]" with 3.19.0-51.

I am able to start Ubuntu with 3.19.0-49 using shift/grub. Thank you Forum for this workaround, I didn't know old versions are still available. Good job !

Regards,
Grégoire.

---

### Post by alexmurray on 2016-02-25
Filed a bug - feel free to add any information there so this can get some attention from the Ubuntu devs.

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1550090](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1550090)

---

### Post by atul-raut on 2016-02-26
I am also getting the same error while boot up.

---

### Post by jrh31 on 2016-02-28
Today correction published
Kernel 3.19.0-51.57 replaced by 3.19.0-51.58
Start on  kernel 3.19.0-49 and apt-get update + upgrade works fine for me

---

### Post by Grgoire on 2016-03-16
Hi !
I updated today : problem fixed. Thank you !
Regards,
Grégoire.

---

