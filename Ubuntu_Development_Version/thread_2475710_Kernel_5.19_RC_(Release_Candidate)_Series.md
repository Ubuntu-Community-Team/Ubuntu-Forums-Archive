---
title: "Kernel 5.19 RC (Release Candidate) Series"
date: 2022-06-05
forum: Ubuntu Development Version
---

### Post by Doug S on 2022-06-05
Kernel 5.19-rc1 should be available shortly.

The kernel configuration has automatically changed considerably between kernel 5.18 and 5.19-rc1.

While I know nothing about most areas of the kernel, I do know that the behaviour of "/sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq" is changing for X86 based computers. It will become pretty much like "grep MHz /proc/cpuinfo" again. Why? Because if the frequency value is stale (outdated) an idle CPU will not be woken up just to determine it's operating CPU frequency. Instead the nominal value will be returned. Examples for a relatively idle test server with 12 CPUs:

First, Kernel 5.18:
```

doug@s19:~/kernel/linux$ [COLOR="#FF0000"]uname -a[/COLOR]
Linux s19 [COLOR="#FF0000"]5.18.0-stock[/COLOR] #1058 SMP PREEMPT_DYNAMIC Mon May 23 07:42:44 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux
doug@s19:~/kernel/linux$ [COLOR="#FF0000"]grep MHz /proc/cpuinfo[/COLOR]
cpu MHz         : 4100.000
cpu MHz         : 4100.000
cpu MHz         : 4100.000
cpu MHz         : 4100.000
cpu MHz         : 4100.000
cpu MHz         : 4100.000
cpu MHz         : 4100.000
cpu MHz         : 4100.000
cpu MHz         : 800.093
cpu MHz         : 800.056
cpu MHz         : 800.029
cpu MHz         : 4100.000
doug@s19:~/kernel/linux$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq[/COLOR]
800233
800239
800122
800084
800517
801667
799822
800232
800367
800856
800188
800042

```
And now with a kernel very close to 5.19-rc1:
```

doug@s19:~/kernel/linux$ [COLOR="#FF0000"]uname -a[/COLOR]
Linux s19 5.18.0-test #1060 SMP PREEMPT_DYNAMIC Sun Jun 5 11:09:15 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux [COLOR="#FF0000"]<<< close to 5.19-rc1[/COLOR]
doug@s19:~/kernel/linux$ [COLOR="#FF0000"]grep MHz /proc/cpuinfo[/COLOR]
cpu MHz         : 4100.000
cpu MHz         : 4100.000
cpu MHz         : 800.001
cpu MHz         : 4100.000
cpu MHz         : 4100.000
cpu MHz         : 4100.000
cpu MHz         : 4100.000
cpu MHz         : 4100.000
cpu MHz         : 4100.000
cpu MHz         : 4100.000
cpu MHz         : 800.166
cpu MHz         : 4100.000
doug@s19:~/kernel/linux$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq[/COLOR]
4100000
4100000
4100000
799943
4100000
4100000
4100000
4100000
800051
4100000
800007
4100000

```

