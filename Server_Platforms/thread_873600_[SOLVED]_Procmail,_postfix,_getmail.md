---
title: "[SOLVED] Procmail, postfix, getmail"
date: 2008-07-29
forum: Server Platforms
---

### Post by cmulcahy on 2008-07-29
First off, I apologize for the length of this post.  I think I have a Postfix problem since that is what I monkeyed with last.  

I have a fairly complex configuration.  I have a couple of domain names with one primary, call it example1.com.  I host example1.com at a hosting provider where my email collects.  I have several email addresses, one for each web site or mailing list, basically, so I can track where email came from (e.g. [email]ubuntuforums.org@example1.com[/email]).  I use getmail to pull my email locally where I run it through procmail for filtering.  I had that all working before I decided to get cute.

For no good reason, I decided to host example2.com locally myself.  I installed and configured postfix which went very easy following the HOWTOs.  I was impressed.  I started receiving email to those addresses I wanted and bouncing those I did not.  Unfortunately, my main email broke.  Getmail continued to retrieve my email but was not deleting it from my hosting provider.  My procmail log file shows:
```
procmail: Assigning "PMDIR=/home/chris/.procmail"
procmail: Assigning "LOGFILE=/home/chris/.procmail/log"
procmail: Opening "/home/chris/.procmail/log"))
  msg   7/187 (1839 bytes), delivery error (command procmail 14441 error (0, procmail: [14441] Mon Jul 28 21:18:06 2008

```
Looking up the delivery error, it would seem that postfix is erroring out on delivery which is causing the delivery to succeed but getmail fails before deleting the email from my host.  Bummer.

I think (THINK) I need a virtual setup in Postfix so I can receive example2.com email using a wildcard catch-all while continuing to receive example1.com email locally but I'm not successful so far.

Snippet from /etc/postfix/main.cf
```

mydestination = office, localhost.localdomain, localhost, example1.com
virtual_alias_domains = example2.com
virtual_alias_maps = hash:/etc/postfix/virtual
relayhost = mail.mchsi.com

```

Then /etc/aliases
```

# Added by installer for initial user
root: chris
chris: chris
postmaster: chris
postoffice: chris
MAILER-DAEMON: chris

```

Finally /etc/postfix/virtual
```

@example2.com chris

```

I run "sudo postmap /etc/postfix/virtual" and "sudo newaliases" then restart postfix and.... nothing.  Same thing as before.

Any help will be greatly appreciated.  If I need to post additional info, let me know.

Thanks in advance!

---

### Post by cmulcahy on 2008-07-29
I think the magic incantation is to change the getmailrc file.  I am testing...

```

[destination]
type = MDA_external
# change from procmail to sendmail with postfix in the picture
#path = /usr/bin/procmail
path = /usr/sbin/sendmail
arguments = ("-bm", "chris")
unixfrom = true
user = chris

```

---

