---
title: "Is it possible to have some folders stored encrypted on hard drive?"
date: 2007-12-30
forum: Server Platforms
---

### Post by legolas_w on 2007-12-30
Hi
Thank you for reading my post.
I have a laptop with Ubuntu 7.10 installed and I am looking for a solution for the following problem.

I have some folders with sensitive information stored on them and I want to encrypt those folders, I need the linux to ask the decryption password each time I(others) want to access that folder, is it possible in Linux?

I can not rely on permission mechanisms because some one can take out the hard drive and  restore the information using another linux installation.

Also, I want to avoid the encrypted partition if possible as they are open to theft as you mount them and forget to unmount it when you leave your desk for some moments.


Thanks.

---

### Post by icheyne on 2007-12-30
Either Truecrypt or GPG should fit your needs.

---

### Post by wheredidrealitygo on 2007-12-30
You want "Cryptkeeper", a program that will (according to this page at least) be included in the next version of Ubuntu Hardy in the Universe Repo.

[http://packages.ubuntu.com/hardy/admin/cryptkeeper]("http://packages.ubuntu.com/hardy/admin/cryptkeeper")

It does exactly what you asked for. Not encrypting another partition, and asks for a password every time you try to mount the folder.

I have tried it and it works well.

You may have to add your user account to the "fuse" group, and then restart in order to be able to use the program properly.

---

### Post by The Cog on 2007-12-31
This howto describes installing encfs, which is what cryptkeeper will use in the next Ubuntu release:
[http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)

---

### Post by kevdog on 2007-12-31
You could also just use plain old gpg with a symmetric rather than asymmetric encryption mechanism.  The interface is from the command line so its not very sexy, however I dont think any packages need to be installed.  A wide variety of ciphers can be used to perform the encryption.  If you need any specific instructions let me know, its actually very easy.

---

### Post by HermanAB on 2008-01-01
The new standard is dm-crypt LUKS and it is configured using the package cryptsetup.  So, I think you need to install cryptsetup, read the man page and go from there.

Cheers,

Herman

---

### Post by kevdog on 2008-01-01
OK, Im gaim -- how does dmcrypt and LUKS (which seems to be a higher level program than dmcrypt) differ from truecrypt??  Im asking this b/c on one website I was reading, it said that dmcrypt LUKS use would in the future be available through TrueCrypt.

Additionally, just for encrypting a few files (rather than volumes), its seems like this solution, as well as true crypt is a little bit overkill.  Why not just use gpg if all you need is a few individual files.  

Both truecrypt and gpg are cross-platform compatible (important for me).

---

