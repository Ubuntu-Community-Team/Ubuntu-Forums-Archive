---
title: "Ecryptfs, Problem whit keyring?"
date: 2009-09-20
forum: Security
---

### Post by tobias_84 on 2009-09-20
After some update I can't access my homefolder anymore.

Have tried a lot of different solutions but can't access my files.

I looks like I can mount .Private but all files are still encrypted.

> ECRYPTFS_FNEK_ENCRYPTED.FWaVbuNSmNkCJERRruRFIHykZ24qwudHr...bleh

Any Idea what to do next? I just want some files from that partion.

```

user@comp:~$ ecryptfs-mount-private 
Enter your login passphrase:
Inserted auth tok with sig [XXXXXXXXXXXXXXXX] into the user session keyring
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'

```

ecryptfs-unwrap-passphrase seems ok?

```

user@comp:~$ ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase 
Passphrase:pass1234 
pass1234

```

---

### Post by Soul-Sing on 2009-09-20
Private is your mountpoint, not .Private
```
sudo mount -t ecryptfs /home/user_name/.Private /home/user_name/Private
```

---

