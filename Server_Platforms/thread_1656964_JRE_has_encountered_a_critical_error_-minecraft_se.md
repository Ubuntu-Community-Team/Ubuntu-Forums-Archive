---
title: "JRE has encountered a critical error -minecraft server"
date: 2010-12-31
forum: Server Platforms
---

### Post by 12345678ew on 2010-12-31
hi, so i'm trying to get my friend's rather failed minecraft server running again.

he rented the space from virpus.com, and they seem to be perfectly fine.

however, he was running it out of root and logging in as root, which i understand causes some problems with it.

so i go through virpus and have them just reinstall the minimum version of ubuntu 10.4 (maybe 10.04, dunno?)
i use **$** sudo apt-get install openjdk-6-jre to get the JRE
i use sudo apt-get install to install gedit (i didn't know about nano or i wouldn't have bothered)
the wget command
the man command
I then create a new user for myself named nick, give it a password

then use visudo and under %sudo ALL=(ALL) ALL
put nick ALL =(ALL) ALL
then i save and i should now have an account with sudo capabilities
i close putty (running all this through putty from my windows 7 pc, hence no GUI, only cmd line. is there any way to get the regular GUI even though server's in germany?)
open and connect again, log in as nick.
mkdir minecraft-server
wget [http://minecraft.net/download/minecraft_server.jar?v=1293826472849](http://minecraft.net/download/minecraft_server.jar?v=1293826472849)
[FONT=monospace]
nick@greg:~/minecraft-server$ java -Xmx1024M -Xms1024M -jar minecraft_server.jar?v=1293784240190 nogui[/FONT]

and i get this:

```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  Internal Error (signature.cpp:60), pid=15592, tid=47636151326480
#  Error: expecting (
#
# JRE version: 6.0_18-b18
# Java VM: OpenJDK 64-Bit Server VM (14.0-b16 mixed mode linux-amd64 )
# Derivative: IcedTea6 1.8
# Distribution: Ubuntu lucid (development branch), package 6b18-1.8-0ubuntu1
# An error report file with more information is saved as:
# /home/nick/minecraft-server/hs_err_pid15592.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/


i used cat to open # /home/nick/minecraft-server/hs_err_pid15592.log, copied it and it's this:

2af4f619c000-2af4f639b000 ---p 00018000 fd:01 67667351                   /lib/libpthread-2.11.1.so
2af4f639b000-2af4f639c000 r--p 00017000 fd:01 67667351                   /lib/libpthread-2.11.1.so
2af4f639c000-2af4f639d000 rw-p 00018000 fd:01 67667351                   /lib/libpthread-2.11.1.so
2af4f639d000-2af4f63a1000 rw-p 2af4f639d000 00:00 0
2af4f63a1000-2af4f63a5000 r-xp 00000000 fd:01 68060796                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/jli/libjli.so
2af4f63a5000-2af4f65a4000 ---p 00004000 fd:01 68060796                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/jli/libjli.so
2af4f65a4000-2af4f65a5000 r--p 00003000 fd:01 68060796                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/jli/libjli.so
2af4f65a5000-2af4f65a6000 rw-p 00004000 fd:01 68060796                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/jli/libjli.so
2af4f65a6000-2af4f65a8000 r-xp 00000000 fd:01 67667308                   /lib/libdl-2.11.1.so
2af4f65a8000-2af4f67a8000 ---p 00002000 fd:01 67667308                   /lib/libdl-2.11.1.so
2af4f67a8000-2af4f67a9000 r--p 00002000 fd:01 67667308                   /lib/libdl-2.11.1.so
2af4f67a9000-2af4f67aa000 rw-p 00003000 fd:01 67667308                   /lib/libdl-2.11.1.so
2af4f67aa000-2af4f67ab000 rw-p 2af4f67aa000 00:00 0
2af4f67ab000-2af4f6923000 r-xp 00000000 fd:01 67667377                   /lib/libc-2.11.1.so
2af4f6923000-2af4f6b23000 ---p 00178000 fd:01 67667377                   /lib/libc-2.11.1.so
2af4f6b23000-2af4f6b27000 r--p 00178000 fd:01 67667377                   /lib/libc-2.11.1.so
2af4f6b27000-2af4f6b28000 rw-p 0017c000 fd:01 67667377                   /lib/libc-2.11.1.so
2af4f6b28000-2af4f6b2f000 rw-p 2af4f6b28000 00:00 0
2af4f6b2f000-2af4f72f0000 r-xp 00000000 fd:01 68060829                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server/libjvm.so
2af4f72f0000-2af4f74ef000 ---p 007c1000 fd:01 68060829                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server/libjvm.so
2af4f74ef000-2af4f755d000 r--p 007c0000 fd:01 68060829                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server/libjvm.so
2af4f755d000-2af4f7576000 rw-p 0082e000 fd:01 68060829                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server/libjvm.so
2af4f7576000-2af4f75b2000 rw-p 2af4f7576000 00:00 0
2af4f75b8000-2af4f763a000 r-xp 00000000 fd:01 67667409                   /lib/libm-2.11.1.so
2af4f763a000-2af4f7839000 ---p 00082000 fd:01 67667409                   /lib/libm-2.11.1.so
2af4f7839000-2af4f783a000 r--p 00081000 fd:01 67667409                   /lib/libm-2.11.1.so
2af4f783a000-2af4f783b000 rw-p 00082000 fd:01 67667409                   /lib/libm-2.11.1.so
2af4f783b000-2af4f783e000 ---p 2af4f783b000 00:00 0
2af4f783e000-2af4f793c000 rw-p 2af4f783e000 00:00 0
2af4f7942000-2af4f7949000 r-xp 00000000 fd:01 67667346                   /lib/librt-2.11.1.so
2af4f7949000-2af4f7b48000 ---p 00007000 fd:01 67667346                   /lib/librt-2.11.1.so
2af4f7b48000-2af4f7b49000 r--p 00006000 fd:01 67667346                   /lib/librt-2.11.1.so
2af4f7b49000-2af4f7b4a000 rw-p 00007000 fd:01 67667346                   /lib/librt-2.11.1.so
2af4f7b4a000-2af4f7b59000 r-xp 00000000 fd:01 68060824                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libverify.so
2af4f7b59000-2af4f7d58000 ---p 0000f000 fd:01 68060824                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libverify.so
2af4f7d58000-2af4f7d5a000 r--p 0000e000 fd:01 68060824                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libverify.so
2af4f7d5a000-2af4f7d5b000 rw-p 00010000 fd:01 68060824                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libverify.so
2af4f7d5b000-2af4f7d88000 r-xp 00000000 fd:01 68060808                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjava.so
2af4f7d88000-2af4f7f87000 ---p 0002d000 fd:01 68060808                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjava.so
2af4f7f87000-2af4f7f88000 r--p 0002c000 fd:01 68060808                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjava.so
2af4f7f88000-2af4f7f8b000 rw-p 0002d000 fd:01 68060808                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjava.so
2af4f7f8b000-2af4f7f8c000 r--p 2af4f7f8b000 00:00 0
2af4f7f8c000-2af4f7f8d000 rw-p 2af4f7f8c000 00:00 0
2af4f7f91000-2af4f7fa8000 r-xp 00000000 fd:01 67667352                   /lib/libnsl-2.11.1.so
2af4f7fa8000-2af4f81a7000 ---p 00017000 fd:01 67667352                   /lib/libnsl-2.11.1.so
2af4f81a7000-2af4f81a8000 r--p 00016000 fd:01 67667352                   /lib/libnsl-2.11.1.so
2af4f81a8000-2af4f81a9000 rw-p 00017000 fd:01 67667352                   /lib/libnsl-2.11.1.so
2af4f81a9000-2af4f81ab000 rw-p 2af4f81a9000 00:00 0
2af4f81ab000-2af4f81b3000 r-xp 00000000 fd:01 68060827                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/native_threads/libhpi.so
2af4f81b3000-2af4f83b2000 ---p 00008000 fd:01 68060827                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/native_threads/libhpi.so
2af4f83b2000-2af4f83b3000 r--p 00007000 fd:01 68060827                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/native_threads/libhpi.so
2af4f83b3000-2af4f83b4000 rw-p 00008000 fd:01 68060827                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/native_threads/libhpi.so
2af4f83ba000-2af4f83c2000 r-xp 00000000 fd:01 67667420                   /lib/libnss_compat-2.11.1.so
2af4f83c2000-2af4f85c1000 ---p 00008000 fd:01 67667420                   /lib/libnss_compat-2.11.1.so
2af4f85c1000-2af4f85c2000 r--p 00007000 fd:01 67667420                   /lib/libnss_compat-2.11.1.so
2af4f85c2000-2af4f85c3000 rw-p 00008000 fd:01 67667420                   /lib/libnss_compat-2.11.1.so
2af4f85c3000-2af4f85cd000 r-xp 00000000 fd:01 67667391                   /lib/libnss_nis-2.11.1.so
2af4f85cd000-2af4f87cc000 ---p 0000a000 fd:01 67667391                   /lib/libnss_nis-2.11.1.so
2af4f87cc000-2af4f87cd000 r--p 00009000 fd:01 67667391                   /lib/libnss_nis-2.11.1.so
2af4f87cd000-2af4f87ce000 rw-p 0000a000 fd:01 67667391                   /lib/libnss_nis-2.11.1.so
2af4f87ce000-2af4f87da000 r-xp 00000000 fd:01 67667334                   /lib/libnss_files-2.11.1.so
2af4f87da000-2af4f89d9000 ---p 0000c000 fd:01 67667334                   /lib/libnss_files-2.11.1.so
2af4f89d9000-2af4f89da000 r--p 0000b000 fd:01 67667334                   /lib/libnss_files-2.11.1.so
2af4f89da000-2af4f89db000 rw-p 0000c000 fd:01 67667334                   /lib/libnss_files-2.11.1.so
2af4f89db000-2af4f89e3000 rw-s 00000000 fd:01 68059145                   /tmp/hsperfdata_root/20272
2af4f89e3000-2af4f89ea000 r-xp 00000000 fd:01 68060825                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libzip.so
2af4f89ea000-2af4f8be9000 ---p 00007000 fd:01 68060825                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libzip.so
2af4f8be9000-2af4f8bea000 r--p 00006000 fd:01 68060825                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libzip.so
2af4f8bea000-2af4f8beb000 rw-p 00007000 fd:01 68060825                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libzip.so
2af4f8beb000-2af4f8e5b000 rwxp 2af4f8beb000 00:00 0
2af4f8e5b000-2af4fbbeb000 rwxp 2af4f8e5b000 00:00 0
2af4fbbeb000-2af4fbbf5000 rwxp 2af4fbbeb000 00:00 0
2af4fbbf5000-2af4fbcab000 rwxp 2af4fbbf5000 00:00 0
2af4fbcb0000-2af4fd170000 rwxp 2af4fbcb0000 00:00 0
2af4fd170000-2af5064b0000 rwxp 2af4fd170000 00:00 0
2af5064b0000-2af5464bb000 rwxp 2af5064b0000 00:00 0
2af5464bb000-2af546504000 rwxp 2af5464bb000 00:00 0
2af546504000-2af546866000 rwxp 2af546504000 00:00 0
2af546866000-2af5468af000 rwxp 2af546866000 00:00 0
2af5468af000-2af5468b0000 ---p 2af5468af000 00:00 0
2af5468b0000-2af5469b0000 rw-p 2af5468b0000 00:00 0
2af5469b0000-2af5469b1000 ---p 2af5469b0000 00:00 0
2af5469b1000-2af546ab1000 rw-p 2af5469b1000 00:00 0
2af546ab1000-2af546ab2000 ---p 2af546ab1000 00:00 0
2af546ab2000-2af546bb2000 rw-p 2af546ab2000 00:00 0
2af546bb2000-2af546bb3000 ---p 2af546bb2000 00:00 0
2af546bb3000-2af546cdb000 rw-p 2af546bb3000 00:00 0
2af546cdb000-2af546e6d000 r--s 03914000 fd:01 68060791                   /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
2af546e6d000-2af546f45000 rw-p 2af546e6d000 00:00 0
2af546f45000-2af546f46000 ---p 2af546f45000 00:00 0
2af546f46000-2af547046000 rw-p 2af546f46000 00:00 0
2af547046000-2af547049000 ---p 2af547046000 00:00 0
2af547049000-2af547147000 rw-p 2af547049000 00:00 0
2af547147000-2af54714a000 ---p 2af547147000 00:00 0
2af54714a000-2af547248000 rw-p 2af54714a000 00:00 0
2af547248000-2af547287000 r--p 00000000 fd:01 67993626                   /usr/lib/locale/en_US.utf8/LC_CTYPE
2af547287000-2af54728e000 r--s 00000000 fd:01 68027539                   /usr/lib/gconv/gconv-modules.cache
2af54728e000-2af547291000 ---p 2af54728e000 00:00 0
2af547291000-2af54738f000 rw-p 2af547291000 00:00 0
2af54738f000-2af547392000 ---p 2af54738f000 00:00 0
2af547392000-2af547490000 rw-p 2af547392000 00:00 0
2af547490000-2af547493000 ---p 2af547490000 00:00 0
2af547493000-2af547591000 rw-p 2af547493000 00:00 0
2af547591000-2af547594000 ---p 2af547591000 00:00 0
2af547594000-2af547692000 rw-p 2af547594000 00:00 0
2af547692000-2af547693000 ---p 2af547692000 00:00 0
2af547693000-2af547793000 rw-p 2af547693000 00:00 0
2af547798000-2af5477a1000 r--s 00065000 fd:01 68062096                   /usr/share/java/gnome-java-bridge.jar
2af5477a1000-2af5477a4000 r--s 0000f000 fd:01 68059628                   /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
2af5477a4000-2af5477a9000 r--s 00051000 fd:01 72648417                   /home/nick/minecraft-server/minecraft_server.jar?v=1293784240190
2af5477a9000-2af5477ac000 r--s 0007a000 fd:01 68059642                   /usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
2af5477ac000-2af5477af000 ---p 2af5477ac000 00:00 0
2af5477af000-2af5478ad000 rw-p 2af5477af000 00:00 0
2af5478ad000-2af5478b0000 ---p 2af5478ad000 00:00 0
2af5478b0000-2af5479ae000 rw-p 2af5478b0000 00:00 0
2af5479ae000-2af5479b1000 ---p 2af5479ae000 00:00 0
2af5479b1000-2af547aaf000 rw-p 2af5479b1000 00:00 0
2af547aaf000-2af547ac4000 r-xp 00000000 fd:01 68060818                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnet.so
2af547ac4000-2af547cc3000 ---p 00015000 fd:01 68060818                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnet.so
2af547cc3000-2af547cc4000 r--p 00014000 fd:01 68060818                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnet.so
2af547cc4000-2af547cc5000 rw-p 00015000 fd:01 68060818                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnet.so
2af547cc5000-2af547ccd000 r-xp 00000000 fd:01 68060819                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnio.so
2af547ccd000-2af547ecc000 ---p 00008000 fd:01 68060819                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnio.so
2af547ecc000-2af547ecd000 r--p 00007000 fd:01 68060819                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnio.so
2af547ecd000-2af547ece000 rw-p 00008000 fd:01 68060819                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnio.so
2af547ece000-2af547ed1000 ---p 2af547ece000 00:00 0
2af547ed1000-2af547fcf000 rw-p 2af547ed1000 00:00 0
2af548000000-2af548b74000 rw-p 2af548000000 00:00 0
2af548b74000-2af54c000000 ---p 2af548b74000 00:00 0
7fff70b9b000-7fff70bd0000 rw-p 7ffffffc9000 00:00 0                      [stack]
ffffffffff600000-ffffffffffe00000 ---p 00000000 00:00 0                  [vdso]

VM Arguments:
jvm_args: -Xmx1024M -Xms1024M
java_command: minecraft_server.jar?v=1293784240190 nogui
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
USERNAME=root
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server:/usr/lib/jvm/java-6-openjdk/jre/lib/amd64:/usr/lib/jvm/java-6-openjdk/jre/../lib/amd64
SHELL=/bin/bash

Signal Handlers:
SIGSEGV: [libjvm.so+0x674c20], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x674c20], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x54ac80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x54ac80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x54ac80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x54ac80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x54a3d0], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x54ca70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x54ca70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x54ca70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x54ca70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 10.04 (lucid)
uname:Linux 2.6.18-194.26.1.el5.028stab070.14 #1 SMP Thu Nov 18 16:34:01 MSK 2010 x86_64
libc:glibc 2.11.1 NPTL 2.11.1
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:0.38 0.10 0.03

CPU:total 4 (4 cores per cpu, 1 threads per core) family 6 model 23 stepping 10, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3, sse4.1

Memory: 4k page, physical 2097152k(122948k free), swap 10125304k(10124796k free)

vm_info: OpenJDK 64-Bit Server VM (14.0-b16) for linux-amd64 JRE (1.6.0_18-b18), built on Apr 14 2010 11:28:48 by "buildd" with gcc 4.4.3

time: Fri Dec 31 19:46:08 2010
elapsed time: 16 seconds
```

what am i doing wrong?

i've actually been through this process more than once now in slightly diferent orders.

what you see here is the latest one however.

so is the JRE i downloaded corrupted or something?

---

### Post by 12345678ew on 2010-12-31
I forgot, i also used cat and added my name and somebody else's name to ops.txt in ~/minecraft-server so that when i get it running we'll be admins on the server, but i did that after this error showed up.

---

