---
title: "Boot takes several hours"
date: 2013-03-24
forum: Server Platforms
---

### Post by LeDieu on 2013-03-24
I have a VPS running Ubuntu 10.04.4 LTS and for a while a reboot is taking several hours before the system is up and running.
After looking at my dmesg I think it might be related to a driver that Ubuntu is trying to load. But since this is really outsize my knowledge zone I decited to post my problem here in the hope some of you can help me solve this.
 
My (questionable) dmesg lines. If the whole dmesg is needed please say so.
```
[    0.264088] hub 1-0:1.0: USB hub found
[    0.264111] hub 1-0:1.0: 2 ports detected
[ 6092.284975] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[ 6092.286765] serio: i8042 KBD port at 0x60,0x64 irq 1
```

Cheers.

---

### Post by matt_symes on 2013-03-24
Hi

Several hours ? Blimey !

It may be better to publish the entire dmesg.

Post it using pastebin and post a link.

```
sudo apt-get install pastebinit
```

```
dmseg | pastebinit
```

or

```
cat /var/log/dmesg | pastebinit
```

Post the link.

Kind regards

---

### Post by LeDieu on 2013-03-24
Sure thing mate. Here you go:
```
[http://pastebin.com/wwkaX6cq](http://pastebin.com/wwkaX6cq)
```

---

### Post by matt_symes on 2013-03-25
Hi
```

[    0.264088] hub 1-0:1.0: USB hub found
[    0.264111] hub 1-0:1.0: 2 ports detected
[ 6092.284975] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[ 6092.286765] serio: i8042 KBD port at 0x60,0x64 irq 1
```

That's quite a delay there :D

I have come across reports of the USB subsystem causing these boot issues on VPS.

Try booting with the kernel command line parameter

```
nousb
```
You'll have to edit ```
/etc/default/grub
``` to do this and you will lose USB, however you have a VPS so i suspect you're not using USB.

Post back on efficacy.

EDIT:

Incidentally, you are also getting a kernel oops at boot up.

```

[    0.028001] Pid: 0, comm: swapper Not tainted 2.6.32-45-generic #104-Ubuntu
[    0.028001] Call Trace:
[    0.028001]  [<c014d2d2>] warn_slowpath_common+0x72/0xa0
[    0.028001]  [<c058b12b>] ? init_amd_k7+0x130/0x157
[    0.028001]  [<c058b12b>] ? init_amd_k7+0x130/0x157
[    0.028001]  [<c014d34b>] warn_slowpath_fmt+0x2b/0x30
[    0.028001]  [<c058b12b>] init_amd_k7+0x130/0x157
[    0.028001]  [<c058b2b2>] init_amd+0x84/0x22f
[    0.028001]  [<c058a54f>] ? generic_identify+0x131/0x178
[    0.028001]  [<c058a65a>] identify_cpu+0xc4/0x224
[    0.028001]  [<c058f452>] ? cpu_callback+0xd/0x11b
[    0.028001]  [<c058f69d>] ? relay_hotcpu_callback+0xe/0x99
[    0.028001]  [<c01d32fc>] ? writeback_set_ratelimit+0x1c/0x60
[    0.028001]  [<c0595263>] ? notifier_call_chain+0x43/0x60
[    0.028001]  [<c058a7cd>] identify_secondary_cpu+0x13/0x1f
[    0.028001]  [<c058d7f4>] smp_store_cpu_info+0x36/0x3a
[    0.028001]  [<c058d8d5>] smp_callin+0xdd/0xeb
[    0.028001]  [<c058db8c>] start_secondary+0x34/0xc6
```

What kernels do you have on the VPS ? 

Do you still set the same issues if you boot into an older kernel ? 

When did this boot time issue start ?

Kind regards

---

### Post by sandyd on 2013-03-25
for kernel oops
```

