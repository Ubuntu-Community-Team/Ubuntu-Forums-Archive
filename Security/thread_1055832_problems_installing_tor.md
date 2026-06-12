---
title: "problems installing tor"
date: 2009-01-31
forum: Security
---

### Post by trilobitomorph on 2009-01-31
need to get the keys to authenticate the package.
here's what the terminal prints out:

diamorph@diamorph2-laptop:~$ sudo gpg --keyserver subkeys.pgp.net -- recv 94C09C7F
gpg: WARNING: unsafe ownership on configuration file `/home/diamorph/.gnupg/gpg.conf


how should i proceed? 
fakeroot?
using ubuntu 8.10.
a newbie.

---

### Post by tubbygweilo on 2009-01-31
trilobitomorph,
I have just looked at my gnupg folder and note that the permissions are;


Owner Access Read / Write.
Group Access None.
Others Access None.

I have sometimes noticed the problem you describe when moving or extracting files from backups and the groups or user information is not quite as expected.

Are your permissions for gnupg folder and files correct?

---

### Post by Dr Small on 2009-01-31
Here are my permissions:
```
[drsmall@darkghost ~]$ ls -la | grep .gnupg
drwx------  4 drsmall users       4096 Jan 29 09:17 .gnupg

[drsmall@darkghost ~]$ ls -la .gnupg
total 136
drwx------  4 drsmall users  4096 Jan 29 09:17 .
drwx--x--x 74 drsmall users  4096 Jan 31 08:11 ..
drwx------  2 drsmall wheel  4096 Jul 17  2008 private-keys-v1.d
-rw----r-x  1 drsmall wheel 46221 Jan  7 16:43 pubring.gpg
-rw-------  1 drsmall wheel  4254 Jan  7 16:43 secring.gpg
-rw----r-x  1 drsmall users  3160 Jan  7 16:43 trustdb.gpg
```

---

### Post by trilobitomorph on 2009-02-01
well yes they are dammit!

---

### Post by trilobitomorph on 2009-02-01
well, alrigt, i just keep pressin' refresh here for a day or two more. x-D

---

### Post by teddks on 2009-02-01
You don't use your own GnuPG configuration to add keys to Apt. You use apt-key. Your permissions are incorrect, because now they're more readable because you ran gpg as root. You should fix that.

By the way, tor is in the Ubuntu repositories, and if installing it is harder than apt-get install tor, there are probably bigger problems.

And on a side note, if you're just going to respond like "yes they are dammit" to people trying to help you, you can expect to hit refresh for many, many days before someone comes along and decides to take a swim in shark-infested waters.

---

