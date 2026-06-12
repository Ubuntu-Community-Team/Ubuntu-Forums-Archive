---
title: "Mail server setup woes"
date: 2014-05-23
forum: Server Platforms
---

### Post by david217 on 2014-05-23
I'm following this guide:
[https://wiki.archlinux.org/index.php/Simple_Virtual_User_Mail_System](https://wiki.archlinux.org/index.php/Simple_Virtual_User_Mail_System)

and I am able to send email from the roundcube client but not receive. I get an email back to the sender (my gmail) stating:
```
This is the mail system at host MYDOMAIN.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<[EMAIL="sysadmin@cmanagement.biz"]sysadmin@MYDOMAIN[/EMAIL]>: mail for MYDOMAIN loops back to myself

```


I'm able to post any relevant config files/logs as needed. Any help is greatly appreciated.

---

### Post by devine.steve on 2014-05-23
What do you get when you run ?> telnet localhost 25

---

### Post by david217 on 2014-05-24
> **devine.steve said:**
> What do you get when you run ?```
&#9484;&#9472;&#9472;[sysadmin@ubuntu-server|~]&#9492;&#9472; $ telnet localhost 25Trying ::1...Connected to localhost.Escape character is '^]'.220 MYDOMAIN ESMTP Postfix (Ubuntu)
```Also works when I do telnet MYDOMAIN 25.

---

### Post by lisati on 2014-05-24
Is "MYDOMAIN" a domain that your copy of postfix is meant to handle?

The error "loops back to myself" can happen when you have an A record or MX record for your domain, but Postfix isn't configured to accept mail for your domain. You might want to check that the [mydestination]("http://www.postfix.org/postconf.5.html#mydestination") parameter in Postfix's main.cf file includes your domain. (....or virtual_mailbox_domain as appropriate)

---

### Post by david217 on 2014-05-24
> **lisati said:**
> Is "MYDOMAIN" a domain that your copy of postfix is meant to handle?The error "loops back to myself" can happen when you have an A record or MX record for your domain, but Postfix isn't configured to accept mail for your domain. You might want to check that the [mydestination]("http://www.postfix.org/postconf.5.html#mydestination") parameter in Postfix's main.cf file includes your domain. (....or virtual_mailbox_domain as appropriate)I had mail working both ways earlier in the install, before all the virtual user stuff.I did some experimenting, and if I make mydestination contain only localhost I get this email response:: User unknown in virtual alias tableHere's my main.cf:[http://pastebin.com/PHDMuZSS](http://pastebin.com/PHDMuZSS)

---

### Post by david217 on 2014-05-24
Also I know that the user exists as I can see it in postfixadmin and can login as it with telnet localhost imap.

---

### Post by lisati on 2014-05-24
If Postfix is telling you that it can't deliver a message to some-user@MYDOMAIN because it "loops back to myself" it usually means that Postfix needs to be told to accept mail for MYDOMAIN. 

If you're using UNIX system accounts to identify user, try adding MYDOMAIN to the mydestination line in main.cf and restarting postfix.

If you're using virtual domains, take a look here: [http://www.postfix.org/postconf.5.html#virtual_alias_domains](http://www.postfix.org/postconf.5.html#virtual_alias_domains)

---

### Post by david217 on 2014-05-25
> **lisati said:**
> If Postfix is telling you that it can't deliver a message to some-user@MYDOMAIN because it "loops back to myself" it usually means that Postfix needs to be told to accept mail for MYDOMAIN. If you're using UNIX system accounts to identify user, try adding MYDOMAIN to the mydestination line in main.cf and restarting postfix.If you're using virtual domains, take a look here: [http://www.postfix.org/postconf.5.html#virtual_alias_domains](http://www.postfix.org/postconf.5.html#virtual_alias_domains)As mentioned before I'm using virtual domains. It was working fine before with regular system accounts but isn't now that I've switched to virtual.I posted my main.cf a few posts back, if you don't mind taking a look.Depending on what I comment and uncomment out I get either the 'loops back to myself' error or the 'user unkown etc etc' error.Thank you.

---

