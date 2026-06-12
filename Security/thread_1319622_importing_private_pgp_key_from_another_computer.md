---
title: "importing private pgp key from another computer"
date: 2009-11-08
forum: Security
---

### Post by kartal on 2009-11-08
Hi

I have created pgp pair on my laptop and now I want to bring it into my netbook. I copied(from laptop) and changed the permissions of .gnupg. But it the netbook does not recognize the new keys saying that there are no keys when I want to sign-encrypt a file. Is there a way to properly import private keys into the new system? I cna use import in one of those gui apps but I think that import function is geared towards importign other people`s public keys, not for transferring keys from computer to computer.


thanks

---

### Post by tubbygweilo on 2009-11-08
kartal,
What are the permissions of your .gnupg?

Mine are 
Owner - Folder Access Create & Delete.
Owner - File Access ---

Others - Folder Access None
Others - File Access ---

They work for me.

---

### Post by kartal on 2009-11-08
tubbygweilo

I have changed the ownership, there is no problem with the user rights. I suspect that this private key needs to be imported into some sort of database, so it does not work by simply copy-pasting of the private betweeen computers.

---

### Post by tubbygweilo on 2009-11-09
kartal,
The sections on [using]("http://www.gnupg.org/documentation/howtos.en.html") [keys]("http://www.dewinter.com/gnupg_howto/english/GPGMiniHowto.html#toc3")  should be of use. IIRC I have on several occasions used the OpenPgp Key Management screen within Mozilla ThunderBird to export both private and public keys as well as just copy/paste of .gnupg - I am now out of ideas, sorry.

---

### Post by kevdog on 2009-11-09
I'm not sure why just copying the keyring files are not working.  I guess you could always export the keys one by one and then import them back on a new keyring as well -- A little bit more time consuming however.

I'd copy from the .gnupg folder

trustdb.gpg
gpg.conf
pubring.gpg
secring.gpg

---

