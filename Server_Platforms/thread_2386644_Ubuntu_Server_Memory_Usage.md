---
title: "Ubuntu Server Memory Usage"
date: 2018-03-08
forum: Server Platforms
---

### Post by SilvaNights on 2018-03-08
Hiya All,

I have 2 virtual Ubuntu 16.04 server's with the same memory allocation to them (512mb), however one of them shows much less memory available.

I have double checked the settings on each one from the virtual side and they are identical.
I have even deleted the server and created a new one pointing at the old virtual disk and still the issue is there, so I think it is something within the OS.

Here is free -m from the server in question:
 ```
             total        used        free      shared  buff/cache   available
Mem:            360         188          20           1         151         137
Swap:          1023         262         761
```

uname -r:
4.4.0-116-generic

And from an identical server (at least on the virtual side):
 ```
             total        used        free      shared  buff/cache   available
Mem:            488          59         274           0         154         155
Swap:          1995          18        1977
```

uname -r:
4.4.0-71-generic

Im stuck on idea's for this one (I know kernel is different but I dont think thats it?)

thx,

tom,

---

### Post by slickymaster on 2018-03-08
*Thread moved to **Server Platforms**.*

---

### Post by Doug S on 2018-03-08
Have a look at what memory your kernels are reserving  and freeing during boot. Example (edited):

```
$ [COLOR="#FF0000"]dmesg  | grep -i 'Memory:'[/COLOR]
...[snip]...
[    0.000000] Memory: 15807824K/16472972K available (12300K kernel code, 2715K rwdata, 4208K rodata, 2336K init, 2432K bss, 665148K reserved, 0K cma-reserved)
[    0.010080] Freeing SMP alternatives memory: 36K
[    0.970513] Freeing initrd memory: 48484K
[    4.038355] Freeing unused kernel memory: 2336K
[    4.084521] Freeing unused kernel memory: 2008K
[    4.111108] Freeing unused kernel memory: 1936K

```
Now, observe via "free":
```
$ [COLOR="#FF0000"]free -k[/COLOR]
              total        used        free      shared  buff/cache   available
Mem:       15862624      103036    15426524        9380      333064    15410080
Swap:      16472060           0    16472060

```and observe that 15862624 = 15807824 + 36 + 48484 + 2336 + 2008 + 1936

---

### Post by TheFu on 2018-03-08
I'd compare the running processes.  A different kernel will probably have different drivers, and systemd will behave differently.

Comparing startup might be useful too - **systemd-analyze blame**

To get a list of installed packages - **dpkg --get-selections**

How did you validate that the VM configs were identical? I know with libvirt we can compare the XML VM definition files.

---

### Post by SilvaNights on 2018-03-09
> **slickymaster said:**
> *Thread moved to **Server Platforms**.*

Oops! Sorry!

---

### Post by SilvaNights on 2018-03-09
> **Doug S said:**
> Have a look at what memory your kernels are reserving  and freeing during boot. Example (edited):

```
$ [COLOR=#FF0000]dmesg  | grep -i 'Memory:'[/COLOR]
...[snip]...
[    0.000000] Memory: 15807824K/16472972K available (12300K kernel code, 2715K rwdata, 4208K rodata, 2336K init, 2432K bss, 665148K reserved, 0K cma-reserved)
[    0.010080] Freeing SMP alternatives memory: 36K
[    0.970513] Freeing initrd memory: 48484K
[    4.038355] Freeing unused kernel memory: 2336K
[    4.084521] Freeing unused kernel memory: 2008K
[    4.111108] Freeing unused kernel memory: 1936K

```
Now, observe via "free":
```
$ [COLOR=#FF0000]free -k[/COLOR]
              total        used        free      shared  buff/cache   available
Mem:       15862624      103036    15426524        9380      333064    15410080
Swap:      16472060           0    16472060

```and observe that 15862624 = 15807824 + 36 + 48484 + 2336 + 2008 + 1936

Many thanks for your reply.
Copied the commands you did, but when I add them up on the "bad" server they don't seem to be equivalent to 512mb of memory?

