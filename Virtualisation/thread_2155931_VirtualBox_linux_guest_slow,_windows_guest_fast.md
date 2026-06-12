---
title: "VirtualBox linux guest slow, windows guest fast"
date: 2013-06-20
forum: Virtualisation
---

### Post by WhiteHatGuy on 2013-06-20
Hi

I have Lubuntu 13.04 installed on my computer, everything runs fine. I have plenty of ram and proccesor. Its a fast machine. So I install VirtualBox latest version.

The problem:

1) My windows guest virtual machines. And also live windows cd's run fine and smooth. As long is a windows OS. Speed its ok and normal.

2) My linux guest virtual machines. And also live linux cd's run extremely slow. As long is a linux OS. Speed its terrible and very slow.

I've been dealing with this problem for years. And I havent been able to figure it out.

Also, when I use VMware this does not happend, and both windows guest OS and linux guest OS, run fine and speed its ok and normal.

So obviously the problem has something to do with Virtual Box.




Thanks.

---

### Post by Toz on 2013-06-20
I find that I have to "Enable IO APIC" (in the System settings) to get my Linux vms to run as fast as the Windows vms. Don't know why and I don't remember having to ever do this prior to 13.04.

---

