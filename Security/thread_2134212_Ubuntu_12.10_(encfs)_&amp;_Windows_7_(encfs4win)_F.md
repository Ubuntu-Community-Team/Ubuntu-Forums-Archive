---
title: "Ubuntu 12.10 (encfs) &amp; Windows 7 (encfs4win) File Issue"
date: 2013-04-10
forum: Security
---

### Post by johnathanamber on 2013-04-10
Hey everyone,

I was wondering if others have seen similar issues.

I've installed Ubuntu 12.10 and updated to the latest release files. I've encrypted several folders and their contents with encfs on an NTFS partition on the same drive.

I've also installed Windows 7 (dual booting on the same hard drive) and have used encfs4win (which uses Dokan) to access the above files (hence the reason for the NTFS partition above).

I use SpiderOak to save the encrypted folders to the cloud for retention purposes and access the above files from Windows for school. Microsoft products are required for school (go figure).

I've recently heavily updated/reorganized my Thunderbird mailbox files and all seemed well... that is until I rebooted into Windows and a consistency check was done on the partition with the encrypted files. Needless to say that the consistency check found a ton of errors and supposedly corrected them.

Now when I access my encrypted files, somewhere my system freezes in both Linux and Windows. I assume a corrupted file somewhere caused an access issue when copied to memory or something similar.

So, I was wondering if anyone else was having similar issues with accessing encfs files across Linux and Windows.

In an effort to avoid this in the future, I am copying the unencrypted files to an external drive, then recreating a TrueCrypt partition, and then storing the files there to be synced with the cloud.

Any thoughts are also welcome.

Thank you,
Johnathan

---

### Post by johnathanamber on 2013-04-10
BTW, just to clarify, the reason why I am moving to TrueCrypt is that there are natives to both Windows and Linux that are available, using the same versions and code bases. I won't have to use any sort of mediary to get it working... i.e. Dokan for Windows, etc.

---

