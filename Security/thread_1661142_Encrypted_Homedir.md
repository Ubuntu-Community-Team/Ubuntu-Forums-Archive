---
title: "Encrypted Homedir"
date: 2011-01-06
forum: Security
---

### Post by Milambar on 2011-01-06
Okay, so I had a laptop installed with ubuntu, and a fileserver, also installed with ubuntu.

The laptop had encrypted homedirs, the fileserver does not.

The laptop died, but I need some files off the hdd. So I took the hdd out, mounted it in an external caddy, and mounted the disk.

That gave me access to the disk, but not to the files on my encrypted homedir. No worries, I thought, as I have the passphrase for it. I noted it down and kept it in my safe when I created the install.

A bit of googling gave me the command I needed. encryptfs-mount-private.

Heres what happened...

> 
root@fundungeon:/media/sdb/home# encryptfs-mount-private
No command 'encryptfs-mount-private' found, did you mean:
 Command 'ecryptfs-mount-private' from package 'ecryptfs-utils' (main)
encryptfs-mount-private: command not found


Okay, so I install encryptfs-utuls...
> 
root@fundungeon:/media/sdb/home# apt-get install encryptfs-utils
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package encryptfs-utils


Ummm... Okay.. so lets do a search...
> 
root@fundungeon:/media/sdb/home# apt-cache search encryptfs
root@fundungeon:/media/sdb/home#


So my question is... What now?

---

### Post by Milambar on 2011-01-06
Found my error, its ecrypt-mount-private, not encrypt-mount-private.

---

