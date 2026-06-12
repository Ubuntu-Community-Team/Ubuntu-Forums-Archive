---
title: "Wine takes 4-5 minutes to start a program"
date: 2010-08-06
forum: Wine
---

### Post by apoorvumang on 2010-08-06
Wine used to work perfectly before I tried installing a program called Hamachi through wine. Hamachi didn't install, and now it takes 5-6 minutes for all programs to start. 

The process for the program appears in the system monitor way before the program actually starts. Also, some programs never start, but they still appear in the system monitor.

I think this might have something to do with Hamachi messing up the network configuration. The wine general troubleshooting guide says:

> **Speed Issues**
Why does it take 2-5 minutes to start up [my favourite program]?
M. Hearn: [Sept 05] Something is definitely wrong, check that your loopback address is configured correctly in /etc/hosts and the output of ifconfig. [You could also post to the list and check the Application Database for tips]. [Ed. check your network printers too]

Here's whats there in /etc/hosts

```
127.0.0.1	localhost
127.0.1.1	computer-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Here's what ifconfig says:

```

eth0      Link encap:Ethernet  HWaddr 00:1c:c0:0d:f4:b7  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe0d:f4b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10516 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8806989 (8.8 MB)  TX bytes:1622493 (1.6 MB)
          Interrupt:28 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7764 (7.7 KB)  TX bytes:7764 (7.7 KB)

```

I'm new to Ubuntu, so I dunno what to do next. Please help.

---

### Post by asdfoo on 2010-08-06
terminal output?  is hamachi set to run on startup? maybe it's not starting a service and it takes 5 minutes to timeout.


Do you have any network printers installed in ubuntu?

---

### Post by apoorvumang on 2010-08-07
Terminal output of what? I tried 'strace wine notepad'. Here's the output:
```

