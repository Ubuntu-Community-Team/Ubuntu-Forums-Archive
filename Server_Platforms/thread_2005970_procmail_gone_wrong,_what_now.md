---
title: "procmail gone wrong, what now?"
date: 2012-06-18
forum: Server Platforms
---

### Post by Hawkoon on 2012-06-18
I am running an Ubuntu 12.04 server and have set up fetchmail to collect mails from two providers, and mails are filtered with procmail and written two different local IMAP directories. I use the maildir format for storing messages.

This is my .fetchmailrc
```
set postmaster "root"
set no bouncemail
set logfile fetchmail.log

## email1
poll xxx protocol POP3
user 'xxx@xxx'
password 'xxx'
ssl
fetchall
#nokeep
mda "/usr/bin/procmail"

## email2
poll yyy protocol POP3
user 'yyy@yyy'
password 'yyy'
ssl
fetchall
#nokeep
mda "/usr/bin/procmail"
```and .procmailrc
```
PATH=/usr/local/bin:/usr/bin:/bin
MAILDIR=/media/DATA/IMAP
DEFAULT=$MAILDIR/

LOGFILE=$HOME/procmail.log
VERBOSE=yes

:0
* ^To.*xxx
.xxx_in/

:0
* ^To.*yyy
.yyy_in/
```Unfortunately the IMAP folders didn't have the correct permissions when runnung fetchmail, so all incomming mail got dumped in one single file in /var/mail/mailuser (mailuser contains all the mail now and is named after the user running fetchmail), and procmail complained for every single mail with

```
procmail: Error while writing to ".yyy_in/tmp/1339963902.12840_1.sun3"
procmail: Couldn't create or rename temp file ".yyy_in/tmp/1339963902.12840_1.sun3"
procmail: Error while writing to "/media/DATA/IMAP/tmp/1339963902.12840_2.sun3"
procmail: Couldn't create or rename temp file "/media/DATA/IMAP/tmp/1339963902.12840_2.sun3"
procmail: Assigning "LASTFOLDER=/var/mail/mailuser"
procmail: Opening "/var/mail/mailuser"
procmail: Acquiring kernel-lock
procmail: [12840] Sun Jun 17 22:11:43 2012
procmail: Notified comsat: "mailuser@0:/var/mail/mailuser"
 Subject: [CS Group: Hitchhikers] july-
  Folder: /var/mail/mailuser
```The worst part is that I still had the nokeep option in the fetchmail config file, so I cant re-fetch the mails.

1) So the first thing I would like to do, make the nokeep option conditional on the successful completion of subsequent processing. Is there any way to actually achieve this?

2) Since I cannot fetch those emails again I have to work with this mailuser file. When I log into the system I get the message "You have mail." I tried mail to read my emails, however mail tells me > No mail for mailuser, and if I specify the mailfile explicitly ```
mail -f /var/mail/mailuser
``` the system tells me ```
/var/mail/mailuser: 0 messages
```I also tried to convert the mailfile to the maildir format with mb2md, but mb2md says that the file is not of the mbox format.

Why isn't any of this working, I particularly don't understand that the system tells me it has mails for me, but mail tells me otherwise. Is there anything else I could try to recover my mail?

Any help is greatly welcome

~H

---

### Post by SeijiSensei on 2012-06-18
Any recipes in /home/username/.procmailrc will be executed with the permissions of the user "username".  So you can direct messages to folders in your home directory, but you have no write privileges in /var/mail.

If you want to process messages with root permissions, then you need to put the recipes in /etc/procmailrc, which you can create using an editor with sudo.

---

### Post by Hawkoon on 2012-06-19
> **SeijiSensei said:**
> Any recipes in /home/username/.procmailrc will be executed with the permissions of the user "username".  So you can direct messages to folders in your home directory, but you have no write privileges in /var/mail.

If you want to process messages with root permissions, then you need to put the recipes in /etc/procmailrc, which you can create using an editor with sudo.

Yes, I am aware of this, I just had my target folders misconfigured, so procmail could not write to them. So instead (as a default?), procmail dumped the mails in this file ```
/var/mail/mailuser

```

