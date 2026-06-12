---
title: "ibm system x2350m4 with &quot;fakeraid&quot; serveraid c100"
date: 2015-04-14
forum: Server Platforms
---

### Post by maksymov on 2015-04-14
Can't install ubuntu 14.04 server on this machine (x3250m4) with raid1 - **unable to install grub in dummy**
serveraid c100 [docs]("http://public.dhe.ibm.com/systems/support/system_x_pdf/serveraid_swr_ug_v3_42214.pdf").[URL="http://public.dhe.ibm.com/systems/support/system_x_pdf/serveraid_swr_ug_v3_42214.pdf"]
[/URL]any ideas?

---

### Post by darkod on 2015-04-14
1. Have you considered using mdadm software raid instead of the built-in raid?

2. I believe it is common grub install to fail on fakeraid. If it failed only on that, last step, you can try booting the machine in live mode with the desktop cd and try installing grub manually. The server os should be there, only the bootloader is missing.

---

### Post by maksymov on 2015-04-14
I tried to use mdadm soft, but i got same error. can't install grub efi. 
I can install grub outside raid, but what I will do when hd with boot partition break?

---

### Post by darkod on 2015-04-14
EFI grub is newer and I still don't have much experience with it. If you set your motherboard to use legacy boot instead of uefi, mdadm + legacy grub should work fine.
You can also try using efi grub but I don't know many details about it. What I do remember reading is that you need a small efi partition as first partition on the disks. The efi bootloader uses it. Probably you didn't have this partition so it failed with the error it gave you.
Grub install to the fakeraid might have been related to using uefi boot too. In my opinion there is no real advantage for uefi when using linux. For windows it's more complicated because it needs uefi if you use gpt tables and on the other hand you need gpt for large disks. In ubuntu the combination gpt + legacy boot works just fine. I have my home server like that. So you don't need to bring uefi boot into play at all.

---

### Post by maksymov on 2015-04-14
ok, is it possible to install grub2 into /boot inside lvm (vg-boot)? or I must keep /boot outside lvm partition?

---

### Post by darkod on 2015-04-14
With the recent versions of ubuntu the boot files can be inside LVM now. No need to have separate /boot partition outside the LVM as earlier.

However, you don't need to create separate LV for boot, you can leave the files/folder as part of the root LV. As you wish...

But to be precise, grub2 will not go "into" the boot partition/folder. Those are the boot files. Grub2 will still need to be on the Master Boot Record of the HDDs, or the fakeraid (if you use it).

---

### Post by maksymov on 2015-04-15
thank you very much for your answers! 
in the future I want to set up a fully encrypted system, so I need a separate partition for /boot. 
If I configure fakeraid in the bios, then during the system installing I have only one partition, the Master Boot Record is not available. Don't know what the problem is, but on fakeraid ubuntu can't be installed even in automatic mode - error installing the bootloader. I want to try to install the bootloader on the usb stick and the rest on the encrypted fakeraid. I think it would be better and safer.

---

### Post by darkod on 2015-04-15
Not exactly true. With fakeraid active you have one DEVICE not one PARTITION. The fakeraid device takes the role of a disk, so it will have a small MBR on it (the first sectors, same like on any hdd). But you do create partitions on this device so you can use them, same like on a hdd.
When installing grub be sure to specify the device as a target, not the partition on it.
I don't know if automatic install of grub should work especially if you are using uefi boot. Did you try with legacy boot?
The problem also might be the fakeraid, but in that case you should be able to add grub later in live mode. Again don't forget to install it onto the fakeraid device, not a partition.
Also don't forget the efi partition if you are using uefi boot.

---