fstat64(6, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7727000
read(6, "# Locale name alias data base.\n#"..., 4096) = 2570
read(6, "", 4096)                       = 0
close(6)                                = 0
munmap(0xb7727000, 4096)                = 0
open("/usr/lib/locale/en_IN/LC_IDENTIFICATION", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFREG|0644, st_size=458, ...}) = 0
mmap2(NULL, 458, PROT_READ, MAP_PRIVATE, 6, 0) = 0xb7727000
close(6)                                = 0
open("/usr/lib/locale/en_IN/LC_MEASUREMENT", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFREG|0644, st_size=23, ...}) = 0
mmap2(NULL, 23, PROT_READ, MAP_PRIVATE, 6, 0) = 0xb7726000
close(6)                                = 0
open("/usr/lib/locale/en_IN/LC_TELEPHONE", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFREG|0644, st_size=53, ...}) = 0
mmap2(NULL, 53, PROT_READ, MAP_PRIVATE, 6, 0) = 0xb7725000
close(6)                                = 0
open("/usr/lib/locale/en_IN/LC_ADDRESS", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFREG|0644, st_size=103, ...}) = 0
mmap2(NULL, 103, PROT_READ, MAP_PRIVATE, 6, 0) = 0xb7724000
close(6)                                = 0
open("/usr/lib/locale/en_IN/LC_NAME", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFREG|0644, st_size=72, ...}) = 0
mmap2(NULL, 72, PROT_READ, MAP_PRIVATE, 6, 0) = 0xb7723000
close(6)                                = 0
open("/usr/lib/locale/en_IN/LC_PAPER", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFREG|0644, st_size=34, ...}) = 0
mmap2(NULL, 34, PROT_READ, MAP_PRIVATE, 6, 0) = 0xb7722000
close(6)                                = 0
open("/usr/lib/locale/en_IN/LC_MESSAGES", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
close(6)                                = 0
open("/usr/lib/locale/en_IN/LC_MESSAGES/SYS_LC_MESSAGES", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFREG|0644, st_size=53, ...}) = 0
mmap2(NULL, 53, PROT_READ, MAP_PRIVATE, 6, 0) = 0xb7721000
close(6)                                = 0
open("/usr/lib/locale/en_IN/LC_MONETARY", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFREG|0644, st_size=294, ...}) = 0
mmap2(NULL, 294, PROT_READ, MAP_PRIVATE, 6, 0) = 0xb7720000
close(6)                                = 0
open("/usr/lib/locale/en_IN/LC_COLLATE", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFREG|0644, st_size=1170770, ...}) = 0
mmap2(NULL, 1170770, PROT_READ, MAP_PRIVATE, 6, 0) = 0x7eee2000
close(6)                                = 0
open("/usr/lib/locale/en_IN/LC_TIME", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFREG|0644, st_size=2578, ...}) = 0
mmap2(NULL, 2578, PROT_READ, MAP_PRIVATE, 6, 0) = 0x7eee1000
close(6)                                = 0
open("/usr/lib/locale/en_IN/LC_NUMERIC", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
mmap2(NULL, 54, PROT_READ, MAP_PRIVATE, 6, 0) = 0x7eee0000
close(6)                                = 0
open("/usr/lib/locale/en_IN/LC_CTYPE", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFREG|0644, st_size=256324, ...}) = 0
mmap2(NULL, 256324, PROT_READ, MAP_PRIVATE, 6, 0) = 0x7eea1000
close(6)                                = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
mmap2(0x220000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x220000
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
writev(3, [{"Y\0\0\0 \0\0\0\0\0\0\0\0\0\0\0?\0\17\0\0\0\0\0\1\0\0\0 \0\0\0"..., 64}, {"M\0a\0c\0h\0i\0n\0e\0\\\0H\0A\0R\0D\0W\0A\0R\0E\0", 32}], 2) = 96
read(5, "\0\0\0\0\0\0\0\0\20\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "\23\0\0\0\0\0\0\0\0\0\0\0\20\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
writev(3, [{"Z\0\0\0\210\0\0\0\0\0\0\0\0\0\0\0\31\0\2\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64}, {"M\0a\0c\0h\0i\0n\0e\0\\\0S\0y\0s\0t\0e\0m\0\\\0C\0"..., 136}], 2) = 200
read(5, "\0\0\0\0\0\0\0\0\20\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\0\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0`\0\0\0\1\0\0\0`\0\0\0$\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "C\0o\0m\0m\0o\0n\0P\0r\0o\0g\0r\0a\0m\0F\0i\0l\0"..., 96) = 96
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\1\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0F\0\0\0\2\0\0\0F\0\0\0\16\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "C\0o\0m\0S\0p\0e\0c\0C\0:\0\\\0w\0i\0n\0d\0o\0w\0"..., 70) = 70
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\2\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0,\0\0\0\1\0\0\0,\0\0\0(\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "N\0U\0M\0B\0E\0R\0_\0O\0F\0_\0P\0R\0O\0C\0E\0S\0"..., 44) = 44
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\3\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\32\0\0\0\1\0\0\0\32\0\0\0\4\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "O\0S\0W\0i\0n\0d\0o\0w\0s\0_\0N\0T\0\0\0", 26) = 26
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\4\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0x\0\0\0\2\0\0\0x\0\0\0\10\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "P\0A\0T\0H\0C\0:\0\\\0w\0i\0n\0d\0o\0w\0s\0\\\0s\0"..., 120) = 120
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\5\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0p\0\0\0\1\0\0\0p\0\0\0\16\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "P\0A\0T\0H\0E\0X\0T\0.\0C\0O\0M\0;\0.\0E\0X\0E\0"..., 112) = 112
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\6\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0004\0\0\0\1\0\0\0004\0\0\0,\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "P\0R\0O\0C\0E\0S\0S\0O\0R\0_\0A\0R\0C\0H\0I\0T\0"..., 52) = 52
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\7\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\210\0\0\0\1\0\0\0\210\0\0\0(\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "P\0R\0O\0C\0E\0S\0S\0O\0R\0_\0I\0D\0E\0N\0T\0I\0"..., 136) = 136
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\10\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\"\0\0\0\1\0\0\0\"\0\0\0\36\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "P\0R\0O\0C\0E\0S\0S\0O\0R\0_\0L\0E\0V\0E\0L\0006\0"..., 34) = 34
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\t\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0.\0\0\0\1\0\0\0.\0\0\0$\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "P\0R\0O\0C\0E\0S\0S\0O\0R\0_\0R\0E\0V\0I\0S\0I\0"..., 46) = 46
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\n\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0:\0\0\0\1\0\0\0:\0\0\0\30\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "P\0r\0o\0g\0r\0a\0m\0F\0i\0l\0e\0s\0C\0:\0\\\0P\0"..., 58) = 58
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\v\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\34\0\0\0\1\0\0\0\34\0\0\0\26\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "S\0y\0s\0t\0e\0m\0D\0r\0i\0v\0e\0c\0:\0\0\0", 28) = 28
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\f\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0*\0\0\0\1\0\0\0*\0\0\0\24\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "S\0Y\0S\0T\0E\0M\0R\0O\0O\0T\0C\0:\0\\\0w\0i\0n\0"..., 42) = 42
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\r\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0(\0\0\0\2\0\0\0(\0\0\0\10\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "T\0E\0M\0P\0C\0:\0\\\0w\0i\0n\0d\0o\0w\0s\0\\\0t\0"..., 40) = 40
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\16\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0&\0\0\0\2\0\0\0&\0\0\0\6\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "T\0M\0P\0C\0:\0\\\0w\0i\0n\0d\0o\0w\0s\0\\\0t\0e\0"..., 38) = 38
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\17\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\"\0\0\0\2\0\0\0\"\0\0\0\f\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "w\0i\0n\0d\0i\0r\0C\0:\0\\\0w\0i\0n\0d\0o\0w\0s\0"..., 34) = 34
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\20\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0:\0\0\0\1\0\0\0:\0\0\0\22\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "w\0i\0n\0s\0y\0s\0d\0i\0r\0C\0:\0\\\0w\0i\0n\0d\0"..., 58) = 58
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\21\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\32\0\0\200\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\0\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0`\0\0\0\1\0\0\0`\0\0\0$\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "C\0o\0m\0m\0o\0n\0P\0r\0o\0g\0r\0a\0m\0F\0i\0l\0"..., 96) = 96
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\1\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0F\0\0\0\2\0\0\0F\0\0\0\16\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "C\0o\0m\0S\0p\0e\0c\0C\0:\0\\\0w\0i\0n\0d\0o\0w\0"..., 70) = 70
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\2\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0,\0\0\0\1\0\0\0,\0\0\0(\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "N\0U\0M\0B\0E\0R\0_\0O\0F\0_\0P\0R\0O\0C\0E\0S\0"..., 44) = 44
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\3\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\32\0\0\0\1\0\0\0\32\0\0\0\4\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "O\0S\0W\0i\0n\0d\0o\0w\0s\0_\0N\0T\0\0\0", 26) = 26
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\4\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0x\0\0\0\2\0\0\0x\0\0\0\10\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "P\0A\0T\0H\0C\0:\0\\\0w\0i\0n\0d\0o\0w\0s\0\\\0s\0"..., 120) = 120
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\5\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0p\0\0\0\1\0\0\0p\0\0\0\16\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "P\0A\0T\0H\0E\0X\0T\0.\0C\0O\0M\0;\0.\0E\0X\0E\0"..., 112) = 112
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\6\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0004\0\0\0\1\0\0\0004\0\0\0,\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "P\0R\0O\0C\0E\0S\0S\0O\0R\0_\0A\0R\0C\0H\0I\0T\0"..., 52) = 52
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\7\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\210\0\0\0\1\0\0\0\210\0\0\0(\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "P\0R\0O\0C\0E\0S\0S\0O\0R\0_\0I\0D\0E\0N\0T\0I\0"..., 136) = 136
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\10\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\"\0\0\0\1\0\0\0\"\0\0\0\36\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "P\0R\0O\0C\0E\0S\0S\0O\0R\0_\0L\0E\0V\0E\0L\0006\0"..., 34) = 34
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\t\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0.\0\0\0\1\0\0\0.\0\0\0$\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "P\0R\0O\0C\0E\0S\0S\0O\0R\0_\0R\0E\0V\0I\0S\0I\0"..., 46) = 46
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\n\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0:\0\0\0\1\0\0\0:\0\0\0\30\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "P\0r\0o\0g\0r\0a\0m\0F\0i\0l\0e\0s\0C\0:\0\\\0P\0"..., 58) = 58
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\v\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\34\0\0\0\1\0\0\0\34\0\0\0\26\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "S\0y\0s\0t\0e\0m\0D\0r\0i\0v\0e\0c\0:\0\0\0", 28) = 28
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\f\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0*\0\0\0\1\0\0\0*\0\0\0\24\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "S\0Y\0S\0T\0E\0M\0R\0O\0O\0T\0C\0:\0\\\0w\0i\0n\0"..., 42) = 42
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\r\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0(\0\0\0\2\0\0\0(\0\0\0\10\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "T\0E\0M\0P\0C\0:\0\\\0w\0i\0n\0d\0o\0w\0s\0\\\0t\0"..., 40) = 40
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\16\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0&\0\0\0\2\0\0\0&\0\0\0\6\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "T\0M\0P\0C\0:\0\\\0w\0i\0n\0d\0o\0w\0s\0\\\0t\0e\0"..., 38) = 38
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\17\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\"\0\0\0\2\0\0\0\"\0\0\0\f\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "w\0i\0n\0d\0i\0r\0C\0:\0\\\0w\0i\0n\0d\0o\0w\0s\0"..., 34) = 34
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\20\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0:\0\0\0\1\0\0\0:\0\0\0\22\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "w\0i\0n\0s\0y\0s\0d\0i\0r\0C\0:\0\\\0w\0i\0n\0d\0"..., 58) = 58
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\20\0\0\0\21\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\32\0\0\200\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "\23\0\0\0\0\0\0\0\0\0\0\0\20\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "\307\0\0\0\0\0\0\0\0\0\0\0\376\377\377\377\10\0\2\0\0\0\0\0\3\0\0\0\0\0\0\0"..., 64) = 64
read(5, "|\0\0\300\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "\307\0\0\0\0\0\0\0\0\0\0\0\377\377\377\377\10\0\2\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\0\0\0\0\20\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "\316\0\0\0\0\0\0\0H\0\0\0\20\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\f\0\0\0\f\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\1\1\0\0\0\0\0\5\4\0\0\0", 12) = 12
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "\23\0\0\0\0\0\0\0\0\0\0\0\20\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
writev(3, [{"Y\0\0\0,\0\0\0\0\0\0\0\0\0\0\0\31\0\2\0@\0\0\0\0\0\0\0,\0\0\0"..., 64}, {"\\\0R\0e\0g\0i\0s\0t\0r\0y\0\\\0U\0s\0e\0r\0\\\0S\0"..., 44}], 2) = 108
read(5, "\0\0\0\0\0\0\0\0\20\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
writev(3, [{"Z\0\0\0\26\0\0\0\0\0\0\0\20\0\0\0\31\0\2\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64}, {"E\0n\0v\0i\0r\0o\0n\0m\0e\0n\0t\0", 22}], 2) = 86
read(5, "\0\0\0\0\0\0\0\0\24\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\24\0\0\0\0\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0006\0\0\0\1\0\0\0006\0\0\0\10\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "T\0E\0M\0P\0C\0:\0\\\0u\0s\0e\0r\0s\0\\\0c\0o\0m\0"..., 54) = 54
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\24\0\0\0\1\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0004\0\0\0\1\0\0\0004\0\0\0\6\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "T\0M\0P\0C\0:\0\\\0u\0s\0e\0r\0s\0\\\0c\0o\0m\0p\0"..., 52) = 52
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\24\0\0\0\2\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\32\0\0\200\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\24\0\0\0\0\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0006\0\0\0\1\0\0\0006\0\0\0\10\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "T\0E\0M\0P\0C\0:\0\\\0u\0s\0e\0r\0s\0\\\0c\0o\0m\0"..., 54) = 54
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\24\0\0\0\1\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0004\0\0\0\1\0\0\0004\0\0\0\6\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "T\0M\0P\0C\0:\0\\\0u\0s\0e\0r\0s\0\\\0c\0o\0m\0p\0"..., 52) = 52
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "`\0\0\0\0\0\0\0\4\10\0\0\24\0\0\0\2\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\32\0\0\200\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "\23\0\0\0\0\0\0\0\0\0\0\0\24\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
writev(3, [{"Z\0\0\0(\0\0\0\0\0\0\0\20\0\0\0\31\0\2\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64}, {"V\0o\0l\0a\0t\0i\0l\0e\0 \0E\0n\0v\0i\0r\0o\0n\0"..., 40}], 2) = 104
read(5, "4\0\0\300\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "\23\0\0\0\0\0\0\0\0\0\0\0\20\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
writev(3, [{"Z\0\0\0\200\0\0\0\0\0\0\0\0\0\0\0\31\0\2\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64}, {"M\0a\0c\0h\0i\0n\0e\0\\\0S\0o\0f\0t\0w\0a\0r\0e\0"..., 128}], 2) = 192
read(5, "\0\0\0\0\0\0\0\0\20\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
writev(3, [{"_\0\0\0\"\0\0\0\4\10\0\0\20\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64}, {"P\0r\0o\0f\0i\0l\0e\0s\0D\0i\0r\0e\0c\0t\0o\0r\0"..., 34}], 2) = 98
read(5, "\0\0\0\0\22\0\0\0\2\0\0\0\22\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "C\0:\0\\\0u\0s\0e\0r\0s\0\0\0", 18) = 18
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
writev(3, [{"_\0\0\0\36\0\0\0\4\10\0\0\20\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64}, {"A\0l\0l\0U\0s\0e\0r\0s\0P\0r\0o\0f\0i\0l\0e\0", 30}], 2) = 94
read(5, "\0\0\0\0\16\0\0\0\2\0\0\0\16\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "P\0u\0b\0l\0i\0c\0\0\0", 14)   = 14
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "\23\0\0\0\0\0\0\0\0\0\0\0\20\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
stat64("/home/computer/.wine/dosdevices/c:/windows", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/home/computer/.wine/dosdevices/c:/windows/system32", {st_mode=S_IFDIR|0755, st_size=16384, ...}) = 0
getcwd("/home/computer", 256)           = 15
stat64("/home/computer", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/home/computer", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
time(NULL)                              = 1281182771
stat64("/home/computer/.wine/dosdevices/a:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/b:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/c:", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/home/computer/.wine/dosdevices/d:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/e:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/f:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/g:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/h:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/i:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/j:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/k:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/l:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/m:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/n:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/o:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/p:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/q:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/r:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/s:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/t:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/u:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/v:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/w:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/x:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/y:", 0xbff11030) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/z:", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/home/computer", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/home", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/home/computer/.wine/dosdevices/z:/home/computer", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
writev(3, [{"\"\0\0\0<\0\0\0\0\0\0\0\0\0\0\0@\0\0\0\0\0\0\0\1\0\0\0!\0\0\0"..., 64}, {"\0\0\0\0\0\0\0\0\0\0\0\0", 12}, {"/home/computer/.wine/dosdevices/"..., 48}], 3) = 124
read(5, "\0\0\0\0\0\0\0\0\20\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "&\0\0\0\0\0\0\0\0\0\0\0\20\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\0\0\0\0\2\0\0\0\0\0\0\0\0\0\0\0!\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
recvmsg(4, {msg_name(0)=NULL, msg_iov(1)=[{"\20\0\0\0", 4}], msg_controllen=16, {cmsg_len=16, cmsg_level=SOL_SOCKET, cmsg_type=SCM_RIGHTS, {6}}, msg_flags=MSG_CMSG_CLOEXEC}, MSG_CMSG_CLOEXEC) = 4
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
fstat64(6, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
pread64(6, 0xbff112a5, 23, 0)           = -1 EISDIR (Is a directory)
fstatfs64(6, 84, {f_type="EXT2_SUPER_MAGIC", f_bsize=4096, f_blocks=58612444, f_bfree=55479627, f_bavail=52502271, f_files=14893056, f_ffree=14650798, f_fsid={26026631, -1631994833}, f_namelen=255, f_frsize=4096}) = 0
prctl(PR_SET_NAME, 0xbff1365c, 0x7b87e5f0, 0x7b87dc5f, 0x7bcb4c29) = 0
stat64("/home/computer/.wine/dosdevices/z:/home/computer/notepad.exe", 0xbff10cf8) = -1 ENOENT (No such file or directory)
stat64("/home/computer/.wine/dosdevices/z:/home", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/home/computer/.wine/dosdevices/z:/home/computer", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/home/computer/.wine/dosdevices/z:/home/computer/notepad.exe", 0xbff10bb8) = -1 ENOENT (No such file or directory)
open("/home/computer/.wine/dosdevices/z:/home/computer", O_RDONLY|O_LARGEFILE|O_DIRECTORY) = 9
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
mmap2(0x222000, 8192, PROT_NONE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x222000
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
mprotect(0x222000, 4096, PROT_READ|PROT_WRITE) = 0
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
ioctl(9, TUNIOCGETINFO or VFAT_IOCTL_READDIR_BOTH, 0x222000) = -1 ENOTTY (Inappropriate ioctl for device)
close(9)                                = 0
open("/home/computer/.wine/dosdevices/z:/home/computer", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
fcntl64(9, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
getdents64(9, /* 96 entries */, 32768)  = 3264
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
stat64("/home/computer/.wine/dosdevices/c:/windows/system32/notepad.exe", {st_mode=S_IFREG|0755, st_size=100768, ...}) = 0
stat64("/home/computer/.wine/dosdevices/c:/windows/system32/notepad.exe", {st_mode=S_IFREG|0755, st_size=100768, ...}) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "\307\0\0\0\0\0\0\0\0\0\0\0\376\377\377\377\10\0\2\0\0\0\0\0\3\0\0\0\0\0\0\0"..., 64) = 64
read(5, "|\0\0\300\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "\307\0\0\0\0\0\0\0\0\0\0\0\377\377\377\377\10\0\2\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\0\0\0\0\24\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "\316\0\0\0\0\0\0\0H\0\0\0\24\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\f\0\0\0\f\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\1\1\0\0\0\0\0\5\4\0\0\0", 12) = 12
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "\23\0\0\0\0\0\0\0\0\0\0\0\24\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
writev(3, [{"Y\0\0\0,\0\0\0\0\0\0\0\0\0\0\0?\0\17\0@\0\0\0\0\0\0\0,\0\0\0"..., 64}, {"\\\0R\0e\0g\0i\0s\0t\0r\0y\0\\\0U\0s\0e\0r\0\\\0S\0"..., 44}], 2) = 108
read(5, "\0\0\0\0\0\0\0\0\24\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
writev(3, [{"Z\0\0\0\32\0\0\0\0\0\0\0\24\0\0\0?\0\17\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64}, {"S\0o\0f\0t\0w\0a\0r\0e\0\\\0W\0i\0n\0e\0", 26}], 2) = 90
read(5, "\0\0\0\0\0\0\0\0\30\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
writev(3, [{"_\0\0\0\30\0\0\0D\0\0\0\30\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64}, {"S\0h\0o\0w\0D\0o\0t\0F\0i\0l\0e\0s\0", 24}], 2) = 88
read(5, "4\0\0\300\0\0\0\0\377\377\377\377\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "\23\0\0\0\0\0\0\0\0\0\0\0\30\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
write(3, "\23\0\0\0\0\0\0\0\0\0\0\0\24\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
read(5, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
stat64("/home/computer/.wine", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/dev", {st_mode=S_IFDIR|0755, st_size=3740, ...}) = 0
stat64("/proc", {st_mode=S_IFDIR|0555, st_size=0, ...}) = 0
stat64("/sys", {st_mode=S_IFDIR|0755, st_size=0, ...}) = 0
open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = 9
fstat64(9, {st_mode=S_IFREG|0644, st_size=26048, ...}) = 0
mmap2(NULL, 26048, PROT_READ, MAP_SHARED, 9, 0) = 0x7ee9a000
close(9)                                = 0
futex(0x7222ba8c, FUTEX_WAKE_PRIVATE, 2147483647) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
writev(3, [{"\327\0\0\0\"\0\0\0\0\0\0\0\6\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64}, {"\\\0B\0a\0s\0e\0N\0a\0m\0e\0d\0O\0b\0j\0e\0c\0t\0"..., 34}], 2) = 98
read(5, "\0\0\0\0\0\0\0\0\24\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
writev(3, [{"\31\0\0\0,\0\0\0\0\0\0\0\3\0\37\0\200\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 64}, {"\24\0\0\0\0\0\0\0 \0\0\0", 12}, {"_\0_\0w\0i\0n\0e\0b\0o\0o\0t\0_\0e\0v\0e\0n\0t\0", 32}], 3) = 108
read(5, "\0\0\0@\0\0\0\0\30\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [HUP INT USR1 USR2 ALRM CHLD IO], 8) = 0
writev(3, [{"\30\0\0\0,\0\0\0\0\0\0\0\4\0\0\0\234\21\361\277\0\0\0\0\0\0\0\0\0\0\0\0"..., 64}, {"\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 40}, {"\30\0\0\0", 4}], 3) = 108
read(5, "\3\1\0\0\0\0\0\0Z\203\3064)6\313\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64) = 64
rt_sigprocmask(SIG_SETMASK, [HUP INT USR1 USR2 ALRM CHLD IO], NULL, 8) = 0
read(7,

```

After this, it just stays there for like 5 minutes, and then notepad starts. (sorry, I dunno what part of the output I should post)


No, hamachi isnt set to run on startup. I don't think it even runs.
No network printers either.

I think the problem might be with the network configuration or something like that getting messed up, since Hamachi is a program for setting up a VPN. (Don't trust me, I'm a newbie)

---

### Post by bprins on 2010-08-07
tried to reinstall wine?
which wine version are you running?
which ubuntu version are you running?

dunno what else you do with wine, but IF it worked properly before, and you are able to reinstall whatever you used wine for, throw away ur ~/.wine folder, uninstall wine, reinstall wine, and see how it goes. 

if ur unsure about throwing away .wine, back it up instead :).

---

### Post by apoorvumang on 2010-08-09
Well, deleting .wine did the trick (notepad works without a hitch). I guess I'll just reinstall the other programs.
A BIG thanks to you, bprins :)

---

### Post by asdfoo on 2010-08-09
terminal output, for future reference: [http://wiki.winehq.org/FAQ#get_log](http://wiki.winehq.org/FAQ#get_log)

---

