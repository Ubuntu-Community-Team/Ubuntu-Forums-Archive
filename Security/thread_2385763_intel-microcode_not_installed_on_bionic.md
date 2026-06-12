---
title: "intel-microcode not installed on bionic"
date: 2018-02-24
forum: Security
---

### Post by corradoventu on 2018-02-24
On my PC different partitions I have Ubuntu Bionic installed from ISO of different dates. In the installation from the ISO dated 20171221 i have intel-microcode installed while i don't have it on the installation from the ISO dated 20180214, also iucode-tool is not installed.
Now my question: should intel-microcode be installed or not? I may install it via synaptic, should I install it or wait for the new one to be released by intel?

```
corrado@corrado-p7-bb-dic17:~$ cat /var/log/installer/media-info
Ubuntu 18.04 LTS "Bionic Beaver" - Alpha amd64 (20171221)
corrado@corrado-p7-bb-dic17:~$ apt policy intel-microcode
intel-microcode:
  Installed: 3.20180108.1+really20171117.1
  Candidate: 3.20180108.1+really20171117.1
  Version table:
 *** 3.20180108.1+really20171117.1 500
        500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-p7-bb-dic17:~$ apt policy iucode-tool
iucode-tool:
  Installed: 2.3.1-1
  Candidate: 2.3.1-1
  Version table:
 *** 2.3.1-1 500
        500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-p7-bb-dic17:~$ inxi -SCx
System:    Host: corrado-p7-bb-dic17 Kernel: 4.15.0-10-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.26.2 (Gtk 3.22.28-1ubuntu3)
           Distro: Ubuntu Bionic Beaver (development branch)
CPU:       Dual core Intel Core i3-7100 (-MT-MCP-) arch: Skylake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15648
           clock speeds: max: 3900 MHz 1: 938 MHz 2: 3216 MHz 3: 3218 MHz 4: 2714 MHz
corrado@corrado-p7-bb-dic17:~$
corrado@corrado-p3-bb:~$ cat /var/log/installer/media-info
Ubuntu 18.04 LTS "Bionic Beaver" - Alpha amd64 (20180214)
corrado@corrado-p3-bb:~$ cat /var/log/installer/apt policy intel-microcode
intel-microcode:
  Installed: (none)
  Candidate: 3.20180108.1+really20171117.1
  Version table:
     3.20180108.1+really20171117.1 500
        500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages
corrado@corrado-p3-bb:~$ apt policy iucode-tool
iucode-tool:
  Installed: (none)
  Candidate: 2.3.1-1
  Version table:
     2.3.1-1 500
        500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages
corrado@corrado-p3-bb:~$ inxi -SCx
System:    Host: corrado-p3-bb Kernel: 4.15.0-10-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.26.2 (Gtk 3.22.28-1ubuntu1)
           Distro: Ubuntu Bionic Beaver (development branch)
CPU:       Dual core Intel Core i3-7100 (-MT-MCP-) 
           arch: Skylake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15648
           clock speeds: max: 3900 MHz 1: 2496 MHz 2: 1881 MHz 3: 1831 MHz
           4: 1852 MHz
corrado@corrado-p3-bb:~$
```

---

### Post by Frogs Hair on 2018-02-24
Intel microcode is not installed by default and is offered as a choice in additional drivers.

---

### Post by corradoventu on 2018-02-24
intel-microcode has been automatically installed by apt updates on my Artful Aardvark on same PC different partition

```
corrado@corrado-p6-aa:~$ cat /var/log/installer/media-info
Ubuntu 17.10 "Artful Aardvark" - Release amd64 (20171018)
corrado@corrado-p6-aa:~$ apt policy intel-microcode
intel-microcode:
  Installed: 3.20180108.0+really20170707ubuntu17.10.1
  Candidate: 3.20180108.0+really20170707ubuntu17.10.1
  Version table:
 *** 3.20180108.0+really20170707ubuntu17.10.1 500
        500 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu artful-security/main amd64 Packages
        100 /var/lib/dpkg/status
     3.20170707.1 500
        500 http://archive.ubuntu.com/ubuntu artful/restricted amd64 Packages
corrado@corrado-p6-aa:~$ apt policy iucode-tool
iucode-tool:
  Installed: 2.1.2-2
  Candidate: 2.1.2-2
  Version table:
 *** 2.1.2-2 500
        500 http://archive.ubuntu.com/ubuntu artful/restricted amd64 Packages
        500 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-p6-aa:~$ inxi -SCx
System:    Host: corrado-p6-aa Kernel: 4.13.0-36-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.2 (Gtk 3.22.25-0ubuntu0.1)
           Distro: Ubuntu 17.10
CPU:       Dual core Intel Core i3-7100 (-HT-MCP-) 
           arch: Skylake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15648
           clock speeds: max: 3900 MHz 1: 3900 MHz 2: 3900 MHz 3: 3900 MHz
           4: 3900 MHz
corrado@corrado-p6-aa:~$
```

