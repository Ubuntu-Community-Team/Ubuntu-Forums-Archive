---
title: "Linux-6.2-rc1-Released"
date: 2022-12-26
forum: Ubuntu Development Version
---

### Post by zika on 2022-12-26
[https://www.phoronix.com/news/Linux-6.2-rc1-Released](https://www.phoronix.com/news/Linux-6.2-rc1-Released)
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.2-rc1/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.2-rc1/)
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.2-rc1/CHANGES](https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.2-rc1/CHANGES)
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.2-rc1/log](https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.2-rc1/log)
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.2-rc1/amd64/log](https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.2-rc1/amd64/log)

---

### Post by IanW on 2022-12-26
It's a shame Ubuntu's official stance on the mainline kernel builds failing is currently "[Won't Fix]("https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/88")".

---

### Post by Doug S on 2022-12-26
Using the "just accept default new kernel configuration parameters" method, I got this:

```
doug@s19:~/kernel/linux$ time make -j13 olddefconfig bindeb-pkg LOCALVERSION=-stock
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/confdata.o
  HOSTCC  scripts/kconfig/expr.o
  HOSTCC  scripts/kconfig/lexer.lex.o
  HOSTCC  scripts/kconfig/menu.o
  HOSTCC  scripts/kconfig/parser.tab.o
  HOSTCC  scripts/kconfig/preprocess.o
  HOSTCC  scripts/kconfig/symbol.o
  HOSTCC  scripts/kconfig/util.o
  HOSTLD  scripts/kconfig/conf
[COLOR="#FF0000"].config:8041:warning: symbol value 'm' invalid for USB_FOTG210_HCD
.config:8275:warning: symbol value 'm' invalid for USB_FOTG210_UDC[/COLOR]
#
# configuration written to .config
#
```But otherwise it compiled fine.

There are many default kernel configuration changes:

```
doug@s19:~/kernel/linux$ scripts/diffconfig | wc -l
121
```

Running now, but haven't tried anything yet:

```
doug@s19:~$ uname -a
Linux s19 6.2.0-rc1-stock #1100 SMP PREEMPT_DYNAMIC Mon Dec 26 07:46:55 PST 2022 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2022-12-26
> **IanW said:**
> It's a shame Ubuntu's official stance on the mainline kernel builds failing is currently "[Won't Fix]("https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/88")".Yes, agreed.

---

### Post by TenPlus1 on 2022-12-27
You would think that the Canonial team would be appreciative of users taking the time to install newer kernels for testing, and reporting any issues that are found, most especially the non-rc releases like 6.0, 6.1 and 6.1.1 stable.

---

### Post by fyfe54 on 2022-12-27
Very disappointing indeed.

---

### Post by Doug S on 2023-01-02
Right on schedule, [Kernel 6.2-rc2 has been released]("https://kernel.org/"). The compile still fails on the [Ubuntu kernel mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.2-rc2/").

```
doug@s19:~$ uname -a
Linux s19 6.2.0-rc2-stock #1101 SMP PREEMPT_DYNAMIC Mon Jan  2 11:03:14 PST 2023 x86_64 x86_64 x86_64 GNU/Linux
```

Other than compile and boot, I haven't done much with it yet.

---

### Post by zika on 2023-01-03
[https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/93](https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/93)

[https://www.thoughtco.com/the-meaning-of-ubuntu-43307](https://www.thoughtco.com/the-meaning-of-ubuntu-43307)

[https://youtu.be/y3KEhWTnWvE](https://youtu.be/y3KEhWTnWvE)[COLOR=#202124][FONT=arial][/FONT][/COLOR]

---

### Post by Doug S on 2023-01-03
See the [kernel team mailing list archives]("https://lists.ubuntu.com/archives/kernel-team/"), specifically [here]("https://lists.ubuntu.com/archives/kernel-team/2023-January/135809.html") and [here]("https://lists.ubuntu.com/archives/kernel-team/2023-January/135808.html").

---

### Post by zika on 2023-01-03
> **Doug S said:**
> See the [kernel team mailing list archives]("https://lists.ubuntu.com/archives/kernel-team/"), specifically [here]("https://lists.ubuntu.com/archives/kernel-team/2023-January/135809.html") and [here]("https://lists.ubuntu.com/archives/kernel-team/2023-January/135808.html").
I'm not writing about the person(s) that will, I'm sure, fix the things and to whom I'm sincerely grateful, for the future efforts as much for the past ones, but about the position (yes, I'm old enough to remember almost two decades ago when it was unthinkable to read that) that &#8220;[FONT=Ubuntu]Canonical has a business to run.&#8220;...
[SIZE=2]Sorry If my position was not clear enough, mea culpa. Hope it is now...

Update&#8321;:  linux-generic-wip just got upgraded at my place, see PPA given above in previous thread, I gave..., to 6.2.0-1... ;) Nice...
Update&#8322;: "*kernel does not provide EFI handover*" so I'll either have to hack a bit or wait for full implementation... 
[/SIZE]
[/FONT]

---

### Post by Doug S on 2023-01-09
Kernel 6.2-rc3 is available from the [Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.2-rc3/"). Finally.

EDIT: There are many kernel configuration changes between now and the one I was using for 6.2-rc2, which was just the accept defaults version of the last one we got from the Ubuntu mainline PPA (kernel 6.0 from October 2nd for me):

```
doug@s19:~/kernel/linux$ scripts/diffconfig .config-6.2-rc2 .config | wc -l
[COLOR="#FF0000"]128[/COLOR]
``` 

Rather by accident I noticed this:

```
doug@s19:~/kernel/linux$ ls -l -t /
total 2097244
drwxrwxrwt  12 root root       4096 Jan 10 08:01 tmp
drwxr-xr-x  28 root root        920 Jan 10 07:51 run
drwxr-xr-x   4 root root      20480 Jan 10 07:34 boot
[COLOR="#FF0000"]lrwxrwxrwx   1 root root         39 Jan 10 07:33 initrd.img -> boot/initrd.img-6.2.0-060200rc3-generic
lrwxrwxrwx   1 root root         33 Jan 10 07:33 initrd.img.old -> boot/initrd.img-5.15.0-53-generic
lrwxrwxrwx   1 root root         36 Jan 10 07:33 vmlinuz -> boot/vmlinuz-6.2.0-060200rc3-generic
lrwxrwxrwx   1 root root         30 Jan 10 07:33 vmlinuz.old -> boot/vmlinuz-5.15.0-53-generic[/COLOR]
drwxr-xr-x  20 root root       4520 Jan  2 11:07 dev
```which I do not understand.

---

### Post by IanW on 2023-01-10
Yay!

---

### Post by mIk3_08 on 2023-01-12
Oh, I'm sure if I do upgrade some of my attached devices won't run. :-D But its cool though. Regards and cheers.

---

### Post by zika on 2023-01-14
```

