---
title: "Problem with procmail.."
date: 2007-07-09
forum: Server Platforms
---

### Post by wgpayne on 2007-07-09
HI,

I've tried to set up procmail so that emails flagged as spam are placed into a spam folder. Emails that arrive normally are fine and the ~/Maildir/new/xxxxx file is owned by the user's username.

If a mail matches the spam rule, it's placed into the ~/Maildir/.spam-mail/new folder correctly but the file is created as owned by root, so the IMAP daemon throws errors when trying to read them.

Am I doing something stupid?

My /etc/postfix/main.cf launches procmail with 'mailbox_command = procmail -a "$EXTENSION"'

My /etc/procmailrc file...

```

UMASK=007
MAILDIR=$HOME/Maildir/
DEFAULT=$HOME/Maildir/
LOGFILE=$HOME/procmail.log

## filter spam
:0:
* ^X-Spam-Status: Yes
$HOME/Maildir/.spam-mail/

```

Can anyone point me in the right direction?

W

---

### Post by wgpayne on 2007-07-09
Pfff.. Ignore me..

Just found the answer [Here]("http://ubuntuforums.org/showthread.php?p=2829823").. Shouldn't have given up searching so soon..

W

---

