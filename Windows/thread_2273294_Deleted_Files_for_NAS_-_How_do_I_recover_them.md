---
title: "Deleted Files for NAS - How do I recover them?"
date: 2015-04-12
forum: Windows
---

### Post by lmangum on 2015-04-12
I was on my Windows 7 laptop browsing files stored on my NAS. I accidently deleted a folder from my NAS. My NAS is a Lenovo Iomega ix2-200 with two 1TB drives. I have all my media on the NAS. I also have an Ubuntu machine with all my usenet services installed.

I am in serious need of help in trying to recover the folder with as much of the data as possible. I have been through the Ubuntu box looking in the trash folders but have had no luck. 

Any help is appreciated.

---

### Post by Sasha_Aderolop on 2015-04-18
1) Stop using your NAS NOW!  The more files that get written to your NAS, the more files you will NOT be able to undelete.   This includes even the log files that the NAS generates.  I&#8217;d recommend turning off all services, applications and protocols except for the basic minimum (SMB, AFP etc.)

2) You MUST copy your undeleted files to the external USB/eSata drive.  This program does not &#8220;undelete&#8221; like Microsoft where it restores the file where it sits, it literally re-writes the new &#8220;recovered&#8221; file &#8211; and thereby will overwrite the files you are trying to undelete.

3) Testdisk vs. Photorec :  My partition was in tact and  my goal was to recover deleted files only.  In this case I&#8217;d strongly recommend using PhotoRec vs. Testdisk.  Ignore the filename, as PhotoRec recovers MUCH MORE than just photos.   If you are recovering from a deleted or corrupt partition &#8211; use Testdisk.  Much of these instructions would also apply to Testdisk, although the specifics would change.   The scope of this HOWTO is to undelete files using PhotoRec
Disclaimer: Obviously this isn&#8217;t supported by QNAP &#8211; although if you ENSURE you recover your files to another partition or external drive, this process is also non-destructive to your existing partition as it only reads from your existing partition/hard drive.

---

