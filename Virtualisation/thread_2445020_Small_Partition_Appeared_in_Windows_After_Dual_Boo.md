---
title: "Small Partition Appeared in Windows After Dual Boot Installation"
date: 2020-06-08
forum: Virtualisation
---

### Post by kirazagaci on 2020-06-08
Hi. I installed Ubuntu 20.04 on a Windows 20.04 installed system as a dual boot. I used the "Install alongside the Windows" option while installing. Everything went as expected. But, when i booted into Windows 10, i noticed that there is an extra 510 MB sized FAT32 partition which was not there before. I have never experienced this with previous Ubuntu versions. 

When i booted back to the Ubuntu, i saw that that partition is mounted as /boot/efi/ I don't know if this is relevant but I don't have UEFI in my computer.


When i was installing ubuntu, i noticed that prompt says 2 partitions are being created. In my previous experiences, promp was mentioning about only one partition. New prompt was like this: [https://linuxconfig.org/images/07-how-to-install-ubuntu-20-04-alongside-windows-10.png](https://linuxconfig.org/images/07-how-to-install-ubuntu-20-04-alongside-windows-10.png)

My question is: _Is this same for everybody or just me? Is everything normal? Did Ubuntu changed the way it handles the partitions in 20.04 ?_

---

### Post by ajgreeny on 2020-06-08
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

Your image shows what I always see when installing a Linux OS in VBox, which you didn't mention you were doing; what you have is not what we call as a dual-boot but a virtual install of Ubuntu inside Windows as a VM.

Did you install Windows-10 yourself or was it pre-installed in your computer?  If it was pre-installed the system will be UEFI without doubt.

I will probably help us diagnose better what has happened if you go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run any default repair** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

