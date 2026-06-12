---
title: "Mounting a restored ecryptfs directory"
date: 2011-05-17
forum: Security
---

### Post by pdwerryhouse on 2011-05-17
Hi all,

I've set up backups (using bacula) of my ecryptfs encrypted home directory (on lucid), and now I am checking that I can restore the filesystem. I've restored it from the backup onto a completely different server, so now I am trying to mount it.

Does anyone know what the default cipher and key bytes are, that Ubuntu uses when it first creates the encrypted filesystem? I know my passphrase is correct, so I'm not sure what I should be entering for the questions below in order to get it to mount.

```
mount -t ecryptfs /restore/home/.ecryptfs/paul/.Private /mnt
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
Enable plaintext passthrough (y/n) [n]: y
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [xxxxxxxxxxxxxxx]: 
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=xxxxxxxxxxxxxxxx
  ecryptfs_passthrough
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=xxxxxxxxxxxxxxx
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [xxxxxxxxxxxxxxxx] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no        
Not adding sig to user sig cache file; continuing with mount.
Mounted eCryptfs

```

Thanks, Paul.

---

### Post by movieman on 2011-05-17
Not sure whether you're backing up all the files or just a subset that have changed, but when I reinstalled Linux on a new hard drive I just created the same user with the same password and then copied over the ecryptfs tree from the old disk. When I logged in all the decrypted files were there.

---

### Post by pdwerryhouse on 2011-05-18
I'm only backing up the /home partition; I don't have the room to back up the entire disk.

Basically, I want to mount it manually in order to learn how it works.

Cheers.

---

### Post by pdwerryhouse on 2011-05-19
Ok, I've figured out the problem now; apparently I have two FNEK signatures, and I was choosing the wrong one.

The default cipher is aes, and the number of bits is 16.

Furthermore, there is a tool in Ubuntu natty and oneiric called "ecryptfs-recover-private" which will do all the mounting for you. It's not in lucid, but I was able to backport it easily.

---

### Post by Dave_L on 2011-05-19
> **pdwerryhouse said:**
> ...there is a tool in Ubuntu natty and oneiric called "ecryptfs-recover-private" which will do all the mounting for you. It's not in lucid, but I was able to backport it easily.

Thanks for reporting that.  I had seen the new script ecryptfs-recover-private described [here](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html), and had wondered whether it would work on 10.04.

---

