---
title: "Question about encrypting /home partition without reinstalling"
date: 2011-06-12
forum: Security
---

### Post by Zeikcied on 2011-06-12
I have Kubuntu 11.04 64-bit installed (software upgrade from 10.10) and I have a separate /home partition.  I want to encrypt my /home partition (and perhaps the swap partition as well) but I don't want to have to reinstall Kubuntu.  (Mostly because it was a software upgrade and I don't have an 11.04 disc.)

I found a tutorial for Encryptfs via one of the stickies that mentions post-install migration, but it says that using Encryptfs on a separate /home partition is more complicated than if it were part of the root partition and that the CDs don't have any software to preserve and configure existing encrypted /home partitions.  (Granted this tutorial is made for 9.04, so things may have changed.)

Also, this tutorial makes it sound like if you have your /home directory encrypted that the encrypted data is stored in a folder on the root partition.  Is it done the same way if the /home directory is on its own partition?  Because I don't think my root partition is large enough to have all of my /home data.  (I purposely kept it small because the root partition doesn't seem to get very large.)

If you can't tell I'm quite clueless about all this.

---

### Post by BkkBonanza on 2011-06-12
See this guys blog. He is the dev on the home encryption and has good info there including old and new posts on migration without re-installing.

[http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html](http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)

Be sure to click to the new update he mentions.

---

### Post by FuturePilot on 2011-06-12
```
sudo ecryptfs-migrate-home
```

Back everything up first.

No, the encrypted data is not stored in the / (root) partition. It's stored in a hidden folder in /home/. And no, having a separate /home partition does not in any way complicate migrating.

---

### Post by Zeikcied on 2011-06-12
Thanks for the replies.

The tutorial I read, and the blog linked above, both say that the user shouldn't be logged in.  But I only have this one user account on my system, and root is disabled by default.  So how can I run the encryptfs-migrate-home command?  Do I have to enable the root user?  Does it automatically log me out?  I get that I have to log out of KDE, and probably stop kdm as well, but other than enabling root and logging in, I don't know how I can do this without my user account being logged in.

---

### Post by FuturePilot on 2011-06-12
> **Zeikcied said:**
> Thanks for the replies.

The tutorial I read, and the blog linked above, both say that the user shouldn't be logged in.  But I only have this one user account on my system, and root is disabled by default.  So how can I run the encryptfs-migrate-home command?  Do I have to enable the root user?  Does it automatically log me out?  I get that I have to log out of KDE, and probably stop kdm as well, but other than enabling root and logging in, I don't know how I can do this without my user account being logged in.

Log out then press Ctrl+Alt+F1 and it will drop you to a console. Login through there with your regular account. That way you only have a couple processes running under your user which is the important part. Run the command and when it's all done press Ctrl+Alt+F7 which will take you back to the login screen.

---

### Post by Zeikcied on 2011-06-22
I guess I should have read up on eCryptfs before using it.  I didn't realize there was a difference in file system encryption.  I guess eCryptfs doesn't encrypt the file names or metadata.  So apparently if I want that, I need to use dm-crypt, which means I have to reformat my /home partition.

I guess that's okay, as long as it doesn't make it too complicated to upgrade to the next version of Kubuntu.  The problem is that the LUKS Alternate CD tutorial link in the "Ubuntu Security" sticky gives a 403 error.

Do I need the alternate CD?  And do I need to reinstall Kubuntu just to fully encrypt my /home partition (and swap)?

---

### Post by BkkBonanza on 2011-06-22
ecryptfs (used by encrypted home) does definitely encrypt the filenames/dirs. I'm not sure about all metadata hidden in the system though. I know it does the filenames because I just had to recover a home folder on a crashed machine and had to go through the process to manually mount it. Filenames become a long gibberish value.

---

### Post by FuturePilot on 2011-06-22
> **Zeikcied said:**
> I guess I should have read up on eCryptfs before using it.  I didn't realize there was a difference in file system encryption.  I guess eCryptfs doesn't encrypt the file names or metadata.  So apparently if I want that, I need to use dm-crypt, which means I have to reformat my /home partition.

I guess that's okay, as long as it doesn't make it too complicated to upgrade to the next version of Kubuntu.  The problem is that the LUKS Alternate CD tutorial link in the "Ubuntu Security" sticky gives a 403 error.

Do I need the alternate CD?  And do I need to reinstall Kubuntu just to fully encrypt my /home partition (and swap)?

Ecryptfs definitely encrypts the file names. As for meta data I'm pretty sure that is encrypted as well.

---

### Post by Zeikcied on 2011-06-22
> **BkkBonanza said:**
> ecryptfs (used by encrypted home) does definitely encrypt the filenames/dirs. I'm not sure about all metadata hidden in the system though. I know it does the filenames because I just had to recover a home folder on a crashed machine and had to go through the process to manually mount it. Filenames become a long gibberish value.

Okay...  I read in the eCryptfs FAQ (linked in the Wikipedia article) that filename encryption is something they're "planning" to include, so I assumed it wasn't included yet.  Maybe they need to update that thing.

I also noticed in the FAQ that it says that metadata such as the size of the file isn't encrypted.  Which makes me have another question.  What exactly is considered metadata?  Is that just size, creation, modified, etc.?  Or does it include stuff like tags in MP3 and video files?  I guess if the metadata is just the size and all that, and nothing that can identify the file, then it's okay.

Since file names are apparently encrypted, I assume that the folder names are, as well?

---

### Post by Dave_L on 2011-06-22
Both file names and folder names are encrypted.

File sizes and dates are not encrypted.

> tags in MP3 and video files

I don't know what those are. If they're contained within the file, they're encrypted.

---

### Post by BkkBonanza on 2011-06-22
MP3 tags are contained in the file data itself and so are encrypted.

---

