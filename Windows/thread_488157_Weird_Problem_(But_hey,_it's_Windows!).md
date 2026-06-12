---
title: "Weird Problem (But hey, it's Windows!)"
date: 2007-06-29
forum: Windows
---

### Post by teddybairs1 on 2007-06-29
Ok, I've been trying to troubleshoot a laptop (an HP running Windows XP) for a friend of my wife's. Initially when I received it, it would only boot into Safe Mode. I ran a few LiveCds on it (PCLinuxOS2007, Ubuntu Feisty, and Slax KillBill) to verify that the hardware wasn't the issue. It wasn't.

The error message it was giving on Normal Boot had to do with the Windows Kernel. I looked it up on the Microsoft website, and this is what it said:


Stop 0x00000077
KERNEL_STACK_INPAGE_ERROR
This article describes how to troubleshoot these error messages.

Back to the top
CAUSE
This issue can occur if a requested page of kernel data could not be read from the paging file into memory, or the master boot record is infected with a virus. To further determine the possible cause, you must properly interpret the error message. If both the first and third parameters are zero, then the four parameters are defined as:
1.	0 (zero)
2.	Page Table Entry (PTE) value at time of error
3.	0 (zero)
4.	Address of signature on kernel stack
If either the first or the third parameter is not a zero, then the following definitions apply:
1.	Status code
2.	I/O status code
3.	Page file number
4.	Offset into page file
If this is the case, the cause of this issue may be determined from the second parameter (the I/O status code) by using the following information that is listed in a "value of second parameter" followed by "general cause" format:

0xC000000E, or STATUS_NO_SUCH_DEVICE: the drive went unavailable, possibly a bad hard drive, disk array, and/or controller card.


I went in and started disabling any drivers which weren't being used in Safe Mode in the Device Manager. I narrowed it down to the Secondary IDE Channel. I also left the floppy controller disabled. The laptop booted normally after that. However, the CDROM (cd-rw/dvd-rom combo) isn't recognized now. We tried to re-enable the cdrom, and the computer now has the same boot problem which it did before.

I know it's not the hardware because the cd burner ran fine under the Slax livecd "nocd" mode.

Is there anyway to really fix this without a "trash, burn, and reinstall" option?

---

### Post by smoker on 2007-06-30
hi, you could try a system file check, 'scannow /sfc' from the command prompt, have a look here: [http://www.updatexp.com/scannow-sfc.html](http://www.updatexp.com/scannow-sfc.html)

if that does not work, you could try a 'windows repair' with the xp cd, a repair install will not format or delete data, programmes, etc.

bear in mind system files, drivers, etc, can be corrupted by a virus, so worth doing some virus checks.

i would also, as a matter of course, do a ram check, you can do this from the ubuntu live cd, or else download and make a bootable version of 'memtest86',

best of luck

---

### Post by teddybairs1 on 2007-06-30
I've already run the virus check, and spyware, and rootkit, with the AVG free tools. I also did a system restore back to about a month or more before the problem surfaced.

---

