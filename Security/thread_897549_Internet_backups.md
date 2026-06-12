---
title: "Internet backups"
date: 2008-08-22
forum: Security
---

### Post by vlc on 2008-08-22
Hi *,

I am looking for a way to make secure backups of some of my data in the Internet. I regularly save all my data to an external hard drive, but this won't help me if my house burns down.

I would like to save some important documents as well as my password save on some kind of internet storage. To ensure that the data is not scanned or read by someone, I consider encrypting the data using GPG. But to prevent dictionary attacks, the password for GPG must use the maximum number of possible characters and the order of the characters must be absolutely random, i.e. a password that nobody can remember (at least I can't).

So I have to store the password in another web storage, saved e.g. in a password file with a weaker password that I can remember. As long as nobody can relate the two web storages, my data should be save (?).

Does anyone here in the forum has a different approach to save its data? Or do you see any weaknesses in my approach?

I appreciate any input.

Thasnk a lot in advance!

---

### Post by solitaire on 2008-08-22
Company "Spider Oak" have an online backup product. up to 2Gb is free.  

[https://spideroak.com/](https://spideroak.com/)

I use it to back up documents and my email database. not the best but it's one of the few backups that work with Linux.

Check your ISP they may give you some Webspace. Nothing saying that you can't use that to store some of your encrypted data.

---

### Post by philetus on 2008-08-24
Better yet, if you want your data to be secure, don't back it up on the web.

---

### Post by hyper_ch on 2008-08-25
well, if you are willing to pay you could (a) get an own server (starting at &#8364; 20.-) or some webhost with enough space... if you get shell access you could store the data in encrypted files....

e.g. mount the remote server/account with sshfs in your local filesystem. Create a truecrypt container and then copy data in there or sync it.

---

