---
title: "eCryptfs private folder advice needed please"
date: 2010-01-03
forum: Security
---

### Post by dogdo on 2010-01-03
Hi
 

I just made a new private folder using eCryptfs on a already existing 9.10 user account. That is the private folder was not made during the live cd installation but after.
I already used sudo to not automatically decrypt the private folder when i log in-but how do i change the password?-at the moment the password is the same as my login passphrase
 

I have read that the default encryption strength is AES 128 bit-is this correct and if so how secure is this?
 

Also if i had reinstalled ubuntu 9.10 in the first place with the option to “Require a password to log in and decrypt your home folder” would the entire home folder be encrypted-including desktop, downloads and music?

---

### Post by BkkBonanza on 2010-01-03
I believe to have a separate passphrase for the encrypted home you have to configure it that way when setting up with ecryptfs-setup-private. It is the -w option that enables using a separate passphrase.

You may also be able to force it to use a second passphrase with the ecryptfs-rewrap-passphrase command. But backup your passphrase file first just in case that doesn't work right and you need to revert. The passphrase is encrypted and stored in /home/.ecryptfs/<user>/.ecryptfs/wrapped-passphrase. I haven't tried this so I'm not sure what the behaviour is at login when the login password doesn't work - it would have to prompt again for the correct one, but maybe it just fails.

The install option for decrypting your home would encrypt the entire home. There is a way around that if you don't want it all encrypted. The way I do it is to put the directories I don't want encrypted elsewhere and symlink them into my home. I have found it handy to put them in "/home/.ecryptfs/<user>/".

With any of this stuff the guy to ask is Dustin Kirkland on his blog,
[http://blog.dustinkirkland.com/](http://blog.dustinkirkland.com/) he is the Ubuntu dev handling this.

---