---

### Post by Frogs Hair on 2018-02-24
It may have changed then, I installed manually after the spectre/meltdown announcement and it has been optional on all my previous installations.I'm not sure the update manager system could determine what cpu is in use. I know there were updates to microcode package after I installed it.

---

### Post by mc4man on 2018-02-24
automatically installed does not mean default installed. 
If you install intel-microcode then iucode-tool is installed as a depend (and marked auto
If you were to  install iucode-tool first then intel-microcode would be installed as a recommend & marked auto.

So the later is possibly what you did..
In any event doesn't much matter as neither is on the 18.04 image so one or the other must be installed by the user in one way or another. Also the current micro-code doesn't do much as far as those spectre bugs but has value in other area's

edit: I guess if the 3rd party option is enabled during install then maybe those packages are installed ??, no idea as I never have used that option & never will.

---

### Post by corradoventu on 2018-02-24
Yes, 3rd party option was enabled during install, do you suggest not to do it?
on my Artful i got intel-microcode installed by unattended-upgrade

```
Start-Date: 2018-01-14  15:45:33
Commandline: /usr/bin/unattended-upgrade
Upgrade: intel-microcode:amd64 (3.20170707.1, 3.20180108.0~ubuntu17.10.1)
End-Date: 2018-01-14  15:45:57

Start-Date: 2018-01-23  08:38:11
Commandline: apt upgrade
Requested-By: corrado (1000)
Install: linux-image-extra-4.13.0-31-generic:amd64 (4.13.0-31.34, automatic), linux-headers-4.13.0-31-generic:amd64 (4.13.0-31.34, automatic), linux-headers-4.13.0-31:amd64 (4.13.0-31.34, automatic), linux-image-4.13.0-31-generic:amd64 (4.13.0-31.34, automatic), linux-signed-image-4.13.0-31-generic:amd64 (4.13.0-31.34, automatic)
Upgrade: intel-microcode:amd64 (3.20180108.0~ubuntu17.10.1, 3.20180108.0+really20170707ubuntu17.10.1), linux-headers-generic:amd64 (4.13.0.30.32, 4.13.0.31.33), grub-common:amd64 (2.02~beta3-4ubuntu7, 2.02~beta3-4ubuntu7.1), linux-image-generic:amd64 (4.13.0.30.32, 4.13.0.31.33), linux-signed-image-generic:amd64 (4.13.0.30.32, 4.13.0.31.33), grub2-common:amd64 (2.02~beta3-4ubuntu7, 2.02~beta3-4ubuntu7.1), linux-signed-generic:amd64 (4.13.0.30.32, 4.13.0.31.33), grub-efi-amd64-bin:amd64 (2.02~beta3-4ubuntu7, 2.02~beta3-4ubuntu7.1), openssh-client:amd64 (1:7.5p1-10, 1:7.5p1-10ubuntu0.1), grub-efi-amd64:amd64 (2.02~beta3-4ubuntu7, 2.02~beta3-4ubuntu7.1), grub-efi-amd64-signed:amd64 (1.85+2.02~beta3-4ubuntu7, 1.85.1+2.02~beta3-4ubuntu7.1), linux-generic:amd64 (4.13.0.30.32, 4.13.0.31.33)
End-Date: 2018-01-23  08:44:56
```

thanks for the clarifications

---

### Post by DuckHook on 2018-02-24
Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar. And also please refrain from using nonstandard fonts or styles, especialy in [CODE] boxes, which changes the output.

---

### Post by mc4man on 2018-02-24
> **corradoventu said:**
> Yes, 3rd party option was enabled during install, do you suggest not to do it?
on my Artful i got intel-microcode installed by unattended-upgrade


In artful unattended-upgrade upgraded it, it was already installed. (basically the upgrade just reverted the microcode to previous  as it was determined to be too buggy.
There are 2 reasons I don't use 3rd party or allow any upgrades at all during the install.
1. I'd rather do myself any such installs or updates after the main install is done rather than let the installer decide what to install.
2. Maybe it's just me but over the last couple of years I've noticed that one can get a really slow connection to Ubuntu servers at times. For ex. I may start an upgrade of a bunch of packages & see 200 KiB/sec or lower. Generally then I cancel, wait a few seconds &  do again, usually then at several MiB/sec or higher.
If the poor connection occurred during install rather than a couple of minutes to install Ubuntu it may take 15-20 or more.

---

