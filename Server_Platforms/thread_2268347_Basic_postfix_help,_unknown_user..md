---
title: "Basic postfix help, unknown user."
date: 2015-03-08
forum: Server Platforms
---

### Post by Slatevine on 2015-03-08
Im not sure where to start reading on this one. Can someone give me some help or reading that might help me please.

I have installed postfix on my local machine (which is not an email server).
I also have mailx running. I can send email to gmail accounts with mailx, using -A to specifiy the gmail account credentials in .mailrc.
I also have an external host (Ill call it externalhost.com.au) through which I can send mail using mailx, using the url and port 25. (cant get 465 working, but that's fora another day).

I need to get sendmail working to the same external host because a program I use uses sendmail to deliver emails. 

Im confused about the part that postfix playins in mailx, if any, but more so why I cant get sendmail working. 

Ive folowed the tutorials and configured postfix using dpkg-reconfigure postfix. Main.cf now has myhostname as externalhost.com.au and mydomain as externalhost.com.au. Not sure if that's correct for what i want though.

when I try sendmail [EMAIL="someone@somedomain.com"]someone@somedomain.com[/EMAIL], the logs tell me this:

```
Gonzalez postfix/pickup[15475]: 344EF17E5004: uid=1000 from=<colic>
Mar  8 21:12:27 Gonzalez postfix/cleanup[15599]: 344EF17E5004: message-id=<20150308101227.344EF17E5004@externalhost.com.au>
Mar  8 21:12:27 Gonzalez postfix/qmgr[15476]: 344EF17E5004: from=<colic@externalhost.com.au>, size=294, nrcpt=1 (queue active)
Mar  8 21:12:27 Gonzalez postfix/local[15604]: 344EF17E5004: to=<someone@somedomain.com>, relay=local, delay=9.3, delays=9.3/0/0/0.05, dsn=5.1.1, status=bounced (unknown user: "someone")
Mar  8 21:12:27 Gonzalez postfix/cleanup[15599]: 4AA8717E5005: message-id=<20150308101227.4AA8717E5005@externalhost.com.au>
Mar  8 21:12:27 Gonzalez postfix/bounce[15605]: 344EF17E5004: sender non-delivery notification: 4AA8717E5005
Mar  8 21:12:27 Gonzalez postfix/qmgr[15476]: 4AA8717E5005: from=<>, size=2178, nrcpt=1 (queue active)
Mar  8 21:12:27 Gonzalez postfix/qmgr[15476]: 344EF17E5004: removed
Mar  8 21:12:27 Gonzalez postfix/local[15604]: 4AA8717E5005: to=<webmaster@externalhost.com.au>, orig_to=<colic@externalhost.com.au>, relay=local, delay=0.1, delays=0.07/0/0/0.03, dsn=5.1.1, status=bounced (unknown user: "webmaster")
Mar  8 21:12:27 Gonzalez postfix/qmgr[15476]: 4AA8717E5005: removed
```

colic is my Ubuntu user. 
Gonzalez is my server name.
[EMAIL="someone@somedomain.com"]someone@somedomain.com[/EMAIL] is who Im trying to send the mail to (as per the sendmail command)
[EMAIL="webmaster@externalhost.com.au"]webmaster@externalhost.com.au[/EMAIL] is the remote smtp email server Im trying to use to send the mail.

Im not really sure what this log is telling me. So Im not sure where to start looking. Several hours of trying has convinced me to ask for help ..... any advice gratefully received.

---

### Post by lisati on 2015-03-08
I've edited your post to use [noparse]```
 and 
``` instead of >  and  because it helps preserve formatting better.[/noparse]

The way I understand the log entries is that email intended for user "colic" is being redirected to user "webmaster" but it isn't working because there is no such user "webmaster." Is this redirect/alias what you intended?

---

### Post by Slatevine on 2015-03-08
OK thanks for that edit. Ill remember for next time!

No I dont want any redirects at all, nor have I deliberately set any up. I just want to be also to send an email to the external server.

---

### Post by SeijiSensei on 2015-03-09
```
Mar  8 21:12:27 Gonzalez postfix/local[15604]: 344EF17E5004: to=<someone@somedomain.com>, 
relay=local, delay=9.3, delays=9.3/0/0/0.05, dsn=5.1.1, status=bounced (**unknown user: "someone"**)
Mar  8 21:12:27 Gonzalez postfix/cleanup[15599]: 4AA8717E5005: message-id=<20150308101227.4AA8717E5005@externalhost.com.au>
Mar  8 21:12:27 Gonzalez postfix/bounce[15605]: 344EF17E5004: **sender non-delivery notification**: 4AA8717E5005

```
The account "someone@somedomain.com" appears not to exist.

If you have experience with sendmail, why not replace postfix with sendmail?  
```

sudo apt-get update
sudo apt-get remove --purge postfix
sudo apt-get install sendmail

```

---

### Post by Slatevine on 2015-03-09
I guess because im quite confused about mailx, sendmail and postfix! I thought sendmail used postfix to deliver mail. 

The above postfix log entries are generated when I use the sendmail command.

---

### Post by SeijiSensei on 2015-03-10
The original sendmail was written at Berkeley and remains in wide use today.  Postfix is an alternative SMTP server that can mimic many sendmail commands, however it is not sendmail itself. If you have never used anything other than mailx, then you should probably stick with Postfix since it comes standard with Ubuntu server.

Regardless of how you called Postfix, it is complaining that it cannot find the mailbox [email]someone@somedomain.com[/email] which it appears to think should be delivered to a local user, presumably one called "somone."

---

### Post by Slatevine on 2015-03-10
Well I have to use sendmal because the program Im using relies on it to send mail. Stil puzzled as to why sendmal causes postfix messages in the logs. Your explanation suggests its an alternate to postfix - but the logs suggest sendmail calls postfix???

Anyway, tht's a digression.

OK, so I get its trying to deliver to a local user ..... but how do I now get it (sendmail or postfix - whatever) to realise that someone isnt a local user, but part of an email address at an external smtp server at somedomain.com?

---

### Post by SeijiSensei on 2015-03-10
The program you're using probably calls sendmail with a command that postfix mimics.  If you want to use plain sendmail, follow the steps I gave you above.

If you really sent something to "@somedomain.com" that isn't going to go anywhere.  Do you have account somewhere else like GMail or the like?  If so, send a message to that account and see what happens.

---