The usual link back trail to previous rc series threads:
[5.18]("https://ubuntuforums.org/showthread.php?t=2473417"),[5.17]("https://ubuntuforums.org/showthread.php?t=2471193"),[5.16]("https://ubuntuforums.org/showthread.php?t=2468916"),[5.15]("https://ubuntuforums.org/showthread.php?t=2466991"),[5.14]("https://ubuntuforums.org/showthread.php?t=2464835"),[5.13]("https://ubuntuforums.org/showthread.php?t=2461891"), [5.12]("https://ubuntuforums.org/showthread.php?t=2458625"), [5.11]("https://ubuntuforums.org/showthread.php?t=2455791"), [5.10]("https://ubuntuforums.org/showthread.php?t=2452692"), [5.9]("https://ubuntuforums.org/showthread.php?t=2448933"), [5.8]("https://ubuntuforums.org/showthread.php?t=2445465"), [5.7]("https://ubuntuforums.org/showthread.php?t=2440607"), [5.6]("https://ubuntuforums.org/showthread.php?t=2436608"), [5.5]("https://ubuntuforums.org/showthread.php?t=2432815"), [5.4]("https://ubuntuforums.org/showthread.php?t=2428734"), [5.3]("https://ubuntuforums.org/showthread.php?t=2423441"), [5.2]("https://ubuntuforums.org/showthread.php?t=2419363"), [5.1]("https://ubuntuforums.org/showthread.php?t=2414938"), [5.0]("https://ubuntuforums.org/showthread.php?t=2409811"), [4.20]("https://ubuntuforums.org/showthread.php?t=2405365"), 4.19 ?, [4.18]("https://ubuntuforums.org/showthread.php?t=2394500"), [4.17]("https://ubuntuforums.org/showthread.php?t=2389561"), [4.16]("https://ubuntuforums.org/showthread.php?t=2384781"), [4.15]("https://ubuntuforums.org/showthread.php?t=2378956"), [4.14]("https://ubuntuforums.org/showthread.php?t=2371638").

---

### Post by zika on 2022-06-05
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.19-rc1/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.19-rc1/)
Incoming... Hopefully... ;)

---

### Post by Doug S on 2022-06-05
Seems the same build error from [5.18-rc2]("https://ubuntuforums.org/showthread.php?t=2473417&p=14089926#post14089926") has returned.

Compiling myself, I have:

```
doug@s19:~$ [COLOR="#FF0000"]uname -a[/COLOR]
Linux s19 [COLOR="#FF0000"]5.19.0-rc1-stock[/COLOR] #1061 SMP PREEMPT_DYNAMIC Sun Jun 5 20:55:38 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by xyz-t on 2022-06-06
3 Kernels the same day, 5.17 is now part of history.



 ```
Operating System: Arch  kde unstable
KDE Plasma Version: 5.25.80
KDE Frameworks Version: 5.95.0
Qt Version: 5.15.4
Kernel Version: 5.19-rc1
Graphics Platform: Wayland
```

God bless the qween,

EDIT: Got a wifi issue, speed is at low (20-1) in Google-chrome unstable (Version 104.0.5098.0). Plus, getting a message for some sites: *This site can be reached*. All is normal with 5.18.2.
 
Edit 2: It appears to be back to normal now.

---

### Post by zika on 2022-06-07
```
uname -r
5.19.0-051900rc1daily20220607-generic
```

---

### Post by Doug S on 2022-06-12
Kernel 5.19-rc2 has been released. Ubuntu mainline should pick it up shortly. I wonder if the amd64 version will compile, as the daily seems somewhat hit and miss.

```
doug@s19:~$ uname -a
Linux s19 5.19.0-rc2-stock #1062 SMP PREEMPT_DYNAMIC Sun Jun 12 16:27:48 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux
```

There were a couple more automatic kernel configuration changes.

EDIT: ... later... [The Ubuntu mainline amd64 build failed]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.19-rc2/").

---

### Post by Doug S on 2022-06-19
Kernel 5.19-rc3 has been released. The [Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.19-rc3/") build actually worked this week.

I have been using the default kernel configuration changes ever since kernel 5.18. There seems to be 57 additional kernel configuration changes that Ubuntu has made:

```
doug@s19:~/kernel/linux$ scripts/diffconfig .config-5.19-rc3-1 .config-5.19-rc3-2 | wc -l
57
``` I don't know that there is any value added in listing them herein, it's just an observation. They are mostly additions, and the kernel ends up 1 megabyte larger.

```
doug@s19:~$ uname -a
Linux s19 5.19.0-rc3-stock2 #1065 SMP PREEMPT_DYNAMIC Sun Jun 19 17:11:07 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux

