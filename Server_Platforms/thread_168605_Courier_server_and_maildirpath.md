---
title: "Courier server and maildirpath"
date: 2006-04-30
forum: Server Platforms
---

### Post by Flannel on 2006-04-30
I'm setting up a local IMAP server, and have installed Courier (and -imap, -ssl, etc).  The first thing that I noticed was that all of the mail utilities (or at least the ones I've used) still use ~/Maildir as their default ([instead of ~/.maildir]("https://wiki.ubuntu.com/MailStorageStandardisation")).
So, when I went to change everything to the hidden file, I found that it wasn't possible to change Couriers MAILDIRPATH.  I've changed both lines in imapd and imapd-ssl (MAILDIRPATH=.maildir) and restarted via init.d, but my imap server still serves the mail in ~/Maildir.

Obviously I'm missing something.  But I can't find any documentation on the configuration file.

Edit:
It's been explained to me that the page I linked was only a suggestion/proposal.  But so that explains why nothing is already configured that way.  However, my inability to change the IMAP mail path still remains.

---

### Post by nagilum on 2006-05-01
There's a third (not so obvious, not to say stupid) place where the MAILDIRPATH is defined: /etc/default/courier. The setting there overrides that in /etc/courier/imapd.conf.

---