[    0.028001] ------------[ cut here ]------------
[    0.028001] WARNING: at /build/buildd/linux-2.6.32/arch/x86/kernel/cpu/amd.c:187 init_amd_k7+0x130/0x157()
[    0.028001] Hardware name: Bochs
[    0.028001] WARNING: This combination of AMD processors is not suitable for SMP.
[    0.028001] Modules linked in:
[    0.028001] Pid: 0, comm: swapper Not tainted 2.6.32-45-generic #104-Ubuntu
[    0.028001] Call Trace:
[    0.028001]  [<c014d2d2>] warn_slowpath_common+0x72/0xa0
[    0.028001]  [<c058b12b>] ? init_amd_k7+0x130/0x157
[    0.028001]  [<c058b12b>] ? init_amd_k7+0x130/0x157
[    0.028001]  [<c014d34b>] warn_slowpath_fmt+0x2b/0x30
[    0.028001]  [<c058b12b>] init_amd_k7+0x130/0x157
[    0.028001]  [<c058b2b2>] init_amd+0x84/0x22f
[    0.028001]  [<c058a54f>] ? generic_identify+0x131/0x178
[    0.028001]  [<c058a65a>] identify_cpu+0xc4/0x224
[    0.028001]  [<c058f452>] ? cpu_callback+0xd/0x11b
[    0.028001]  [<c058f69d>] ? relay_hotcpu_callback+0xe/0x99
[    0.028001]  [<c01d32fc>] ? writeback_set_ratelimit+0x1c/0x60
[    0.028001]  [<c0595263>] ? notifier_call_chain+0x43/0x60
[    0.028001]  [<c058a7cd>] identify_secondary_cpu+0x13/0x1f
[    0.028001]  [<c058d7f4>] smp_store_cpu_info+0x36/0x3a
[    0.028001]  [<c058d8d5>] smp_callin+0xdd/0xeb
[    0.028001]  [<c058db8c>] start_secondary+0x34/0xc6
[    0.028001] ---[ end trace 772b99519d7ae729 ]---

```
see [http://www.gossamer-threads.com/lists/linux/kernel/1208301](http://www.gossamer-threads.com/lists/linux/kernel/1208301)

---

### Post by LeDieu on 2013-03-26
Ah! Awesome matt_symes that indeed did the trick. System is booting within a couple of seconds now. That is much better haha.
Also thanks for your comment sandyd, but I don't really know what you mean. I do the following occuring a fair bit in my dmesg:
```

[    4.110303] Info fld=0x0
[    4.110307] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[    4.110316] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[    4.110328] end_request: I/O error, dev sr0, sector 0
[    4.111698] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    4.111705] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 

```
But i'm not noticing any issues. Would you mind explaining a bit more about what you're seeing in my dmesg?
Thanks heaps for you help so far guys.

---

### Post by matt_symes on 2013-03-26
Hi

Thanks for posting back and confirming that the solution works.

sr0 will be any CD/DVD ROM drives you may have configured. They are usually symlinked to /dev/dvd and /dev/cdrom.

Take a look at 

```
ls -l /dev/{sr0,cdrom,dvd}
```

As this is a VPS, i would not worry too much about it. 

If it bothers you because it clutters up the logs then disable the CD/DVD ROM by unbinding the driver, deleting the device or some such.

Out of interest, can you post the output of

```
cat /proc/cpuinfo
```

and

```
ls /sys/block
```

Kind regards

---

### Post by sandyd on 2013-03-26
> **LeDieu said:**
> Ah! Awesome matt_symes that indeed did the trick. System is booting within a couple of seconds now. That is much better haha.
Also thanks for your comment sandyd, but I don't really know what you mean. I do the following occuring a fair bit in my dmesg:
```

[    4.110303] Info fld=0x0
[    4.110307] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[    4.110316] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[    4.110328] end_request: I/O error, dev sr0, sector 0
[    4.111698] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    4.111705] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 

```
But i'm not noticing any issues. Would you mind explaining a bit more about what you're seeing in my dmesg?
Thanks heaps for you help so far guys.

The kernel oops msg can be ignored - amd_k7_smp_check() just doesnt handle your processor. It is not certified for SMP by AMD.

---

### Post by LeDieu on 2013-04-03
Again, thanks for your help guys. Problem seems to be solved, although I only rebooted once since its a production server. Although I doubt the problem will reoccur. Thanks heaps.
Related error messages don't really bother me to be honest. Glad my system is booting again under the minute haha.

Just to close the thread here is the information you requested:

"cat /proc/cpuinfo"
```

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 3
model name      : QEMU Virtual CPU version 0.14.0
stepping        : 3
cpu MHz         : 2813.122
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 4
wp              : yes
flags           : fpu de pse tsc msr pae mce cx8 apic pge cmov pat mmx fxsr sse sse2 pni popcnt hypervisor
bogomips        : 5626.24
clflush size    : 32
cache_alignment : 32
address sizes   : 36 bits physical, 32 bits virtual
power management:

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 3
model name      : QEMU Virtual CPU version 0.14.0
stepping        : 3
cpu MHz         : 2813.122
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 4
wp              : yes
flags           : fpu de pse tsc msr pae mce cx8 apic pge cmov pat mmx fxsr sse sse2 pni popcnt hypervisor
bogomips        : 5626.24
clflush size    : 32
cache_alignment : 32
address sizes   : 36 bits physical, 32 bits virtual
power management:

```

And: "ls /sys/block":
```

dm-0  loop0  loop2  loop4  loop6  ram0  ram10  ram12  ram14  ram2  ram4  ram6  ram8  sr0
dm-1  loop1  loop3  loop5  loop7  ram1  ram11  ram13  ram15  ram3  ram5  ram7  ram9  vda

```

---

