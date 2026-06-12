---
title: "Cryptkeeper Solution."
date: 2011-02-27
forum: Security
---

### Post by AbdRahim on 2011-02-27
I lost some files encrypted with Cryptkeeper in one of my attempts to sync a Folder from my NAS which had been synced from a Fedora 14 machine. Upon attempting to mount the encrypted file in Ubuntu Maverick, I got an invalid password error. I am not sure what caused this problem. Cryptkeeper 0.9.4 on Maverick and 0.9.5 on Fedora.

What I discovered was that an encrypted file folder created in Fedora 14, and synced to the NAS (via Unison), could not be imported into an encrypted folder in Maverick - neither an existing folder mounted with Cryptkeeper or one created upon attempting the import from the NAS. The resultant folder on the Maverick machine would always be empty, despite the fact that Cryptkeeper indicated a successful import.

The only way to get these  to all sync up was as follows;
1) Use Cryptkeeper to create an ecrypted 
   folder with identical names on both 
   computers
2)Copy the initial folders you want to sync 
  (identical contents into the encrypted 
  folders on each machine.
3)Syc the Maverick machine to the NAS first 
  then sync the Fedora machine.
4) If you want to move a file within the 
   encrypted folder or add one from another 
   folder, copy it and make sure all gets 
   transfered before deleting it from the 
   original location.
From there on all seems to work ok. Apparently the .encfs6.xml created on each machine must stay with that machine.

Also, one cannot move or rename the .xxx_encfs
file without losing the ability to decrypt the folder.

Hope that helps someone.

---

### Post by mdwy62 on 2011-03-29
This sounds similar to a problem I ran into trying to use encfs/cryptkeeper with Ubuntu One (u1). I want to synchronize my encrypted files so that I can read them on two computers. It doesn't sound as though that is possible.

I created an encrypted folder on U1 using encfs. I then imported it with cryptkeeper on the same machine and it is working fine (under maverick). I then installed encfs and cryptkeeper on my lucid machine that also synchronizes with u1. I also get the password error on the lucid machine when I try to open the encrypted folder, even though cryptkeeper says the import was fine.

---

