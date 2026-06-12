---
title: "Ubuntu Server 18.04 on Raid1 array"
date: 2018-05-01
forum: Server Platforms
---

### Post by happyblue on 2018-05-01
Hello everyone,
I've been doing a lot of research recently in order to install Ubuntu on my 2x1 TB Raid1 Array. At first, I tried installing the Desktop version of Ubuntu, but I've read in several forum that using the Server version is more suited to Raid array, and that the only difference between Ubuntu Desktop or Server are the pre installed software.
Hence I did try today to install the Server version 18.04. The thing is, no partition are showing up.

My configuration is as follow:
2x1TB in raid1 array
1 200GB partition, NTFS with Windows 10
1 200GB partiton, NTFS with nothing on it
1 531.41GB partition (the rest), NTFS, used as a data partition.

Should I remove the second partition in order to put it into "unallocated space" ?
N.B.:As far as I have understood, the type of raid1 I am using is fakeraid: my HDD are in "RAID" mode in the BIOS
N.B.2: If another linux distro is more suited for Raid, I am open to it, but I have not find one so far

Thank you in advance for your time !

---

### Post by TheFu on 2018-05-01
Google found this: [https://askubuntu.com/questions/1028643/18-04-server-does-new-intaller-supports-mdadm-raid-install-did-not-find-the](https://askubuntu.com/questions/1028643/18-04-server-does-new-intaller-supports-mdadm-raid-install-did-not-find-the)

---

### Post by SeijiSensei on 2018-05-01
It sounds like your computer may have what is termed "fakeRAID" which requires a driver at the operating system level.  Most systems like this are designed for Windows and include the drivers.  Linux may or may not have the equivalent drivers.

You need to tell us more about your plans for this system.  Does it have a Windows installation that you are trying to preserve?  Are you willing to delete all the data on the machine and start from scratch?  When all is said and done, what do you want this machine to do?

---

### Post by happyblue on 2018-05-02
Thankk you for your reply.
@TheFu: I have already tried the alternate installer, without success
@SeijiSensei: Do you know if it possible to search for these drivers in the installer ?

Concerning my plans for the system: yes I am trying to preserve the Windows installation but if there is no other way, it is possible for me to reinstall.
When all is said and done, I simply want to use the system as my personal computer. The Windows part will mainly be there for gaming and the Linux part to do everyday stuff (internet, video, etc)

For further info: [https://imgur.com/a/ezoqftM](https://imgur.com/a/ezoqftM), this is what I see instead of the parition

Edit: i have found this: [https://askubuntu.com/questions/455511/dual-boot-ubuntu-14-04-and-windows-7-on-fakeraid-installation-error-question-m](https://askubuntu.com/questions/455511/dual-boot-ubuntu-14-04-and-windows-7-on-fakeraid-installation-error-question-m)
I plan to do further research, but do you think it can works despite being 4 years old ? Will it break Raid ?

---

