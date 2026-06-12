---
title: "password manager with public and private keys"
date: 2009-08-08
forum: Security
---

### Post by DoppyNL on 2009-08-08
Hi people,

I'm looking for the following wich I can use on Ubuntu.
I've been searching for it, but I can't seem to find it...

An application that:
- stores my passwords encrypted
- I need a single password to access it.
- preferably can also store a description and username along with the password.
- no need for automatic password completion (for web forms or whatever)

But I also need to:
- store other people's public key, manually; I just want to put it in manually; no need for "auto update features" and stuff.
- encrypt text with other people's key (so I can email it them encrypted).
- decrypt text I receive from others who encrypted it with my public key.
This encyption process is mainly used for passing along passwords via email or msn.


What software for Ubuntu can best be used for this?
Where can I find info about it?
Any other advise regarding this?

tnx!

---

### Post by shaggy999 on 2009-08-08
For storing passwords I use revelation, which is in the repositories. It allows you to store a lot of metadata with your passwords. For storing encryption keys and encrypting text I think seahorse is the gui interface to gnupg and it manages all of that.

---

### Post by nair on 2009-08-09
I've used KeePass on my Windows XP system for a couple of months and have been very happy with it.
[http://keepass.info/](http://keepass.info/)

I'm not sure about all of it's features, but it can at least do the majority of the things you listed.  I've never used it on Linux though, but wiki says that it's possible.
[http://en.wikipedia.org/wiki/KeePass](http://en.wikipedia.org/wiki/KeePass)

Also of note, I literally just started using Linux and Ubuntu, so I've likely never heard of any password program that is Linux promoted/exclusive.

---

### Post by DoppyNL on 2009-08-16
Thanks for the feedback.

I'm now using revelation as a password manager, works perfectly :).
Easy to setup and easy to get the needed passwords! tnx!


As for the encrypting and decrypting of information. This is currently on hold, as the previous windows-tool I was using isn't capable of exporting my own private key or other people's public key. Very annoying.
I'll post back later sometime when I get that done.

tnx for the help.

---

