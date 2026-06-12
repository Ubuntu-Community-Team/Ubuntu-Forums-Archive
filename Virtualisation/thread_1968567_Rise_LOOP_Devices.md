---
title: "Rise LOOP Devices"
date: 2012-04-29
forum: Virtualisation
---

### Post by Mindpopper on 2012-04-29
Hi,

i installed the new Ubuntu 12.04 LTS Server and added XEN Hypervisor by installing ```
xen-hypervisor-4.1-amd64
```Also i created 4 virtual machines.

Every machine works good. But if i want to start more than 3 machines i get an error message at ```
xm create xyz.cfg
``` ```
Error: Device 51728 (vbd) could not be connected. Failed to find an unused loop device
```my ubuntu installation (under Xen 4.1) has 8 loop devices in /dev
```
root@xenserver:/# ls -la /dev/loop*
brw-rw---- 1 root disk  7,   0 Apr 29 01:07 /dev/loop0
brw-rw---- 1 root disk  7,   1 Apr 29 01:07 /dev/loop1
brw-rw---- 1 root disk  7,   2 Apr 29 14:16 /dev/loop2
brw-rw---- 1 root disk  7,   3 Apr 29 14:16 /dev/loop3
brw-rw---- 1 root disk  7,   4 Apr 29 14:16 /dev/loop4
brw-rw---- 1 root disk  7,   5 Apr 29 14:28 /dev/loop5
brw-rw---- 1 root disk  7,   6 Apr 29 14:28 /dev/loop6
brw-rw---- 1 root disk  7,   7 Apr 29 14:20 /dev/loop7
crw------- 1 root root 10, 237 Apr 29 01:07 /dev/loop-control
```Then i tried to rise/increase[]("http://dict.leo.org/ende?lp=ende&p=DOKJAA&search=increase&trestr=0x8002") the count of loop devices:

1st try:
Create ```
/etc/modprobe.d/local-loop.conf
``` and add ```
options loop max_loop=64
```Same result, ls /dev/loop* lists 8 loop Devices (loop0 - loop7) and loop-control

2nd try:
changed in ```
/etc/modules
``` the line ```
loop
``` with ```
loop max_loop=64
```Same result

Both examples i tried with and without ```
update-initramfs -u
``` and/or ```
[FONT=&quot]update-grub2[/FONT]
```At google i find nothing else to fix this problem.

Can anybody help, please!

---

### Post by Mindpopper on 2012-04-30
The Answer is so simple:

edit **/etc/defaults/grub**

and added the code **max_loop=64** just after the [B]GRUB_CMDLINE_LINUX_DEFAULT=""

[/B]then execute **update-grub2**, reboot and verify with **ls /dev/loop***

---

