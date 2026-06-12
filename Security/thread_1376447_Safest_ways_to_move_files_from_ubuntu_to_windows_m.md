---
title: "Safest ways to move files from ubuntu to windows machine"
date: 2010-01-09
forum: Security
---

### Post by dogdo on 2010-01-09
Hi 

If i download files from the internet to the ubuntu home download folder will that kill off windows viruses? Ive also have avast on demand scanner-but are anti-viruses effective against windows viruses these days?

---

### Post by CharlesA on 2010-01-09
Most (if not all) virus scanners for linux will scan for Windows viruses.

---

### Post by dogdo on 2010-01-09
But what happens if i download windows viruses while using ubuntu-do the infections simply remain dormant or are they killed off?

---

### Post by CharlesA on 2010-01-09
Windows viruses won't run on Linux. You'd have to run an anti-virus to remove them.

---

### Post by Flyers2391 on 2010-01-09
> **dogdo said:**
> But what happens if i download windows viruses while using ubuntu-do the infections simply remain dormant or are they killed off?

If the file is infected, simply downloading it in Ubuntu will not clean the file.  Repositories are the safest way to go, if it is something that isn't available in one, you are taking a risk (small or not).  I don't know of a 100% safe way to download a suspect file

---

### Post by adam814 on 2010-01-09
It won't infect your Ubuntu install just by downloading it, but you'll probably want to at least scan it with ClamAV before transferring to Windows and with a good Windows AV software and anti-malware prior to actually running it.

---

### Post by __p1n__ on 2010-01-09
Resident malware is a core aspect of the Windows experience.  Don't accidentally deprive yourself of that fun by scanning/cleaning files before they reach their destination.

With respect to physically moving them to an NTFS partition if it's on the same physical node just mount the partition and copy the files over.

edit: if you absolutely insist on scanning the files I've found the elfsh utility (part of the eresi installation) to be very good for manually analysing executables. Ollydbg is another good utility however it only supports 32-bit executables and can only run within a windows environment.

---

