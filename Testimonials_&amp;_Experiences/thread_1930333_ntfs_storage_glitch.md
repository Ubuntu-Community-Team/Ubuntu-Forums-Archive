---
title: "ntfs storage glitch"
date: 2012-02-23
forum: Testimonials &amp; Experiences
---

### Post by m_ghv_geo on 2012-02-23
okay
I found this glitch in ntfs support of ubuntu
so whenever I save/copy/move data on NTFS drive 

there is 50% chance that data will not be there though i used "safe remove" and 
25%chance that data will be there but WINDOWS O.S. will not be able find it and 
25% everything will be good

I saw this problem on different types of drive but I always was using NTFS

and I also had this problem on previus versions of Ubuntu
and right know I have this problem on KUBUNTU 11.10

I lost a lot of work because of this but right know i lost 100GB folder full of my data right know am trying to recover it, if the Recovery software will be able to find it.

---

### Post by leclerc65 on 2012-02-23
I had that problem with 8.10, 9.10.
I never touched a x.10 Ubuntu since then.

---

### Post by lukeiamyourfather on 2012-02-23
NTFS support in Linux is hit and miss. It has known issues with encrypted or compressed partitions and sometimes has issues with file permissions. Those issues are documented in the help. If possible use a native Linux filesystem with better support like ext4 or Btrfs. If the issue here is letting Windows access files you can use FAT32 to transfer data between them which is more reliable in Linux than NTFS.

---

### Post by coffeecat on 2012-02-23
> **m_ghv_geo said:**
> there is 50% chance that data will not be there though i used "safe remove" and 
25%chance that data will be there but WINDOWS O.S. will not be able find it and 
25% everything will be good

Was Windows in hibernation when you lost data? This a known issue to do with the way Windows handles NTFS filesystems. So long as you do not try to use a NTFS fileystem from Ubuntu when Windows is in hibernation, you should find NTFS support in Ubuntu generally robust and reliable.

---

### Post by recluce on 2012-02-25
> **coffeecat said:**
> Was Windows in hibernation when you lost data? This a known issue to do with the way Windows handles NTFS filesystems. So long as you do not try to use a NTFS fileystem from Ubuntu when Windows is in hibernation, you should find NTFS support in Ubuntu generally robust and reliable.

+ 1

What the OP reports sound EXACTLY like running Ubuntu while Windows is hibernated. It is not even an "issue" per se, but a logical consequence of how hibernation works:

1.) Windows is hibernated, remembering the status of the NTFS file system and the journal

2.) Ubuntu is started, unaware of Windows and makes changes to the file system.

3.) Ubuntu shuts down and Windows wakes up from hibernation, completely convinced that the file system is the same as when it was hibernated. The very first write leads to NTFS corruption.

Hibernating windows before starting Ubuntu is a newbie mistake I made when I started with Ubuntu four years ago and I learned the hard way, with corrupted NTFS volumes and lost files/data.

Avoiding the hibernation issue, NTFS has been rock-solid for me in 10.04, 10.10 and Mint 12 (bases on Ubuntu 11.10) - the "hit or miss" period has been ages ago.

---

### Post by m_ghv_geo on 2012-02-25
> **recluce said:**
> + 1

What the OP reports sound EXACTLY like running Ubuntu while Windows is hibernated. It is not even an "issue" per se, but a logical consequence of how hibernation works:

1.) Windows is hibernated, remembering the status of the NTFS file system and the journal

2.) Ubuntu is started, unaware of Windows and makes changes to the file system.

3.) Ubuntu shuts down and Windows wakes up from hibernation, completely convinced that the file system is the same as when it was hibernated. The very first write leads to NTFS corruption.

Hibernating windows before starting Ubuntu is a newbie mistake I made when I started with Ubuntu four years ago and I learned the hard way, with corrupted NTFS volumes and lost files/data.

Avoiding the hibernation issue, NTFS has been rock-solid for me in 10.04, 10.10 and Mint 12 (bases on Ubuntu 11.10) - the "hit or miss" period has been ages ago.

Okay lets leave the windows a side(because i had same problem with hibernate when WIN was not able to find file I removed the drive(without using safe remove or eject turn off computer boot-up Ubuntu plugged my usb and everything was there))

Lets say I **formatted **the **usb flash storage drive** and created only one **NTFS** partition
and in this drive I copied files, and safely removed this drive. inserted back in **UBUNTU**, in this case probability for me to all the files be there is approximately somewhere at 50%.

---

### Post by Elfy on 2012-02-26
This appears to be turning into support. Please start a support thread - this forum is not for support.

Closed.

---

