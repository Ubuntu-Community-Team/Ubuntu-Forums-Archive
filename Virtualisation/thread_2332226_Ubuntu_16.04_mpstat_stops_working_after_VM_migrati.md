---
title: "Ubuntu 16.04 mpstat stops working after VM migration"
date: 2016-07-29
forum: Virtualisation
---

### Post by dirtydabe on 2016-07-29
I have some ubuntu 16.04 VM running on a KVM host running Red Hat 7.1 kernel.   When I migrate the ubuntu VMs between hosts, the performance statistics reported by mpstat or the top section of top quit working.

E.G.   This is an mpstat running on an idle VM when it is migrated between hosts.   Not that the last entries are entirely 0, which should not be possible:
[FONT=courier new]11:53:18 AM  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest  %gnice   %idle[/FONT]
[FONT=courier new]11:53:23 AM  all    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00  100.00[/FONT]
[FONT=courier new]11:53:23 AM    0    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00  100.00[/FONT]
[FONT=courier new]11:53:23 AM  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest  %gnice   %idle[/FONT]
[FONT=courier new]11:53:28 AM  all    0.00    0.00    0.00    0.00    0.00    0.00  100.00    0.00    0.00    0.00[/FONT]
[FONT=courier new]11:53:28 AM    0    0.00    0.00    0.00    0.00    0.00    0.00  100.00    0.00    0.00    0.00[/FONT]
[FONT=courier new]11:53:28 AM  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest  %gnice   %idle[/FONT]
[FONT=courier new]11:53:33 AM  all    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00[/FONT]
[FONT=courier new]11:53:33 AM    0    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00[/FONT]

This is the same VM running a cpu-intensive workload.   Note that the top section claims 100% idle, but the md5sum process is consuming 99.9% cpu:
[FONT=courier new]top - 11:58:45 up 18:20,  1 user,  load average: 0.15, 0.03, 0.01[/FONT]
[FONT=courier new]Tasks: 120 total,   2 running, 118 sleeping,   0 stopped,   0 zombie[/FONT]
[FONT=courier new]%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st[/FONT]
[FONT=courier new]KiB Mem :  8175496 total,  7822328 free,    53328 used,   299840 buff/cache[/FONT]
[FONT=courier new]KiB Swap:  4190204 total,  4190204 free,        0 used.  7849064 avail Mem [/FONT]
[FONT=courier new]  PID USER      PR  NI    VIRT    RES    SHR S %CPU %MEM     TIME+ COMMAND                                                                        [/FONT]
[FONT=courier new] 3452 root      20   0    7300    664    592 R 99.9  0.0   0:07.37 md5sum                                                                         [/FONT]
[FONT=courier new] 3453 root      20   0   41820   3880   3276 R  0.3  0.0   0:00.01 top                                                                            [/FONT]
[FONT=courier new]    1 root      20   0   37828   5936   4032 S  0.0  0.1   0:01.44 systemd   [/FONT]      


If I reboot the VM, the statistics work as expected until I migrate the VM.   
I have seen this issue every time I migrated a Ubuntu 16.04 VM.
I do not see any issues on the same hosts with CentOS 7.1 clients.

Thanks for any feedback,
   David

---

