---
title: "Decrypting whole partition"
date: 2014-08-12
forum: Security
---

### Post by aleksandersynowiec on 2014-08-12
Hi!

I've encrypted whole drive during Ubuntu 14.04.1 installation (easy peasy part). I have Win7 on other partition and I cannot acces it no matter how - not listed in grub, other partitions looks to be marged into one 921 GB partition. So here comes my question - how am I supposed to decrypt whole drive and get Windows back?

EDIT: Even when I'm logged in and I gave encryption password, it looks like I have only 1 partition with 921 GB space and not a single file or folder connected to old system. Is it possibile, that amazing Ubuntu just got rid of Windows, my documents, pictures, music, movies ect.?

---

### Post by TheFu on 2014-08-12
Anything is possible - garbage in, garbage out - that's how computers work.

If you told the installer to "*encrypted whole drive during Ubuntu 14.04.1 installation*" - well - that is the **whole drive**.

If you could please open a terminal, then run **sudo parted -l** and post the results back here, we will know the answer.

---

### Post by sandyd on 2014-08-12
> **aleksandersynowiec said:**
> Hi!

I've encrypted whole drive during Ubuntu 14.04.1 installation (easy peasy part). I have Win7 on other partition and I cannot acces it no matter how - not listed in grub, other partitions looks to be marged into one 921 GB partition. So here comes my question - how am I supposed to decrypt whole drive and get Windows back?

EDIT: Even when I'm logged in and I gave encryption password, it looks like I have only 1 partition with 921 GB space and not a single file or folder connected to old system. Is it possibile, that amazing Ubuntu just got rid of Windows, my documents, pictures, music, movies ect.?

You clicked on "Encrypt whole drive" (or similar, I cant remember the exact wording). That removes all existing partitions to generate an encrypted LVM setup, with which Windows is not compatible.

---

### Post by aleksandersynowiec on 2014-08-12
```
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size   File system  Name  Flags
 1      1049kB  538MB   537MB  fat32              boot
 2      538MB   794MB   256MB  ext2
 3      794MB   1000GB  999GB


Error: /dev/mapper/ubuntu--vg-swap_1: unrecognised disk label             

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 991GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0,00B  991GB  991GB  ext4


Error: /dev/mapper/sda3_crypt: unrecognised disk label    

```

Ok, but since when encrypting equals formating equals formating partition/drive?


**sandyd**, that's a great ifnormation. Shame there was none in the installer. CryptLocker and SynLocker menaged to encrypt whole disks without deleting any data to blackmail owners. Shame Ubuntu can't do this. ;/ One more thing - Windows might not be compatibile, but shouldn't NTFS partition be?

---

### Post by TheFu on 2014-08-12
> **aleksandersynowiec said:**
> Ok, but since when encrypting equals formating equals formating partition/drive?


**sandyd**, that's a great ifnormation. Shame there was none in the installer. CryptLocker and SynLocker menaged to encrypt whole disks without deleting any data to blackmail owners. Shame Ubuntu can't do this. ;/ One more thing - Windows might not be compatibile, but shouldn't NTFS partition be?

Linux/Ubuntu is NOT Windows. Things work differently. [http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) may help with understanding.

I've never seen/used/touched CryptLocker or SynLocker.  I don't understand the blackmail comment, sorry.

Thanks for posting the partition data. It does appear that the entire HDD was used for a fresh Ubuntu install.  It is considered a best practice to backup all data before doing any install or partition changes with any computing platform - Windows, OSX and Linux included.

I don't think there is much hope of getting the Windows data back - it did repartition everything, but [http://blog.miketoscano.com/?p=72](http://blog.miketoscano.com/?p=72) might help someone else coming later.

No, NTFS is NOT compatible for a Linux OS install. It is a foreign partition type and only has limited support in Linux. The OS and normal partitions cannot use NTFS for programs due to the incompatible file and directory permissions model of Windows.  It can use it for data, but not where any file permissions are required.

