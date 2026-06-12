---
title: "securing the private folder (ecryptfs)"
date: 2010-10-27
forum: Security
---

### Post by whoop on 2010-10-27
The passphrase of the ubuntu private folder is quite easy to retrieve if you have the password of the account. It can be retrieved via:
```

ecryptfs-unwrap-passphrase /home/.ecryptfs/username/.ecryptfs/wrapped-passphrase

```

I'm wondering what the best solution is to harden this, in other words, make the private passphrase not recoverable.
if I remove /home/.ecryptfs/username/.ecryptfs/wrapped-passphrase this will work but I don't see an easy solution how to mount the folder again, that's fast enough for every day use...

This should probably be quite easy, maybe I'm overlooking something...

Any ideas?

---

### Post by movieman on 2010-10-27
> **whoop said:**
> I'm wondering what the best solution is to harden this, in other words, make the private passphrase not recoverable.

You have to be able to decrypt the key file with the password in order to get the real encryption key to access the files after you log in. The only way I can see to make it more secure would be to move the key file to a USB key or whatever so it's only accessible when you want to log in (I presume creating a symbolic link for the passphrase to the file on the USB key would work).

But then if the USB key dies, as they often do, you lose all your files.

---

### Post by whoop on 2010-10-27
OK, I think I got it. For anyone interested, if you have a private folder that you would like to harden via:
* not mounting it automatically when logging in
* making the passphrase unrecoverable using the login password

```

rm -f ~/.ecryptfs/auto-mount
ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase

```

ecryptfs-rewrap-passphrase is used to change the passphrase, you could change it to the passphrase used to encrypt you private folder or you could use a different passphrase altogether... Note: this command is not for changing the passphrase of your private data, it's for changing the passphrase used to encrypt the file containing the encryption information used for encrypting/decrypting your private data

This seems to work, for me at least. Be very careful when using ecryptfs-rewrap-passphrase as it asks for a new passphrase just once. I posted a report on this as I deemed it hazardous: [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/667331](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/667331)

Be careful when playing around with your data... cheers...

---

