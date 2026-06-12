---
title: "BSOD after installing Ubuntu"
date: 2016-10-16
forum: Windows
---

### Post by centipede2 on 2016-10-16
**TL;DR Trying to install windows from scratch, but when booting from USB I get [this BSOD]("http://i.imgur.com/NY3viNW.jpg") telling me to use the recovery tools. The problem is that the recovery tools are part of the install process that the BSOD is blocking... Someone else has had the same problem a few years ago [here]("http://answers.microsoft.com/en-us/windows/forum/windows_8-update/windows-8-boot-issue-error-0xc000000f/2d34ca16-9ed5-40cf-88d7-08207cdf4e16").**


Background: A series of events happened, explained quickest thusly: built new rig a few weeks ago with win7 > install ubuntu alongside > upgrade this morning to win10 > delete ubuntu partition in win10 disk manager > need to delete grub with a few steps > boot from win10 usb > repair > bootrec fixmbr, bootrec fixboot, bootrec buildbcd > grub rescue > live boot ubuntu > boot repair > grub rescue, but its even worse because now I get the BSOD described above and I can't install win10 at all! > reinstall ubuntu > grub doesn't see win10 > boot ubuntu > update > reboot ubuntu > reboot > grub sees win10 (it's on sda1) > now I'm here.


I'm considering doing win10's built in "Reset This PC" function, but I don't know if that's totally equivalent to how wiping an SSD and reinstalling an OS re-does the partition tables and everything.


OK, so where do I go from here, with the goal of installing win10 on a blank SSD?


System:


MOBO: gigabyte h170n-wifi


STORAGE: samsung 850 evo 500gb

---

### Post by Bucky Ball on 2016-10-16
*Thread moved to **Windows**.*

> OK, so where do I go from here, with the goal of installing win10 on a blank SSD?

Here to start with. Good luck.

---

### Post by centipede2 on 2016-10-16
Wait...please re-read. The problem occured after installing Ubuntu. It was all originally a Grub problem, but there were two problems in total: grub, and then the post-Ubuntu install BSOD. My post even shows that other people have had this problem after installing Ubuntu; Ubuntu changes something.

---

### Post by Bucky Ball on 2016-10-16
Ubuntu is booting fine, now you can't install Windows and want support installing Windows? You say you want help to install Windows on a blank SSD? Unsure what that has to do with Ubuntu. :-k

---

### Post by centipede2 on 2016-10-16
> **Bucky Ball said:**
> Ubuntu is booting fine, now you can't install Windows and want support installing Windows? You say you want help to install Windows on a blank SSD? Unsure what that has to do with Ubuntu. :-k

Thank you for your "help" but time is running out for my situation and I'm not just posting this anywhere mindlessly. I'm sorry if I didn't make it clear in the OP.

Accessing recovery tools via a win10 install USB was not a problem in the past. Nor do I need help installing windows, I can do that myself. The problem is that Ubuntu has changed something with the partition tables that is preventing windows install media from functioning. You'll notice that half of the problem originated with getting stuck in Grub rescue and was possibly solidified by Boot Repair within Ubuntu. Further, other people have this problem after installing Ubuntu.

From start to finish it's totally a primarily-Ubuntu-related issue. Please allow this post where I originally posted it, where it will get visibility by people who know Ubuntu! (I don't care about windows people in this situation, I don't believe they'll be helpful.)

---

### Post by cariboo on 2016-10-17
Unfortunately, you are going about this in the wrong order, you'll probably have to start all over again. Windows needs to be installed first on a bare hard drive, as it needs to have a couple of partitions at the start of the hard drive. A 100MiB boot partition, and the Efi partion, I'm not sure about the EFI partition, but better safe than sorry. your Ubuntu install is probably preventing Windows from creating the partitions it needs.

---

### Post by 7dEfOk4AgU on 2016-10-17
The quickest resolution for this would be to bite the bullet and start again by cleaning your drives and reinstalling Windows 10. You may have to create a install media on another machine using the media creation tool available at microsoft.com. Your Win 10 licence should be ok as this this associated with your MS account. After reinstalling Windows you can install Ubuntu, this is the right order for dual boot installs.

---

### Post by centipede2 on 2016-10-17
> **mikeb42 said:**
> The quickest resolution for this would be to bite the bullet and start again by cleaning your drives and reinstalling Windows 10. You may have to create a install media on another machine using the media creation tool available at microsoft.com. Your Win 10 licence should be ok as this this associated with your MS account. After reinstalling Windows you can install Ubuntu, this is the right order for dual boot installs.

That's the problem, though. Install media doesn't boot, because of the BSOD. If you try to boot a win10 install USB, you get that BSOD.

---

### Post by 7dEfOk4AgU on 2016-10-17
Do you have secure boot activated in the UEFI?

---

### Post by centipede2 on 2016-10-17
> **mikeb42 said:**
> Do you have secure boot activated in the UEFI?

No.

---

### Post by ajgreeny on 2016-10-17
Assuming you can still boot to Ubuntu can you show us the output of ```
sudo parted -l
``` in terminal please, which will tell us what partitions are on disk at present and may give us more clues to your problems.

However the suggestions by cariboo and mikeb42 will probably be the fastest way to get your dual boot working as you want it.

---

### Post by 7dEfOk4AgU on 2016-10-17
Try reactivating secure boot in the UEFI.

---

