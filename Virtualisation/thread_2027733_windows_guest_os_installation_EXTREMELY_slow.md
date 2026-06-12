---
title: "windows guest os installation EXTREMELY slow"
date: 2012-07-16
forum: Virtualisation
---

### Post by 13east on 2012-07-16
I've successfully installed and ran VirtualBox with winxp and win7 on kubuntu 10.04x64.

But everytime I try to install either winxp or win7 in kubuntu 11.10 or 12.04 in either x32 or x64, the software always hangs at the formating the virtual drive (i don't even get as far as getting to installation process).  The longest i've let the process go in is with winxp: after three hours the process gets as far as formating the drive (ntfs-quick format) and 50% of copying the files.

I still have a seperate partition with kubuntu 10.04x64 running on my computer because i can't get virtualization running on other OSes.  I've completely quit Windows and only use it for the occasonal software that requries it (i.e. TurboTax), so i'd rather not have to dedicate an entire partion back for windows.

Any help anyone can provide would be very much appreciated.

---

### Post by Dedoimedo on 2012-07-17
What settings do you use for storage?
What controller are you using (e.g. sata) and what type (e.g. ahci)?
Dedoimedo

---

### Post by 13east on 2012-07-17
> **Dedoimedo said:**
> What settings do you use for storage?
What controller are you using (e.g. sata) and what type (e.g. ahci)?
Dedoimedo

I haven't changed any settings within storage: IDE controller, PIIX4 type, and "use host i/o cache" checked.

---

### Post by Dedoimedo on 2012-07-18
Can you try first:
Disable io cache see if it makes a difference
Change type to other available options, see if it makes a difference.
One by one!
Dedoimedo

---

