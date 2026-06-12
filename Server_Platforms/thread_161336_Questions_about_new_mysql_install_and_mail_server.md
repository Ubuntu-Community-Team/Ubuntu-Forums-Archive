---
title: "Questions about new mysql install and mail server"
date: 2006-04-16
forum: Server Platforms
---

### Post by spyke01 on 2006-04-16
i just installed XAMPP, and i have MySQL 5.0.18, i pass protected the root account, but i have a few questions.

1. How do i add new mysql users(im sure you wouldnt put your databases in the root users section)?
2. What is a good mail server prog?
3. How can i add new email accounts for people?

---

### Post by nagilum on 2006-04-17
Well, it basically boils down to a typical RTFM reponse... if you had looked into the MySQL manual you'd have spotted the good documentation and helpful examples about user management: [http://dev.mysql.com/doc/refman/5.0/en/user-account-management.html](http://dev.mysql.com/doc/refman/5.0/en/user-account-management.html)

As for the mail server, you might want to try [Exim](http://www.exim.org) or [Postfix](http://www.postfix.org). They are both mature and rather easy to setup. If you have decided for a specific program you again should refer to the manuals since they contain all the information you asked for.

---

### Post by spyke01 on 2006-04-17
ok thank you, i skimmed through the manual, but couldnt find the right section, thanks for linking me there

---

### Post by nagilum on 2006-04-17
Uhm, what about chapter [5.9.2. Adding New User Accounts to MySQL](http://dev.mysql.com/doc/refman/5.0/en/adding-users.html)?

---

### Post by mike4ubuntu on 2006-04-20
What is the relationship between MySQL and postfix email server.  I wanted to install and test a different email server (Apache James), but IP ports conflicted with postfix (port 25 is smtp).  So, I tried to remove the postfix package:

sudo apt-get remove postfix

But, apt-get also wanted to remove MySQL and other packages:

> 
$ sudo apt-get remove postfix
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  mailx mysql-server mythtv mythtv-database postfix
0 upgraded, 0 newly installed, 5 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 11.7MB disk space will be freed.
Do you want to continue [Y/n]?


Of course, I don't want the other packages removed.

so how do I just get rid of postfix?

---

### Post by nagilum on 2006-04-20
[QUOTE=mike4ubuntu]Of course, I don't want the other packages removed.

so how do I just get rid of postfix?[/QUOTE]
Not that easily, it's a dependancy problem of DPKG. The other packages depend on a MTA to be installed, this can either be postfix, exim, sendmail or whatever, there just has to be installed one. Since Apache James is not available as a .deb package DPKG cannot know it will be installed.

The easiest solution would be to just disable postfix, remove the startup links from /etc/rc2.d/ and it will not start and therefore cannot interfere with James.

---

### Post by mike4ubuntu on 2006-04-20
Thanks, I took your suggestion on removing references for postfix in /etc/init.d/rc*.d directories, and that seems to be working ok with using Apache James.

However, I not sure why MySQL requires an MTA.

---

### Post by peanut butter on 2006-04-20
if you are more o a gui person you could try phpmyadmin

---

### Post by peanut butter on 2006-04-20
i had touninstall both and then just install mysql again. all configuration is kept intact.:D

---

