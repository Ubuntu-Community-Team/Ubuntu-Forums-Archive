---
title: "(UNABLE TO !) Access your private data desktop"
date: 2010-10-12
forum: Security
---

### Post by Larion on 2010-10-12
Hi,

I have a seperate partition for my "/home" folder.
Whenever I install a new distro I format my "/" folder.

This way I was able to access my old home data files since I install using a different username. Everything worked fine until last Sunday.

10.10, unlike other versions of ubuntu, has encrypted my old username in my home folder. 

Then using this document

[https://help.ubuntu.com/community/EncryptedPrivateDirectory?action=fullsearch&context=180&value=linkto:%22EncryptedPrivateDirectory%22](https://help.ubuntu.com/community/EncryptedPrivateDirectory?action=fullsearch&context=180&value=linkto:%22EncryptedPrivateDirectory%22)

I was able to mount my hard drive again. But all the file and folder names are like this.

ECRYPTFS_FNEK_ENCRYPTED.FWYlf-E9K6.TOEToYY9GtUP66EZdOW8xspGHoxOTvAkeLM2uTuud7V2A2---

ECRYPTFS_FNEK_ENCRYPTED.FWYlf-E9K6.TOEToYY9GtUP66EZdOW8xspGHWNjDTs0Mqk0kgYBjJvDcu---

How can I fix this ?

Btw I don't remember selecting an option to encrypt my old home directory in the first place, what is this ?

---

### Post by bodhi.zazen on 2010-10-12
Looks as if you have encrypted your home directory. It is an option during the installation, but it is not the default setting.

You can try to mount and back up the data (boot your old distro perhaps).

---

### Post by whistlerspa on 2010-10-21
I've just fsllen foul of this as well. I backed up my 10.04 distro files on the HDD that had 10.04 on it and then installed 10.10 to the other drive. Now i can't accesss my backed up files. The instruction to decrypt it isn't working. Thisis bloody annoying:confused::frown:

---

