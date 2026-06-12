---
title: "sendmail relay configuration ... something's wrong through php mail() function"
date: 2006-09-27
forum: Server Platforms
---

### Post by gix on 2006-09-27
Hi all!
I've spent all day under sendmail and php conf docs but I can't find a solution to my problem...

I've added to my /etc/mail/sendmail.mc the following lines:
define('SMART_HOST', 'my.smtp.server')

and, in the php.ini I've added the line:
sendmail_path=/usr/sbin/sendmail -t -i

But when I'm testing this little php code:

```

$recpt = "rcpt@mail.com";
$subject = "test subject";
$body = "the body!";
$from = "from@mail.com";
mail("$recpt","$subject", "$body", "FROM: $from");

```

I see, through the smtp mail server that the header contains the followin FROM: [email]www-data@linux.mydomain.com[/email]

And the sending is aborted (relay is denied out of our domains to prevent spammers...)

How can I remove this line?

thanks
g

---

### Post by chrisfay on 2006-09-27
> And the sending is aborted (relay is denied out of our domains to prevent spammers...)

I'm assuming then that your mail server is not on the same machine as the one you are trying to send mail from since relaying would not be an issue. 

Do you have access to the mail server to add your IP for relaying? Can you authenticate with the server using smtp_sasl_auth? I used the smtp_sasl_auth to authenticate with my Comcast mail server to relay mail from my Postfix server that was being blocked by Hotmail.

> I see, through the smtp mail server that the header contains the followin FROM: [email]www-data@linux.mydomain.com[/email]

This is correct. Since you are using a PHP script to send mail it is being executed through Apache and therefore the daemon account www-data. You will not be able to remove this line, and it wouldn't do you any good as its your domain/IP thats blocking you from relaying. You would have to add either your IP/domain to the mail server or configure some type of authentication. Adding a 'Smart Host' is not enough, which you already have found out through your mail being blocked from relaying.

---

### Post by MJN on 2006-09-28
There is no reason why a mail sent with PHP through Apache must be sent www-data on the From line. Defining the From: header in the PHP function to be whatever you want is perfectly valid (just as you would with a 'normal' e-mail client).
 
However, given you've munged the domains I can't really help you pin-point the cause of the problem further (for example, is linux.mydomain.com 'your' domain as far as Sendmail is concerned?), and we could also do with seeing your sendmail config.
 
Can you post a verbatim copy (copy-and-paste as otherwise we could be chasing red herrings) of an example e-mail sent (i.e. one sent to yourself) along with the mail log?
 
Mathew

---

### Post by chrisfay on 2006-09-28
> There is no reason why a mail sent with PHP through Apache must be sent www-data on the From line. Defining the From: header in the PHP function to be whatever you want is perfectly valid (just as you would with a 'normal' e-mail client).

This is true, I did not mean that you can't change the headers option in the php script; of course you can change it to whatever you want but it has no effect on allowing/dissalowing mail relaying; the domain/ip does (unless using some type of authentication). 

From my experience, [email]www-data@yourdomain.com[/email] will always show up in the 'Return-Path:' and if 'yourdomain.com' is not listed within the mail server's relay allowance, it will get blocked; regardless of how you change the headers in your PHP script.

The www-data portion of the email headers is not casuing the relaying problem.

---

