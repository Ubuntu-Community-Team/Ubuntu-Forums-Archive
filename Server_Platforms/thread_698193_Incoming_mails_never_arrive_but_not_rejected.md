---
title: "Incoming mails never arrive but not rejected"
date: 2008-02-16
forum: Server Platforms
---

### Post by satimis on 2008-02-16
Hi folks,


Ubuntu 7.04 server amd64
Postfix 2.3.8
SquirrelMail version 1.4.11



I discovered the cause of the non-arrival of incoming mails to users.  The mails were not rejected.

Users have their mailbox on $HOME/Maildir.  Addtionally they have another mail_files on;

$ ls /var/mail/
Maildir  user1 user2 user3 user4 etc.

$ ls /var/mail/Maildir/
cur  new  tmp

/var/mail/Maildir/cur and /tmp are empty
/var/mail/Maildir/new having spam mails


Each time when new mails arrive the same will be added on their mail-files on /var/mail.  For such a reason the new mails never arrive on $HOME/Maildir.


When creating a new account with;

$ sudo useradd -m -s /bin/bash user100

New mail box will be created on user's $HOME/Maildir automatically.  However the first new mail to user100 will create a new mail_file on /var/mail/user100.  All later mails to user100 will be added on /var/mail/user100 (the mail_file)


Please advise where shall I check and how to fix this problem.  I don't need mail_files.  I need all incoming mails delivered on respective $HOME/Maildir.  TIA


B.R.
satimis

---

### Post by MJN on 2008-02-16
Are you using procmail to deliver the mail? (You are if you've got the default *mailbox_command = procmail -a "$EXTENSION"* directive in your Postfix config)

If so, it needs to be told where to dump it (given the departure from default). Edit /etc/procmailrc to read the following:

```
DROPPRIVS=YES
ORGMAIL=$HOME/Maildir/
DEFAULT=$ORGMAIL
```Mathew

---

### Post by satimis on 2008-02-16
Hi Mathew,


This box, an Mail Server running on Ubuntu 7.04 as Host, is used for testing, having undergone many changes and update/upgrade.  I'm a little bid confused now.  The server worked w/o problem before with all incoming mails delivered to respective $HOME/Maildir.


> Are you using procmail to deliver the mail? (You are if you've got the default *mailbox_command = procmail -a "$EXTENSION"* directive in your Postfix config)
The line is already there.

$ cat /etc/postfix/main.cf | grep mailbox_command```

mailbox_command = procmail -a "$EXTENSION"

```


On commenting out the said line, incoming mails will be delivered to respective $HOME/Maildir


> 
If so, it needs to be told where to dump it (given the departure from default). Edit /etc/procmailrc to read the following:

```
DROPPRIVS=YES
ORGMAIL=$HOME/Maildir/
DEFAULT=$ORGMAIL
```Mathew
I don't have /etc/procmailrc here.

$ sudo find / -name procmailrc
No printout


The server is running courier, applying maildrop instead of procmail, I suppose.   Maildrop works with authdaemon via courier-imap or courier-pop.  I tried tracing the notes taken down during tests and building of this server.  Unfortunately I could not find anything relevant to setup of the server, maybe too many notes.


I found;

$ apt-cache policy procmail```

procmail:
  Installed: 3.22-16ubuntu3
  Candidate: 3.22-16ubuntu3
  Version table:
 *** 3.22-16ubuntu3 0
        500 http://us.archive.ubuntu.com feisty/main Packages
        100 /var/lib/dpkg/status

```


$ apt-cache policy courier-imap```

courier-imap:
  Installed: 4.1.1.20060828-5ubuntu1
  Candidate: 4.1.1.20060828-5ubuntu1
  Version table:
 *** 4.1.1.20060828-5ubuntu1 0
        500 http://us.archive.ubuntu.com feisty/universe Packages
        100 /var/lib/dpkg/status

```


$ apt-cache policy courier-pop```

courier-pop:
  Installed: 0.53.3-5ubuntu1
  Candidate: 0.53.3-5ubuntu1
  Version table:
 *** 0.53.3-5ubuntu1 0
        500 http://us.archive.ubuntu.com feisty/universe Packages
        100 /var/lib/dpkg/status

```

running on this box.  Whether I have to remove "procmail"?  How to reconfigure Maildrop to make all incoming mails delivered to respective $HOME/Maildir?  TIA


B.R.
satimis

---

### Post by MJN on 2008-02-16
> **satimis said:**
> I don't have /etc/procmailrc here.

Create one then and you'll be good to go (and uncomment that mailbox_command that you've just commented out!).

You could remove Procmail but I'd leave it in. In a few months time you'll be asking how to do server-side filtering of messages and we'll be telling you Procmail! ;)

Mathew

---

### Post by satimis on 2008-02-16
> **MJN said:**
> Create one then and you'll be good to go (and uncomment that mailbox_command that you've just commented out!).

You could remove Procmail but I'd leave it in. In a few months time you'll be asking how to do server-side filtering of messages and we'll be telling you Procmail! 
Hi Mathew,


I got my problem fixed as advised.  Thanks

Would there be any conflict if procmail, courier-imap and courier-pop are running on the same box?


satimis

---

### Post by MJN on 2008-02-16
Not at all - they're all responsible for different aspects of 'mail handling'.

Mathew

---

### Post by satimis on 2008-02-16
> **MJN said:**
> Not at all - they're all responsible for different aspects of 'mail handling'.

Noted and thanks


satimis

---

