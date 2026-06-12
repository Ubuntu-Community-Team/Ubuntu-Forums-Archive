---
title: "X crashes"
date: 2012-02-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by karolbe on 2012-02-14
I am getting X crashes since yesterday update. After using system for a few minutes I get some garbarge on the screen and following messages in the log:

```
[  249.813442] NVRM: Xid (0000:01:00): 13, 0004 00000000 00009097 00002480 00001030 00000000
[  280.246315] NVRM: Xid (0000:01:00): 13, 0004 00000000 00009097 00002480 00001030 00000000
[  280.260177] NVRM: Xid (0000:01:00): 31, Ch 00000004, engmask 00000101, intr 10000000
[  280.271436] NVRM: Xid (0000:01:00): 31, Ch 00000004, engmask 00000101, intr 10000000
[  282.271760] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
[  286.271832] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
```

Then system almost completely freezes, the mouse pointer can sometimes be moved around and every minute or so all unfreezes for a fraction of second so it is possible to switch to the console and kill the X session. Most of the time however I am forced to do reboot.

Just after logging in I see screen full of garbage. The GDM screen is fine.

I have a nVidia GT460 card and this is a 64 bit system. It has been quite stable since I have installed it in December, until yesterday :-(

Any ideas what's wrong?

Karol

---

### Post by paul_in_london on 2012-02-14
> **karolbe said:**
> I am getting X crashes since yesterday update. After using system for a few minutes I get some garbarge on the screen and following messages in the log:

```
[  249.813442] NVRM: Xid (0000:01:00): 13, 0004 00000000 00009097 00002480 00001030 00000000
[  280.246315] NVRM: Xid (0000:01:00): 13, 0004 00000000 00009097 00002480 00001030 00000000
[  280.260177] NVRM: Xid (0000:01:00): 31, Ch 00000004, engmask 00000101, intr 10000000
[  280.271436] NVRM: Xid (0000:01:00): 31, Ch 00000004, engmask 00000101, intr 10000000
[  282.271760] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
[  286.271832] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
```

Then system almost completely freezes, the mouse pointer can sometimes be moved around and every minute or so all unfreezes for a fraction of second so it is possible to switch to the console and kill the X session. Most of the time however I am forced to do reboot.

Just after logging in I see screen full of garbage. The GDM screen is fine.

I have a nVidia GT460 card and this is a 64 bit system. It has been quite stable since I have installed it in December, until yesterday :-(

Any ideas what's wrong?

Karol

Which kernel are you using?

Which version of the nvidia driver are you using (or are you using nouveau)?

What does:

```
dmesg|grep alloc
```

give?

See this thread, which may have some relevance to your problem:

[ubuntuforums.org/showthread.php?t=1681696](ubuntuforums.org/showthread.php?t=1681696)

I'm ok here with nvidia on 64 bit:

```
paul@lubuntu-64:~$ uname -a
Linux lubuntu-64 3.2.0-16-generic #25-Ubuntu SMP Tue Feb 14 02:55:04 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
paul@lubuntu-64:~$
```

```
paul@lubuntu-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 295.20-0ubuntu1~xedgers~precise1
  Candidate: 295.20-0ubuntu1~xedgers~precise1
  Version table:
 *** 295.20-0ubuntu1~xedgers~precise1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     290.10-0ubuntu2 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
paul@lubuntu-64:~$ 
```

This is with the xorg-edgers ppa enabled.

Also ok with the 3.3-rc3 kernel on my other 64 bit install.

---

### Post by karolbe on 2012-02-15
Hi I am using the latest kernel available in precise, as of now it is:
3.2.0-16-generic #25-Ubuntu

I have just upgraded to xorg-edgers ppa nvidia driver and Xorg but it didn't help. nVidia driver version is 295.20.

Here are some other messages from the log:

```
[ 1032.911832] NVRM: Xid (0000:01:00): 31, Ch 00000003, engmask 00000101, intr 10000000
[ 1033.010203] NVRM: Xid (0000:01:00): 13, 0003 00000000 00009097 00002490 00000030 00000000
[ 1037.035782] NVRM: Xid (0000:01:00): 31, Ch 00000001, engmask 00000101, intr 10000000
[ 1037.046654] NVRM: Xid (0000:01:00): 32, Channel ID 00000001 intr 00040000
[ 1037.046822] NVRM: Xid (0000:01:00): 32, Channel ID 00000001 intr 00040000
[ 1037.056227] NVRM: Xid (0000:01:00): 13, 0001 00000000 00009097 00001614 00000000 0000000d
[ 1037.060297] NVRM: Xid (0000:01:00): 32, Channel ID 00000001 intr 00800000
[ 1037.060473] NVRM: Xid (0000:01:00): 32, Channel ID 00000001 intr 00800000
[ 1060.115225] compiz[2160]: segfault at 118 ip 00007f6d75e0dc64 sp 00007fff18ddc360 error 4 in libnvidia-glcore.so.295.20[7f6d74b28000+1927000]
[ 1081.757174] compiz[3879]: segfault at 58 ip 00007f1f4a0a96d1 sp 00007fff5a210668 error 4 in libnvidia-glcore.so.295.20[7f1f48d4b000+1927000]
```

dmesg | grep alloc gives:

```

[    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.020029] ftrace: allocating 26992 entries in 106 pages
[    1.073654] HugeTLB registered 2 MB page size, pre-allocated 0 pages

```

---

### Post by karolbe on 2012-03-03
I have just upgraded to Precise again and unfortunately the bug is still there. It is actually very critial because system is completely unusable. It crashes in 5 minutes, most usually when displaying some context menu (right mouse click) or when switching applications.

I have noticed though that it couldy trigerred by different than standard application switcher in Compiz (I am using Application Switcher).

Anyone else experiencing it?

---

### Post by djmurf on 2012-03-04
I've been experiencing the same problems.. Nvidia GTX 560.

The box dual boots linux and windows 7. I've never seen an issue or a hang with windows, but I've been hard locking with linux at random intervals with:

Mar  4 15:46:09 media2 kernel: [50116.314032] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context

I have been through just about every nvidia driver version you can throw at it, as well as tried every ubuntu distro from 10.04 -> 12.04 ( currently running since last night, and have locked 3 times already )...

I'm at the point now where I'm ready to ditch the Nvidia card and pick up an ATI/AMD card.

I'm open to trying anything on this box if anyone has any suggestions...

---

