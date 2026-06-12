---
title: "Blue Screen trying to boot from a real HDD using Virtualbox"
date: 2011-06-01
forum: Virtualisation
---

### Post by ddr3XD on 2011-06-01
I'm trying to use Virtualbox to boot off of a real HDD that has Windows 7 installed on it. I followed some tuts and got it to boot off the HDD but it blue screens while at the loading screen.
I've actually googled and search these forums and got alot of results but still cant figure out y it blue screens. Please if anyone can give me any help on this i would greatly appreciate it.

PS: My Ubuntu is also installed on the same HDD.

---

### Post by MartyBuntu on 2011-06-01
1, Did you install Windows 7 as a virtual machine on this drive? Is that how it was installed? Through Virtualbox?
2. Is the drive mounted when you start Virtualbox?

---

### Post by ddr3XD on 2011-06-01
> **MartyBuntu said:**
> 1, Did you install Windows 7 as a virtual machine on this drive? Is that how it was installed? Through Virtualbox?
No, It was not installed through Virtualbox, it was installed the normal way, now im trying to boot off of the drive that Windows 7 is installed on.

> **MartyBuntu said:**
> 
2. Is the drive mounted when you start Virtualbox?

The partition that Windows 7 is installed on isn't mounted but the partition that my Ubuntu is installed on is mounted. Both partitions are on the same drive.

---

### Post by MartyBuntu on 2011-06-01
> **ddr3XD said:**
> No, It was not installed through Virtualbox, it was installed the normal way, now im trying to boot off of the drive that Windows 7 is installed on.

Yeah...Virtualbox doesn't work that way.

You might *(and I mean might)* have some succes with this:


[See Post #5](http://ubuntuforums.org/showthread.php?t=1751439)

---