$uname -r
6.2.0-060200rc3daily20230114-generic
```
Thanks to everybody that made this possible. Nice work.

---

### Post by fyfe54 on 2023-01-15
RC-4 is available today n Mainline.

Thank you for resuming these builds.

---

### Post by #&amp;thj^% on 2023-01-23
Still no issue's here:
```
ii  linux-image-unsigned-6.2.0-060200rc5-generic                6.2.0-060200rc5.202301212030           amd64        Linux kernel image for version 6.2.0 on 64 bit x86 SMP

```
I can't run the Ubuntu Driver install so 
```
apt policy nvidia-driver
nvidia-driver:
  Installed: (none)
  Candidate: 510.108.03-3
  Version table:
     510.108.03-3 500

```
But:
```
nvidia-smi
Mon Jan 23 10:03:04 2023       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 525.85.05    Driver Version: 525.85.05    CUDA Version: 12.0     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0  On |                  N/A |
| N/A   42C    P0    15W /  50W |    856MiB /  4096MiB |     13%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      1515      G   /usr/lib/xorg/Xorg                675MiB |
|    0   N/A  N/A      2515      G   xfwm4                               2MiB |
|    0   N/A  N/A      7200      G   /usr/bin/firefox                  139MiB |
+-----------------------------------------------------------------------------+


```
Thanks ajgreeny ;)

---

### Post by Doug S on 2023-02-19
Kernel 6.2 has been released and is available from the [Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.2/").
While the master git tree has the 6.2 tag, [kernel.org]("https://kernel.org/") does not yet show it as having been released. I don't think I have ever seen that before.

```
doug@s19:~$ uname -a
Linux s19 6.2.0-stock #1107 SMP PREEMPT_DYNAMIC Sun Feb 19 16:50:16 PST 2023 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by xyz-t on 2023-02-19
Back to work the Debian way since rc4. All is good

```
$ uname -a
Linux n_u 6.2.0-060200-generic #202302191831 SMP PREEMPT_DYNAMIC Sun Feb 19 23:37:22 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
```

```
$ mokutil --sb
SecureBoot enabled
SecureBoot validation is disabled in shim
```

```
$ sudo fwupdmgr update
Devices with no available firmware updates:
 • SDSSDH3 256G
 • System Firmware
 • UEFI Device Firmware
 • UEFI Device Firmware
Devices with the latest available firmware version:
 • UEFI dbx
```

---

### Post by xyz-t on 2023-04-16
lunar-proposed:Synaptic > New in repository

Commit Log for Sun Apr 16 17:45:10 2023

Installed the following packages:
linux-headers-6.2.0-21 (6.2.0-21.21)
linux-headers-6.2.0-21-generic (6.2.0-21.21)
linux-image-6.2.0-21-generic (6.2.0-21.21)
linux-modules-6.2.0-21-generic (6.2.0-21.21)
linux-modules-extra-6.2.0-21-generic (6.2.0-21.21)

---

