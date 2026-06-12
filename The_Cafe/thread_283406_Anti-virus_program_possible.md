---
title: "Anti-virus program possible?"
date: 2006-10-24
forum: The Cafe
---

### Post by morequarky on 2006-10-24
I think this would be too cool and a real shot in the face of Microsoft.

Is it possible to make a Linux LiveCD with a good anti-virus program and use it to debug and de-virus windows?  This would be a boon for linux.  You name the virus and another OS has to come to the rescue to save windows.  How humiliating!

I would love to distribute this CD, as well as Ubuntu.

Maybe it is already possible, but I don't know about it.  Fairly new at this.

---

### Post by nocturn on 2006-10-24
> **morequarky said:**
> I think this would be too cool and a real shot in the face of Microsoft.

Is it possible to make a Linux LiveCD with a good anti-virus program and use it to debug and de-virus windows?  This would be a boon for linux.  You name the virus and another OS has to come to the rescue to save windows.  How humiliating!

I would love to distribute this CD, as well as Ubuntu.

Maybe it is already possible, but I don't know about it.  Fairly new at this.

It exists, but there's a big problem.
NTFS cannot be written reliably with the kernel module, but you need write support to clean a disk.

That's why CD's that support this use captive-ntfs but it is harder to use as it first needs to get some DLL's before being able to use it.

---

### Post by nocturn on 2006-10-24
Take a look here:
[http://ubuntuforums.org/showpost.php?p=898614&postcount=3](http://ubuntuforums.org/showpost.php?p=898614&postcount=3)

I found trinity because of that thread:
[http://trinityhome.org/](http://trinityhome.org/)

---

### Post by Sunnz on 2006-10-24
Is it possible to convert ntfs to vfat THEN clean the virus?

---

### Post by NetworkGuy on 2006-10-24
I don't think you can convert NTFS to vfat.  You can go the other way however.   

Also rememeber that virus pattern files can change every day.  You would end up having to repackage a CD every day if you want the most up-to-date cleaners.

---

### Post by Karma_Police on 2006-10-24
There are 3 Linux anti-virus live cds in the list here: [http://www.frozentech.com/content/livecd.php]("http://www.frozentech.com/content/livecd.php")

So... You just need to chose one :)

---

### Post by jdong on 2006-10-24
It's certainly possible, but there's few good virus scanners that run under Linux to clean Windows. And, with ntfs-3g, you can indeed write quite reliably to NTFS.

I know of clamav, f-prot, and sophos as commonly available Linux AV scanners with some level of merit. In addition, Lavasoft's Ad-aware runs under Wine acceptably. so, you can make a LiveCD with those three to scan and possibly repair a virus-ridden Windows box.

I'd prefer something with a Kaspersky engine though, but KAV and F-Secure for Linux are both relatively expensive for Linux.


This job is better done with a Windows-based LiveCD such as BartPE or Avast's livecd scanner.

---

### Post by DoctorMO on 2006-10-24
I thought KAV was free for the home user? you only have to pay for the email filtering for servers and all that jaz.

---

### Post by jdong on 2006-10-24
> **DoctorMO said:**
> I thought KAV was free for the home user? you only have to pay for the email filtering for servers and all that jaz.

[http://www.kaspersky.com/linux_fileserver](http://www.kaspersky.com/linux_fileserver)

Err, no... the Linux versions of Kaspersky are clearly targetted towards server use, and cost around $300/yr, not close to practical for home users.


There is no 'free' version of Kaspersky for Windows either... it's about $50/yr (IMO well worth the money for the spectacular product, but that's another discussion in itself)... though AOL's ActiveVirusShield is basically a free Kaspersky 6.

---

