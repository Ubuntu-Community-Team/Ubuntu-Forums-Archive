---
title: "postfix/dovecot virtual host setup"
date: 2006-07-28
forum: Server Platforms
---

### Post by nlippincott on 2006-07-28
I have a server on which I need to process e-mail for multiple domain names, each of which may have multple mail users. The users will need to access e-mail via POP3.

After nearly two days of reading documentation and experimenting, I have succedded in receiving mail into both mbox and maildir format with postfix. Further, I have succeeded in having a POP3 server respond and authenticate users. However, I have yet to successfully deliver the mail received from postfix through dovecot and POP3.

Can anyone point me to some straightforward documentation on how to set up mail specifically for a virtual host environment?

Any help would be much appreciated.

---

### Post by nlippincott on 2006-07-28
Here's some more info, if anyone can help me...

I have postfix dropping mail for [email]mailuser@domain.tld[/email] into an mbox at this location: /var/mail/domain.tld/mailuser

The mail gets there successfully - that all works fine.

Now, I want to retrieve that mail using POP3. That's where I'm stuck. My impression is that I should use dovecot, but I just can't get it to pick up the mail from that location. Perhaps I should be using something else.

Any suggestions would be greatly appreciated. Thank you.

---

### Post by keithweddell on 2006-07-28
I got it working with these two wiki pages:

[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto]("https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto")
[https://help.ubuntu.com/community/PostfixBasicSetupHowto]("https://help.ubuntu.com/community/PostfixBasicSetupHowto")

There are also a couple of threads in this forum - iirc started by flurdy.


Keith

---

### Post by nlippincott on 2006-07-28
Thanks for passing that along, Kieth.

There's a lot of reading there, but it looks like just what I needed. I'll probably end up backing out everything I did so far and starting over - and doing it right this time.

Thanks again.

- Norm

---

### Post by nlippincott on 2006-07-29
After following the postfix set instructions, acquiring postfixadmin, and adding a couple of test e-mail accounts, I tested sending mail to the server without success. I was getting the following error message in syslog:

Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'

This was followed by numerous errors referring to a table-lookup error.

I found this posting:
[http://forums.high5.net/index.php?showtopic=347](http://forums.high5.net/index.php?showtopic=347)

This suggested changing master.cf to change all '-' entries in the chroot column to 'n'.

I did that for all entries, sent another test message, then the maildir directory was created and the mail was delivered.

If anyone knows of a reason to NOT change ALL chroot entries to 'n', please reply.

---

### Post by sputicus on 2006-10-24
> **nlippincott said:**
> After following the postfix set instructions, acquiring postfixadmin, and adding a couple of test e-mail accounts, I tested sending mail to the server without success. I was getting the following error message in syslog:

Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'

This was followed by numerous errors referring to a table-lookup error.

I found this posting:
[http://forums.high5.net/index.php?showtopic=347](http://forums.high5.net/index.php?showtopic=347)

This suggested changing master.cf to change all '-' entries in the chroot column to 'n'.

I did that for all entries, sent another test message, then the maildir directory was created and the mail was delivered.

If anyone knows of a reason to NOT change ALL chroot entries to 'n', please reply.

Some argue that postfix does not need to be run in a chrooted environment since it is secure enough. That may be true, but it is hard to prove any program is secure; you can only say an exploit for the program has not been found yet.

You can run in a chrooted environment and still have postfix communicate with mysql if you set the "hosts = 127.0.0.1" in the  configuration file which will have postfix use TCP rather than the unix socket to communicate with mysql. I just posted to the following thread with more details:

[http://www.ubuntuforums.org/showthread.php?p=1656729#post1656729](http://www.ubuntuforums.org/showthread.php?p=1656729#post1656729)

---