My question is how can I read the mail in /var/mail/mailuser. Everytime I log into the server I get the message "You have mail.", but using the mail program or a mail conversion tool like mb2md on the mailuser file doesnt work, in fact mail tells me there is 0 mail in the file.  Does the system message upon login refer to another mail location?

---

### Post by SeijiSensei on 2012-06-20
Are you running a POP/IMAP server like dovecot?  If so, you should be able to set up your mail client to connect to the server using one of those protocols.

If you aren't running something like dovecot or imapd, then I'd suggest installing **alpine**, an excellent text-mode mail client.  Once installed, log into the "mailuser" account, then open a Terminal and type "alpine" at the prompt.  When you get to the main screen, you should be able to display the contents of /var/mail/mailuser as your inbox by typing "i" for the "index".  If that doesn't work for some reason, type "g" ("go"), enter /var/mail/mailuser when it prompts for a folder, then hit Enter.  You should see a list of the messages it contains.

---

### Post by Hawkoon on 2012-06-21
> **SeijiSensei said:**
> Are you running a POP/IMAP server like dovecot?  If so, you should be able to set up your mail client to connect to the server using one of those protocols.

Yes, I am running fetchmail+procmail+dovecot to collect mail from different providers and serve it to all my clients. It is now working as one might expect. But I am still struggling to make any sense of /var/mail/mailuser file, which was created during the very first call of fetchmail/procmail, because dovecot destination folders on my data partition were not writeable then.

> 
If you aren't running something like dovecot or imapd, then I'd suggest installing **alpine**, an excellent text-mode mail client.  Once installed, log into the "mailuser" account, then open a Terminal and type "alpine" at the prompt.  When you get to the main screen, you should be able to display the contents of /var/mail/mailuser as your inbox by typing "i" for the "index".  If that doesn't work for some reason, type "g" ("go"), enter /var/mail/mailuser when it prompts for a folder, then hit Enter.  You should see a list of the messages it contains.

I just tried alpine now but - like the mail program - cannot make any sense of /var/mail/mailuser. It expects a folder, but mailuser is a file containing catenated mails.

What actually bothers me the most at this point are the system messages "You have mail." 
If I run the mail program on my server, I get "No mail for mailuser", likewise sudo mail returns "No mail for root". So what mail is the server telling me about?

---

### Post by SeijiSensei on 2012-06-23
> I just tried alpine now but - like the mail program - cannot make any sense of /var/mail/mailuser. It expects a folder, but mailuser is a file containing catenated mails.

/var/mail/mailuser is in mbox format.  In the mbox format, the term "folder" actually means exactly the type of file you see, a set of concatenated messages separated by an extra return.  Is that not what you're using for everyone else, or are you using Maildir?  Alpine reads mbox-formatted mailboxes just fine.   Did you configure the server to use Maildir instead?  Did you try opening /var/mail/mailuser directly with the "g" command?  Are you running a POP/IMAP server like dovecot, too?

---

### Post by Hawkoon on 2012-06-23
> **SeijiSensei said:**
> /var/mail/mailuser is in mbox format.  In the mbox format, the term "folder" actually means exactly the type of file you see, a set of concatenated messages separated by an extra return.  Is that not what you're using for everyone else, or are you using Maildir?  Alpine reads mbox-formatted mailboxes just fine.   Did you configure the server to use Maildir instead?  Did you try opening /var/mail/mailuser directly with the "g" command?  Are you running a POP/IMAP server like dovecot, too?

I use the Maildir format, incoming mails are stored as individual files and dovecot serves them to my clients. All this is working fine.

Only during the very first run of procmail things went wrong and procmail decided to dump mail in /var/mail/mailuser. I did not tell procmail to do so, so this must be some kind of default.

I looked at the file with nano, it contains messages. And yes, the are indeed separated by returns.

Anyhow, I am not sure this file IS of mbox format, because I installed a mbox-2-maildir conversion tool (mb2md), and it cant open the file, telling me it is NOT of mbox standard. 

I tried the mail program, it should be able to open the file. But it say there are 0 emails in the file. The file is 700kb large, so plenty of mail in there.

---

