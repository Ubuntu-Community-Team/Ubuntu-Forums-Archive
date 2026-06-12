---
title: "How encrypted home works?"
date: 2010-10-22
forum: Security
---

### Post by marcosestevesbarbosa on 2010-10-22
Hi everybody! I'm developing a graduate project to university and here is a question: How encrypted home works? EncSF? eCryptFS? I can't  create a encrypted home to study because this may be destroy my user data partition. This is Why i ask. Sorry my English. Thanks. :)

---

### Post by linux-hack on 2010-10-22
Well you can encrypt in the command line with openssl ... 

or you could take a look at this : [http://www.linuxjournal.com/article/6481](http://www.linuxjournal.com/article/6481)
[https://blueprints.launchpad.net/ubuntu/+spec/encrypted-home-directory](https://blueprints.launchpad.net/ubuntu/+spec/encrypted-home-directory)
[http://www.linux-mag.com/id/7568/2/](http://www.linux-mag.com/id/7568/2/)

you just need to become a good friend with google :D

---

### Post by FuturePilot on 2010-10-22
[http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html]("http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html")
[http://blog.dustinkirkland.com/2009/03/ubuntu-encrypted-home-with-2-factor.html]("http://blog.dustinkirkland.com/2009/03/ubuntu-encrypted-home-with-2-factor.html")

---

### Post by BkkBonanza on 2010-10-23
Those two articles are good. But also,

You can create an encrypted home for a test user easily without worrying about your "real" data. Just **adduser --encrypt-home test**. After you're finished you can deluser again. Nothing wrong with having a second user account to play with.

You'll see,

/home/test is where the encrypted home gets mounted and some default files are created there for when the user isn't logged in.

/home/.ecryptfs/test is where the config files for the encrypted home are located. In that folder,

.ecryptfs is where the actual wrapped passphrase and config files are, and
.Private is where the actual encrypted files are located and they get mapped into /home/test by the ecryptfs driver.

What it doesn't show you is that the mounting at login is handled by the pam-ecryptfs module which is tied into the login session by /etc/pam.d/common-session. Likewise unmounting at logout (and during suspend/screensaves).

---