doug@s19:~/kernel$ ls -l linux-image-5.19.0-rc3*
-rw-r--r-- 1 doug doug [COLOR="#FF0000"]78244468[/COLOR] Jun 19 17:30 linux-image-5.19.0-rc3-stock2_5.19.0-rc3-stock2-1065_amd64.deb
-rw-r--r-- 1 doug doug [COLOR="#FF0000"]77248596[/COLOR] Jun 19 15:54 linux-image-5.19.0-rc3-stock_5.19.0-rc3-stock-1064_amd64.deb
```

---

### Post by xyz-t on 2022-06-19
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.19-rc3/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.19-rc3/)
Edit: We were there at the same time. The daily kernel worked one day this week.

---

### Post by corradoventu on 2022-07-10
Kernel 5.19 in proposed: [https://launchpad.net/ubuntu/kinetic/+package/linux-image-generic](https://launchpad.net/ubuntu/kinetic/+package/linux-image-generic)

---

### Post by IanW on 2022-07-11
RC6 is out

[https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.19-rc6-Released](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.19-rc6-Released)

EDIT: However, Bluetooth remains broken for me - Intel AX200 wifi/Bluetooth module not recognised.

EDIT 2: The latest update to bluedevil *seems* to have fixed my problem with bluetooth

---

### Post by xyz-t on 2022-07-17
Happy camper! 

At least for me, Kernel 5.15 is also part of history. Thanks to the Proposed team.

```
ls /lib/modules
5.19.0-051900rc7-generic  5.19.0-9-generic
```

---

### Post by IanW on 2022-07-18
5.19 will get an rc8, due partly to the recent "Retbleed" exploit

[QUOTE="Linus Torvalds"]It's a Sunday afternoon, I wonder what that might mean..

Another week, another rc. We obviously had that whole "Retbleed"
thing, and it does show up in both the diffstat and the shortlog, and
rc7 is definitely bigger than usual.

And also as usual, when we've had one of those embargoed hw issues
pending, the patches didn't get the open development, and then as a
result missed all the usual sanity checking by all the automation
build and test infrastructure we have. So no surprise - there's been
various small fixup patches afterwards too for some corner cases.

That said, last week there were two other development trees that
independently also asked for an extension, so 5.19 will be one of
those releases that have an additional rc8 next weekend before the
final release. We had some last-minute btrfs reverts, and there's also
a pending issue with a intel GPU firmware.

When it rains it pours.

Not that things really look all that bad. I think we've got the
retbleed fallout all handled (knock wood), and the btrfs reverts are
in place. And the Intel GPU firmware issue seems to have a patch
pending too (or we'll just revert). So it's not like we have any huge
issues, but an extra week is most definitely called for.

          Linus[/QUOTE]

---

### Post by Doug S on 2022-07-19
Since kernel 5.19-rc1, I have been getting these /var/log/kern.log entries for some commands:

```
Jul 18 20:56:58 s19 kernel: [   38.362155] loop0: detected capacity change from 0 to 8
Jul 18 20:56:58 s19 kernel: [   38.377708] Dev loop0: unable to read RDB block 8
Jul 18 20:56:58 s19 kernel: [   38.377712]  loop0: unable to read partition table
Jul 18 20:56:58 s19 kernel: [   38.377713] loop0: partition table beyond EOD, truncated
```

Example command (from over on the [inspired]("https://ubuntuforums.org/showthread.php?t=2465764&page=67&p=14104802#post14104802") thread):

```
$ snap list curl
error: no matching snaps installed
```

The problem commit is:

```
commit b9684a71fca793213378dd410cd11675d973eaa1 (HEAD)
Author: Christoph Hellwig <hch@lst.de>
Date:   Fri May 27 07:58:06 2022 +0200

    block, loop: support partitions without scanning

    Historically we did distinguish between a flag that surpressed partition
    scanning, and a combinations of the minors variable and another flag if
    any partitions were supported.  This was generally confusing and doesn't
    make much sense, but some corner case uses of the loop driver actually
    do want to support manually added partitions on a device that does not
    actively scan for partitions.  To make things worsee the loop driver
    also wants to dynamically toggle the scanning for partitions on a live
    gendisk, which makes the disk->flags updates non-atomic.

    Introduce a new GD_SUPPRESS_PART_SCAN bit in disk->state that disables
    just scanning for partitions, and toggle that instead of GENHD_FL_NO_PART
    in the loop driver.

    Fixes: 1ebe2e5f9d68 ("block: remove GENHD_FL_EXT_DEVT")
    Reported-by: Ming Lei <ming.lei@redhat.com>
    Signed-off-by: Christoph Hellwig <hch@lst.de>
    Reviewed-by: Ming Lei <ming.lei@redhat.com>
    Link: https://lore.kernel.org/r/20220527055806.1972352-1-hch@lst.de
    Signed-off-by: Jens Axboe <axboe@kernel.dk>
