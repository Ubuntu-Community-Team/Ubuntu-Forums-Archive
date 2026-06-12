---
title: "Mailserver: move spam to junk folder"
date: 2012-10-01
forum: Server Platforms
---

### Post by harveyd on 2012-10-01
I have setup a mail server following these details exactly (with the exception of installing roundcube instead of horde):-

www [dot] exratione [dot] com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/

Everything is working perfectly from what I can see but need a little help with managing spam email. Currently all spam is just deleted. Instead I would like each user to have a 'Spam' folder along with 'Sent' and 'Trash' and all messages deemed as spam be moved to there.

Can anyone suggest the best method to achieve this based on my setup using the above.

Many Thanks 
Harv.

---

### Post by SeijiSensei on 2012-10-01
Install the **procmail** package and create a file called /etc/procmailrc that looks like this:

```

VERBOSE=on
LOGFILE=/var/log/procmail

:0
* ^Subject.*Spam\?
$HOME/mail/spam

```

Procmail uses regular expressions to determine what to do with messages.  In this case I'm looking for the string "Spam?" in the "Subject" header.  I use  [MailScanner]("http://www.mailscanner.info/") which adds the string "{Spam?}" to the beginning of the subject line of tagged messages.  Depending on how your system identifies likely spam messages, you'll want to use a different key.  

Rules (called "recipes" in procmail-speak) that are stored in /etc/procmailrc are executed with root privileges, but the $HOME global refers to the home directory of the user to whom the message is delivered.  So this single rule will route all spam into the corresponding user's spam folder.

You may need to modify $HOME/mail/spam to point to a different location depending on where users' mail folders are stored. 

The log file /var/log/procmail will contain the processing information for every message.

---

