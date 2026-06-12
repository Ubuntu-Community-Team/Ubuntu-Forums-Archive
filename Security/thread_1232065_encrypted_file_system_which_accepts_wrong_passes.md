---
title: "encrypted file system which accepts wrong passes?"
date: 2009-08-05
forum: Security
---

### Post by thinking on 2009-08-05
hi all

im using luks - which works great for my purpose
but just of interest im asking myself
is there a file system which can be mounted
without a password OR the wrong password?
to be more precise: i think about the idea that a user just doestn know if he entered the right password
the FS mounts either way
and maybe as a nice to have feature the FS provides access to dummy files for some passes

is there a FS with such features for linux/ubuntu?

thx all

---

### Post by Moop on 2009-08-05
Truecrypt supports hidden containers, a encrypted file system within a encrypted file system. You fill the outside container with "dummy" files and the secret stuff goes in the inside container. One password opens the outside container or a different password opens the hidden inside container. 

It works on linux.  [http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by shaggy999 on 2009-08-08
What you could do is to have two '/' filesystems. One of them unencrypted, the other encrypted. Set it up so that the encrypted partition when unencrypted is mounted on top of the unencrypted / with unionfs so that it "overrides" the unencrypted partition. Then you would just change the bootscripts so that instead of re-asking for a password when a bad password is given it just continues booting ignoring the encrypted drive.

Don't ask me how to do that though. I'm not even sure if unionfs will work on the root file system.

---

