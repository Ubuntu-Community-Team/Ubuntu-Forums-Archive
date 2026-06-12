---
title: "User procmailrc isnt being executed"
date: 2013-03-27
forum: Server Platforms
---

### Post by babueter on 2013-03-27
Running ubuntu server 12.04 with sendmail and spamassassin.  I have a .procmailrc to call spamc which doesnt seem to be executing.  Trying to understand where it fails.

Here is some info on my setup:

```

    $ grep procmail /etc/mail/sendmail.mc
    MAILER(procmail)dnl

    $ cat ~/.procmailrc
    ...
    :0 fw
    * < 256000
    | spamc
    
    # Mails with a score of 15 or higher are almost certainly spam (with 0.05%
    # false positives according to rules/STATISTICS.txt). Let's put them in a
    # different mbox. (This one is optional.)
    :0:
    * ^X-Spam-Level: \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
    /dev/null
    
    # All mail tagged as spam (eg. with a score higher than the set threshold)
    # is moved to spam folder
    :0:
    * ^X-Spam-Status: Yes
    Maildir/.spam/

    $ dpkg -l procmail
    +++-====================================-====================================-========================================================================================
    ii  procmail                             3.22-19                              Versatile e-mail processor

```

However, if I double check my last spam message it seems to have been skipped:

```

    $ cd ~/Maildir/cur
    $ ls -alrt|tail -3
    -rw-------  1 babueter babueter    5055 Mar 27 06:02 1364378554.M631147P7825.eldorado,S=5055,W=5156:2,
    drwx------  2 babueter babueter   90112 Mar 27 06:12 .
    drwx------ 18 babueter babueter   12288 Mar 27 06:22 ..
    $ time cat 1364378554.M631147P7825.eldorado\,S\=5055\,W\=5156\:2\, | spamc > /tmp/spam.txt
    
    real    0m0.541s
    user    0m0.000s
    sys     0m0.008s
    $ grep X-Spam-Status /tmp/spam.txt
    X-Spam-Status: Yes, score=16.1 required=4.0 tests=BAYES_99,HS_INDEX_PARAM,

```

Not sure where I'm going wrong?  This did at one time work.

Thanks in advance.

---

### Post by SeijiSensei on 2013-03-27
Add this to the top of .procmailrc:

```

LOGFILE=$HOME/procmailog

```

and see what shows up in the log.

I presume you've checked to make sure clamd is running with "ps ax | grep clamd".

---

### Post by babueter on 2013-03-27
I will add the LOGFILE option when i get home (dont have access here at work).

I'm guessing you mean spamd?  I'll verify that is running as well.  However since spamc worked from the command line manually can I assume spamd is running?

---

### Post by babueter on 2013-03-27
No dice with the LOGFILE derective in ~/.procmailrc.

procmail is definitely working because it logs to the system procmail (/var/log/procmail.log).  Here is my /etc/procmailrc file if that helps:

```
# file: /etc/procmailrc
# system-wide settings for procmail
SHELL="/bin/bash"
SENDMAIL="/usr/sbin/sendmail -oi -t"
LOGFILE="/var/log/procmail.log"
DELIVER="/usr/lib/dovecot/deliver"

# Use the following if you get "destination user parameter (-d user) not given":
DROPPRIVS="YES"

# fallback:
DEFAULT="$HOME/Maildir/"
MAILDIR="$HOME/Maildir/"
:0 w
* ^X-Spam-Status: Yes
| $DELIVER -m spam
:0 w
| $DELIVER

```

---

### Post by SeijiSensei on 2013-03-28
Sorry, yes, I meant spamd.

Are you sure .procmailrc is owned by the user in whose home directory it is stored?  Any errors in the sendmail logs?

I wonder if passing the message directly to /usr/lib/dovecot/deliver bypasses the user's procmailrc since that would mean deliver does the final delivery rather than procmail.

I do all the spam and virus checking at the SMTP level with [MailScanner]("http://www.mailscanner.info/").  Then the processed messages are handed to sendmail for delivery via procmail.

---

### Post by babueter on 2013-03-28
The only oddity with my /home permissions is that it is nfs mounted, however since mail is delivered to ~/Maildir without issue i dont think there are permission errors.  But it would be easy to swap that for a test.  I'll add that to my list of trouble shooting steps this weekend.

Would something like INCLUDERC=$HOME/.procmailrc, or SWITCHRC=$HOME/.procmailrc, be of value here?  I've never had to mess with /etc/procmailrc because it seemed to just work (ubuntu 10.04).

I use spamass-milter with sendmail, however it doesnt seem to catch anything but the obvious spam, so thats why I have spamc setup.

Thanks!

---

### Post by SeijiSensei on 2013-03-28
My home directory is NFS-mounted as well.  I wasn't talking so much about the permissions on $HOME, but on $HOME/.procmailrc itself.

Would it not be possible to merge the user-level procmailrc and /etc/procmailrc?  INCLUDERC would essentially be doing the same thing.  I have a rather complex set of procmail rules running on a server that handles listservers.  I use INCLUDERC to segregate the rules functionally to make them more manageable.

I still think the issue is handing the message to deliver in /etc/procmailrc. 

Also $HOME is a valid parameter in /etc/procmailrc; it takes on the value of the user to whom the message is delivered.  On one server I set up we had this in /etc/procmailrc:

```

:0
* ^Subject.*Spam\?
* ! X-MailScanner-SpamCheck:.*whitelisted
{
        :0
        * score=[456]\.
        $HOME/mail/maybe-spam

        :0
        $HOME/mail/likely-spam
}

```

This identified messages tagged as spam by MailScanner and delivered them to one of two folders in the user's mail directory depending on its SpamAssassin score.  (I use mbox instead of Maildir.)

---

### Post by babueter on 2013-03-28
Sorry, I did check but forgot to metion, .procmailrc is definitely owned by the user.

I went ahead and put INCLUDERC="$HOME/.procmailrc" in /etc/procmailrc and it definitely is working now.  Your probably right about handing it off to deliver, I cant remember if I copied this procmailrc from someplace or if this is from the package install.  I'm thinking I did this when I converted to Maildir because dovecot has the exact procmailrc file posted: [http://wiki.dovecot.org/procmail](http://wiki.dovecot.org/procmail)

Anyway, thank you for your time!

---

