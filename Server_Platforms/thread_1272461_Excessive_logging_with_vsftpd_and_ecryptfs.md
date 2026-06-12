---
title: "Excessive logging with vsftpd and ecryptfs"
date: 2009-09-22
forum: Server Platforms
---

### Post by gencha on 2009-09-22
I have installed Ubuntu server 9.04 with the encrypted homdir option enabled.
I created a user for FTP uploads on this system with --encrypt-homedir.
Now when I upload a file I get these messages logged to syslog:
```

Sep 22 13:07:47 media vsftpd: pam_sm_authenticate: Called
Sep 22 13:07:47 media vsftpd: pam_sm_authenticate: username = [frontend]
Sep 22 13:07:47 media vsftpd: Warning: Using default salt value (undefined in ~/.ecryptfsrc)
Sep 22 13:07:48 media vsftpd: Passphrase key already in keyring; rc = [1]
Sep 22 13:07:48 media vsftpd: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [906421af9035e45e] to the keyring; rc = [1]
Sep 22 13:07:48 media vsftpd: Error attempting to add filename encryption key to user session keyring; rc = [1]
Sep 22 13:07:48 media vsftpd: Passphrase key already in keyring; rc = [1]
Sep 22 13:07:48 media vsftpd: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [ec344dfd4caf0ea3] to the keyring; rc = [1]
Sep 22 13:07:48 media vsftpd: Error attempting to add passphrase key to user session keyring; rc = [1]
Sep 22 13:07:48 media vsftpd: There is already a key in the user session keyring for the given passphrase.

```

Although this only happens after the second connection after reboot. The first upload only results in:
```

Sep 22 12:59:40 media vsftpd: pam_sm_authenticate: Called
Sep 22 12:59:40 media vsftpd: pam_sm_authenticate: username = [frontend]
Sep 22 12:59:40 media vsftpd: Warning: Using default salt value (undefined in ~/.ecryptfsrc)

```I actually don't require encryption for that users homedir. When I first added the user I created it without --encrypt-homedir, which resulted in these error messages:
```

Sep 21 19:45:54 media vsftpd: pam_sm_authenticate: Called
Sep 21 19:45:54 media vsftpd: pam_sm_authenticate: username = [frontend]
Sep 21 19:45:54 media vsftpd: Warning: Using default salt value (undefined in ~/.ecryptfsrc)
Sep 21 19:45:54 media vsftpd: Error attempting to open [/home/frontend/.ecryptfs/wrapped-passphrase] for reading
Sep 21 19:45:54 media vsftpd: Error attempting to unwrap passphrase from file [/home/frontend/.ecryptfs/wrapped-passphrase]; rc = [-5]
Sep 21 19:45:54 media vsftpd: Error adding passphrase key token to user session keyring; rc = [-5]

```

I was hoping, that enabling encryption would resolve these complaints. Sadly, I was wrong.

I would be glad to know how to resolve these errors.

---

### Post by ynnek on 2010-01-09
Hello, 

that is a bug: [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/313330](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/313330)

You have two options:

a) Uninstall ecryptfs, if you do not need it.
b) Reinstall ecryptfs from karmic

and the problem will be solved.

I hope this will be usefull for you.

---

### Post by gencha on 2010-01-10
That's very useful indeed. Thanks a lot!

---

