---
title: "What if I have Linux and Windows?"
date: 2008-02-10
forum: Server Platforms
---

### Post by newbie2 on 2008-02-10
> We decided to test this situation in the lab, using an internal hard disk with two partitions and LILO (or Grub) as boot loader. If your MBR is infected by Mebroot while in Windows (the threat will not run within Linux), the computer will still be able to boot up normally into both operating systems. While Linux is totally unaffected by this threat, and will work as normal, Windows XP will continue to run the rootkit when it finishes booting up. This was something expected, since the threat stores a backup copy of the old MBR to boot up correctly. However, this fact raises an interesting consideration: if the MBR is the weakest point in the chain, [it could eventually be possible to create the first multi-platform malware targeting both the Windows and Linux kernels during the boot process]("http://www.symantec.com/enterprise/security_response/weblog/2008/02/the_flow_of_mbr_rootkit_trojan.html").
:rolleyes:

---

### Post by solar george on 2008-02-10
At which point having windows installed could become a security vulnerability for linux.

---

