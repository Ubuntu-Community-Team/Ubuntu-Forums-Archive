---
title: "procinfo on 8.04 server 64-bit - segfault?"
date: 2008-04-25
forum: Server Platforms
---

### Post by tubezninja on 2008-04-25
Is anyone else having trouble running procinfo on ubuntu 8.04LTS for amd64 processors?  I have a machine that I just upgraded yesterday, running on an Intel Q6600 Core2Quad.  

Procinfo displayed just fine before the upgrade, running 7.10 server edition, but ever since completing a do-release-upgrade, procinfo segfaults.  I've tried reinstalling the package, to no avail.

FWIW, procinfo runs fine on an old 32-bit Xeon server that I upgraded to Hardy around the same time.

Is there any way I could search the logs and find out _why_ it's segfaulting?

thanks in advance!

---

### Post by geertn on 2008-04-25
Run it through strace:
```

strace procinfo

```

Using strace you can see all system calls executed prior to the segfault.

---

### Post by tubezninja on 2008-04-25
Okay, well, unfortuantely I'm not enough of a linux guru to be able to parse the output very well.  Here's what was produced.  Would anyone here be kind enough to help me make heads or tails of this? :)

```
~$ strace procinfo
execve("/usr/bin/procinfo", ["procinfo"], [/* 19 vars */]) = 0
brk(0)                                  = 0x60c000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2e8363d000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2e8363b000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=20949, ...}) = 0
mmap(NULL, 20949, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f2e83635000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libncurses.so.5", O_RDONLY)  = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\6\1"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=241408, ...}) = 0
mmap(NULL, 2338176, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f2e831e6000
mprotect(0x7f2e8321d000, 2093056, PROT_NONE) = 0
mmap(0x7f2e8341c000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x36000) = 0x7f2e8341c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\342"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1436976, ...}) = 0
mmap(NULL, 3543672, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f2e82e84000
mprotect(0x7f2e82fdc000, 2097152, PROT_NONE) = 0
mmap(0x7f2e831dc000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x158000) = 0x7f2e831dc000
mmap(0x7f2e831e1000, 17016, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f2e831e1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libdl.so.2", O_RDONLY)       = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \16\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=14624, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2e83634000
mmap(NULL, 2109728, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f2e82c80000
mprotect(0x7f2e82c82000, 2097152, PROT_NONE) = 0
mmap(0x7f2e82e82000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7f2e82e82000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2e83633000
arch_prctl(ARCH_SET_FS, 0x7f2e836336e0) = 0
mprotect(0x7f2e831dc000, 12288, PROT_READ) = 0
munmap(0x7f2e83635000, 20949)           = 0
uname({sys="Linux", node="servername", ...})  = 0
brk(0)                                  = 0x60c000
brk(0x62d000)                           = 0x62d000
open("/proc/version", O_RDONLY)         = 3
open("/proc/uptime", O_RDONLY)          = 4
open("/proc/loadavg", O_RDONLY)         = 5
open("/proc/meminfo", O_RDONLY)         = 6
open("/proc/stat", O_RDONLY)            = 7
open("/proc/diskstats", O_RDONLY)       = 8
open("/proc/vmstat", O_RDONLY)          = 9
open("/proc/modules", O_RDONLY)         = 10
open("/proc/devices", O_RDONLY)         = 11
open("/proc/filesystems", O_RDONLY)     = 12
open("/proc/interrupts", O_RDONLY)      = 13
open("/proc/dma", O_RDONLY)             = 14
open("/proc/cmdline", O_RDONLY)         = 15
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B9600 opost isig icanon echo ...}) = 0
stat("/home/username/.terminfo", 0x7fff8b63cb80) = -1 ENOENT (No such file or directory)
stat("/etc/terminfo", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
access("/etc/terminfo/v/vt102", R_OK)   = -1 ENOENT (No such file or directory)
stat("/lib/terminfo", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
access("/lib/terminfo/v/vt102", R_OK)   = 0
open("/lib/terminfo/v/vt102", O_RDONLY) = 16
read(16, "\32\1\20\0&\0\7\0\16\0018\2vt102|dec vt102\0\0\1\0\0"..., 4097) = 1188
close(16)                               = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B9600 opost isig icanon echo ...}) = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B9600 opost isig icanon echo ...}) = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B9600 opost isig icanon echo ...}) = 0
ioctl(1, TIOCGWINSZ, {ws_row=39, ws_col=80, ws_xpixel=720, ws_ypixel=780}) = 0
ioctl(1, TIOCGWINSZ, {ws_row=39, ws_col=80, ws_xpixel=720, ws_ypixel=780}) = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B9600 opost isig icanon echo ...}) = 0
uname({sys="Linux", node="servername", ...})  = 0
uname({sys="Linux", node="servername", ...})  = 0
fstat(3, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2e8363a000
lseek(3, 0, SEEK_SET)                   = 0
read(3, "Linux version 2.6.24-16-server ("..., 1024) = 127
open("/proc/stat", O_RDONLY)            = 16
fstat(16, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2e83639000
read(16, "cpu  103011 0 8583 22025905 4898"..., 1024) = 1024
read(16, "0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 "..., 1024) = 1024
read(16, "0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 "..., 1024) = 1024
read(16, "0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 "..., 1024) = 1024
read(16, "0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 "..., 1024) = 825
read(16, "", 1024)                      = 0
close(16)                               = 0
munmap(0x7f2e83639000, 4096)            = 0
uname({sys="Linux", node="servername", ...})  = 0
uname({sys="Linux", node="servername", ...})  = 0
lseek(3, 127, SEEK_SET)                 = 127
fstat(7, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2e83639000
read(7, "cpu  103011 0 8584 22025905 4898"..., 1024) = 1024
read(7, "0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 "..., 1024) = 1024
read(7, "0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 "..., 1024) = 1024
read(7, "0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 "..., 1024) = 1024
read(7, "0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 "..., 1024) = 825
open("/etc/localtime", O_RDONLY)        = 16
fstat(16, {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
fstat(16, {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2e83638000
read(16, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\4\0\0\0\4\0\0"..., 4096) = 3519
lseek(16, -2252, SEEK_CUR)              = 1267
read(16, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\5\0\0\0\5\0\0"..., 4096) = 2252
close(16)                               = 0
munmap(0x7f2e83638000, 4096)            = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3519, ...}) = 0
read(7, "", 1024)                       = 0
close(4)                                = 0
open("/proc/uptime", O_RDONLY)          = 4
fstat(4, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2e83638000
read(4, "52535.18 52651.49\n", 1024)    = 18
close(6)                                = 0
open("/proc/meminfo", O_RDONLY)         = 6
fstat(6, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2e83637000
read(6, "MemTotal:      4043836 kB\nMemFre"..., 1024) = 748
close(6)                                = 0
munmap(0x7f2e83637000, 4096)            = 0
open("/proc/meminfo", O_RDONLY)         = 6
fstat(6, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2e83637000
read(6, "MemTotal:      4043836 kB\nMemFre"..., 1024) = 748
read(6, "", 1024)                       = 0
close(6)                                = 0
munmap(0x7f2e83637000, 4096)            = 0
open("/proc/meminfo", O_RDONLY)         = 6
fstat(6, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2e83637000
read(6, "MemTotal:      4043836 kB\nMemFre"..., 1024) = 748
read(6, "", 1024)                       = 0
fstat(5, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2e83636000
lseek(5, 0, SEEK_SET)                   = 0
read(5, "0.06 0.02 0.00 2/184 16175\n", 1024) = 27
read(5, "", 1024)                       = 0
fstat(9, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2e83635000
lseek(9, 0, SEEK_SET)                   = 0
read(9, "nr_free_pages 825823\nnr_inactive"..., 1024) = 976
read(9, "", 1024)                       = 0
fstat(8, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2e83632000
lseek(8, 0, SEEK_SET)                   = 0
read(8, "   1    0 ram0 0 0 0 0 0 0 0 0 0"..., 1024) = 1024
read(8, " 0 0 0 0\n   7    6 loop6 0 0 0 0"..., 1024) = 85
read(8, "", 1024)                       = 0
lseek(7, 0, SEEK_SET)                   = 0
read(7, "cpu  103011 0 8584 22025905 4898"..., 1024) = 1024
read(7, "0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 "..., 1024) = 1024
read(7, "0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 "..., 1024) = 1024
read(7, "0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 "..., 1024) = 1024
read(7, "0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 "..., 1024) = 825
read(7, "", 1024)                       = 0
fstat(13, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2e83631000
lseek(13, 0, SEEK_SET)                  = 0
read(13, "           CPU0       CPU1      "..., 1024) = 1024
read(13, "  0          0          0       "..., 1024) = 767
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
Process 16175 detached

```

---

### Post by geertn on 2008-04-25
Looks like it's crashing when reading out the interrupt information. Found a bug for this issue:
[https://bugs.launchpad.net/ubuntu/+source/procinfo/+bug/217624](https://bugs.launchpad.net/ubuntu/+source/procinfo/+bug/217624)

---

