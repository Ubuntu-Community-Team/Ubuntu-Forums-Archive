---
title: "&quot;NTLDR is missing&quot;"
date: 2014-12-23
forum: Windows
---

### Post by gelubotezan on 2014-12-23
I read what I was able to find before asking but didn't help in this stage;
I've got an old asus(2006) running windows7. I don't usually work under windows so,  I decided to simply change the hard disk with another one that has a dual boot  xubuntu12.04/ windows 7 , intending to work under 12.04. This hard disk was running before on another computer, got some issues with windows but the 12.04 partition was still working an year ago. Now I get that "NTLDR is missing" message. I suppose the windows is broken but why Grub does not show me the OS choices as it did on the older computer?
How could I convince the 12.04 to start without reinstalling as I do have data (on both systems) I would like to keep.

Eager to use the above  computer  I tried another HD, this one has only a 12.04 instalation (previously had a windows but was formatted  when installing the 12.04)
I get the same "NTLDR is missing " issue.  
Is this from my HDs or does it come from the computer itself? Sorry not to know this. As I read  there must be the HDs but need some confirming in order to search further.
Thanks for any help

---

### Post by Mark Phelps on 2014-12-23
> Now I get that "NTLDR is missing" message.

Problem is that NTLDR is not used in Windows 7; it was retired prior to Vista.

---

### Post by gelubotezan on 2014-12-23
Thanks  Mark, good hint, that means, I should have some older remainings from vista or XP under windows7?  No idea what was there before, being my wive's computer. Over that the windows 7 was instaled. 
Still, on the old computer I used to get a OS choice dialogue from grub, what I don't get anymore on the new machine with the same HD. So I supposed its the machine.

---

### Post by oldfred on 2014-12-23
That also could be any NTFS partition, particularly those created by gparted as they have the NTLDR setting in the NTFS partition boot sector. 
And you must then have a Windows boot loader in the MBR, That Windows boot loader jumps to NTFS partition with boot flag, and does not find NTLDR.

A few motherboards, primarily Intel, may have similar error from BIOS. And that is because no partition has boot flag. Grub does not use boot flag and will boot any system without one. But if BIOS has to see one, then we add a boot flag on a primary partition, just to make BIOS happy.

---

### Post by gelubotezan on 2014-12-24
The board is  Asus P5LD2VM/S  from 2006(first generation) with a celeron processor. The Chipset is Intel 945G
OLDFRED; When you say "But if BIOS has to see one, then we add a boot flag on a primary partition, just to make BIOS happy"  is this me the one that should add a flag on a primary partition?

Edit; Ok, got that, I did flagged with Gparted but still same answer. I'll check with another machine if the HDs are booting.

---

### Post by oldfred on 2014-12-24
Did you reinstall grub to MBR?

If you did and still get errors:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by gelubotezan on 2014-12-25
Oldfred, thanks for all infos, I will carefully study the matter.   
I tryed two live LINUX  CDs I have, with CD-ROM boot first. None of them will boot so, I rather think its a BIOS matter. 
The same CDs boot on a HP machine (Intel Xeon 2.8GHZ) from 2004

---

### Post by oldfred on 2014-12-25
It was about 2006 that vendors updated BIOS to boot from USB. Can you boot from a USB flash drive?

---

