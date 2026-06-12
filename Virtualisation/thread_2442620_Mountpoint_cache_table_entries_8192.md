---
title: "Mountpoint cache table entries 8192"
date: 2020-05-05
forum: Virtualisation
---

### Post by sekiro on 2020-05-05
Hello Everyone,

I run Ubuntu Server 18.04 with virtualbox.
My windows has rebooted after installed Docker.

Since that reboot Ubuntu don't boot anymore, and there start the trouble.
I have no idea about how to fix a Linux that stuck a booting.

It's seems that it is possible to extract the boot text sequence but I don't know how to do so.
So I extraced it manually hope it can help.

```
0.000000] ftrace: al locating 39364 entries in 154 pages
0.004000] Hierarchical RCU implementation.
0.004000] oRCU restricting CPUs from NR_CPUS=8192 to nr_cpu_ids=4.
0.004000] oTasks RCU enabled.
9.004000] RCU: Adjusting geometry for rcu_fanout_leaf-16, nr_cpu_ids=4
O. O040001 NR_IRAS: 524511, m_irqs: 456, preallocated irqs: 16
0.004000] Console : colour UGA+ 80x25
0.004000] console [tty0] enabled
0.004000] ACP I : Core revision 20170831
O. 004000] ACPI: 2 ACPI AML tables successfully acquired and loaded
0.004000] APIC: Switch to symmetric I/0 mode setup
0.004000] . .TIMER&#3632; vector=0x30 apic1-0 pin1-2 apic2=-1 pin2=-1
0.004000] tsc: Detected 3192.746 MHz processor
8.004000] Calibrating delay loop (skipped) preset value.. 6385.49 BogoMIPS
(lpj=12770984)
0.004000] pid_max: default: 32768 minimum: 301
8.004000] Security Framework initialized
0.004000 Yama: becoming mindful.
0.004000] Apprmor: Apparmor initialized
8.037160] Dentry cache hash table entries: 524288(order: 10, 4194304 bytes
8.9577201 Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
9.961315] Mount-cache hash table entries: B192 (order: 4. 65536 bytes)
0.068425] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)


```

---

### Post by sekiro on 2020-05-06
Solution *disable Hyper*-V (got activated by update)
Then all is working fine.

---

