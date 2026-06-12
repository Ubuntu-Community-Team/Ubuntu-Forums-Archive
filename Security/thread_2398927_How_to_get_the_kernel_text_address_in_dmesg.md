---
title: "How to get the kernel text address in dmesg"
date: 2018-08-19
forum: Security
---

### Post by dafran on 2018-08-19
[COLOR=#242729][FONT=Arial][CENTER][FONT=inherit]
[/FONT][/CENTER]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][FONT=inherit]I am trying to do some CVE experiments and the CVE-2017-7308 poc needs to get the kernel text address according to the "Freeing SMP" string in dmesg
[/FONT]
[FONT=inherit]I loaded the vulnerable kernel which is v4.8.0-41-generic but when I run the poc it didn't work and implied that it couldn't find the string in dmesg.
[/FONT]
[FONT=inherit]I searched the internet and find that "Freeing SMP" should appear in the dmesg. Can somebody please tell me why it doesn't appear in my dmesg.
[/FONT]
[FONT=inherit]Is it relative to the pr_debug() or should I enable any funcitonality else?[/FONT]

[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2018-08-19
will this help:
```
journalctl -k > kernel.txt
```
mine shows:
```
<snip>
Aug 19 06:24:56 me-pc kernel: Freeing SMP alternatives memory: 28K
Aug 19 06:24:56 me-pc kernel: TSC deadline timer enabled
Aug 19 06:24:56 me-pc kernel: smpboot: CPU0: Intel(R) Core(TM) i5-6400 CPU @ 2.70GHz (family: 0x6, model: 0x5e, stepping: 0x3
)<snip>
```

---

### Post by dafran on 2018-08-19
I tried this command but it only showed the "Freeing unused ..." messages. 
```

Aug 19 10:27:50 kernel: Freeing unused kernel memory: 2368K
Aug 19 10:27:50 kernel: Write protecting the kernel read-only data: 18432k
Aug 19 10:27:50 kernel: Freeing unused kernel memory: 2024K
Aug 19 10:27:50 kernel: Freeing unused kernel memory: 88K

```
But the CVE-2017-7308 requires the following message:
```

[SIZE=2][ 0.000000] Memory: 2003288K/2059928K available (6352K kernel code, 607K rwdata, 2640K rodata, 880K init, 908K bss, 56640K reserved, 1146920K highmem)[/SIZE]
[SIZE=2][ 0.000000] virtual kernel memory layout:[/SIZE]
[SIZE=2][ 0.004291] Initializing cgroup subsys memory[/SIZE]
[SIZE=2][ 0.004609] Freeing SMP alternatives memory: 28K (c1a3e000 - c1a45000)[/SIZE]
[SIZE=2][ 0.899622] Freeing initrd memory: 23616K (f51d0000 - f68e0000)[/SIZE]
[SIZE=2][ 0.899813] Scanning for low memory corruption every 60 seconds[/SIZE]
[SIZE=2][ 0.946323] agpgart-intel 0000:00:00.0: detected 32768K stolen memory[/SIZE]

```


Then you can get the kernel text address according to the string behind "Freeing SMP".

---

