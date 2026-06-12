---
title: "Postfix _+ Maildir howto?"
date: 2006-03-19
forum: Server Platforms
---

### Post by sleepkreep on 2006-03-19
I'm using postfix + courier IMAP + squirrelmail to manage mail for my local users.  I however need postfix to stop using the /var/mail/$user mbox for mail storage.  I have set up a Maildir in each of the user's home directories and would like postfix to use that.  I however do not want to use any databases, postgresql or mysql, to accomplish this which is what all of the howtos say to do it.   Thanks in advance.

---

### Post by MJN on 2006-03-19
It's a while since I did this however I seem to recall there's not all that much to it i.e. merely a simple case of adding **DEFAULT=$HOME/Maildir/ MAILDIR=$HOME/Maildir  **to the **mailbox_command = procmail -a "$EXTENSION" **hence:

```
mailbox_command = procmail -a "$EXTENSION" DEFAULT=$HOME/Maildir/ MAILDIR=$HOME/Maildir
``` 
You might find the mb2md script at [http://batleth.sapienti-sat.org/projects/mb2md/]("http://www.ubuntuforums.org/ht%0Ahttp://batleth.sapienti-sat.org/projects/mb2md/") handy to convert mbox mailboxes (including all messages and folders) into maildir format - it even  builds the necessary maildir structure (if non exists) for you. If you do go down this route I'll dig out my record of a few 'gotchas' which caught me out when I went through this process.

Mathew

---

### Post by sleepkreep on 2006-03-19
Thanks for your quick reply.  It turns out you can add a line to /etc/postfix/main.cf
```
home_mailbox = Maildir/
```
This will assume to use the $USER_HOME/Maildir.

---

### Post by MJN on 2006-03-20
So it does! I'll change mine to that as it's slightly more intuitive (and memorable) for when I come to look back on the config in years to come!
 
Mathew

---

### Post by LordHunter317 on 2006-03-20
Setting home_mailbox won't work if you're using procmail.

Instead of setting those vars on the procmail command line (they're wrong anyway), it's better to create a /etc/procmailrc and set them there:```
DROPPRIVS=YES
ORGMAIL=/home/${USER}/Maildir/
DEFAULT=${ORGMAIL}
```

---

### Post by MJN on 2006-03-20
Thanks LH for the comprehensive response one comes to expect from you! ;)
 
Seriously, can you at least give me a pointer as to why the options I gave were wrong? It's puzzling me given they've been like this for around six months and so far so good! :-? 
 
Incidentally, your mention of '*if you're using procmail'* suddenly make me think... well, yes, I am - isn't everybody? Then I remembered back on RedHat when I had Postfix installed it had no such **mailbox_command** in place... I merely thought that the Debian/Kubuntu version of Postfix used procmail by default (I certainly didn't install off my own back - honest guv!) and the **mailbox_command = ....** directive was in the default main.cf so I left it there (added to as discussed when I switched from mbox to maidir).
 
However, your comment suggests that procmail is not necessary? Assuming therefore I have a choice, why did procmail get installed for me, do I really need it and, finally, can I remove it? (presumably leaving Postfix to handle the delivery?)
 
Mathew

---

### Post by LordHunter317 on 2006-03-20
[QUOTE=MJN]Seriously, can you at least give me a pointer as to why the options I gave were wrong?[/quote]MAILDIR doesn't mean what you think it does to procmail.  It means the root directory to take all other mailboxes relative to.

A sysadmin could set out of niceness for his users, but it has little value otherwise.

More importantly, setting DEFAULT isn't enough for procmail.  If delivery to DEFAULT fails, procmail trys to deliever to ORGMAIL.  By default, this is /var/mail/$USER.  We don't want delivery there, we want it to bounce the mail back to postfix.  As such, ORGMAIL must be set to ${HOME}/Maildir/ (incidentally, that's what it should say in my procmailrc, I was braindead).

> It's puzzling me given they've been like this for around six months and so far so good! :-?You won't see any problems until you hit an error case.   Setting DEFAULT is sufficent until something breaks.  Then mail 'disappears' in a regular mail spool.
 
This is all in the procmailrc manpage, but isn't obvious unless you've deeply read through it. 

> Incidentally, your mention of '*if you're using procmail'* suddenly make me think... well, yes, I am - isn't everybody?Nope.

> I merely thought that the Debian/Kubuntu version of Postfix used procmail by default (I certainly didn't install off my own back - honest guv!) and the **mailbox_command = ....** directive was in the default main.cf so I left it there (added to as discussed when I switched from mbox to maidir).Debian's postfix doesn't require procmail, but suggests it.  I've always run with it, however.
 
> However, your comment suggests that procmail is not necessary?Of course it is not.

> Assuming therefore I have a choice, why did procmail get installed for me, do I really need itIf you want any server-side filtering, you need it or an equivalent program.

> and, finally, can I remove it? (presumably leaving Postfix to handle the delivery?)Yes, just clear mailbox_command and set home_mailbox as appropriate.
 
It should already be set anyway, for the rare case when procmail borks, so the mail is bounced correctly.

---

### Post by MJN on 2006-03-20
Okay, thanks for taking the time to elaborate - it's appreciated (far more so than simply being told *I'm wrong*! :)).
 
I'm not using procmail for any server-side filtering (indeed, as mentioned, I'm only using it because it appeared to default to it - perhaps the configuration (mightily small/short if I remember correctly?) suggested it and I went with it.. who knows) so I guess I might as well remove it.
 
As I'm sure you can tell I don't know the first thing about procmail so the last thing I want is for me having to pick it up if it ever falls over... No point over-complicating things in this case.
 
Cheers,
 
Mathew

---

### Post by sleepkreep on 2006-03-24
> A sysadmin could set out of niceness for his users, but it has little value otherwise.

Yeah, that's why I'm doing it.  I have a bunch of friends that have user accounts on my machine and I thought an email system with webmail would be great for us to share messages back and forth.  Thanks for the help guys!

---

### Post by MJN on 2006-03-24
With regards to webmail I can highly recommend Squirrelmail - [http://www.squirrelmail.org/]("http://www.squirrelmail.org/") - we (family and friends) have been using it for a couple of years now and so have plenty of opportunity to thoroughly test the ins and outs of it. Very fast, doesn't hog bandwidth and plenty of 'plugins' too to customise the functionality to your needs. Works great over SSL too.

Mathew

---

### Post by sleepkreep on 2006-03-24
[QUOTE=MJN]With regards to webmail I can highly recommend Squirrelmail - [http://www.squirrelmail.org/]("http://www.squirrelmail.org/") - we (family and friends) have been using it for a couple of years now and so have plenty of opportunity to thoroughly test the ins and outs of it. Very fast, doesn't hog bandwidth and plenty of 'plugins' too to customise the functionality to your needs. Works great over SSL too.

Mathew[/QUOTE]

Yeah, that's actually what I'm using.  I meant to say web mail.  I didn't mean the interface Webmail.  
:D

---

