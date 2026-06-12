---
title: "Why am I not using the latest kernel?"
date: 2013-04-09
forum: Ubuntu Development Version
---

### Post by stinkeye on 2013-04-09
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **sudo apt-get update && sudo apt-get upgrade**
[sudo] password for glen:

*< blah blah blah with no errors >*
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Rebooted and ran....
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **uname -a**
Linux Raring [COLOR="#FF0000"]3.8.0-13-generic[/COLOR] #23-Ubuntu SMP Mon Mar 18 18:09:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **dpkg-query -l 'linux-image*'**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                Version                Architecture           Description
+++-===================================-======================-======================-============================================================================
ii  linux-image                         3.8.0.17.32            amd64                  Generic Linux kernel image.
un  linux-image-3.0                     <none>                                        (no description available)
ii  linux-image-3.8.0-10-generic        3.8.0-10.19            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-11-generic        3.8.0-11.20            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-12-generic        3.8.0-12.21            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-13-generic        3.8.0-13.23            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-14-generic        3.8.0-14.24            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-15-generic        3.8.0-15.25            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-16-generic        3.8.0-16.26            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-17-generic        3.8.0-17.27            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-6-generic         3.8.0-6.13             amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-7-generic         3.8.0-7.15             amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-8-generic         3.8.0-8.17             amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-9-generic         3.8.0-9.18             amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-10-generic  3.8.0-10.19            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-11-generic  3.8.0-11.20            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-12-generic  3.8.0-12.21            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-13-generic  3.8.0-13.23            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-14-generic  3.8.0-14.24            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-15-generic  3.8.0-15.25            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-16-generic  3.8.0-16.26            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-17-generic  3.8.0-17.27            amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-6-generic   3.8.0-6.13             amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-7-generic   3.8.0-7.15             amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-8-generic   3.8.0-8.17             amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-9-generic   3.8.0-9.18             amd64                  Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic                 3.8.0.17.32            amd64                  Generic Linux kernel image
```

---

### Post by ptn107 on 2013-04-09
Restart and make sure you're selecting the latest kernel in the grub menu.

---

### Post by stinkeye on 2013-04-09
> **ptn107 said:**
> Restart and make sure you're selecting the latest kernel in the grub menu.
Have rebooted and grub only shows up to 3.8.0-13

---

### Post by stinkeye on 2013-04-09
> **ptn107 said:**
> Restart and make sure you're selecting the latest kernel in the grub menu.
Aha, thanks for the brain kickstart. #-o
I'm also running Quantal on a separate disk which is the default boot device and therefore using it's grub.
I booted into Quantal and ran **sudo update-grub** and am now using latest kernel.

```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **uname -a**
Linux Raring [COLOR="#FF0000"]3.8.0-17[/COLOR]-generic #27-Ubuntu SMP Sun Apr 7 19:39:35 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by PJs Ronin on 2013-04-09
have you tried [Boot Repair]("http://ubuntuforums.org/showthread.php?t=1769482&highlight=boot+repair").   Has saved my bacon many times.

---

### Post by stinkeye on 2013-04-09
Yes, I've used Boot Repair in the past and works well.
I'm on top of it now and could fix the kernel updating by selecting my Raring Drive as the boot device in the BIOS.
I remember now I left the Bios to boot into Quantal's grub because I had customized it and
hate the default purple grub screen.
Thanks for the help.

---