```

and a related email thread is[ here]("https://lore.kernel.org/lkml/aa126250-9f7f-b48b-79dc-bdb8b4bf5ca9@gmail.com/T/") and [here]("https://lore.kernel.org/all/368afc66-3781-4f56-134e-e08210ad6c93@comcast.net/t/")

The workaround (confirmed) is to disable Amiga partition table support:

```

doug@s19:~/kernel/linux$ scripts/config --disable AMIGA_PARTITION
doug@s19:~/kernel/linux$ scripts/diffconfig .config-5.19-rc7 .config
 AMIGA_PARTITION y -> n
```

The commit says it fixes a previous commit, and the discussion on the emails suggests it fixes a regression. The tags for the previous commit are:

```
doug@s19:~/kernel/linux$ git tag --contains 1ebe2e5f9d68
v5.17
v5.17-rc1
v5.17-rc2
v5.17-rc3
v5.17-rc4
v5.17-rc5
v5.17-rc6
v5.17-rc7
v5.17-rc8
v5.18
v5.18-rc1
v5.18-rc2
v5.18-rc3
v5.18-rc4
v5.18-rc5
v5.18-rc6
v5.18-rc7
v5.19-rc1
v5.19-rc2
v5.19-rc3
v5.19-rc4
v5.19-rc5
v5.19-rc6
v5.19-rc7
```Yet, older kernels from pre 5.17 do not have this issue.

---

### Post by xyz-t on 2022-07-20
The latest update out of Proposed should include the vulnerability correction.

Here's how to clean the Kernel in Synaptic.

```
Commit Log for Wed Jul 20 20:43:20 2022


Completely removed the following packages:
linux-modules-extra-5.19.0-9-generic
```

```
Commit Log for Wed Jul 20 20:42:41 2022


Completely removed the following packages:
linux-headers-5.19.0-9
linux-image-5.19.0-9-generic
linux-modules-5.19.0-9-generic

Removed the following packages:
linux-headers-5.19.0-9-generic
linux-modules-extra-5.19.0-9-generic
```
```

