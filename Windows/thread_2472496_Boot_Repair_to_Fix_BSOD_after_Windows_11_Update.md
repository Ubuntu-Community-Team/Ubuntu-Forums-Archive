---
title: "Boot Repair to Fix BSOD after Windows 11 Update"
date: 2022-02-28
forum: Windows
---

### Post by matatigre36 on 2022-02-28
Hello all,

I bought a new, open-box gaming PC with Windows 10 preinstalled. I immediately upgraded to Windows 11, and the computer worked fine for about three weeks. Unfortunately, when I updated Windows on Feb. 15, 2022, I got the Blue Screen of Death upon Restart. I tried rolling back the updates through BIOS but it didn't work. It just kept kicking out of the uninstall about 5% into the process (and undoing the changes that it was trying to make).

So, after a couple of weeks of puttsing around using my kids' computer, I decided to try an Ubuntu boot drive to try and fix the Windows problem. Good news is that the problem computer boots Ubuntu from a flash drive just fine, and now I'm tempted to just do a full Ubuntu install and say sayonara to Windows 11.

BUT... it's been a loooong time since I've used Linux (about 11 years) and I'd rather not take that kind of a plunge just yet. So, I'm here to ask if you more knowledgeable Boot Repair users think that it can fix my Windows boot issue. Here's the bin file for your consideration:

[URL="https://paste.ubuntu.com/p/CSHTWjGchp/"]https://paste.ubuntu.com/p/CSHTWjGchp/
[/URL]
I really don't know very well what I'm doing. Thanks, in advance, for the help!

Andrew

---

### Post by oldfred on 2022-02-28
Moved to Windows sub-forum since not Ubuntu issue.

Boot-Repair is for Linux issues. It primary updates or offers to reinstall grub boot loader.
Report is good for seeing issues. But it cannot fix Windows issues.
To fix Windows you need your Windows repair flash drive or the Windows installer with its repair console.

You show UEFI install of Windows, but have a BIOS boot loader in gpt's protective MBR.
If system is correctly set for UEFI boot, not BIOS/CSM/Legacy boot then old Windows boot loader in MBR will never be used. It is often more dangerous to delete the code in MBR with dd and just ignoring it as it never should be used.
But be sure to always boot in UEFI boot mode.

Is system encrypted? Partitions were shown, but could not be parsed at all to see files in ESP or in NTFS partitions.

---

