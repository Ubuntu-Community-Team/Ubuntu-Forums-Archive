---
title: "Windows 11 - UEFI Bios"
date: 2023-10-20
forum: Ubuntu, Linux and OS Chat
---

### Post by Shibblet on 2023-10-20
I purchased a new computer.  A Minisforum HX90G (Ryzen 9 5900HX & AMD 6600M GPU)  I love this little computer...
It came pre-installed with Windows 11.  And since I added a second SSD to the computer, I decided to go ahead and Dual-Boot Kubuntu 23.04
I figured I'd keep Windows 11 on one of the SSD's, just in case there was a game or something I wanted to play...

Well, the other day, Windows 11 did an update of it's own.  Right after a reboot, it no longer booted from my Kubuntu drive... it went straight to the Windows Bootloader.
So, I went into the bios, and changed the default boot-loader back to Grub on my Kubuntu Drive.  Rebooted, and the computer went into Grub, and I booted Kubuntu from there.

Turned off the computer that night... woke up the next moring, and booted the computer... Lo and Behold the Bios had reverted back to booting to the Windows 11 Drive by default!!!

I figured I may have forgotten to save the bios before I exited... tried it again...
Same thing the next day. Lather, rinse, repeat, for the last few days.

My Computer will no longer boot from the assigned drive in BIOS, it keeps reverting to the Windows Bootloader. 

Does anyone know what causes this?  Secureboot?  TPM 2.0?  Microsoft's nefarious attempt to rule all PC's?

---

### Post by oldfred on 2023-10-20
Windows updates set Windows as first in boot order. Ubuntu/grub do that with major update to grub to set Ubuntu as first.
Ubuntu uses efibootmgr to set boot order. Post this to see boot order:
sudo efibootmgr -v

man efibootmgr
The -o parameter can be used to set boot order. But some systems, particularly HP, do nor work with efibootmgr settings & reset to Windows. But even HP will keep a setting change made in UEFI settings (not UEFI boot menu). 

Do you have latest UEFI firmware from vendor?
Since external drive, is UEFI boot set using an "ubuntu" entry in the internal drive's ESP or an ESP on external drive?
When external drives are unplugged UEFI typically removes or changes a fixed entry. UEFI boot of external drives uses /EFI/Boot/bootx64.efi or a "drive" entry, similar to how you boot live installer.

---

### Post by Shibblet on 2023-10-24
> **oldfred said:**
> Windows updates set Windows as first in boot order. Ubuntu/grub do that with major update to grub to set Ubuntu as first.
Ubuntu uses efibootmgr to set boot order. Post this to see boot order:
sudo efibootmgr -v

Thank you for that command.  It showed Windows 11 as Boot 1 and Garuda Linux as Boot 2, followed by (K)Ubuntu as Boot 3.
Thus ultimately solved the problem.  I reinstalled Kubuntu and removed the Garudua Boot option from the Windows UEFI drive.

> **oldfred said:**
> Do you have latest UEFI firmware from vendor?
Since external drive, is UEFI boot set using an "ubuntu" entry in the internal drive's ESP or an ESP on external drive?
When external drives are unplugged UEFI typically removes or changes a fixed entry. UEFI boot of external drives uses /EFI/Boot/bootx64.efi or a "drive" entry, similar to how you boot live installer.

Yep, it's the most current BIOS for the computer... but it does make me think this might have been a "refurbished" model, as SOMEONE put Gardua on it.  I don't know if the factory does this, or it ewass the reseller... but there were no indications of a previously opened package.  However, I will be contacting the manufacturer to see if this is part of their "install" process.

Thanks again!

---

### Post by zoli62 on 2023-10-24
> **Shibblet said:**
> I 

Well, the other day, Windows 11 did an update of it's own.  Right after a reboot, it no longer booted from my Kubuntu drive... it went straight to the Windows Bootloader.
So, I went into the bios, and changed the default boot-loader back to Grub on my Kubuntu Drive.  Rebooted, and the computer went into Grub, and I booted Kubuntu from there.



Does that mean you reset ubuntu's grub by going into bios or did you just select ubuntu from there and boot it? Because in such a case, when the Windows update changes the system boot order, after logging into Ubuntu, the grub-install /dev/sdX and update-grub commands must be executed in the terminal.  [https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition](https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition)

