---
title: "Do I need to run ClamAV in both OS's?"
date: 2010-10-23
forum: Security
---

### Post by vernoti on 2010-10-23
Hello

I currently have Ubuntu 10.10 installed and am going to be installing Windows 7 via VirtualBox. If I'm sharing folders between both OS's do I need to install ClamAV on Ubuntu and Windows to protect Windows? Obviously viruses aren't going to effect Linux like they do Windows but I'm assuming a file downloaded via Linux could certainly effect my Windows install. Am I correct? Is there a better way of dealing with this type of situation?

I hope it makes sense as to what I'm asking.

Thanks

---

### Post by wacky_sung on 2010-10-23
Technically the answer is yes to install both clamav in both OS.You installed clamav in Ubuntu is to prevent any damage migrated to your window issue.The best choice is sololy just using Ubuntu which solved you days of nightmares.

---

### Post by mainerror on 2010-10-24
> **vernoti said:**
> Hello

I currently have Ubuntu 10.10 installed and am going to be installing Windows 7 via VirtualBox. If I'm sharing folders between both OS's do I need to install ClamAV on Ubuntu and Windows to protect Windows? Obviously viruses aren't going to effect Linux like they do Windows but I'm assuming a file downloaded via Linux could certainly effect my Windows install. Am I correct? Is there a better way of dealing with this type of situation?

I hope it makes sense as to what I'm asking.

Thanks

If you run Windows 7 in VirtualBox there is actually no need to install ClamAV on both systems however an anti-virus program is not dab to have on Windows 7 too.

---

### Post by alan2796 on 2010-10-25
I was going to ask something along these lines too...I have a dual boot system and wondering if mounting and scanning my windows partition with clam AV is as affective as running Norton or AVG on windows, id rather not slow windows down with antivirus software if possible. ?

---

### Post by Chayak on 2010-10-25
ClamAV will only catch what it has signatures for.  There's a lot of malware that's polymorphic now and will change each time it's run to defeat that type of protection.  ClamAV on the host doesn't hurt but consider something with behavioral based detection like Norton's Sonar or Kaspersky on the windows VM.  I would lean towards Norton because it's a lot less resource intensive than Kaspersky

---

### Post by uRock on 2010-10-25
Install [Windows Security Essentials]("http://www.microsoft.com/security_essentials/") in Windows and you will be good to go. It is what I use and it has not given me any problems.

---

### Post by cariboo on 2010-10-25
+1 for Windows Security essentials, I just did a test last week, using several different av products, in every case Security Essentials found things that the others didn't.

---

### Post by Chayak on 2010-10-25
> **uRock said:**
> Install [Windows Security Essentials]("http://www.microsoft.com/security_essentials/") in Windows and you will be good to go. It is what I use and it has not given me any problems.

+1  That's another really good solution that I forgot to mention.

---

