---
title: "This is why I love Ubuntu"
date: 2005-04-10
forum: The Cafe
---

### Post by vnbuddy2002 on 2005-04-10
[PHP]top - 04:23:02 up  9:06,  2 users,  load average: 0.00, 0.00, 0.00
Tasks:  81 total,   2 running,  79 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0% us,  0.0% sy,  0.0% ni, 100.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    775524k total,   603708k used,   171816k free,    38960k buffers
Swap:  1020116k total,     3484k used,  1016632k free,   417880k cached[/PHP]


After all the needed tweaking, here is the performance of my system. As you see, the distro handling my laptop "efficiently".

I had install to copies of Ubuntu on two different machines in my room: 1 Desktop and 1 Laptop. Others are still under windows but will soon going to the same direction.

The report on the top is from my old Laptop Toshiba M35 S359

Intel Centrino 1.2ghz
785 SDRAM
60 Gig

:) Long live ubuntu

---

### Post by localzuk on 2005-04-10
[QUOTE=vnbuddy2002][PHP]top - 04:23:02 up  9:06,  2 users,  load average: 0.00, 0.00, 0.00
Tasks:  81 total,   2 running,  79 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0% us,  0.0% sy,  0.0% ni, 100.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    775524k total,   603708k used,   171816k free,    38960k buffers
Swap:  1020116k total,     3484k used,  1016632k free,   417880k cached[/PHP]


After all the needed tweaking, here is the performance of my system. As you see, the distro handling my laptop "efficiently".

I had install to copies of Ubuntu on two different machines in my room: 1 Desktop and 1 Laptop. Others are still under windows but will soon going to the same direction.

The report on the top is from my old Laptop Toshiba M35 S359

Intel Centrino 1.2ghz
785 SDRAM
60 Gig

:) Long live ubuntu[/QUOTE]
 How'd you manage to get 0.00 for all cpu? Do you have no running tasks? Such as gnome-netstatus?

The 'top' command would make a small footprint in that so how did you manage it?

---

### Post by paul cooke on 2005-04-10
[QUOTE=localzuk]How'd you manage to get 0.00 for all cpu? Do you have no running tasks? Such as gnome-netstatus?

The 'top' command would make a small footprint in that so how did you manage it?[/QUOTE]

either he's edited his top output... or else he's got an extremely fast cpu...


what I want to see is his bogomips figure...

```
paulc@big-box:~ $ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 3
model name      : AMD Athlon(tm) Processor
stepping        : 1
cpu MHz         : 857.791
cache size      : 64 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr pni syscall mmxext 3dnowext 3dnow
bogomips        : 1699.84
``` 

and my top output :

```
paulc@big-box:~ $ top
top - 13:51:54 up 3 days, 17:00,  1 user,  load average: 0.84, 0.68, 0.37
Tasks:  96 total,   1 running,  95 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.6% us,  2.7% sy,  2.0% ni, 83.5% id,  1.0% wa,  0.2% hi,  1.0% si
Mem:    516480k total,   512164k used,     4316k free,    26520k buffers
Swap:   512020k total,    47984k used,   464036k free,   215240k cached
```

ps, azureus is currently running, seeding two ubuntu live cd torrents... :) and two instances of gkrellm, plus loads of other stuff.

---

### Post by vnbuddy2002 on 2005-04-10
nautilus is not running. just a plain desktop. :) BTW, what is the point to edit the headers? 

I am running:

XFCE
No daemons

---

