---
title: "Needing Windows Drivers for Win10"
date: 2023-11-10
forum: Windows
---

### Post by lwalper on 2023-11-10
I've got a strange situation going on. I've got a HP laptop 17-cn1003ca with an 11th Gen i5-1155G7 processor; AMI BIOS which reads the drive as an Intel SSDPEKNU512GZH  (the label on the drive matches the BIOS information). When I got the computer it came with Windows 11 installed. I've never really fallen in love with that version of the OS so I used Gparted, deleted the partition and installed Ubuntu on a clean drive. I'd like to reinstall Windows 10 on the computer, but when I run the install media the USB stick boots into the Win OS installation and proceeds  normally until there is a need to begin installing to the SSD. Then I'm presented with a window telling me that there is no bootable media installed and I need to install a driver. I've gone to Intel and gotten a driver installation file, but it's a .exe file and at that point in the installation there is no way to run an executable file. Documentation accompanying the .exe tells me (with included instructions) that I can extract the .exe file into a folder that will contain the needed .inf driver files. NO JOY.

Ubuntu installs to the SSD drive with no problems and Gparted reads (and does all the other stuff it does) without a hitch. Have I maybe deleted a boot partition from the SSD that Windows is looking for?--and if I have, how do I fix it?

---

### Post by yancek on 2023-11-11
To start, I would suggest that you boot into Ubuntu and run the following command and look for an EFI partition (Lower case letter L in the command):

```
sudo parted -l
```

Also in the parted output it should show "Partition Table: gpt".   It should also show an EFI partition, does it show both.  I would expect you would need to put the .exe file on the USB somewhere, did you do that?  Does it have instructions on how to do that?   It seems curious that you got a message no bootable media installed if you are booting from the media (a USB drive).

Your problem is actually unrelated to Ubuntu/Linux and you might try posting the problem at a windows forum.

---

### Post by lwalper on 2023-11-11
Thanks for that. Yeah I know it's a Windows thing, but there are pretty smart people over here and since I'd been using Ubuntu and Gparted thought it might have been related to that.

Here's the output for that command -

```
Model: INTEL SSDPEKNU512GZH (nvme)Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  538MB  537MB  fat32        EFI System Partition  boot, esp
 2      538MB   512GB  512GB  ext4



```

---

### Post by tea for one on 2023-11-11
I assume that you want to dual boot?
You will need free space on /dev/nvme0n1.
Boot into a "Try Ubuntu" session and use gparted to shrink nvme0n1p2.
The Windows installation USB should then see the free space.

---

### Post by oldfred on 2023-11-11
Moved to Windows sub-forum since only Windows issues.
May really need to ask on Windows forum.

Windows cannot see ext4 partition and will not auto shrink it, you have to make unallocated space.
Since system is newer Windows 10 may not even have drivers for it.

Make sure you have good backups.

I have similar generation Dell laptop. After it came back from motherboard replacement, my Kubuntu install worked just find, but Windows 11 did not. I tried just about every repair option, nothing worked. Even tried reinstalling Windows 11 using Windows latest ISO. File structure of Windows looked correct. Not sure if then some issue with Windows product key stored in UEFI and install. Dell may not have correctly updated product key. My only fix was to download a Dell recovery drive. While it worked it restored system to as purchased. Totally erased my Kubuntu install and all the Windows software apps I had added.

Your product key in UEFI is probably only valid for Windows 11.
[https://support.microsoft.com/en-us/windows/find-your-windows-product-key-aaa2bf69-7b2b-9f13-f581-a806abf0a886](https://support.microsoft.com/en-us/windows/find-your-windows-product-key-aaa2bf69-7b2b-9f13-f581-a806abf0a886)

---

### Post by lwalper on 2023-11-12
I just tried the "free space" thing with same "Install driver" prompt; drive not recognized. I've also tried installing Windows 11 with the same result. Machine boots fine from the USB stick, but Win install hangs at the "need driver" screen.

---

### Post by rectec794613 on 2024-01-08
I don't know if you're still having this problem, but I have an idea. I just ran into the same kind of issue trying to reinstall Windows 11 on my laptop that also has a newer Intel processor (12th gen i3). I saw [this video]("https://www.youtube.com/watch?v=HuCY0ChsqAM") and tried getting Intel Rapid Storage Technology (IRST) drivers for it but they didn't work. What did work was the other solution, which is to disable Intel Volume Management Device or VMD. Try going into your BIOS, look for the Intel VMD setting and then disable it. For me it was in the Main tab of the BIOS and I had to press CTRL+S to show hidden settings.

---

