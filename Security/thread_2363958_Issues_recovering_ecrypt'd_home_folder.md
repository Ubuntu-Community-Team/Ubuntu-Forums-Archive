---
title: "Issues recovering ecrypt'd home folder"
date: 2017-06-16
forum: Security
---

### Post by chomafin on 2017-06-16
I'm on 16.04. From a fresh install, I had encrypted my home drive through the installer.  This was some time back, but recently I changed my password using passwd.  After a reboot (after running the system updates), I'm no longer able to log into Ubuntu. On my system I only had 1 user + guest session.

I was able to Alt+F1 to get to a terminal and logged in successfully where I found only : 
```

root@ubuntu:/media/ubuntu/49e9aa7b-3551-46a4-adef-ffbc42f33031/.ecryptfs/user/.ecryptfs# ls
auto-mount  auto-umount  Private.mnt  Private.sig  wrapped-passphrase

```

With that, I found that my folder is no longer being decrypted at login, so my profile cannot be loaded into gnome.

Reading around, I checked to verify I know my passphrase.
```

root@ubuntu:/media/ubuntu/49e9aa7b-3551-46a4-adef-ffbc42f33031/.ecryptfs/user# ecryptfs-unwrap-passphrase .ecryptfs/wrapped-passphrase 
Passphrase: 
Passw0rd!

```

It seems to be the correct password if it prints out right?  When I tried to mount though, 
```

ubuntu@ubuntu:/media/ubuntu/49e9aa7b-3551-46a4-adef-ffbc42f33031/.ecryptfs/user$ sudo ecryptfs-mount-private 
ERROR: Encrypted private directory is not setup properly

```

```

ubuntu@ubuntu:/media/ubuntu/49e9aa7b-3551-46a4-adef-ffbc42f33031/.ecryptfs/user$ sudo ecryptfs-recover-private .ecryptfs/
INFO: Found [.ecryptfs/].
Try to recover this directory? [Y/n]: y
INFO: Found your wrapped-passphrase
Do you know your LOGIN passphrase? [Y/n] y
INFO: Enter your LOGIN passphrase...
Passphrase: 
Error: Unwrapping passphrase and inserting into the user session keyring failed [-5]
Info: Check the system log for more information from libecryptfs

```

```

ubuntu@ubuntu:/media/ubuntu/49e9aa7b-3551-46a4-adef-ffbc42f33031/.ecryptfs/user$ sudo ecryptfs-recover-private .ecryptfs/
INFO: Found [.ecryptfs/].
Try to recover this directory? [Y/n]: y
INFO: Found your wrapped-passphrase
Do you know your LOGIN passphrase? [Y/n] y
INFO: Enter your LOGIN passphrase...
Passphrase: 
Inserted auth tok with sig [26aXXXXXeefa662] into the user session keyring
ERROR: The key required to access this private data is not available.

```

syslog enteries
```
Jun 17 00:34:38 ubuntu systemd[1]: proc-sys-fs-binfmt_misc.automount: Got automount request for /proc/sys/fs/binfmt_misc, triggered by 6736 (find)
Jun 17 00:34:38 ubuntu systemd[1]: Mounting Arbitrary Executable File Formats File System...
Jun 17 00:34:38 ubuntu systemd[1]: Mounted Arbitrary Executable File Formats File System.
Jun 17 00:34:54 ubuntu ecryptfs-insert-wrapped-passphrase-into-keyring: Incorrect wrapping key for file [.ecryptfs//../.ecryptfs/wrapped-passphrase]
Jun 17 00:34:54 ubuntu ecryptfs-insert-wrapped-passphrase-into-keyring: Error attempting to unwrap passphrase from file [.ecryptfs//../.ecryptfs/wrapped-passphrase]; rc = [-5]
Jun 17 00:35:04 ubuntu ecryptfs-insert-wrapped-passphrase-into-keyring: Incorrect wrapping key for file [.ecryptfs//../.ecryptfs/wrapped-passphrase]
Jun 17 00:35:04 ubuntu ecryptfs-insert-wrapped-passphrase-into-keyring: Error attempting to unwrap passphrase from file [.ecryptfs//../.ecryptfs/wrapped-passphrase]; rc = [-5]
```


```
root@ubuntu:/media/ubuntu/49e9aa7b-3551-46a4-adef-ffbc42f33031/.ecryptfs/user/.ecryptfs# ecryptfs-add-passphrase --fnek 
Passphrase: 
Inserted auth tok with sig [26a5a3134eefa662] into the user session keyring
Inserted auth tok with sig [c1d2ffe2f61b0436] into the user session keyring
```

