---
title: "Resume cracked by Tor usders"
date: 2015-03-06
forum: Security
---

### Post by kayve on 2015-03-06
I just sat down today to update my resume that was composed using Libra office, and to my horror, none of my resume files were properly viewable.  I noticed 4 suspicious files in the directory 

[http://paste.ubuntu.com/10552727/](http://paste.ubuntu.com/10552727/)


upon some investigation, I found them associated with a Tor website.  

[http://www.kayve.net/cracked.png](http://www.kayve.net/cracked.png)

[http://kayve.net/tor_ubuntu_files.png](http://kayve.net/tor_ubuntu_files.png)

How do I diagnose this attack and restore my resume file?  The file is on an external drive, Seagate... I have unplugged that disk and brought it to a school mac  at the Teachers College of San Joaquin 

[http://teacherscollegesj.edu/content.aspx?ID=1318&title=About%20Us](http://teacherscollegesj.edu/content.aspx?ID=1318&title=About%20Us)

How do I diagnose whether the attack occurred there or into my Ubuntu?

---

### Post by QIII on 2015-03-06
Are other .txt and .doc files similarly affected.

---

### Post by unspawn on 2015-03-06
> **kayve said:**
> How do I diagnose whether the attack occurred there or into my Ubuntu? It's CryptoWall ([http://www.bleepingcomputer.com/virus-removal/cryptowall-ransomware-information](http://www.bleepingcomputer.com/virus-removal/cryptowall-ransomware-information)) which only runs on the Other OS, not Linux.

---

### Post by QIII on 2015-03-06
Yes, but ...

If your machine is connected to a network when cryptowall is searching for files to encrypt and you have no incoming rules in iptables ...

Anyway, the attack occurred when you were on a server running Windows or one to which a dirty Windows machine was connected.

By the way, stop using the machine and read up on Photorec.  You may be able to recover the unencrypted files that were deleted.  But the more you use the machine, the more likely it becomes that you will overwrite the areas of the disk where those files are.

---

### Post by kayve on 2015-03-08
OK.. here is the deal as I see it now:

I have multiboot with a terrible Windows 8 that I have neglected with the anti virus.  It is almost undoubtably the culprit because all my data is on an external drive that I let Windoze use and also unplug to bring to school and use it on Mac.  Now I want to do some repartitioning wipe things.. I think I will create a partition on my internal hard drive to save that data and wipe the external drive and start over with that.  Any recommendations for the safe way to do this?

also I have another external drive that I haven't been able to read.  Are there recommendations on diagnosing that chuck of smoking metal?

---

### Post by PondPuppy on 2015-03-10
On the drive that you can't read, I've had good success with TestDisk. My condolences on the Windows contamination. I too have Windows a dual-boot on one of my machines, and I rarely allow it to access the Internet anymore.

---

