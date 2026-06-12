---
title: "postfix"
date: 2011-04-22
forum: Server Platforms
---

### Post by num on 2011-04-22
so i got postfix installed but how does it exactly store the emails? I found that it stores them in /var/mail but I am not sure in what format.

---

### Post by bmathis on 2011-04-22
You should think about using Maildir instead of mbox change home_mailbox to Maildir:> home_mailbox = Maildir/

The "format" that are asking about doesn't matter, since you'll need to use a mail client to access the email via POP or IMAP

[Postfix info]("https://help.ubuntu.com/community/Postfix")

---

### Post by num on 2011-04-22
well the reason i am asking is to figure out how would i go about making sure it is backed up and how to restore the emails in case something goes wrong.

should i use maildir or maildir++?

---

### Post by HermanAB on 2011-04-23
Howdy,

IMHO, Postfix is a very old, primitive and arcane mail server, only marginally better than Sendmail. 

You could do much better with Zimbra or Citadel, both of which use a database backend. Citadel is in the repos.  The advantage of Citadel is that you get a complete working system out of the box, then after that, you can go on and customize it with a different skin or change the web server completely for Roundcube or whatever you fancy.  It is very mature and supports all mail protocols ever invented.

---

### Post by TheFu on 2011-04-23
> **HermanAB said:**
> Howdy,

IMHO, Postfix is a very old, primitive and arcane mail server, only marginally better than Sendmail. 

You could do much better with Zimbra or Citadel, both of which use a database backend. 

I hope you realize that Zimbra uses postfix as the MTA in their system.

---

### Post by TheFu on 2011-04-23
> **num said:**
> well the reason i am asking is to figure out how would i go about making sure it is backed up and how to restore the emails in case something goes wrong.

should i use maildir or maildir++?

Normal file-based backups work for mail too.  Nothing special is needed unless you run something to put them into a DBMS.

I run Zimbra servers and use file-based backup for them too.  For a high volume mail system, you'll want to have protected storage and strongly consider using LVM snapshots for your backups, but for a small business, file-based backups work just fine.  Not all email is stored in /var/spool/mail  Some is stored in user HOME dirs.  The spool dir is used for inbox messages. IMAP servers can store the messages in a number of locations or even in a DBMS, so you'll want to ensure consistent backups. How to accomplish tthat depends on the DBMS used.

---

### Post by HermanAB on 2011-04-23
As pointed out above, Zimbra uses Postfix as the SMTP front end, but it replaces the poorly designed back end of Postfix through LMPT with a database engine.

The main advantage of a database for mail storage is that the system will only save one copy of a message addressed to multiple recipients, which can save oodles of disk space.

---

### Post by elico on 2011-04-24
Citadel or what ever....
try to telnet any ISP mail server and see what is the Mail server welcome message..
almost any organization that uses some unix\linux system is using postifx as mta.
leave alone Debian that choose exim and others that choose  Qmail.
all of them have almost the same options and the main thing between them is the way the are constructed and used.
in our days to save space on email system unless you have a very primitive system without san\nas is almost useless.
the main problem is not the duplicates or multiple recipients but SPAM!

well it's from my experience.
if you do have some other experience i would like to hear about it.

---

### Post by num on 2011-04-24
> **TheFu said:**
> Normal file-based backups work for mail too.  Nothing special is needed unless you run something to put them into a DBMS.

I run Zimbra servers and use file-based backup for them too.  For a high volume mail system, you'll want to have protected storage and strongly consider using LVM snapshots for your backups, but for a small business, file-based backups work just fine.  Not all email is stored in /var/spool/mail  Some is stored in user HOME dirs.  The spool dir is used for inbox messages. IMAP servers can store the messages in a number of locations or even in a DBMS, so you'll want to ensure consistent backups. How to accomplish tthat depends on the DBMS used.

i thought that postfix was the only one that dealt really with the email, the imap or pop software, dovecot, courier only allowed connecting the server and downloading it no?

i got mysql running on the system, is it possible to set up the database in the /etc/mail/ folder and have all emails stored in there?

also i found this guide as to how to setup multiple users:

[http://www.debian-administration.org/articles/243](http://www.debian-administration.org/articles/243)

but if it is using local users how can i create those users securely cause the server will be used to do more than just email.

---

### Post by num on 2011-04-24
anyone?

i tried editing the main.cf file to add the virtual names via webmin but everytime i do it, it just starts to hang up webmin continues to load up but it never loads the postfix module back up again.

---

### Post by TheFu on 2011-04-26
> **num said:**
> anyone?

i tried editing the main.cf file to add the virtual names via webmin but everytime i do it, it just starts to hang up webmin continues to load up but it never loads the postfix module back up again.

I don't use webmin. Sorry.
There are different ways to add email accounts to a system. How you do that depends completely on your goals and available tools. Do you want
* local users with email
* virtual users with email  (DBM/gdbm/mysql/postgres)
* imap via dovecot or some other 
* Zimbra or some other all-in-one communications system

There are how-to guides to accomplish each of these methods on the internet, so it doesn't make sense to repeat them here.  Here's what a quick search found [http://www.howtoforge.com/installing-courier-imap-courier-authlib-maildrop-fedora-redhat-centos](http://www.howtoforge.com/installing-courier-imap-courier-authlib-maildrop-fedora-redhat-centos)  Even if it isn't Ubuntu-based, most admins will be able to translate between RPM and APT package managers. Here's a Debian version [http://www.howtoforge.com/virtual-users-with-postfix-dovecot-mysql-roundcube-iredadmin-on-debian-6-squeeze](http://www.howtoforge.com/virtual-users-with-postfix-dovecot-mysql-roundcube-iredadmin-on-debian-6-squeeze) for a slightly different result.

Lastly, if you find a how-to, don't stop with just that. It is very likely they didn't secure the box sufficiently to be placed on the internet. That's the difference between a professional administrator and someone blindly following a guide.

---

### Post by PhillSlevin on 2011-04-27
This is very well documented in the following tutorial: [http://workaround.org/ispmail/lenny](http://workaround.org/ispmail/lenny)

---

