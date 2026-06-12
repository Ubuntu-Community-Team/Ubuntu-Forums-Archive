---
title: "Full Disk Encryption Back Up Issues"
date: 2010-05-10
forum: Security
---

### Post by TaoWanderer on 2010-05-10
Are there any complications with backing up data that's been encrypted using LUKS and LVM via the guided full disk encryption with the alternate CD?  i.e. is it possible to use back up software and do incremental back ups, and recover the data, etc.? 

Does just encrypting the home directory work better for back ups or same?

Thank you, trying to figure out which encryption method to use for new install.

---

### Post by TaoWanderer on 2010-05-10
This article: [Ubuntu’s Encrypted Home Directory: A Canonical Approach to Data Privacy]("http://www.linux-mag.com/id/7568/1/") says: > The eCryptfs layered file system approach also eliminates the need for a dedicated partition, sparse file, or preallocated disk space for the encrypted data. eCryptfs files are written to the administrator’s chosen underlying file system with the total disk capacity available. Since each encrypted file is written to disk as an atomic unit, users can perform per-file incremental encrypted backups to remote storage – something that is **impractical and dangerous** with block device encryption solutions.

Anyone know what's impractical and dangerous about encrypting the whole drive with LVM and LUKS (which I believe is block device encryption) and performing per-file incremental encrypted backups to remote storage?

---

### Post by Rubicon_82 on 2010-05-10
Although I don't know the specific implementation details of LUKS, I think the following explanation may help.

Incremental backups of individual files on encrypted block devices is impractical because you have no way of determining where on the device the individual file is located.  With a regular, non-encrypted file system, you could use tools such as 'stat', or lower-level functions to provide information on the inodes/blocks used by the file.  In theory, you could then use 'dd' or similar to copy those specific bytes to remote storage.  If encryption on a block device file system is properly implemented, there shouldn't be a direct correspondence between the information provided by 'stat' and the actual location of the file on the device.

The danger comes when you try to restore your files.  Suppose you have copied a specific sequence of bytes corresponding to your file from a block device (encrypted or otherwise).  How do you ensure that you don't overwrite something important when you restore those bytes to their original location?  Chances are that by doing so, you'll destroy the integrity of the file system on that block device.

A safe option for backing up of an encrypted block device would be to use rsync or rdiff on an image of the device.

---

### Post by TaoWanderer on 2010-05-11
Thank you.  That is a very good explanation.

The encrypted home directory option (“Require a password to log in and decrypt your home folder”) on install using eCryptfs doesn't have that problem, right?

With the encryption home directory can you perform incremental backups the same as you would with an unencrypted home?

---

### Post by Rubicon_82 on 2010-05-11
> **TaoWanderer said:**
> Thank you.  That is a very good explanation.

The encrypted home directory option (“Require a password to log in and decrypt your home folder”) on install using eCryptfs doesn't have that problem, right?

With the encryption home directory can you perform incremental backups the same as you would with an unencrypted home?

Yes, this is right.

However, instead of backing up '/home/user/' (the decrypted mount point), you should be backing up '/home/.ecryptfs/user/' (the encrypted data).  If you choose to to this, you should also look at [https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome).  There are caveats on that page regarding potential data leaks when running with an unencrypted swap partition, etc.

---

### Post by frostschutz on 2010-05-11
I use full disk encryption, and back up to an external encrypted backup HDD.

It works exactly the same way as backing up an unencrypted system - once you mounted the encrypted drives properly, programs like tar or rsync don't know the difference anyway.

So the only trick you need to figure out is how to mount your encrypted drives. How to do that depends on the encryption method you're using.

---

