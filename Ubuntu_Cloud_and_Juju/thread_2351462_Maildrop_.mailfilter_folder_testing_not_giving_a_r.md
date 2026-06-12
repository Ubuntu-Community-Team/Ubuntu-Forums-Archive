---
title: "Maildrop .mailfilter folder testing not giving a return code"
date: 2017-02-03
forum: Ubuntu Cloud and Juju
---

### Post by David_Goodnature on 2017-02-03
[COLOR=#5230E1][FONT=Menlo]
Postfix - Courier - Spamassassin - CLAVAV - Maildrop

Mail is delivered fine to users maildir.
Beginning to add folder creation tests:


[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# THIS FILE REQUIRED IN EACH VIRTUAL DOMAIN DIR[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Make needed Directories[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# Deliver to Inbox or Spam box (create spam box if it does not exist)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#5230E1][FONT=Menlo]# commands and variables for making the mail directories[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]maildirmake=/usr/bin/maildirmake[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]mkdir=/bin/mkdir[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]rmdir=/bin/rmdir[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]MAILDIR=$DEFAULT[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo][COLOR=#000000]logfile [/COLOR]"/var/spool/mail/virtual/xxxxxx.com/.maildrop.log"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo][COLOR=#000000]log [/COLOR]"=========="[/FONT][/COLOR]


[COLOR=#5230E1][FONT=Menlo]
### .Junkmail[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Junkmail_FOLDER=.Junkmail[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]_Junkmail_DEST=$MAILDIR$Junkmail_FOLDER/[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo][COLOR=#000000]log [/COLOR]"Junkmail Destination: $_Junkmail_DEST"[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo]'test -d $_Junkmail_DEST'[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo][COLOR=#000000]log [/COLOR]"RETURN CODE: $RETURNCODE"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]if ($RETURNCODE != 0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]{[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo][COLOR=#000000]    [/COLOR]'$maildirmake $_Junkmail_DEST'[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo][COLOR=#000000]    [/COLOR]'echo INBOX.Junkmail >> $MAILDIR/courierimapsubscribed'[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo][COLOR=#000000]    log [/COLOR]"Spam folder missing.  Created."[/FONT][/COLOR]
[COLOR=#000000][

folder is not being made. RETURNCODE appears to be empty. I added to log hoping that would show something:

[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]==========[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Junkmail Destination: /var/spool/mail/virtual/xxxxxx.com/bobh/.Junkmail/[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RETURN CODE: [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Date: Fri Feb  3 12:51:27 2017[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]From: "Fidelity Life" <Edward@mun.aiogis.cu.cc>[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Subj: Less info for more quote[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]File: /var/spool/mail/virtual/sbfnet.com/bobh/

it appears the test is not being recognized. 
Any help would be appreciated.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]

[/FONT][/COLOR]

---

