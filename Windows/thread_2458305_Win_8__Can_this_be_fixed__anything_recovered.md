---
title: "Win 8:  Can this be fixed / anything recovered?"
date: 2021-02-21
forum: Windows
---

### Post by mattoau on 2021-02-21
Hi,

Hope this is in the right place.

I've got an HP laptop running Windows 8 that refuses to boot. BIOS checks suggest a failed HDD. I've run a bootable Ubuntu distro, and Drive and Gparted can see the disk but it is unmountable, and SMART check shows up a failed drive.

However, Gparted shows the disk having 6 partitions and only 3 of those have warnings (although the one with the data I want has a warning). Is anyone able to confirm if this is a terminal failure, or if there are options can suggest to me the next route to take.

Having trouble physically removing it at the moment, so haven't been able to see if it will run externally. No need to try further if it is terminal.

Thanks in advance.

[[IMG]https://imagizer.imageshack.com/v2/xq90/924/uq7KTD.png[/IMG]]("https://imageshack.com/i/pouq7KTDp")

---

### Post by QIII on 2021-02-21
My best guess is that the partitions were not completely dismounted the last time you shut down.  Linux will not touch a Windows partition that has not been properly unmounted because Windows will throw a fit if the contents of a directory have changed since shutdown, suspend or hibernation.

I would suggest as your first and easiest step a stop a Windows forum to see if they can they can help you with that bit.  We're happy to help, but if you can get Win 8 (and I would suggest a supported OS, by the way) working I think the road ahead would be easier.

That doesn't mean someone else won't be along in this thread to help, however.

Moved to Windows.

---

### Post by grahammechanical on 2021-02-21
Those three partitions (sda2; sda3; sda4) are not showing any part of them as being Used. I suggest that you need Windows tools to work on this drive & operating system. You need advice from a Microsoft/Windows 8 forum.

Linux/Ubuntu tools might have difficulty in accessing this drive if Windows 8 was suspended or hibernated instead of being shutdown. This might explain the impossibility of mounting the drive in the Ubuntu live session.

It seems from this Microsoft help page that you start from a working Windows 8 and create a Windows 8 recovery USB drive from the recovery partition on that drive. Which you do not have.

[https://support.microsoft.com/en-us/windows/create-a-usb-recovery-drive-460091d5-1e8f-cb33-2d17-8fdef77412d5](https://support.microsoft.com/en-us/windows/create-a-usb-recovery-drive-460091d5-1e8f-cb33-2d17-8fdef77412d5)



Regards

---

### Post by dragonfly41 on 2021-02-21
If you have Gparted a long shot is to first try the top menu > Device > Attempt Data Rescue.

---

### Post by deadflowr on 2021-02-21
I would guess that fast startup was enabled when they failed.
As far as I know that needs to be disabled in order to mount elsewhere.
(I have no idea how you disable fast startup outside of Windows)

---

### Post by QIII on 2021-02-21
I think that before we suggest possibly risky data recovery methods, we allow the user to consult with Windows experts to see if there is anything to be done in the native OS first.

---

### Post by oldfred on 2021-02-21
No software can fix a failed drive.
But you are showing partitions?

The error on sda3, System reserved is normal. That is required to be unformatted & gparted does not like unformatted partitions.
The error on sda4 could be normal as Windows default is fast start up which sets hibernation flag. Then Linux NTFS driver cannot mount it.
Only if you boot Windows & clear fast start up will it be shown correctly, if no other errors that require chkdsk from Windows.

You may just need repairs on the ESP - efi system partition, your sda2.
You can run chkdsk on it by mounting with your Windows repair/recovery flash drive.

Or you may be able to run dosfsck from Linux. 
Must be unmounted
sudo dosfsck -t -a -w /dev/sda2
The -a seems to help in clearing dirty bit

---

### Post by Impavidus on 2021-02-22
If you have trouble removing the hard drive, you could at least use Ubuntu to clone it to a healthy external hard drive, using ddrescue. But you still need Windows tools to recover files.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by mattoau on 2021-02-23
Many thanks to you all for all of the useful tips and advice, I have lots of options to investigate. Thanks also for the good manners, I half expected a "just google it" or try the forum search function kind of response, but all of you took the time to consider and respond to my problem.

:D

---