Or didn't you do it that way? A few days ago, I also upgraded to the latest edition of Windows 10 on a laptop where, in addition to Windows, three other Linux distributions are installed. (MX Linux, Kubuntum and EndeavorOS). booting is done by EndeavorOS grub. I ran into a very similar problem to you. After the Windows 10 feature update, there was only grub rescue. I don't know how to set the boot order in the BIOS of my Lenovo laptop, as you wrote, if it is possible at all. On the other hand, after turning on the machine, I started the temporary startup menu with the appropriate key and tried that the updated Windows starts. Since I was able to log in to Windows, I started Kubuntu at the next reboot because I didn't know EndeavorOS. After logging in, I issued the above commands. I even modified the Kubuntu grub.cfg entries for the EndeavorOS kernel, because update-grub causes os-prober to run (which I don't have disabled), and it arbitrarily modifies these kernel entries in question. Then I restarted the machine and I was able to start EndeavorOS from Kubuntu's grub. Logged in and restored the EndeavorOS grub.
That is why it is recommended to create a separate EFI partition for each installed operating system in case of multiboot to avoid startup errors after Windows updates.
By the way, in my case, I also saw videos on restoring grub in grub rescue afterwards. I didn't try these, but it seemed that the grub restore was much faster.

---

### Post by Shibblet on 2023-10-25
> **zoli62 said:**
> Does that mean you reset ubuntu's grub by going into bios or did you just select ubuntu from there and boot it? Because in such a case, when the Windows update changes the system boot order, after logging into Ubuntu, the grub-install /dev/sdX and update-grub commands must be executed in the terminal.  [https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition](https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition)

Or didn't you do it that way? A few days ago, I also upgraded to the latest edition of Windows 10 on a laptop where, in addition to Windows, three other Linux distributions are installed. (MX Linux, Kubuntum and EndeavorOS). booting is done by EndeavorOS grub. I ran into a very similar problem to you. After the Windows 10 feature update, there was only grub rescue. I don't know how to set the boot order in the BIOS of my Lenovo laptop, as you wrote, if it is possible at all. On the other hand, after turning on the machine, I started the temporary startup menu with the appropriate key and tried that the updated Windows starts. Since I was able to log in to Windows, I started Kubuntu at the next reboot because I didn't know EndeavorOS. After logging in, I issued the above commands. I even modified the Kubuntu grub.cfg entries for the EndeavorOS kernel, because update-grub causes os-prober to run (which I don't have disabled), and it arbitrarily modifies these kernel entries in question. Then I restarted the machine and I was able to start EndeavorOS from Kubuntu's grub. Logged in and restored the EndeavorOS grub.
That is why it is recommended to create a separate EFI partition for each installed operating system in case of multiboot to avoid startup errors after Windows updates.
By the way, in my case, I also saw videos on restoring grub in grub rescue afterwards. I didn't try these, but it seemed that the grub restore was much faster.

When I did the installation, I make a separate partition for /boot/efi, about 512MB.  This way, GRUB can be installed on that partition, and I don't have to worry about it affecting Windows.  This computer has two 1TB SSD's installed.  Windows 11 on one, and Kubuntu on the other.

In this case, I received the computer, which had Windows 11 pre-installed.  I installed Kubuntu (like I stated above), and then switched my UEFI Bios to boot from the Kubuntu drive.

After I switched off the computer, the UEFI Bios would "revert" to booting from the Windows 11 drive, and not the Kubuntu one.

I ran the command "sudo efibootmgr -v" it came back with Windows 11 being "Boot 1," Garuda as "Boot 2", and "Ubuntu" as Boot 3.

Since I just got the computer, and have never used Garuda, I can only assume someone else installed it on this PC at some point, and it left some remnant of itself in the Windows Bootloader.  I also assume that the Samsung SSD I had purchased at the same time (New), was blank.  The new Samsung SSD is the drive I installed Kubuntu on.

How I resolved this, was to install Kubuntu on it's own drive, and then "re-install" the UEFI partition of the Windows Drive by restoring a recovery partition on the initial SSD.

Now I can select my boot drive from BIOS, and it stays that way after power cycling.

---

