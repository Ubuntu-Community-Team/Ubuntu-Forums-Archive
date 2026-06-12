---
title: "[SOLVED] Server - Setting up specialty PostFix install..."
date: 2007-12-20
forum: Server Platforms
---

### Post by Kzin on 2007-12-20
Hey everyone,
Just made the switch from Slackware/Sendmail/Procmail to Ubuntu/Postfix/?MaybeProcmail?.

On one of my slack servers, I had it so anyone who used the SMTP service at all had their email forwarded to one specific email address.  SO, an email going FROM ANYONE TO ANYONE would actually go to a catchall.  The reason it was set up like this was the only server that connected to this SMTP service was a testing server for a website.  That way you could see what your website was about to send to its customers instead of actually sending it.

Well, I've made the switch to Ubuntu and am a little lost.  Does anyone have suggestions on what Postfix settings I should be messing with?  
Should I install procmail?  
Is it necessary?  
In Postfix is there a way to send all SMTP traffic, not just local, thru procmail so I can catch it like I did in Sendmail?

:guitar:

Thanks ahead of time..

---

### Post by tgilber1 on 2007-12-21
you can add the users to the /etc/aliases file

sample /etc/aliases

#<user-mail to be forward:   <user to receive forwarded email>
root:  jane
john:  jane


After editing aliases file, run the following to commands

sudo newaliases #creates update aliases database
postfix reload # forces postfix to reread the aliases database

---

### Post by Kzin on 2007-12-24
Thank you for the suggestion.  However, this does not satisfy the nuances of my question.

All email to ANYONE must forward to a single email address.  Not just [email]anyone@localhost.localdomain[/email], but [email]anyone@anywhere.domain[/email].  So email sent to [email]tgilber1@hotmaildotcom [/email] would go to the catchall just as readily.

Thanks again,
Dylan.

---

### Post by tgilber1 on 2007-12-27
> **Kzin said:**
> Thank you for the suggestion.  However, this does not satisfy the nuances of my question.

All email to ANYONE must forward to a single email address.  Not just [email]anyone@localhost.loca[/email]ldomain, but [email]anyone@anywhere.doma[/email]in.  So email sent to tgilber1@hotmaildotcom would go to the catchall just as readily.

Thanks again,
Dylan.

It looks like the luser_relay option may be what you're looking for

[http://www.postfix.org/ADDRESS_REWRITING_README.html#luser_relay](http://www.postfix.org/ADDRESS_REWRITING_README.html#luser_relay)

---

### Post by Kzin on 2007-12-27
Once again, thank you for the consideration.  It would seem that this luser deal only works for local users.  I want to also trap mail destined for outside networks.

Is there a way I can send ALL email to go to procmail?  For example, I can go...
/etc/postfix/main.cf
```
mailbox_command = /usr/bin/procmail 
```
/etc/procmailrc
```
:0
! myCatchAll@example.com
```

What that recipe does is send ALL email FROM ANYONE TO ANYONE to [email]myCatchAll@example.com[/email].  I can't get postfix to send ALL email to procmail though, only that which it destines as local delivery. 

I was experimenting with the recipient_canonical_maps as follows...
/etc/postfix/main.cf
```
recipient_canonical_maps = regexp:/etc/postfix/regMapping
```
/etc/postfix/regMapping
```
/[A-Z0-9._%-]+@[A-Z0-9.-]+\.[A-Z]+/i myCatchAll@example.com
```
But I don't think that is the intended use of the canonical maps.  Is it?  Could someone come up with some variation of that which would work?  I don't mind hacks, fudges, or frowned-upon-by-RFC methods, as this is an internal testing server only.  As long as all email is trapped I am happy.

---

### Post by Kzin on 2008-01-03
bump

---

### Post by Kzin on 2008-01-03
K, going to install Sendmail as I cannot for the life of me come up with a solution in Postfix.  Thanks anyways.

:confused::(

---

### Post by Kzin on 2008-01-04
Ok, this is partially for my own reference...
But for anyone who wants to know,
If you want to send ALL emails through your MTA to one single email address...
I used Sendmail.
Enable mailertables
in the mailertable file put in 
```
.       smtp:email@youwanttosenditto.com
```

Note the . is important.  Be wary of mail loops.

If anyone knows how to do that with postfix in as easy a manner, would love to know how.

---

