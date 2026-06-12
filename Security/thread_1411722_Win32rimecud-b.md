---
title: "Win32:rimecud-b"
date: 2010-02-20
forum: Security
---

### Post by Richiegs on 2010-02-20
I am using Ubuntu 9.10 .  I run Virus Scanner daily, but it detects no virus. Nevertheless, When I went to Open DNS, it told me that my computer was infected with malware. I immediately installed Avast and scanned my computer again. It found a virus - Win32:rimecud-b!
I then tried to send the virus to the virus chest, but it didn't work.

1. Is there any other way to remove this virus?
2. I assume this is a virus from Windows. Will this virus still work on Ubuntu 9.10?
3. Why can't I remove this virus? Is it because it is too powerful to be deleted?
4. Since Virus Scanner finds no virus, I guess Virus Scanner is not as good as Avast. Is there any other anti-virus for Ubuntu which is better than Avast?
5. How do I find out if this virus already did something bad or stole personal information from me?

Many thanks

---

### Post by cariboo on 2010-02-20
Notice that the name of the virus is **Win**32:rimecud-b. That means it is a Windows virus, it will not run unless you run it in Wine. Just delete the file and relax, you have nothing to worry about.

---

### Post by Richiegs on 2010-02-21
> **cariboo907 said:**
> Notice that the name of the virus is **Win**32:rimecud-b. That means it is a Windows virus, it will not run unless you run it in Wine. Just delete the file and relax, you have nothing to worry about.

Thanks
 Avast and Virus Scanner don't seem to work well to detect viruses.  Is there any good anti-virus software for Ubuntu 9.10? I tried to download Bitdefender, but it didn't have the Debian version.

---

### Post by cariboo on 2010-02-21
Unless you are running a file/mail server, there really is no need to run a Windows virus scanner on a Linux variant. There aren't any native linux viruses in the wild, and the only virus scanner that claims to scan for Linux viruses is clamav.

---

