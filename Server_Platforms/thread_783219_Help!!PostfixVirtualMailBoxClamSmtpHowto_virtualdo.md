---
title: "Help!!PostfixVirtualMailBoxClamSmtpHowto virtualdomain problem"
date: 2008-05-05
forum: Server Platforms
---

### Post by exaviorn on 2008-05-05
Help!!
I have finished the greatPostfixVirtualMailBoxClamSmtpHowto at ubuntu docs.
I was really pleased with the virtual users scripts and the general problem free postfix setup,however the clamsmtp somehow did not work and I could not add virtual domains except  one:
when I tried my virtual domain login with squirrelmail I got:```
ERROR:
ERROR: Connection dropped by IMAP server.
Query: CAPABILITY
```:(

when I sent a message I checked webmin and the message had been queued in mail queue with the message:
[CODE]maildir delivery failed: create maildir file /home/vmail/hostname/user/tmp/1210013979.P2985.jumpserve: Permission denied/CODE]
Please help:confused:

---

### Post by pfsdanny on 2008-05-06
Have you configure your squirrelmail to use dovecot as IMAP server.

Check your /etc/posfix/master.cf for the setting of clamsmtp.

---

### Post by exaviorn on 2008-05-06
> Have you configure your squirrelmail to use dovecot as IMAP server.

How would I do that:confused:
P.S the first address (me@firsthostname.com)works

---

### Post by pfsdanny on 2008-05-06
cd to squirrelmail folder and run its conf

---

### Post by exaviorn on 2008-05-08
how do I run conf.pl:confused:

---

### Post by songshu on 2008-05-08
the last i did it like this

cd /var/www/squirrelmail && ./configure

and then select you imap server

---

### Post by exaviorn on 2008-05-09
I am going to try it as soon as I boot my windows machine! but would the imap server name be different for each virtualmail ? plus I only have an at host name,eg:lampserve,how do I change it to my domain?

---

### Post by songshu on 2008-05-09
where is the guide you followed?
i can't seem to find it

---

### Post by exaviorn on 2008-05-10
> **songshu said:**
> where is the guide you followed?
i can't seem to find it
Its at:[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto]("https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto")

---

### Post by exaviorn on 2008-05-10
I tried the command you gave me but I installed squirrelmail via APT-get:)

---

### Post by songshu on 2008-05-10
well the last time i installed it was via the ports tree on FreeBSD ;)

after apt-get it should give you the following message

Run /usr/sbin/squirrelmail-configure as root to configure/upgrade config.


so that would be

```
/usr/sbin/squirrelmail-configure
```

that should give you a menu where you need to select dovecot

---

### Post by exaviorn on 2008-05-10
this is what is printed when I select server (2) from squirrelmail config:
```
SquirrelMail Configuration : Read: config.php (1.4.0)
---------------------------------------------------------
Server Settings

General
-------
1.  Domain                 : trim(implode('', file('/etc/'.(file_exists('/etc/mailname')?'mail':'host').'name')))
2.  Invert Time            : false
3.  Sendmail or SMTP       : SMTP

A.  Update IMAP Settings   : localhost:143 (other)
B.  Update SMTP Settings   : localhost:25

R   Return to Main Menu
C   Turn color off
S   Save data
Q   Quit

Command >>

```
I am a bit confused:confused:

---

### Post by songshu on 2008-05-10
```

SquirrelMail Configuration : Read: config.php (1.4.0)
---------------------------------------------------------
Main Menu --
1.  Organization Preferences
2.  Server Settings
3.  Folder Defaults
4.  General Options
5.  Themes
6.  Address Books
7.  Message of the Day (MOTD)
8.  Plugins
9.  Database
10. Languages

D.  Set pre-defined settings for specific IMAP servers

C   Turn color on
S   Save data
Q   Quit

Command >> D    
```


ahum, you went for option 2, while you should have gone for option D

just```
 R   Return to Main Menu
``` like it says

---

### Post by exaviorn on 2008-05-10
oh sorry :)
I presumed that it was server settings! i set it to dovecot but it still does not work!

---

### Post by songshu on 2008-05-10
i had the same thing last week, i was driving along the motorway and the enigine just started stuttering forcing me to stop..

i quiclly called the mechanic at the garage with my cellphone and i told him
```
my car does not work!
```

strangely enough he had no clue either ;)

---

### Post by exaviorn on 2008-05-10
sorry I had not seen the D command,I thought u had to type in a number :lolflag:

The only problem is I still get:
```
ERROR:
ERROR: Connection dropped by IMAP server.
Query: CAPABILITY
```
and if I access it by thunderbird I never recive the message as it cant create the files.

---

