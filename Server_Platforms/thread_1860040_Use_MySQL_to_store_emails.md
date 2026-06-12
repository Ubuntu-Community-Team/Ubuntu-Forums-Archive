---
title: "Use MySQL to store emails?"
date: 2011-10-14
forum: Server Platforms
---

### Post by jahservant on 2011-10-14
Greetings Ubuntu community!

I've been searching all over for how to do this, but to no avail.  I would like to use MySQL to store emails in an imap/smtp server.

All I can find is using Postfix Virtual Hosting, or using MySQL for authentication, but nothing actually uses MySQL as the storage engine.

Before anyone asks "why", I'll answer it for you:
 - MySQL, is fast, scalable, and easy to back up
 - with a cluster, I get automatic redundancy with (almost) infinite sclability
 - it's virtual, so adding/editing/etc users is easy
When the data is stored in MySQL, as opposed to a file system, I can easily replicate the data to back it up.  In a cluster environment, if a server goes down, there is no loss of data, and I can easily add servers into the cluster for more storage, redundancy, and availability.

If you have a solution that easily does all of that without MySQL, I'm all ears.  But I'm wondering if anyone has ever seen an email server setup (preferably open source) that uses MySQL as the storage engine?

I'm curious as to why it hasn't been done (or if it has, why is it so hard to find?) - I have a hard time believing people haven't asked for this before.  How does everyone else scale to thousands or millions of users? A mounted, clustered file system where the emails are stored? A dedicated server for every X users?  If I'm missing something, please enlighten me; I'm always up for learning knew things ^_^

---

### Post by ruffEdgz on 2011-10-14
I remember reading up on something like this awhile back and wanted to see if this would help you:

[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

Also, I believe you should be able to backup emails from your local system without MySQL but I will look into that some more.

Hope I find something useful for you.

---

### Post by jahservant on 2011-10-14
Looks interesting, and very complicated.  I'll have to try it tomorrow when I have more time.

I also found dbmail, and here is a setup (for Debian) that looks promising:
[http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fwww.sysadmin-blog.de%2Flinux%2Fdbmail-mysql-postfix-und-smtp-auth-unter-debian.html&act=url]("http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fwww.sysadmin-blog.de%2Flinux%2Fdbmail-mysql-postfix-und-smtp-auth-unter-debian.html&act=url")

Dovecot/Postfix/Courier are all pretty easy to setup, but once you add a DB or try combining them, things just get really messy :/  Maybe one day I'll get angry enough to create my own. Alas, time is my enemy...

Let me know if you find anything else.

P.S.: backing up email with MySQL looks pretty easy to do, but I've also seen some things where they use command-line arguments that run whenever an email is received to dump it to MySQL then delete the email on the local filesystem.  It may get the job done, but there's a huge performance hit, it's buggy, and very "hack-ish"....

---

