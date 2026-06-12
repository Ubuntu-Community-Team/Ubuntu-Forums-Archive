---
title: "How to migrate WinXP virtual machine after disk crash"
date: 2011-07-09
forum: Virtualisation
---

### Post by manybodycpa on 2011-07-09
Dear all,

After suffering a disk crash which made the disk unbootable, I was able
to save the whole /home directory. The system was Ubuntu 10.04, and the most crucial issue for the new installation is that the user was using WinXP via Virtualbox. 

As I will be installing Ubuntu Lucid on a new disk soon, I was wondering if I can transfer the virtual machine to the new disk using only the contents of /home - I cannot run the old system anymore. I did make a snapshot of the WinXP machine using Virtualbox, which I also saved.

The installation of WinXP also had various important programs running,
which would be a lot of trouble to reinstall (license servers etc).

Any help (or pointers to websites) is greatly appreciated.

Best wishes,

Martin

---

### Post by bowens44 on 2011-07-09
I'm not sure that IO follow completely, but I believe that if you had windows installed in virtualbox and you have the associated .vdi file, all you have to do is copy this to the appropriate directory in the new installation and tell virtualbox to use it.

---

### Post by manybodycpa on 2011-07-17
Hi!

It turned out that virtualbox is very generous in this respect. I installed
Ubuntu on a fresh hard disk, including a much more recent version of virtualbox (4.0 instead of 1.9). I simply copied the .virtualbox directory
from the backup, and voila, the Windows virtual machine was there!

Best,

Martin

---

