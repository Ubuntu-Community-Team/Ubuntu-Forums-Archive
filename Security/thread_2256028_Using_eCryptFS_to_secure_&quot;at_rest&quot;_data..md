---
title: "Using eCryptFS to secure &quot;at rest&quot; data. How to mount at boot?"
date: 2014-12-09
forum: Security
---

### Post by rwurttem on 2014-12-09
I'm trying to find a way to use eCryptFS to secure the "at rest" data on a server. 

I have ecryptfs installed and I understand how to encrypt a directory.  What I am missing, is how to mount the encrypted folder at boot (i.e. fstab).  

I have been Googling for a few hours but everything I have found is how to mount an encrypted home folder, which is not what I am looking to accomplish.

Any assistance would be greatly appreciated.

Kind regards,
/Raj

---

### Post by rwurttem on 2014-12-09
Got some feedback from our local Atlanta Linux Enthusiast (ALE) group:

By: Leam Hall

#####
 
### /root/.ecrypt_key
 
passphrase_passwd=ecryptTHIS####
 
### Make the first volumes
 
mkdir /opt/.fred_ecrypt
mkdir /opt/fred
 
### Edit /etc/fstab
 
/dev/vgroup2/fred      /opt/.fred_ecrypt     ext3    defaults        1 2
 
/opt/.fred_ecrypt /opt/fred ecryptfs rw,ecryptfs_sig=1234567890abcdef, key=passphrase:passphrase _passwd_file=/root/.ecrypt_key,ecryptfs_passthrough=no,ecryptfs_unlink_sigs,ecryptfs_cipher=aes,ecr
yptfs_key_bytes=24 0 0
 
### Mount those two volumes
### If it asks you for approval, then answer yes.
### That generally only happens on the first mount.
 
mount /opt/.fred_ecrypt
mount /opt/fred
 
### Make the tmpfs mount
 
mkdir /opt/fred/testdir
 
### Edit /etc/fstab
### This lets you use 90% of the RAM
 
tmpfs   /opt/fred/testdir   tmpfs   defaults,size=90%       0 0
 
#####

---