```

ubuntu@ubuntu:/media/ubuntu/49e9aa7b-3551-46a4-adef-ffbc42f33031/.ecryptfs/user$ sudo mount -t ecryptfs .Private/ /home/user/
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32
 2) blowfish: blocksize = 8; min keysize = 16; max keysize = 56
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16
Selection [aes]: 1
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 1
Enable plaintext passthrough (y/n) [n]: y
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [26a5XXXeefa662]: c1d2ffeXXX0436
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=c1d2ffeXXX0436
  ecryptfs_passthrough
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=26a5XXXeefa662
Mounted eCryptfs

ubuntu@ubuntu:/media/ubuntu/49e9aa7b-3551-46a4-adef-ffbc42f33031/.ecryptfs/user$ sudo ls /home/user/
ECRYPTFS_FNEK_ENCRYPTED.FaZ9g0TlFJU3LUTQ89J1HPiDzUFtCfFbV97-13bG6sVTRgxYqc98ak0HYbTikP5bsmslT6L-0486tfAUNY-V2kPg0oDyP4vyM3C2SnPhE5ZzDcaNWSU2YvaKVcHrmsEX9jipV9pK9xFqjCA-
ECRYPTFS_FNEK_ENCRYPTED.FWZ9g0TlFJU3LUTQ89J1HPiDzUFtCfFbV97-0asMdTGLhrvBDTJC7I4vH---
ECRYPTFS_FNEK_ENCRYPTED.FWZ9g0TlFJU3LUTQ89J1HPiDzUFtCfFbV97-1YSiSyucnY-J4KuYDw1ZA---
ECRYPTFS_FNEK_ENCRYPTED.FWZ9g0TlFJU3LUTQ89J1HPiDzUFtCfFbV97-21WS2gcT6ZFQc7CfZQlo5U--
ECRYPTFS_FNEK_ENCRYPTED.FWZ9g0TlFJU3LUTQ89J1HPiDzUFtCfFbV97-2DIKrPXzisUU3EdEYTY15k--
ECRYPTFS_FNEK_ENCRYPTED.FWZ9g0TlFJU3LUTQ89J1HPiDzUFtCfFbV97-3Tw4YHn8CaG958Hn5OZv0k--
ECRYPTFS_FNEK_ENCRYPTED.FWZ9g0TlFJU3LUTQ89J1HPiDzUFtCfFbV97-3xQkqlcM1ylIE3G9qYfS4---
ECRYPTFS_FNEK_ENCRYPTED.FWZ9g0TlFJU3LUTQ89J1HPiDzUFtCfFbV97-3z8Nd.kvswNn4XVUcL8WH---
ECRYPTFS_FNEK_ENCRYPTED.FWZ9g0TlFJU3LUTQ89J1HPiDzUFtCfFbV97-42EnKql3dByVPE7XemSHWU--
ECRYPTFS_FNEK_ENCRYPTED.FWZ9g0TlFJU3LUTQ89J1HPiDzUFtCfFbV97-6y4nuM.Ka2fPBFQ94C5qOU--
ECRYPTFS_FNEK_ENCRYPTED.FWZ9g0TlFJU3LUTQ89J1HPiDzUFtCfFbV97-7c7M6PdZrl4ByFMo4Q6tIU--
ECRYPTFS_FNEK_ENCRYPTED.FWZ9g0TlFJU3LUTQ89J1HPiDzUFtCfFbV97-8cxw0hvcSWcRa9ry6Ii0vE--
ECRYPTFS_FNEK_ENCRYPTED.FWZ9g0TlFJU3LUTQ89J1HPiDzUFtCfFbV97-9qqTPN8v5bfXIM5Y7.P-A---
ECRYPTFS_FNEK_ENCRYPTED.FWZ9g0TlFJU3LUTQ89J1HPiDzUFtCfFbV97-a6434GLcu7g.gkj1GM3n2E--
ECRYPTFS_FNEK_ENCRYPTED.FWZ9g0TlFJU3LUTQ89J1HPiDzUFtCfFbV97-AD1fipTMXy7NdXf2cEDVx---

```

I'm at a loss at this point. It seems like, from following all the guides, that I should be in and good to go?  But I can't seem to get to anything.  Any help would be much appreciated. 
Thanks

---

