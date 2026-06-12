---
title: "I can access an encrypted home folder using sudo caja. Is that right?"
date: 2015-12-30
forum: Security
---

### Post by PopsTheSailor on 2015-12-30
I'm starting to mess around with encryption and I created 2 encrypted home folders. One was on an account that was already installed so I used the "sudo ecryptfs-migrate-home -u user" command. On the second account, I encrypted the home folder when I created the new account. 

I proceeded to shut down the computer to make sure the passphrase was no longer in memory. I then put in a Live CD booted up and then ran "sudo caja" from the terminal. This allowed me to access the files in the encrypted home folders (both users).

Is this really right or did I do something wrong during the encryption process? If it really works this way, I don't see much use for encrypting anything.

This was all done on Ubuntu-Mate 15.04.

If the above (sudo caja) really does allow access to the data, is there a security process that doesn't? Seems to me if my laptop is stolen, anyone could just boot off the live CD and access all my bank account info, passwords, etc.

---

### Post by ian-weisser on 2016-01-02
Encryption is not a super-password that can be bypassed. It's scrambling the stored bytes on disk so that only a password (key) holder can unscramble them.
If your dir is properly encrypted, caja should be able to see files, but not to read any of them. The password provides the mathematical key to decrypting.

[EDIT] Thanks to Sudodus below for getting to the core of the problem!

---

### Post by sudodus on 2016-01-02
I think there are problems with encrypted home in the versions 14.04 and 15.04. At least cryptswap does not work correctly. I'm not sure about the encrypted home, I thought it would work.

That problem was fixed in 15.10, which works correctly with encrypted home and cryptswap.

So you have two options:

1. ***Use the version 15.10*** and later upgrade to 16.04 LTS, when it will be released.

2. ***Use encrypted disk*** instead of encrypted home. You create encrypted disk during the installation. At the partitioning page of the installer, you select 'LVM with encryption'. I'm testing it right now for the alpha version of Lubuntu Xenial (to be released as 16.04 in April).

---

### Post by PopsTheSailor on 2016-01-02
Thanks for the ideas. I'll probably go with the upgrade to 15.10. Question about that though. Is there anything special I need to do  for the upgrade. Meaning. Upgrade and then create a new user. The copy the files over. Or will the upgrade just "fix" the encryption issue?

---

### Post by sudodus on 2016-01-02
I would do a fresh installation. Otherwise there may be old 'cruft' that still destroys the function of the encrypted home and cryptswap. (And encrypted disk requires a fresh installation.)

You can try to keep the content of the home directory (make a backup of it) and restore it when booted into the new system.

-o-

In general, these kinds of actions, particularly when encryption is involved, need ***good backups*** of important data. Good luck :-)

---

### Post by PopsTheSailor on 2016-01-02
One final question. I prefer to use Ubuntu/Mate. Will this have an impact on 15.10 working?

---

### Post by sudodus on 2016-01-02
I have only *tested* Ubuntu MATE. It think it should work with this encryption. But let us hope that a *real Ubuntu MATE user* will chip in and give you a better answer!

---

