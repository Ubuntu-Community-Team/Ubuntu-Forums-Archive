---
title: "How to move VMs in group?"
date: 2017-05-07
forum: Virtualisation
---

### Post by satimis on 2017-05-07
Hi all,

Host - Ubuntu 16.04
VirtualBox
C-drive 1TB SSD
VMs - Ubuntu desktop/Windows

I have 41 VMs installed.  I'm prepared to install a new 2TB SSD on this box and move all existing VMs to its VirtualBox.  Then the C-drive will be wiped out for another use.

Is there an easy way moving all VMs in group?

A breif googling found following links:-
1)
VirtualBox: how to move a vm to another disk
[https://robertoschiabel.wordpress.com/2013/04/21/virtualbox-move-vm-to-another-disk/](https://robertoschiabel.wordpress.com/2013/04/21/virtualbox-move-vm-to-another-disk/)

2)
How to move VirtualBox VMs from one drive to another
[http://www.techrepublic.com/article/how-to-move-virtualbox-vms-from-one-drive-to-another/](http://www.techrepublic.com/article/how-to-move-virtualbox-vms-from-one-drive-to-another/)

Are they relevant?

Thanks

Regards
satimis

---

### Post by TheFu on 2017-05-08
If you clone the 1T disk completely to the 2T disk, then you don't need to deal with VMs separately.

If you just want to move the VM image files/backend storage, then use vboxmanage. Google has 20+ good answers for how to do this. You can export each VM into an ovf, then import each. I prefer to go to the original source for how-to information. [https://www.virtualbox.org/manual/ch01.html#ovf](https://www.virtualbox.org/manual/ch01.html#ovf)

I would clone the disk using ddrescue.

---

### Post by satimis on 2017-05-08
> **TheFu said:**
> If you clone the 1T disk completely to the 2T disk, then you don't need to deal with VMs separately.

If you just want to move the VM image files/backend storage, then use vboxmanage. Google has 20+ good answers for how to do this. You can export each VM into an ovf, then import each. I prefer to go to the original source for how-to information. [https://www.virtualbox.org/manual/ch01.html#ovf](https://www.virtualbox.org/manual/ch01.html#ovf)

I would clone the disk using ddrescue.
Hi,

Thanks for your advice.

My headache is the running VirtualBox having problem.  Please see #6 and #7 of following posting;
[https://ubuntuforums.org/showthread.php?t=2360720&p=13642727#post13642727](https://ubuntuforums.org/showthread.php?t=2360720&p=13642727#post13642727)

I must install a fresh VirtualBox on the new SSD and move the VMs to it.

Regards
satimis

---

### Post by TheFu on 2017-05-08
i provided 2 options.

Did you click the link provided?  Import/Export of VMs is the answer.

---

### Post by satimis on 2017-05-08
> **TheFu said:**
> i provided 2 options.

Did you click the link provided?  Import/Export of VMs is the answer.
If I understand your suggestion correctly.

1.  Install a new VirtualBox on the new SSD
2.  Export VMs, one by one, and Import them one by one to the new VirtualBox.  I did it several years ago.

I have a spare box also running VirtualBox.  I'll test Import/Export several VMs via internal network, the router, to check.

Thanks

Regards
satimis

---

