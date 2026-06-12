---
title: "Server 18.04.3 GRUB problem preventing updates"
date: 2020-02-13
forum: Server Platforms
---

### Post by vellofrell on 2020-02-13
This is a similar problem others have encountered, but none of my troubleshooting has worked so far. When running ```
sudo apt upgrade dist
```[COLOR=#000000][FONT=Menlo]
[SIZE=3][FONT=Helvetica]- I get the following error:[/FONT][/SIZE][/FONT][/COLOR][SIZE=3]
[/SIZE][COLOR=#000000][FONT=Menlo][SIZE=4]
[/SIZE][/FONT][/COLOR]```
[COLOR=#000000][FONT=Menlo]Removing linux-image-4.4.0-171-generic (4.4.0-171.200) ...[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]/etc/kernel/postrm.d/initramfs-tools:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]update-initramfs: Deleting /boot/initrd.img-4.4.0-171-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/etc/kernel/postrm.d/x-grub-legacy-ec2:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Searching for GRUB installation directory ... found: /boot/grub[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Searching for default file ... found: /boot/grub/default[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Testing for an existing GRUB menu.lst file ... [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) /usr/sbin/update-grub-legacy-ec2: line 1101: read: read error: 0: Bad file descriptor[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]run-parts: /etc/kernel/postrm.d/x-grub-legacy-ec2 exited with return code 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]**dpkg:** error processing package linux-image-4.4.0-171-generic (--remove):[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] installed linux-image-4.4.0-171-generic package post-removal script subprocess returned error exit status 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Errors were encountered while processing:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] linux-image-4.4.0-171-generic[/FONT][/COLOR]

[COLOR=#000000][FONT=Menlo]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT][/COLOR]
```[COLOR=#000000][FONT=Menlo][SIZE=4]


[/SIZE][/FONT][/COLOR]I have tried some basic grub updating tips seen from the forums but haven&#8217;t been successful pinning down the problem. I'm still fairly novice with admin work on my own server. I'll add 'journalctl -xb' output if it helps. I'm sure it reveals more than one problem. Are there other logs I should post?

```
Jan 24 21:25:47 server kernel: Couldn't get size: 0x800000000000000e
Jan 24 21:25:47 server kernel: MODSIGN: Couldn't get UEFI db list
Jan 24 21:25:47 server kernel: Couldn't get size: 0x800000000000000e


Jan 24 21:25:47 server kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 24 21:25:47 server kernel: No Local Variables are initialized for Method [_GTF]
Jan 24 21:25:47 server kernel: No Arguments are initialized for method [_GTF]
Jan 24 21:25:47 server kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.PRT4._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 24 21:25:47 server kernel: ata5.00: supports DRM functions and may not be fully accessible
Jan 24 21:25:47 server kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 24 21:25:47 server kernel: No Local Variables are initialized for Method [_GTF]
Jan 24 21:25:47 server kernel: No Arguments are initialized for method [_GTF]
Jan 24 21:25:47 server kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.PRT3._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 24 21:25:47 server kernel: ata5.00: disabling queued TRIM support
Jan 24 21:25:47 server kernel: ata5.00: ATA-9: Samsung SSD 850 EVO 250GB, EMT03B6Q, max UDMA/133
Jan 24 21:25:47 server kernel: ata5.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
Jan 24 21:25:47 server kernel: ata4.00: ATA-10: ST12000NM0007-2A1101, SN02, max UDMA/133
Jan 24 21:25:47 server kernel: ata4.00: 23437770752 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jan 24 21:25:47 server kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 24 21:25:47 server kernel: No Local Variables are initialized for Method [_GTF]
Jan 24 21:25:47 server kernel: No Arguments are initialized for method [_GTF]
Jan 24 21:25:47 server kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.PRT4._GTF, AE_NOT_FOUND (20170831/psparse-550)
Jan 24 21:25:47 server kernel: ata5.00: supports DRM functions and may not be fully accessible
Jan 24 21:25:47 server kernel: ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Jan 24 21:25:47 server kernel: No Local Variables are initialized for Method [_GTF]
Jan 24 21:25:47 server kernel: No Arguments are initialized for method [_GTF]
Jan 24 21:25:47 server kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.PRT3._GTF, AE_NOT_FOUND (20170831/psparse-550)


Jan 24 21:25:49 server ovpn-server2[1373]: Options error: In [CMD-LINE]:1: Error opening configuration file: /etc/openvpn/server2.conf


Jan 24 21:25:49 server systemd[1]: Failed to start OpenVPN connection to server2.

```



[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]

---

### Post by darkod on 2020-02-13
First check which grub version you have installed (legacy or uefi):
```
apt-cache policy grub-pc
apt-cache policy grub-efi
```

Post the output here.

---

### Post by vellofrell on 2020-02-13
> **darkod said:**
> First check which grub version you have installed (legacy or uefi):
```
apt-cache policy grub-pc
apt-cache policy grub-efi
```

Post the output here.



```
[COLOR=#000000][FONT=Menlo]$ [/FONT][/COLOR][COLOR=#000000][FONT=Menlo]apt-cache policy grub-pc[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]grub-pc:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  Installed: (none)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  Candidate: 2.02-2ubuntu8.14[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  Version table:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]     2.02-2ubuntu8.14 500[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]     2.02-2ubuntu8 500[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages[/FONT][/COLOR]
```


```
[COLOR=#000000][FONT=Menlo]$ apt-cache policy grub-efi[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]grub-efi:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  Installed: (none)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  Candidate: 2.02-2ubuntu8.14[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  Version table:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]     2.02-2ubuntu8.14 500[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]     2.02-2ubuntu8 500[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages[/FONT][/COLOR]
```


Thanks!
(I probably messed up the bootloader when something went wrong trying to clone my boot drive using Clonezilla.)

---

### Post by TheFu on 2020-02-13
**sudo apt upgrade dist**
is not a valid command set with correct options.

I suspect you want
```
sudo apt update
sudo apt dist-upgrade
```
The first command needs to be run with in an hour or so of the 2nd command to ensure the repository information is current.  Other distros, like CentOS and RHEL do the update automatically. Ubuntu does not.

Lets try my two command first, then we can look at issues.  The 2nd command might require/suggest a reboot after it completes.

But running the correct commands is the first step.

---

### Post by vellofrell on 2020-02-13
> **TheFu said:**
> **sudo apt upgrade dist**
is not a valid command set with correct options.

I suspect you want
```
sudo apt update
sudo apt dist-upgrade
```
The first command needs to be run with in an hour or so of the 2nd command to ensure the repository information is current.  Other distros, like CentOS and RHEL do the update automatically. Ubuntu does not.

Lets try my two command first, then we can look at issues.  The 2nd command might require/suggest a reboot after it completes.

But running the correct commands is the first step.

Sounds good, thanks. Here's what I'm seeing:

```
[COLOR=#000000][FONT=Menlo]sudo apt update[/FONT][/COLOR][COLOR=#000000][FONT=Menlo][sudo] password for 'USER': [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Hit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Get:2 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Get:3 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]         [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Get:4 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]       [COLOR=#AAAB25]          [/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Get:5 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [853 kB][COLOR=#AAAB25]           [/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Get:6 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [642 kB][COLOR=#AAAB25]          [/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Get:7 http://us.archive.ubuntu.com/ubuntu bionic-updates/main Translation-en [298 kB][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Get:8 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [1,049 kB][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Get:9 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [1,008 kB][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Get:10 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe Translation-en [324 kB][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Get:11 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [636 kB][COLOR=#AAAB25]  [/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Get:12 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages [437 kB][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Get:13 http://security.ubuntu.com/ubuntu bionic-security/main Translation-en [208 kB][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Get:14 http://security.ubuntu.com/ubuntu bionic-security/universe i386 Packages [617 kB][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Get:15 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [645 kB][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Get:16 http://security.ubuntu.com/ubuntu bionic-security/universe Translation-en [217 kB][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Fetched 7,185 kB in 2s (4,571 kB/s)[COLOR=#AAAB25]                              [/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Building dependency tree       [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Reading state information... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]30 packages can be upgraded. Run 'apt list --upgradable' to see them.[/FONT][/COLOR]
```

and...

```
[COLOR=#000000][FONT=Menlo]$ sudo apt dist-upgrade[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Building dependency tree       [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Reading state information... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Calculating upgrade... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]The following packages will be REMOVED:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  linux-image-4.4.0-171-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]The following packages will be upgraded:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  base-files bsdutils fdisk libblkid1 libdrm-common libdrm2 libfdisk1 libmount1 libnss-systemd libpam-systemd libsasl2-2 libsasl2-modules libsasl2-modules-db[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  libsmartcols1 libsystemd0 libudev1 libuuid1 libxml2 mdadm mount python3-distupgrade sudo systemd systemd-sysv ubuntu-release-upgrader-core ubuntu-server[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  ubuntu-standard udev util-linux uuid-runtime[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]30 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]2 not fully installed or removed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Need to get 0 B/8,090 kB of archives.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]After this operation, 7,199 kB disk space will be freed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Do you want to continue? [Y/n][/FONT][/COLOR][COLOR=#000000][FONT=Menlo] [/FONT][/COLOR]
```


```
[COLOR=#000000][FONT=Menlo]Do you want to continue? [Y/n] Y[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]Preconfiguring packages ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo](Reading database ... 126164 files and directories currently installed.)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Removing linux-image-4.4.0-171-generic (4.4.0-171.200) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/etc/kernel/postrm.d/initramfs-tools:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]update-initramfs: Deleting /boot/initrd.img-4.4.0-171-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/etc/kernel/postrm.d/x-grub-legacy-ec2:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Searching for GRUB installation directory ... found: /boot/grub[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Searching for default file ... found: /boot/grub/default[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Testing for an existing GRUB menu.lst file ... [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) /usr/sbin/update-grub-legacy-ec2: line 1101: read: read error: 0: Bad file descriptor[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]run-parts: /etc/kernel/postrm.d/x-grub-legacy-ec2 exited with return code 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]**dpkg:** error processing package linux-image-4.4.0-171-generic (--remove):[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] installed linux-image-4.4.0-171-generic package post-removal script subprocess returned error exit status 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Errors were encountered while processing:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] linux-image-4.4.0-171-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT][/COLOR]
```

...is it a typo in the grub file? If so, wondering on best way to edit and repair?

---

### Post by TheFu on 2020-02-13
/boot/grub/menu.lst  gets created either by **grub-install** or **update-grub** commands. I don't know which.

Whenever I've seen a post-removal script error,  usually have to either create an empty file with the name/location that script seeks 
or
edit the script causing the problem to stop doing that.  Think I've done both of these, combined, across 30+ systems just about 5 times total the last 15 yrs. That's just 5 issues, not 30x5. I wouldn't pretend to explain to someone else how to edit any script like this. Usually takes me a few trial and error attempts.  

A few months ago, I wiped out my /boot/ area completely.  /boot/ is not an area that I backup, so a quick restore wasn't possible.  I was careful after the mistake not to reboot, then did a grub-install /dev/sdb and an update-grub. sdb is where that system boots.  That system is uefi running 16.04 server.  You could try that.

---

### Post by vellofrell on 2020-02-14
> **TheFu said:**
> /boot/grub/menu.lst  gets created either by **grub-install** or **update-grub** commands. I don't know which.

Whenever I've seen a post-removal script error,  usually have to ether create an empty file with the name/location that script seeks 
or
edit the script causing the problem to stop doing that.  Think I've done both of these, combined, across 30+ systems about 5 times. I wouldn't pretend to explain to someone else how to edit any script like this. Usually takes me a few trial and error attempts.  

A few months ago, I wiped out my /boot/ area completely.  /boot/ is not an area that I backup, so a quick restore wasn't possible.  I was careful after the mistake not to reboot, then did a grub-install /dev/sdb and an update-grub.  That system is uefi running 16.04 server.  You could try that.

Thanks Fu. I needed to make a blank file that was listed as needed in all of the output. Then running your suggestion of **update-grub** and selecting the package maintainer's version instead of the local one has fixed the issue. Everything is up to date and I successfully rebooted. Thanks for the tips, cheers!

---

