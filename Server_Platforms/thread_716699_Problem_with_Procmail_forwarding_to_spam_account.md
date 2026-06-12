---
title: "Problem with Procmail forwarding to spam account"
date: 2008-03-06
forum: Server Platforms
---

### Post by jprealini on 2008-03-06
Hi... I am experimenting with procmail and spamassassin. This is my need, and my problem. I have set up spamassassin to mark all spam mail, and it´s working great, but all marked spam (*****SPAM***** in header) is being received by the users. So I tried to set up a configuration where,  using procmail, all mail marked as SPAM could be sent to a spamking account, where I can process it, and from there train Bayesian filter.

Now, this is my procmailrc file:

[FONT="Courier New"]
**********************************
/PATH=/usr/bin:/bin:/usr/local/bin:.
MAILDIR=$HOME/Maildir
DEFAULT=$MAILDIR/
SPAM=/home/spamking/Maildir/new
/usr/bin/maildirmake /etc/skel/Maildir
DROPPRIVS=yes

:0fw
| /usr/bin/spamassassin

#Recipe 7
#Borrar extensiones
:0 B
        * Content-Disposition: attachment
        * name=.*\.(com|exe|pif|scr|bat|lnk|shf|vbs|wmv|pps|mov)
        {
                # Stick it somewhere
                :0 B:
                /dev/null
        }

## option 2.2: delete spam with 15 points or more; save rest in subfolder
:0
* ^X-Spam-Level: \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
/dev/null

:0
  * ^X-Spam-Flag: YES
  $SPAM

***************************[/FONT]

The last recipe is supposed to send SPAM marked mails with less than 15 points to the MAILDIR folder in the spamking account... No matter what changes I make, mail is not being sent there.... 

I tried changing it like this:

[FONT="Courier New"]
****************************
:0
  * ^X-Spam-Flag: YES
   ! [email]spamking@domain.com[/email]

****************************
[/FONT]

But the problem is that when procmail sends the email to the account, those mails go into a loop (spamassassin takes them again, marks them, and the recipe sends them again to spamking account.... CPU usage and load in the server goes to the roof!!!! )

Any ideas??? Thanks in advanced

---

### Post by MJN on 2008-03-06
I'm no procmail expert, but I have a working installation similar to yours (although I just filter all spam-tagged mail into a sub-folder) and here is my config if it helps:
 
```
DROPPRIVS=YES
ORGMAIL=$HOME/Maildir/
DEFAULT=$ORGMAIL
 
:0:
* ^X-Spam-FLAG: YES
$HOME/Maildir/.Spam/
```
 
Briefly comparing with yours I see your destination lacks a trailing slash hence it may well be trying to save the message in MH format. Try a trailing slash to imply it's a maildir format (and indeed given this drop the *new* also as it's not required).
 
Mathew

---

