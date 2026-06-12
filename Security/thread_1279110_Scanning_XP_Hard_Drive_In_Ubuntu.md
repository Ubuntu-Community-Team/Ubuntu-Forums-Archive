---
title: "Scanning XP Hard Drive In Ubuntu"
date: 2009-09-30
forum: Security
---

### Post by madprofessor on 2009-09-30
I have an interesting issue. I have a dock for SATA hard drives. I have a Windows hard drive that has spyware on it. I am trying to dock the hard drive to my Ubuntu machine and scan it for viruses and spyware. Trend Micro House Call has an online scanner that works with Windows, Mac and Linux, but the question is how do I do the spyware scan?

---

### Post by mikewhatever on 2009-09-30
I suspect most online scanners rely on some activx or another, which implies using internet explorer. Can you explain what's problem exactly. Can you see the Windows partition from Ubuntu? Can you launch the scan from Firefox/Ubuntu?

---

### Post by cariboo on 2009-09-30
I would suggest intalling [Malwarebytes]("http://www.malwarebytes.org/") on your Windows computer and using that. There aren't really any Linux apps that scan for malware.

---

### Post by madprofessor on 2009-09-30
Actually Trend Micro doesn't use ActiveX it uses Java. And with Gparted and ntfsprogs, Ubuntu can recognize and open the ntfs partition on the other drive. The thing I'm trying to figure out is what program online or offline can do the same thing as Trend Micro where you can select a partition or folder, even in Linux and scan it for viruses, but to do it for spyware.

---