I'm sorry, but unless you have a backup, the Windows stuff is gone.  
At this point, I'd be really frustrated too. Sorry this happened.

If I install Windows AFTER linux and tell it to use the entire HDD, I'd expect all my data to be gone. OTOH, Windows consistently trashes Linux boots without asking. It is a tough problem to solve. Hopefully, it will get better.

---

### Post by aleksandersynowiec on 2014-08-12
All in all, byebye everything, I have to start over. Hope I won't fell that cruel loss in future that bad. But seriously, simple information, since installer detects Windows, that encrypting will f*** up all of your data would be nice.

CryptLocker and SynLocker are viruses, that encrypts your drive and send you decrypting key for money. About $400.


EDIT: I need advice - should I stay with Windows or change to Linux (but other distro)? Laptop: i5 3210, nVidia GTX 660M, 8 GB RAM, 1 TB HDD. Should I stay with Windows for gaming and stuff and use Ubuntu booted from USB drive for programming?

---

### Post by andyfied on 2014-08-12
CryptLocker/SynLocker **do not encrypt your whole drive**, they encrypt your **files **but allow the system to boot so they can extort you.

---

### Post by TheFu on 2014-08-12
> **andyfied said:**
> CryptLocker/SynLocker **do not encrypt your whole drive**, they encrypt your **files **but allow the system to boot so they can extort you.

[https://www.decryptcryptolocker.com/](https://www.decryptcryptolocker.com/) - free decryption thanks to security researchers.  I assume these things are Windows only, at least for now?  I don't let Windows on the internet.

---

### Post by aleksandersynowiec on 2014-08-12
**andyfied - **Then what's the actual benefit of encrypting whole drive but not just files? Performance?

**[COLOR=#000000]TheFu[/COLOR]** - unfortunately there's no such thing for SynLocker. I've read that at least paying actually pays off.

---

### Post by sandyd on 2014-08-13
> **aleksandersynowiec said:**
> **andyfied - **Then what's the actual benefit of encrypting whole drive but not just files? Performance?

**[COLOR=#000000]TheFu[/COLOR]** - unfortunately there's no such thing for SynLocker. I've read that at least paying actually pays off.

Encryption makes your drive slower. It takes time for the CPU to decrypt it using the algorithm chosen.

If you want to use windows and linux side by side, _dont_ click the encrypt drive option. Instead, when specifying your user, click 'encrypt home directory' or similar. Note that backups should still be taken, people have found that it is quite difficult to retrieve data from encrypted home volumes.

---

### Post by uRock on 2014-08-13
> **aleksandersynowiec said:**
>  I've read that at least paying actually pays off.

Backing up data on a regular basis is cheaper, more efficient, and the bad guy doesn't get to make his or her money.

I am sorry your Windows was trashed. 
> **TheFu said:**
> [https://www.decryptcryptolocker.com/](https://www.decryptcryptolocker.com/) - free decryption thanks to security researchers.  I assume these things are Windows only, at least for now?  I don't let Windows on the internet.
That's a great link to bookmark, thanx! The ransomwares have moved on to all three major phone OSes. Backing up data and taking care of what one installs on the phone is becoming more and more important.

---

### Post by andyfied on 2014-08-14
> **aleksandersynowiec said:**
> **andyfied - **Then what's the actual benefit of encrypting whole drive but not just files? Performance?

As has been mentioned, encryption uses more CPU cycles to access things that if it wasn't encrypted. The whole idea is security if someone gets hold of your computer/harddrive. Without encryption, someone could access the whole drive by taking it out and putting it into a caddy. If it's encrypted, it will look like it is blank.

IMO most people don't need encryption on their drives unless they are expecting them to get stolen or have super sensitive data (maybe work information you don't want to be taken). The most important thing is encrypting data that is being sent to and from the internet and other networks as it's easier to intercept.

---

