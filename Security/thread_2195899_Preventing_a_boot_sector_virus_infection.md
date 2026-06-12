---
title: "Preventing a boot sector virus infection"
date: 2013-12-27
forum: Security
---

### Post by jsvidyad on 2013-12-27
Hello,

   My question is about boot sector viruses. Since they infect the boot sector and are loaded from the boot sector before the operating system gets loaded, they can affect all operating systems, right? This would make linux also vulnerable to boot sector viruses. What can we do to prevent this? If I make the internal hard drive the only bootable device in the BIOS and then password protect the BIOS so that the settings cannot be changed, will that protect me from boot sector virus infected media left inadvertently in the computer during shutdown or boot up? By media I mean things like DVDs, USB flash drives, floppy discs etc. Can linux get a boot sector virus infection from just regular internet web browsing? I know that windows is vulnerable to such boot sector virus infections from just browsing the internet. Is linux vulnerable too?

---

### Post by Hungry Man on 2013-12-27
SecureBoot / TrustedBoot are pretty much the defacto methods for preventing bootkits.

---

### Post by jsvidyad on 2013-12-27
As far as I can make out, those two are for newer computers running microsoft windows. Mine is an older laptop and I plan to install ubuntu 12.04 on it. Can someone please respond to my original post?

---

### Post by CitadelUniversal on 2013-12-27
Maybe this will help - [http://en.wikipedia.org/wiki/Boot_sector#Boot_sector_viruses](http://en.wikipedia.org/wiki/Boot_sector#Boot_sector_viruses)  - & - it looks like someone over at the Linux Mint forums have asked the same question here [http://forums.linuxmint.com/viewtopic.php?f=90&t=51320&sid=f0bdd1eb30ec915f39ce3a7d8e7ad7fd](http://forums.linuxmint.com/viewtopic.php?f=90&t=51320&sid=f0bdd1eb30ec915f39ce3a7d8e7ad7fd)  & was marked as [solved].

---

### Post by jsvidyad on 2014-01-01
Hello,

    My BIOS does not have the option to prevent writing to the boot sector as mentioned in that wikipedia article. The linux mint forum article also does not answer my original post. 

Can someone please answer the questions I raised in the first post in this thread?

---

### Post by CharlesA on 2014-01-01
If you don't have the option of secure boot, you are pretty much out of luck.

With that being said, I have never seen a boot sector virus in all my time of working in IT. Regular ones, sure, but nothing that went after the boot sector itself.

---

### Post by jsvidyad on 2014-01-01
If I make the internal hard drive the only bootable device in the BIOS and then password protect the BIOS so that the settings cannot be changed, will that protect me from boot sector virus infected media left inadvertently in the computer during shutdown or boot up? By media I mean things like DVDs, USB flash drives, floppy discs etc.

---

### Post by CharlesA on 2014-01-01
> **jsvidyad said:**
> If I make the internal hard drive the only bootable device in the BIOS and then password protect the BIOS so that the settings cannot be changed, will that protect me from boot sector virus infected media left inadvertently in the computer during shutdown or boot up? By media I mean things like DVDs, USB flash drives, floppy discs etc.

Yes. Unless someone resets the BIOS and changes the boot order, of course.

Physical access > all.

---

### Post by cariboo on 2014-01-01
Stop using floppy disks. :-P

---

### Post by bashiergui on 2014-01-02
> **cariboo907 said:**
> Stop using floppy disks. :-PYou mean I shouldn't use this as my sole backup anymore? :(

---

