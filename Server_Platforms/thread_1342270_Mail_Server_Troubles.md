---
title: "Mail Server Troubles"
date: 2009-11-30
forum: Server Platforms
---

### Post by jasond496 on 2009-11-30
I'm trying to get a local fetching mailserver working, to fetch mail from my various accounts, store them on my RAID server, and distribute over IMAP (for my lan) and webmail (outside my lan).

I'm using fetchmail with a local ~/.fetchmailrc to fetch, postfix to transfer, and dovecot/squirrelmail to distribute.  My original setup used the default mbox setup with /var/mail as the spool.

Here's where the trouble comes in.  I wanted to use Procmail for filtering, and everywhere I read said I should switch to Maildir format to make everything easier.

I downloaded the [mb2md ]("http://batleth.sapienti-sat.org/projects/mb2md/") perl script and ran it to convert my current inbox to Maildir format.  I backed up /var/mail/user (it was a regular file), and then created a /var/mail/user directory for Maildir.

Now, my mail is still getting fetched.  It shows up in /var/mail/user as a "msg.*" file.  I can read files as they show up there, but dovecot is not serving anything new, and I don't believe that procmail is doing its job.

Here are my relevant config lines, dealing with paths:
```
/etc/procmailrc:
SHELL="/bin/bash"
SENDMAIL="/usr/sbin/sendmail -oi -t"
LOGFILE="/var/log/procmail.log"
MAILDIR=$MAIL/
INBOX=$MAIL/

/etc/postfix/main.cf:
mailbox_command = procmail -a "$EXTENSION"
home_mailbox = /var/mail/$USER/

/etc/dovecot/dovecot.conf:
mail_location = maildir:/var/mail/%u/

```

Like I said, I do appear to be getting my mail, they are showing up as msg.* files in /var/mail/user, but they do not appear to be going to the right place.  Can anyone shed any light on this for me?  Thanks in advance.

---

### Post by jasond496 on 2009-11-30
I've been messing around with this a bit more, and I seem to be making progress.  When I send myself test mails they are getting served up by dovecot and squirrelmail.  I am still having trouble with filtering.

Here's my procmailrc setup:
```
/etc/procmailrc:
SHELL="/bin/bash"
SENDMAIL="/usr/sbin/sendmail -oi -t"
LOGFILE="/var/log/procmail.log"
MAILDIR=$MAIL
INBOX=$MAIL/

~/.procmailrc:
LOGFILE="~/Procmail/pmlog"

:0
* ^Subject:.*test
.testing/

:0
$DEFAULT

```

Here's the log output:
```
/var/log/procmail.log:
procmail: Couldn't chdir to ""

~/Procmail/pmlog:
procmail: Unable to treat as directory ".testing"
procmail: Error while writing to ".testing"
From sender@domain.com  Mon Nov 30 18:35:42 2009
 Subject: procmail testing
  Folder: /var/mail/user/new/1259624142.12070_0.ServerName                 2747

```

So what I'm looking for in this example is to have anything with the word "test" in the subject line moved into a testing/ subfolder of my inbox.  I get the testing messages, but they are showing up in the regular inbox (Subject: procmail testing).

---

