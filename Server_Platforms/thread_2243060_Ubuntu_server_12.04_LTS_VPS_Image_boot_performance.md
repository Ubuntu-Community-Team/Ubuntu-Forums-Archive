---
title: "Ubuntu server 12.04 LTS VPS Image boot performance question"
date: 2014-09-06
forum: Server Platforms
---

### Post by ryan108 on 2014-09-06
Hi guys,

I'm still fairly newb with linux I'd say even though I've used it off and on for the past decade..
My question today is regarding ubuntu server 12.04 LTS and VPS providers images boot times.

I have one VPS provider whom my VPS image runs flawlessly and amazingly fast. It runs on 3 vcores, 1gb ram and 1gb vswap with a 75gb SSD.
My other one runs slowish, 1 vcore, 512mb ram, 10gb SSD.

both run 12.04 LTS.

The first one can reboot/boot and be ready within around 5 seconds. The second one takes a good minute to reboot/boot. I know it could be combination of hardware and the VPS providers 12.04 custom image they provide.

I was wondering what steps I could take to figure out if it is a hardware issue that is causing the 1 minute boot time or if its something that can be drastically reduced via software tweaks(kernel/startup services).

I did uname -a and the fast one shows:
Linux vps 2.6.32-042stab084.12 #1 SMP Tue Nov 26 20:18:08 MSK 2013 x86_64 x86_64 x86_64 GNU/Linux

slow VPS provider shows:
Linux ubuntu 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


the TOP for the fast one shows:




top - 13:26:18 up 1 day, 11:13,  2 users,  load average: 0.00, 0.00, 0.00
Tasks:  29 total,   1 running,  28 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1048576k total,   191824k used,   856752k free,        0k buffers
Swap:  1048576k total,        0k used,  1048576k free,   137532k cached


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
    1 root      20   0 24140 2112 1344 S    0  0.2   0:00.05 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd/881
    3 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper/881
   82 root      20   0 17192  740  516 S    0  0.1   0:00.00 upstart-udev-br
  106 root      20   0 21532 1364  792 S    0  0.1   0:00.00 udevd
  107 messageb  20   0 23776  788  520 S    0  0.1   0:00.00 dbus-daemon
  142 root      20   0 21528  924  348 S    0  0.1   0:00.00 udevd
  143 root      20   0 21528  924  348 S    0  0.1   0:00.00 udevd
  188 root      20   0 15148  544  360 S    0  0.1   0:00.00 upstart-socket-
  320 root      20   0 49996 2940 2332 S    0  0.3   0:00.00 sshd
  349 root      20   0  4360  780  608 S    0  0.1   0:00.00 rc
  355 root      20   0 19072  940  732 S    0  0.1   0:00.08 cron
  356 root      20   0 14928 1124  928 S    0  0.1   0:00.00 xinetd
  399 syslog    20   0 12712  860  660 S    0  0.1   0:00.09 syslogd
  425 bind      20   0  327m  30m 2824 S    0  3.0   0:18.51 named
  473 root      20   0 78700 1140  440 S    0  0.1   0:00.00 saslauthd
  475 root      20   0 78700  740   40 S    0  0.1   0:00.00 saslauthd
  530 root      20   0  4360  748  580 S    0  0.1   0:00.00 S99rc.local
  531 root      20   0   808  132  104 S    0  0.0   0:00.22 .IptabLex
  534 root      20   0  4360  648  548 S    0  0.1   0:00.00 sh
  539 root      20   0 23976 1144  900 S    0  0.1   0:00.14 screen
  540 root      20   0 24108 1380  900 S    0  0.1   0:00.00 screen
  541 root      20   0  643m  10m 4640 S    0  1.0   0:00.03 node
  737 daemon    20   0 22616 1580  964 S    0  0.2   0:03.49 sniproxy
  738 root      20   0 13856  236  108 S    0  0.0   0:00.00 sniproxy
16406 root      20   0 73400 3760 2892 S    0  0.4   0:00.32 sshd
16419 root      20   0 18264 2228 1508 S    0  0.2   0:00.00 bash
19608 root      20   0 11044  336  288 S    0  0.0   0:00.00 .IptabLex
19614 root      20   0 17160 1220  960 R    0  0.1   0:00.00 top


