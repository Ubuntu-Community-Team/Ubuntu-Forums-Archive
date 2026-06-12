---
title: "Security with VM Player"
date: 2012-12-13
forum: Security
---

### Post by Bizzy1 on 2012-12-13
Hi

I am playing around with Ubuntu for the first time as a more secure platform for development and maintenance of my websites.

I have set up Ubuntu as a virtual machine within VM Player running on Windows XP. I'm a bit nervous about setting up dual-boot on my PC and I figure that the VM Player will get me into Ubuntu quicker than shutdown then reboot.

Getting to the point : would the virtual machine within Windows be as secure as Ubuntu on full dual boot ? Opinions much appreciated.

---

### Post by CharlesA on 2012-12-13
Yes. The OS doesn't really know it is running on a VM, so it will be a good way to learn how to secure the machine properly.

---

### Post by Bizzy1 on 2012-12-13
Am I correct in assuming that it should be nearly impossible for any malware, viruses etc which might infect the Windows host to infect the Ubuntu guest ? I have a shared folder for file transfer. Would that impact security ?

---

### Post by CharlesA on 2012-12-13
Should be fine, but keep in mind anything that could corrupt data could affect the VM's virtual hard drive as it is just stored in a file on the host's hard drive.

---

### Post by Bizzy1 on 2012-12-14
So with regular backups it would be reasonably secure ?

---

### Post by CharlesA on 2012-12-14
Yeah. Anyone not doing backups, does not care about their data.

---

