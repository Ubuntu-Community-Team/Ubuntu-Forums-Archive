---
title: "Installation of Courier is not working"
date: 2010-12-08
forum: Server Platforms
---

### Post by jchiera93 on 2010-12-08
Hello, I hav recently installed Ubuntu 10.10 32 Bit Server Edition. I am planning on making it into a LAMP server to I can run a webapage for a gaming clan and possibly webmail, if I ever get it setup. the guide that I have been following is this one found [here]("http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3-p4") (link to guide). But the thing is I do not want to create an FTP server or install ISPConfig either. So when I got to the steps for installing Postfix, Courier, Saslauthd, MySQLm rkhunter, and binutils I did all of what it told me. I then installed Amavisd-new, SpamAssassin, ad Clamav. I then move on to the step where I install Apache2, PHP5, phpMyAdmin, FCGA, suExec, Pear, and mcrypt. All of these install fine and Apache2 is working correctly. When I get to the step where h wants me to install FTPd and Quota, I skip it. I also skip the step where he wants me to install fail2ban, jailkit, Vlogger, Webalizer, and AWstats. After these steps I stopped using that guide for a while and found this guide [here]("https://help.ubuntu.com/community/MailServer"). I read the howto on installing Postfix and settings it up. I also read the "[PostfixAmavisNew]("https://help.ubuntu.com/community/PostfixAmavisNew")" (link to article) article. Now I am stuck on this article; [Courier]("https://help.ubuntu.com/community/Courier") (link to article). I have read and done everything that was told in the article but when I go to test my IMAP server I do not get the same output they get and I do not connect. This is what it should look like

```
telnet localhost imap
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2004 Double Precision, Inc.  See COPYING for distribution information.
imap login user password
imap OK LOGIN Ok.
```But... this is what my output looks like

```

Trying ::1...
Connected to localhost.localdomain.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION] Courier-IMAP ready. Copyright 1998-2010 Double Precision, Inc.  See COPYING for distribution information.
imap login ************* ********
* BYE [ALERT] Fatal error: Account's mailbox directory is not owned by the correct uid or gid:
Connection closed by foreign host.

```I am totally stuck on what to do and I have tried Google and I have found one where you change ```
IMAP_MAILBOX_SANITY_CHECK=1
``` to ```
IMAP_MAILBOX_SANITY_CHECK=0
``` But that did not work. Would anybody else know what to do here?

-Thank You


EDIT: Problem solved! :) All I did was go into /etc/passwd and saw that administrator (me) was group 1000 so I typed in ```
chown -R administrator:1000 /home/myuser/Maildir

```After that I ran a telnet and logged in and my imap login was successful :)

---