slow one shows:
Tasks:  67 total,   1 running,  66 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us,  0.1%sy,  0.0%ni, 98.7%id,  1.1%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    502716k total,   331180k used,   171536k free,    13076k buffers
Swap:   976892k total,        0k used,   976892k free,   261040k cached


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
    1 root      20   0 24320 2248 1360 S  0.0  0.4   0:01.18 init
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.35 ksoftirqd/0
    5 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kworker/0:0H
    6 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kworker/u:0
    7 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kworker/u:0H
    8 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 rcu_bh
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.18 rcu_sched
   11 root      RT   0     0    0    0 S  0.0  0.0   0:00.04 watchdog/0
   12 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset
   13 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper
   14 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kdevtmpfs
   15 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 netns
   16 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default
   17 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kintegrityd
   18 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kblockd
   19 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 ata_sff
   20 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khubd
   21 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 md
   22 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 devfreq_wq
   23 root      20   0     0    0    0 S  0.0  0.0   0:02.87 kworker/0:1
   25 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khungtaskd
   26 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
   27 root      25   5     0    0    0 S  0.0  0.0   0:00.00 ksmd
   28 root      20   0     0    0    0 S  0.0  0.0   0:00.00 fsnotify_mark
   29 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-kthrea
   30 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 crypto
   41 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kthrotld
   42 root      20   0     0    0    0 S  0.0  0.0   0:00.15 kworker/u:1
   43 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
   44 root      20   0     0    0    0 S  0.0  0.0   0:00.02 scsi_eh_1
   46 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 binder
   66 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 deferwq
   67 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 charger_manager
  201 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 mpt_poll_0
  202 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 mpt/0
  212 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2
  225 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kdmflush
  241 root      20   0     0    0    0 S  0.0  0.0   0:00.02 jbd2/dm-0-8
  242 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 ext4-dio-unwrit
  335 root      20   0 17456  984  536 S  0.0  0.2   0:00.07 upstart-udev-br
  338 root      20   0 21588 1392  804 S  0.0  0.3   0:00.05 udevd
  456 root      20   0 21584  884  332 S  0.0  0.2   0:00.00 udevd
  457 root      20   0 21600  872  324 S  0.0  0.2   0:00.00 udevd
  543 messageb  20   0 23820  932  644 S  0.0  0.2   0:00.02 dbus-daemon
  547 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kpsmoused
  551 syslog    20   0  243m 1536 1124 S  0.0  0.3   0:00.02 rsyslogd
  552 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 ttm_swap
  583 root      20   0 15192  400  204 S  0.0  0.1   0:00.00 upstart-socket-
  643 root      20   0 50036 2908 2300 S  0.0  0.6   0:00.00 sshd
  741 root      20   0 15788  964  800 S  0.0  0.2   0:00.00 getty
  746 root      20   0 15788  960  800 S  0.0  0.2   0:00.00 getty
  758 root      20   0 15788  964  800 S  0.0  0.2   0:00.00 getty
  759 root      20   0 15788  964  800 S  0.0  0.2   0:00.00 getty



I have yet to even configure anything on the slow VPS. the fast one has everything I want configured and has way less stuff running it seems. 

I don't know if that is the issue or if its a combo still of startup stuff and hardware limitations seeing as the slow one is on 1 vcore vs the fast VPS image has 3 vcores.

I've tried looking up some optimization guides but haven't found a lot of luck other than guides that explain to optimize 12.04 desktops not servers or when they explain server optimization its mostly showing me stuff for optimizing mysql/apache etc. which I don't even use.


Can someone give me some pointers as to how to optimize a VPS image kernel/remove all these stock services? Along with if you think it's a hardware limitation vs software. I know there's only so much you can optimize with software before hardware does become the limitation. However I believe 1 vcore vs 3 isn't even really the issue since I believe that 1 vcore dedicated to my node is plenty enough for making a speedy ubuntu, on my 3 vcore VPS package I dont even think the other vcores ever get utilized during the boot process.

---

### Post by ryan108 on 2014-09-10
*bump* is there anyone able to help out with this problem?

---

