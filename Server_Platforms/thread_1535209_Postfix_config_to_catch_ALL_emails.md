---
title: "Postfix config to catch ALL emails"
date: 2010-07-20
forum: Server Platforms
---

### Post by stevanbt on 2010-07-20
Hi,
We have a number of servers at work, some production and some non-production.  We run some java applications on these servers.  At present these java applications send emails via an SMTP connection to our live email servers.

In production all is well, the java apps send emails to customers.  However, in the non-production environments all emails must not be sent out.  Instead they must end up in some kind of generic inbox.

We don't want to mess with the production setup at all and it isn't an option to lose the non-prod emails altogether.  So on non-prod we can reference another SMTP server and send all emails there.  So far I've set up a postfix, dovecot, squirrelmail email server which appears to work. 

The question is how do I config my new email server so that any emails sent from our non-prod server to [email]fred@hotmail.com[/email], [email]bill@yahoo.com[/email], [email]jenny@gmail.com[/email] etc all end up in one inbox?

Thanks in advance, Steve.

---

### Post by cdenley on 2010-07-20
[http://www.postfix.org/postconf.5.html#always_bcc](http://www.postfix.org/postconf.5.html#always_bcc)

---

### Post by stevanbt on 2010-07-21
Hi,
I've tried adding always_bcc to the /etc/postfix/main.cf, but it doesn't allow me to send emails to other domains:-

```
250 2.0.0 Ok: queued as EEAEDEE1B8
helo
501 Syntax: HELO hostname
mail from:steve
250 2.1.0 Ok
rcpt to:steve@gmail.com
550 5.1.1 <steve@gmail.com>: Recipient address rejected: gmail.com
quit
221 2.0.0 Bye

```

Thanks, Steve.

---

### Post by lisati on 2010-07-21
If I understand the question correctly, you might want to look into [virtual alias domains]("http://www.postfix.org/postconf.5.html#virtual_alias_domains") for use on your non-production machines. Although it probably wasn't intended to be used this way, this feature can be used to redirect email for one or more specific domains to a particular email address.

---

### Post by stevanbt on 2010-07-23
Sorted it...

I created a file called /etc/postfix/virtual as follows:-

```

/.*/                        webmail

```

edited /etc/postfix/main.cf to add this line:-
```
virtual_alias_maps = pcre:/etc/postfix/virtual

```

and have tested it with ```
postmap -q test@a pcre:/etc/postfix/virtual
webmail
```

Thanks, Steve.

---

### Post by tagnu on 2010-11-08
Thank you that worked.  I had to install the postfix-pcre package too. ```
 sudo apt-get install postfix-pcre 
``` For the absolute newbies (like me), if the configuration is correct, the query command: ```
postmap -q test@a pcre:/etc/postfix/virtual
```  would return the **email id** specified in virtual file (/etc/postfix/virtual). In this case. ```
webmail
```  To test the working, use the mail command from the terminal. ```
mail testmail@example.com 
``` enter the subject, mail body and press [Ctrl+D]("http://www.gnu.org/software/mailutils/manual/html_node/Quitting-Compose-Mode.html#Quitting-Compose-Mode") (to exit the compose window).

To view the message use the following command. (webmail is the mail id configured in virtual file. Substitute with your name.)
```
mail webmail
```
 
PS:To check the mail log use the following command.
```
tail -f /var/log/mail.log 
```

---

