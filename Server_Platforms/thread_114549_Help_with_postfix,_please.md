---
title: "Help with postfix, please"
date: 2006-01-08
forum: Server Platforms
---

### Post by RichSPK on 2006-01-08
I'm trying to make sure my postfix/courier-IMAP server is configured correctly before I edit my domain's zone file.  I tried logging in using telnet from another computer on the LAN and get an error (see below).  What do I need to do next?

```
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION] Courier-IMAP ready. Copyright 1998-2004 Double Precision, Inc.  See COPYING for distribution information.
a01 login uname password
* BYE [ALERT] Fatal error: Maildir: No such file or directory
```

Thanks!

---

### Post by nordmann on 2006-01-08
Hi Rich,

Something like this happened to me, too.  The problem is that the proper Maildir directory structure doesn't exist yet where it is supposed to exist (probably under the root directory of the user you are trying to send mail to).  You can fix this by hand by building a directory structure under the account you want to send to.  It should look like this:

~/Maildir
~/Maildir/tmp
~/Maildir/cur
~/Maildir/new

Another way of getting what you need is to just send an email to the user on that machine.  Even if you have to use an IP address as the domain part of the email address, this should work, I think, although I haven't tried exactly that.

---

### Post by RichSPK on 2006-01-08
It turns out there's a command called *maildirmake* that will build the directory structure for you, so I tried it in my $HOME directory:
/rich>maildirmake Maildir

That gave me /rich/Maildir along with the subdirectories.  I reloaded postfix, but that didn't fix anything.

I noticed there was a file named *rich* in /var/mail so I renamed it, figuring that it would prevent postfix/courier/procmail from creating a directory named *rich* if that's what it was trying to do.  No luck.

I'm going through lots of ".dist" configuration files and man pages right now, but haven't gotten anywhere yet.  I think I'm going to head to bed.

---

### Post by nordmann on 2006-01-10
Hmmm...are you sure you set your Postfix home_mailbox setting pointing to "Maildir/"?  That's not a misprint--you actually do need the trailing slash.

Try:

sudo postconf -e 'home_mailbox = Maildir/"

---

### Post by nordmann on 2006-01-10
You might take a look at this page of a HOWTO I've found to be quite helpful:

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p4](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p4)

Hope this helps.

---

### Post by RichSPK on 2006-01-11
[QUOTE=nordmann]You might take a look at this page of a HOWTO I've found to be quite helpful:

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p4](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p4)

Hope this helps.[/QUOTE]

That's a helpful howto, but the last instruction on the page says:
> Please go sure to enable Maildir under Management -> Settings -> EMail  in the ISPConfig web interface.
What if you weren't planning to install ISPConfig?

Also, you mentioned using *postconf* to edit postfix parameters.  I've been editing *main.cf* using *gedit*, then reloading postfix.  Do I have to use postconf, instead?

Anyway, I still don't have postfix working.  Here's a dump of the output from postconf:
[http://66.92.78.154/postconfout.txt]("http://66.92.78.154/postconfout.txt")

I'm stuck in the house with a cold today, so I'll take another look at it now.

---

### Post by RichSPK on 2006-01-11
I finally noticed that the maildir/ directory in my Home directory was spelled in all lower-case.  I changed the directory name to Maildir/ and I can now log in, via telnet, to POP3, SMTP, and IMAP ports, but all my test emails just sit in the spool file (/var/mail/rich).  Also, it won't let me log in as root.  That's not a big deal since mail to root is forwarded to rich, but I'd like to know why I can't log in as root.

Any ideas?

Thanks for all the help, Nordmann!

---

