---
title: "How to Install/Boot from MS Windows Recovery Partition?"
date: 2010-06-04
forum: Virtualisation
---

### Post by zappal on 2010-06-04
Hi ya'll, I've searched around but I can't find an answer to this.

I'm running Ubuntu Lucid Lynx
VirtualBox is installed

I have a recovery partition with Microsoft Windows that I would like to install/boot from.
All I can see in VirtualBox settings is to attach a .vdi file or CD from.
So, I'm assuming I have to create a .vdi from the partition, then boot from that. :confused: if so, how?

I'm not sure about this at all.

Any guidance or advice would be appreciated.

---

### Post by zappal on 2010-06-05
Actually, I would like to point out that in this case.
It's not an actual recovery partition.
It's a partition just holding the installation of Windows.
This partition was created by the company sys admin long ago.

I understand that actual recovery partitions might not be possible because it has to detect its original hardware state.

---

### Post by zappal on 2010-06-05
I think I'm close.
I dd it
then i convert it to vdi with the VBoxManage command
but when i try to boot from my vdi
It says:
Disk error
Press any key to restart
:(
then my CPU processor usage goes up and stays at 100% until I close the window

---