[FONT=monospace][COLOR=#000000] ls /boot [/COLOR]
config-5.19.0-051900rc7-generic      memtest86+.elf 
config-5.19.0-10-generic             memtest86+_multiboot.bin 
[COLOR=#5454ff]**efi**[/COLOR][COLOR=#000000]                                  System.map-5.19.0-051900rc7-generic [/COLOR]
[COLOR=#5454ff]**grub**[/COLOR][COLOR=#000000]                                 System.map-5.19.0-10-generic [/COLOR]
[COLOR=#54ffff]**initrd.img**[/COLOR][COLOR=#54ffff]**vmlinuz**[/COLOR]
initrd.img-5.19.0-051900rc7-generic  vmlinuz-5.19.0-051900rc7-generic 
initrd.img-5.19.0-10-generic         vmlinuz-5.19.0-10-generic 
[COLOR=#54ffff]**initrd.img.old**[/COLOR][COLOR=#54ffff]**vmlinuz.old**[/COLOR]
memtest86+.bin[/FONT]
```

All the best,

[https://launchpad.net/ubuntu/+source/linux-meta/5.19.0.10.10](https://launchpad.net/ubuntu/+source/linux-meta/5.19.0.10.10)

---

### Post by IanW on 2022-07-26
5.19-rc8 has appeared on the mainline kernel PPA. Several builds succeeded, but the self-tests all seem to have failed.
Might want to wait an extra day or two on this one.

[https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2022-07-25/](https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2022-07-25/)

---

### Post by Doug S on 2022-07-26
> **IanW said:**
> 5.19-rc8 has appeared on the mainline kernel PPA. Several builds succeeded, but the self-tests all seem to have failed.
Might want to wait an extra day or two on this one.

[https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2022-07-25/](https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2022-07-25/)Well the self-test is failing during compile. I think someone just screwed up somewhere:

```
make[2]: Entering directory '/home/kernel/COD/linux/tools/testing/selftests/memfd'
gcc -D_FILE_OFFSET_BITS=64 -I../../../../include/uapi/ -I../../../../include/ -I../../../../usr/include/    memfd_test.c common.c  -o /home/kernel/COD/linux/tools/testing/selftests/memfd/memfd_test
gcc -D_FILE_OFFSET_BITS=64 -I../../../../include/uapi/ -I../../../../include/ -I../../../../usr/include/    fuse_test.c common.c  -o /home/kernel/COD/linux/tools/testing/selftests/memfd/fuse_test
gcc -D_FILE_OFFSET_BITS=64 -I../../../../include/uapi/ -I../../../../include/ -I../../../../usr/include/    fuse_mnt.c -lfuse -pthread -o /home/kernel/COD/linux/tools/testing/selftests/memfd/fuse_mnt
fuse_mnt.c:17:10: fatal error: fuse.h: No such file or directory
   17 | #include <fuse.h>
      |          ^~~~~~~~
compilation terminated.
make[2]: *** [../lib.mk:173: /home/kernel/COD/linux/tools/testing/selftests/memfd/fuse_mnt] Error 1
```

Actually looking back, have the self tests ever complied properly? Not that I can tell. They started between kernel 5.7-rc7 and 5.7 and have always failed (not that I checked every RC from then to now).

Anyway, I have been running it since Sunday without any issues:

```
doug@s19:~/tmp/system-info$ uname -a
Linux s19 5.19.0-rc8-c1e #1080 SMP PREEMPT_DYNAMIC Sun Jul 24 16:57:03 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by xyz-t on 2022-07-27
@IanW
 When packages are there, many of us jump on them. All has been good since early Sunday afternoon. So, go ahead and test the last RETBleed corrections.


 If you take a close look at the Kernels chronology, there is no correction after Sunday (every 7 days), robot self-test failure or not.

---

### Post by zika on 2022-07-27
**[COLOR=#333333]ppa:canonical-kernel-team/bootstrap[/COLOR]**

---

### Post by IanW on 2022-07-28
Thanks guys. I'll give it a shot tonight.

---

### Post by IanW on 2022-07-28
> **Doug S said:**
> Well the self-test is failing during compile. I think someone just screwed up somewhere:

```
make[2]: Entering directory '/home/kernel/COD/linux/tools/testing/selftests/memfd'
gcc -D_FILE_OFFSET_BITS=64 -I../../../../include/uapi/ -I../../../../include/ -I../../../../usr/include/    memfd_test.c common.c  -o /home/kernel/COD/linux/tools/testing/selftests/memfd/memfd_test
gcc -D_FILE_OFFSET_BITS=64 -I../../../../include/uapi/ -I../../../../include/ -I../../../../usr/include/    fuse_test.c common.c  -o /home/kernel/COD/linux/tools/testing/selftests/memfd/fuse_test
gcc -D_FILE_OFFSET_BITS=64 -I../../../../include/uapi/ -I../../../../include/ -I../../../../usr/include/    fuse_mnt.c -lfuse -pthread -o /home/kernel/COD/linux/tools/testing/selftests/memfd/fuse_mnt
fuse_mnt.c:17:10: fatal error: fuse.h: No such file or directory
   17 | #include <fuse.h>
      |          ^~~~~~~~
compilation terminated.
make[2]: *** [../lib.mk:173: /home/kernel/COD/linux/tools/testing/selftests/memfd/fuse_mnt] Error 1
```

Actually looking back, have the self tests ever complied properly? Not that I can tell. They started between kernel 5.7-rc7 and 5.7 and have always failed (not that I checked every RC from then to now).

Anyway, I have been running it since Sunday without any issues:

```
doug@s19:~/tmp/system-info$ uname -a
Linux s19 5.19.0-rc8-c1e #1080 SMP PREEMPT_DYNAMIC Sun Jul 24 16:57:03 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux
```

> **xyz-t said:**
> @IanW
 When packages are there, many of us jump on them. All has been good since early Sunday afternoon. So, go ahead and test the last RETBleed corrections.


 If you take a close look at the Kernels chronology, there is no correction after Sunday (every 7 days), robot self-test failure or not.

Thanks, guys.
I'll give it a shot tonight.

---

### Post by IanW on 2022-07-28
> **Doug S said:**
> Well the self-test is failing during compile. I think someone just screwed up somewhere:

```
make[2]: Entering directory '/home/kernel/COD/linux/tools/testing/selftests/memfd'
gcc -D_FILE_OFFSET_BITS=64 -I../../../../include/uapi/ -I../../../../include/ -I../../../../usr/include/    memfd_test.c common.c  -o /home/kernel/COD/linux/tools/testing/selftests/memfd/memfd_test
gcc -D_FILE_OFFSET_BITS=64 -I../../../../include/uapi/ -I../../../../include/ -I../../../../usr/include/    fuse_test.c common.c  -o /home/kernel/COD/linux/tools/testing/selftests/memfd/fuse_test
gcc -D_FILE_OFFSET_BITS=64 -I../../../../include/uapi/ -I../../../../include/ -I../../../../usr/include/    fuse_mnt.c -lfuse -pthread -o /home/kernel/COD/linux/tools/testing/selftests/memfd/fuse_mnt
fuse_mnt.c:17:10: fatal error: fuse.h: No such file or directory
   17 | #include <fuse.h>
      |          ^~~~~~~~
compilation terminated.
make[2]: *** [../lib.mk:173: /home/kernel/COD/linux/tools/testing/selftests/memfd/fuse_mnt] Error 1
```

Actually looking back, have the self tests ever complied properly? Not that I can tell. They started between kernel 5.7-rc7 and 5.7 and have always failed (not that I checked every RC from then to now).

Anyway, I have been running it since Sunday without any issues:

```
doug@s19:~/tmp/system-info$ uname -a
Linux s19 5.19.0-rc8-c1e #1080 SMP PREEMPT_DYNAMIC Sun Jul 24 16:57:03 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux
```

> **xyz-t said:**
> @IanW
 When packages are there, many of us jump on them. All has been good since early Sunday afternoon. So, go ahead and test the last RETBleed corrections.


 If you take a close look at the Kernels chronology, there is no correction after Sunday (every 7 days), robot self-test failure or not.

Thanks, guys.
I'll give it a shot tonight.

---

### Post by xyz-t on 2022-07-29
Freshly baked! It should cover the latest patches.


 ```
[FONT=monospace][COLOR=#000000]ls /lib/modules [/COLOR]
[COLOR=#5454ff]**5.19.0-051900rc8-generic  **[/COLOR][COLOR=#5454ff]**5.19.0-13-generic**[/COLOR][/FONT]
```

---

### Post by xyz-t on 2022-07-31
This is the end of 5.x series, next will be or should be 6.0.
```


 [FONT=monospace][COLOR=#000000]cat /proc/version [/COLOR]
Linux version 5.19.0-051900-generic (kernel@sita) (x86_64-linux-gnu-gcc-11 (Ubuntu 11.3.0-5ubuntu1) 11.3.0, GNU ld (GNU Binutils for Ubuntu) 2.38.90.20220713) #202207312230 SMP PREEMPT_DYNAMIC Sun Jul 31 22:34:11 UTC 2022[/FONT]
``` 

[https://9to5linux.com/linux-kernel-5-19-officially-released-this-is-whats-new](https://9to5linux.com/linux-kernel-5-19-officially-released-this-is-whats-new)[FONT=monospace][/FONT]

---

