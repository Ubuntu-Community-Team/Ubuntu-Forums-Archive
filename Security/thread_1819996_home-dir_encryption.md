---
title: "home-dir encryption"
date: 2011-08-07
forum: Security
---

### Post by korgash on 2011-08-07
Hi,
I was going to create a new user with an encrypted homedir and simply used `adduser --encrypt-home`, but I think it does not work. Could anybody explain this phenomenum to me? (neuerbenutzer is the user with a home-dir that should be encrypted, i guess it didn't work) I'm using ubuntu 11.
[FONT=Fixedsys]
# encfs -f .crypt/ crypt/
EncFS-Passwort:
# mount | grep encfs
encfs on /root/crypt type fuse.encfs (rw,nosuid,nodev,default_permissions)
# su neuerbenutzer
$ mount | grep encfs encfs on /root/crypt type fuse.encfs (rw,nosuid,nodev,default_permissions)[/FONT]
 
I'm quite sure nothing is encrypted if there is no mountpoint. Am I right?
Korgash

---

### Post by bodhi.zazen on 2011-08-07
You are mixing apples and oranges

Encrypting home uses ecryptfs, and next you use encfs ???

That is not how encrypting a users's home directory works.

See:

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

---

### Post by korgash on 2011-08-10
oh, now i've got it.

I encrypted my home dir, but now i cannot login again - afer suspending my laptop performed a normal boot and `ls .ecryptfs``="auto-mount  auto-umount  Private.mnt  Private.sig".  "wrapped-passphrase" is minssing. Is there any chance to recover my data? I guess not. How can this files go missing? /lost+found/ is empty.

---