Bad server:
```
dmesg  | grep -i 'Memory:'
Memory: 328132K/523832K available (8530K kernel code, 1309K rwdata, 3992K rodata, 1508K init, 1316K bss, 195700K reserved, 0K cma-reserved)
[    0.004000] Freeing SMP alternatives memory: 32K
[    2.197945] Freeing initrd memory: 37248K
[    2.436214] Freeing unused kernel memory: 1508K
[    2.439591] Freeing unused kernel memory: 1700K
[    2.441630] Freeing unused kernel memory: 104K
```

```
free -k
              total        used        free      shared  buff/cache   available
Mem:         368724      174200       15896        1184      178628      160248
Swap:       1048572      329580      718992
```

Whats weird is that the "good" server that has equal virtual settings gives a different output format to the above commands (I think they are memory addresses, I assume this is because it is a different kernel?)
Good server:
```
dmesg  | grep -i 'Memory:'
Memory: 461996K/523832K available (8452K kernel code, 1293K rwdata, 3976K rodata, 1484K init, 1316K bss, 61836K reserved, 0K cma-reserved)
[    0.585631] Freeing SMP alternatives memory: 32K (ffffffff820b8000 - ffffffff820c0000)
[    3.249593] Freeing initrd memory: 34636K (ffff88001d1cd000 - ffff88001f3a0000)
[    3.293839]  memory: hash matches
[    3.444115] Freeing unused kernel memory: 1484K (ffffffff81f45000 - ffffffff820b8000)
[    3.454482] Freeing unused kernel memory: 1776K (ffff880001844000 - ffff880001a00000)
[    3.455653] Freeing unused kernel memory: 120K (ffff880001de2000 - ffff880001e00000)
```

```
free -k
              total        used        free      shared  buff/cache   available
Mem:         500044       71344      192736        2044      235964      401232
Swap:       2043900           0     2043900
```

---

### Post by Doug S on 2018-03-09
> **SilvaNights said:**
> Copied the commands you did, but when I add them up on the "bad" server they don't seem to be equivalent to 512mb of memory?
They aren't supposed to. They are only supposed to add up to show the difference between how much the kernel says is available during boot verses what you see with "free".

Your biggest difference is here:
```

Memory: 328132K/523832K available (8530K kernel code, 1309K rwdata, 3992K rodata, 1508K init, 1316K bss, [COLOR="#FF0000"]195700K[/COLOR] reserved, 0K cma-reserved)
Memory: 461996K/523832K available (8452K kernel code, 1293K rwdata, 3976K rodata, 1484K init, 1316K bss, [COLOR="#FF0000"]61836K [/COLOR]reserved, 0K cma-reserved)

```
> **SilvaNights said:**
> Whats weird is that the "good" server that has equal virtual settings gives a different output format to the above commands (I think they are memory addresses, I assume this is because it is a different kernel?)Yes, mostly.

---

### Post by SilvaNights on 2018-03-13
> **TheFu said:**
> I'd compare the running processes.  A different kernel will probably have different drivers, and systemd will behave differently.

Comparing startup might be useful too - **systemd-analyze blame**

To get a list of installed packages - **dpkg --get-selections**

How did you validate that the VM configs were identical? I know with libvirt we can compare the XML VM definition files.

Thanks for your reply. I ran those commands, the output was quite large but I couldnt see anything obvious that would be causing this issue (can post on here if needed though).

I only validated them by manually checking the virtual settings, I have checked and rechecked many times though. :)

---

### Post by SilvaNights on 2018-03-13
> **Doug S said:**
> They aren't supposed to. They are only supposed to add up to show the difference between how much the kernel says is available during boot verses what you see with "free".

Your biggest difference is here:
```

Memory: 328132K/523832K available (8530K kernel code, 1309K rwdata, 3992K rodata, 1508K init, 1316K bss, [COLOR=#FF0000]195700K[/COLOR] reserved, 0K cma-reserved)
Memory: 461996K/523832K available (8452K kernel code, 1293K rwdata, 3976K rodata, 1484K init, 1316K bss, [COLOR=#FF0000]61836K [/COLOR]reserved, 0K cma-reserved)

```
Yes, mostly.

Thanks, is it possible to change how much memory is being reserved?

---

