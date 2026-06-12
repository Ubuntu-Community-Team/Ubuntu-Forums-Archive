---
title: "Can viruses transfer from ubuntu to windows?"
date: 2013-06-10
forum: Security
---

### Post by 3mutts on 2013-06-10
Ok, I'm scanning a external hard drive for my family to make sure viruses don't transfer from the hard drive to thier recently fixed PC, I dual boot Windows 7 and Ubuntu 13.04 and I'm wondering if I connect this hard drive through Ubuntu without the Windows partition mounted, can the viruses on the hard drive transfer to ubuntu and then jump to the Windows partition?

---

### Post by The Cog on 2013-06-10
No. I don't think there are any hybrid windows/linux viruses around, and that's what you would need to catch a virus from the external drive and have it make ubuntu copy it to your windows installation.

However, if you use the external drive from windows after scanning, then anything the scanner missed will get back again (of course).

---

### Post by 3mutts on 2013-06-10
^ Yes, I'm basically wondering if a virus can jump partitions glad to know they can't. And yes, I'm definitely not connecting this hard drive until I know it is 100% clean.

---

### Post by kurt18947 on 2013-06-10
If I'm reading the O.P.s question correctly, here is what I think:

Windows malware files can be copied to or from an Linux partition.  The malware probably can't do anything (execute) while on a Linux partition but it can be copied.  Hence the reason that Linux antivirus looks for Windows malware moving through a mail server, for instance.  If Java and/or Flash are installed, a Java or Flash bug might execute.  If that Java or Flash bug also requires Windows services to do its dirty work and those services are not present, that bug is present but 'defanged'.  Am I mistaken in my understanding?  Wouldn't be the first time :redface:.

---

### Post by 3mutts on 2013-06-10
^ I know Windows viruses can be on a Linux system and transferred manually (ie plugging in a USB that was on a Linux system infected with a virus into a windows system) but I'm  wondering if the virus can write itself from Linux to windows automatically.

---

### Post by GrimReaperAxeKick on 2013-06-10
Your Ubuntu OS. can have Windows viruses in it which can be transferred via storage device or via transfer of information from the Ubuntu partition to the Windows partition. 

If you want to transfer data from Ubuntu to Windows, then put the data on a storage device, and scan the device with you windows anti-virus before unpacking the data, that way you will be safe.

No virus can automatically go from Ubuntu to Windows, or vice versa, as that is impossible. The only way for it to transfer is if you transfer it.

---

