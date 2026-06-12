---
title: "procmail delivering new emails into new separate folders"
date: 2010-12-15
forum: Server Platforms
---

### Post by balia on 2010-12-15
Ever since I set up procmail filtering, all new emails are delivered into a new folder (e.g. msg.XxX) and skip the inbox.

I tried to set LASTFOLDER=INBOX in procmailrc but to no avail.

My procmailrc file is:
PATH=/usr/bin:/usr/local/bin
LOGFILE=/var/log/procmail.log
MAILDIR=$HOME/mail
DEFAULT=$HOME/mail
LASTFOLDER=INBOX
VERBOSE=on

:0H
* ^From.*-bounce
{
 :0:c
 mymailbox

 :0:
 | /home/mydomain/public_html/script.cgi
}


How do I make procmail deliver to the inbox and not create a new folder for every new email?

BTW, the filter I have setup fails to pipe to script.cgi

Any help would be appreciated.

---

### Post by SeijiSensei on 2010-12-15
I see a couple of issues.

First, I doubt you can write a log file in /var/log since procmail runs with your user privileges.  Write the log into $HOME.

Next, if you specify the DEFAULT as $HOME/mail, that where messages will be delivered if they don't match any rules.  You don't tell us what type of mail system this is.  If you're using something that stores mail in maildir format, then each message that doesn't match a rule will be placed in a separate file in $HOME/mail.  If you're using mbox formats, and $HOME/mail is a directory, I'm not sure what will happen.  I use mbox and let all the inbound messages be delivered to /var/spool/mail/username which is typically the default inbox unless you override it in .procmailrc.

Next, you don't really tell us what the CGI script does, so it's hard to know whether it's the source of the problem.  Do you have permissions to execute the script?  Have you tested it from the command line?

---

### Post by balia on 2010-12-15
Thank you for your reply.

I have root privileges on the server. So permissions are not a problem.

Effectively, the messages go in $HOME/mail but each new message is put into a new sub-directory instead of going into the inbox directory. As a consequence, if I check the mailbox from horde, the inbox folder is always empty and below it dozens of new folders appear each one containing a new email.

I use postfix as the mail server.
Until your reply I wasn't aware of the 2 models: maildir vs. mbox
Does postfix uses mbox by default?

One post suggests the following:
Add home_mailbox = Maildir/ in main.cf
In /etc/procmailrc, set 
DROPPRIVS=YES
ORGMAIL=/home/${USER}/Maildir/
DEFAULT=${ORGMAIL}

The test script is just for testing right now: it reads the email message and appends it to a file in the home directory.
This way, I can check that the script has been executed by just looking at the file size: currently zero.
The script has been tested successfully on a different server.

---

### Post by balia on 2010-12-26
For anyone else who may encounter this issue, I solved the email delivery issue in postfix and procmail.
It took me almost an entire week to get there!
Thank you for SeijiSensei for pointing me in the right direction.

1) In /etc/procmailrc, you must have:
DEFAULT=$HOME/Maildir/
MAILDIR=.

2) In /etc/postfix/main.cf, set
mail_location = maildir:~/Maildir

I still have to resolve the procmail filter ...

---

