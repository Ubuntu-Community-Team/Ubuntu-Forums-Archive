---
title: "Cannot reach encrypted part. from Live CD with hash"
date: 2011-01-24
forum: Security
---

### Post by namosthatha on 2011-01-24
Hi All,

My system hang and corrupted something in the ext3 filesystem or RAID 1 config. This seems to be fixed using a 10.04 Live CD, so filesystems and RAID are OK in the live session but booting failed (it complains about filesystem errors). I decided to reinstall the system, but my home partition is encrypted and needs to be saved first. I have followed the instructions at [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory)
but nothing happens. I have my long hexadecimal hash to decrypt the partition but forgot the encription settings (AES, blowfish, etc). I have tried all combinations, but no result. No error message like incorrect hash or similar arrives. Here is an example from my experiments:
```
root@ubuntu:/#mount -r -t ext3 /dev/sda2 /mnt
root@ubuntu:/#mkdir /home/balazs
root@ubuntu:/#cd /mnt/balazs 
root@ubuntu:/mnt/balazs# ecryptfs-add-passphrase --fnek
Passphrase: 
Inserted auth tok with sig [715eada30fefcf05] into the user session keyring
Inserted auth tok with sig [e5d134f2cf51fc8e] into the user session keyring
root@ubuntu:/mnt/balazs# mount -t ecryptfs /mnt/balazs/.Private/ /home/balazs/
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [715eada30fefcf05]: 
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=715eada30fefcf05
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=715eada30fefcf05
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [715eada30fefcf05] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : yes
Successfully appended new sig to user sig cache file
Mounted eCryptfs
root@ubuntu:/mnt/balazs# ls /home/balazs/
ECRYPTFS_FNEK_ENCRYPTED.FWYYlkYNlADK.USEyS5z1oebD6H.g8SifF-B0B-t9BhD3OhYA1-grwUYHk--
ECRYPTFS_FNEK_ENCRYPTED.FWYYlkYNlADK.USEyS5z1oebD6H.g8SifF-B11rjmg2MdEDFs3OWsSNxJ---
```...
what can be the problem?

Thank you in advance.
Best regards: Balazs Bamer

---

