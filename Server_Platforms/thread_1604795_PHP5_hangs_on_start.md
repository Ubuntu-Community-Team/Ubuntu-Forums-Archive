---
title: "PHP5 hangs on start"
date: 2010-10-24
forum: Server Platforms
---

### Post by Manshtein on 2010-10-24
Hello Dear all!!!

I have faced a problem in installing PHP5 on my Ubuntu 10 Server.
I did apt-get php5 php5-cli to install it.

The problem is -- php command hangs on when i trying it=(((. Please help!

Here is strace fragment, may be it will help to find solution.

open("/dev/urandom", O_RDONLY)          = 3
read(3, "q\"\2229"..., 4)               = 4
close(3)                                = 0
open("/dev/urandom", O_RDONLY)          = 3
read(3, "o\237p4"..., 4)                = 4
close(3)                                = 0
open("/dev/urandom", O_RDONLY)          = 3
read(3, "\370\344\366\4"..., 4)         = 4
close(3)                                = 0
brk(0x9a7d000)                          = 0x9a7d000
time(NULL)                              = 1287940854
getcwd("/usr/local/lib"..., 4096)       = 15
time(NULL)                              = 1287940854
lstat64("/usr", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/usr/local", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/usr/local/lib", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/usr/local/lib/-", 0xbfb283e8) = -1 ENOENT (No such file or directory)
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
fstat64(0, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb8008000
read(0, **---at that place it hangs---**:(

---

### Post by Manshtein on 2010-10-24
Ohhh....

One more thing!

I have also tried to install php5.3.2 from sources -- the same thing!

It stacking on the same action looking by strace:(

---

### Post by JHSaunders on 2012-10-10
I am getting the same issue, at the same point in strace.

---

### Post by sandyd on 2012-10-10
**Necromancing - Thread Closed**
As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

Thanks!

---

