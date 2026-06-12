---
title: "Linux_reader.exe and Trojan"
date: 2008-03-14
forum: Security Discussions
---

### Post by oscarmeyer51 on 2008-03-14
I have a dual boot system (Ubuntu 7.10 and Windows XP) and rarely use my laptop running XP. I had a need to boot into XP last night and noticed that AVG Free was running excessively long. When I checked the Virus Vault of AVG, I found that it reported Linux_Reader.exe as being infected with a Trojan (Downloader.ZLOB.MCI). As Linux_Reader.exe allows access to my Linux partitions (xfs..), it concerned me considerablly. Especially since with Linux_Reader.exe installed, I can update data on my Linux partitions.

This may be an isolated case, but I felt it was worthy of a post. 

btw, I downloaded the Linux_Reader.exe program in July of last year, which should give you an indication of how often I am in XP. Unfortunately, I do not recall the site I pulled it down from, so I cannot identify the source.

Does anyone else have this or seen it before?  FYI, I am in the process of cleaning off the possible infections under XP via a tool for ZLob/Smitfraud removal as AVG only seems to identify the infection and is unable to remove it.

---

### Post by LifeInfusion on 2008-03-16
I also had Linux Reader but I never had a virus from it. Did you download from a mirror or directly from DiskInternals (which is now bought by Microsoft)?

---

### Post by oscarmeyer51 on 2008-03-31
I cannot even recall where I got the program from. Pretty sure I got it from the primary web site (not secondary or mirror), but would not guarantee that. Regardless, that issue has been resolved and cleaned and all is well now.

Thanks for the reply.

---

### Post by brian_p on 2008-04-02
> **oscarmeyer51 said:**
> I have a dual boot system (Ubuntu 7.10 and Windows XP) and rarely use my laptop running XP. I had a need to boot into XP last night and noticed that AVG Free was running excessively long. When I checked the Virus Vault of AVG, I found that it reported Linux_Reader.exe as being infected with a Trojan (Downloader.ZLOB.MCI). As Linux_Reader.exe allows access to my Linux partitions (xfs..), it concerned me considerablly. Especially since with Linux_Reader.exe installed, I can update data on my Linux partitions..

The authors of Linux_Reader.exe claim it only reads ext2/ext3 file systems. If you trust that you have no worries. If you don't you should consider not using it.

---

### Post by netlogic on 2008-04-03
no worries!
It is how XP manages your device drivers. Your anti-virus is catching it with the heuristic mode. It isn't catching it by the database mode. Your virus vendor just haven't  heard the app or the developer was too busy to report it to the virus vendor. It is catching it by monitoring your memory protection. These things happen. Commercial windows vendors treat open source and freeware developers for windows like dirt. i guess that is why so many of them are developing for linux now. if you are going to lose money, why not get some respect for it.

---

