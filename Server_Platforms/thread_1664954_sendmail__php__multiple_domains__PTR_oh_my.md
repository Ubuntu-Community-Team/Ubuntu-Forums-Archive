---
title: "sendmail / php / multiple domains / PTR oh my"
date: 2011-01-11
forum: Server Platforms
---

### Post by banditti on 2011-01-11
Here is what I have and my problem too.

I have a Ubuntu 10.04 server.  Multiple domains with multiple IP's.

I have php forms that need to send mail.  I have sendmail installed.

I have my email for said domains hosted with google apps standard.  I can send email to some domains and not others.  

I am pretty sure I need PTR/reverse DNS entries.  SPAM and all. 

My question is how to I configure sendmail to use a certain outgoing IP's so I can have a reverse DNS entry created so it will quit getting flagged as SPAM.

What am I missing?

---

### Post by SeijiSensei on 2011-01-13
> **banditti said:**
> My question is how to I configure sendmail to use a certain outgoing IP's so I can have a reverse DNS entry created so it will quit getting flagged as SPAM.

Add this to sendmail.cf:

O ClientPortOptions=Address=1.2.3.4

to force it to send on address 1.2.3.4.

You might also want to look into using [SPF records]("http://www.openspf.org/") for your domains to specify the legitimate sending host(s).

Things get tricky with mail sent from PHP forms.  By default, the SMTP envelope sender will be www-data@host.example.com unless you have some form of masquerading set up in sendmail.  You might want to consider using custom From headers in the PHP mail() command like this:

```
mail($to,$subject,$message,"From: bounce@example.com");
```

You'll need to add the apache user to the list in /etc/mail/trusted-users so PHP can rewrite the SMTP sender without generating a warning header.  

One other option is to create an entry in /etc/mail/genericstable like this:

```

cd /etc/mail
touch genericstable
echo 'www-data     bounce@example.com' >> genericstable
makemap genericstable < genericstable

```

Now sendmail should automatically rewrite mail sent by the www-data user to use bounce@example.com as the SMTP sender.  This has less flexibility than the other approach since all your domains will have their mail sent from bounce@example.com.

---

### Post by SeijiSensei on 2011-01-13
Website acting up tonight; duplicate message suppressed.

---

### Post by SeijiSensei on 2011-01-13
see above

---

