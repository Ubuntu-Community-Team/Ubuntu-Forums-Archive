---
title: "Cannot find windows in BIOS after trying to dual booting"
date: 2024-09-06
forum: Windows
---

### Post by adarshkr2902 on 2024-09-06
I tried dual booting my PC with windows 11 and Ubuntu 22 but now i cannot see my windows boot manager in my BIOS. I am using ubuntu on a pendrive right now . I did a diagnostic using boot-repair and here is the link for the report:
[https://paste.ubuntu.com/p/nxrVz76NRs/](https://paste.ubuntu.com/p/nxrVz76NRs/)

Can someone help me with this ?

Thanks

---

### Post by oldfred on 2024-09-06
It looks like you have an almost empty NVMe drive? It only shows an ESP - efi system partition.
It looks like your Windows & Ubuntu installs are on sdb. And sda is your flash drive.
If you unplug flash drive, then sdb becomes sda on reboot. So keep track of which drive is which.

It looks like you have Windows fast startup, bitlocker or hibernation on. Or it needs chkdsk.
And/or you have drive in "RAID" mode. Most systems need drive setting in UEFI changed from "FakeRAID" to AHCI. But you then have to install AHCI drivers into Windows.
Check UEFI settings.

Do you  have latest firmware for UEFI and NVMe drive?
Compare to vendors support site
sudo dmidecode -s bios-version
udisksctl status

You have UEFI boot files in nvme0n1p1 but no UEFI boot entry.
You have several ubuntu entries in UEFI, 

Looks like Windows was installed to HDD, but UEFI boot entry was added to ESP on NVMe drive.
Windows may install boot on default drive, when installing to different drive. You should set default in UEFI first to be same drive.
Most users want systems on fast drive or your NVMe drive and use HDD for data or backup.

From Linux you often can add a new UEFI boot entry for Windows if all the files are in the ESP and Windows has no other errors. Otherwise you have to use your Windows repair/recovery, backup or install disk to repair Windows.

sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" -d /dev/nvme0n1 -p 1

I might see if above entry allows boot of Windows before changing from RAID to AHCI. If it boots then you can add AHCI driver & change UEFI settings.
Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571) & 
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems) & 
But if you do a safe boot first to update Windows, then boot to UEFI/BIOS and change to AHCI and finally boot normally, it works
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500) & 

[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347) & 
[https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/)

---

