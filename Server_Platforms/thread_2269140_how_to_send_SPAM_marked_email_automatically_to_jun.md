---
title: "how to send ***SPAM*** marked email automatically to junk folder"
date: 2015-03-13
forum: Server Platforms
---

### Post by Martin_Schenk on 2015-03-13
How can i all mails in all mailboxes which are marked by spamassassin as ***SAM*** automatically send to the junk folders of each mailbox?
Is there a way to configure the server directly to do that?

As of now, i have to call the mails in a cliente like for example thunderbird and thunderbird ist doing that job. but i would like to have it automized already from the server.

---

### Post by Irihapeti on 2015-03-13
*Thread moved to **Server Platforms**.*

---

### Post by lisati on 2015-03-13
Thunderbird has filters that can be used for this purpose.

I used to do something similar when I was running a postfix server. It has been a while, and I don't have access to the server box I set it up on. If memory serves correctly, it was with a "maildrop" utility other than the default postfix component. I'm about to go out, so I'm not in a position to Google a suitable utility.

---

### Post by SeijiSensei on 2015-03-14
The "mail delivery agent" called procmail is the best solution.  Procmail uses "recipes" to determine how to deliver messages based on their characteristics.  It's possible to write system-wide recipes by putting them in a file called /etc/procmailrc.  In your case you could use a recipe like
```

:0
* ^Subject:.*SPAM 
$HOME/mail/junk

```
The ":0" denotes the beginning of a recipe. Without any qualifiers, it searches the headers for matches using the regular expression on the second line.  The third line indicates that messages with SPAM in their subject lines should be delivered to /home/username/mail/junk.  Even though /etc/procmailrc is run as root, $HOME contains the recipient's home directory.

When you first start out using procmail, you might want to include the lines 
```

LOGFILE=/var/log/procmail
VERBOSE=on

```
at the top of the file so you can make sure the recipe is working properly.  You might also want to create an archive of messages in case something goes wrong.  Here's a more elaborate version of /etc/procmailrc:
```

LOGFILE=/var/log/procmail
VERBOSE=on

:0 c
/var/mail/archive

:0
* ^Subject:.*SPAM 
$HOME/mail/junk

```

The first recipe stores a copy of every incoming message in /var/mail/archive.

There is lots of documentation on the Internet for using procmail, though I recommend reading the manual pages with "man procmailrc" and especially "man procmailex" which has many examples.

---

