---
title: "postfix issues."
date: 2008-01-14
forum: Server Platforms
---

### Post by wparsons on 2008-01-14
I'm trying to get postfix installed and configured, simply to send out mail from the PHP mail() function.  I've tried about 5 different ways of configuring it(with and without sasl, etc), as well as trying sendmail, all with no luck.

I'm really banging my head off the wall now, with no real ideas as to why its not working, or where to start trouble shooting.

Any help would be GREATLY appreciated!

---

### Post by mmichalik on 2008-01-14
This is a GREAT HOWTO:

[http://flurdy.com/docs/postfix/#data_add](http://flurdy.com/docs/postfix/#data_add)

I used it to set up our postfix configuration and we currently run 4 different domains out of it.

It works really well.

---

### Post by MJN on 2008-01-14
Postfix should work pretty much out of the box, certainly for outgoing mail at least.

What happens when you try and send a message?

Mathew

---

### Post by HermanAB on 2008-01-14
If you only want to send mail really simple, then you can use nullmailer.  There is nothing simpler than that.

Cheers,

Herman

---

### Post by wparsons on 2008-01-14
Nothing happens when I try to send mail..  It doesn't get to any recipients(I've tried yahoo, gmail, etc).  I'm not sure where to dig to find the errors, or if its getting spooled somewhere and why its not making it off the server.

---

### Post by MJN on 2008-01-14
I think I'd go with HermanAB's suggestion and configure it to send via your ISP. There's no point over-complicating things if this is all you need.

Mathew

---

### Post by wparsons on 2008-01-14
My ISP requires authentication on outgoing messages, will nullmailer allow that?

---

### Post by ronald.higgins on 2008-01-15
Found this link which suggests nullmailer does support smtp  authentication :

[http://ubuntuforums.org/showthread.php?t=114665](http://ubuntuforums.org/showthread.php?t=114665)

rH

---

### Post by zazuge on 2008-03-02
well I installed postfix on my home
I have a yahoo account and  I use the  587 submission port
so here's some key attributes on my /etc/postfix/main.cf file
```

smtp_sasl_type = cyrus
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl/smtp_auth
smtp_sasl_security_options = noanonymous
smtp_generic_maps = hash:/etc/postfix/generic
relayhost = smtp.mail.yahoo.fr:587

```
I use the submission port because 25 port is blocked
the noanonymous means that postifx won't use anonymous submission but cause plain text  smtp authentification in this case
beacause here 
> 
 The following security features are defined for the cyrus client SASL implementation:

Specify zero or more of the following:

noplaintext
    Disallow methods that use plaintext passwords. 
noactive
    Disallow methods subject to active (non-dictionary) attack. 
nodictionary
    Disallow methods subject to passive (dictionary) attack. 
noanonymous
    Disallow methods that allow anonymous authentication. 
mutual_auth
    Only allow methods that provide mutual authentication (not available with SASL version 1). 


and the smtp_auth
must have
smtp.mail.yahoo.fr:587 mymailaccount:mypassword

the generic file must have
username  [email]mymailaccount@yahoo.fr[/email]
username@localhost [email]mymailaccount@yahoo.fr[/email]

well I think that's all you need 
hope that will help

---

