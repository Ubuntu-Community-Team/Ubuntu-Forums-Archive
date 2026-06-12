---
title: "PostFix problem SMTP"
date: 2013-11-02
forum: Server Platforms
---

### Post by giroux.oli on 2013-11-02
Hi I'm new in the forum .... and sorry for my english I'm a french-canadien.

I'm on ubuntu about a lot of time.... like 10years. But It's the first time I build a Mail server. 
All work good , but I got a message when I try to send a email by thunderbird on my PC. If I send a email using telnet or postfixadmin, that working.

My error is :

 [FONT=Menlo]NOQUEUE: reject: RCPT from 69-165-196-215.cable.teksavvy.com[69.165.196.215]: 554 5.7.1 <giroux.oli@gmail.com>: Relay access denied; from=<ogiroux@infonuage.com ..... 
[/FONT]
So... This is my /etc/postfix/main.cf file

[FONT=Menlo]smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)[/FONT]
[FONT=Menlo]biff = no[/FONT]
[FONT=Menlo]disable_vrfy_command = yes[/FONT]
[FONT=Menlo]smtpd_helo_required = yes[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]smtp_use_tls = yes[/FONT]
[FONT=Menlo]smtp_tls_note_starttls_offer = yes[/FONT]
[FONT=Menlo]smtpd_tls_auth_only = no[/FONT]
[FONT=Menlo]smtpd_use_tls = yes[/FONT]
[FONT=Menlo]smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key[/FONT]
[FONT=Menlo]smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt[/FONT]
[FONT=Menlo]smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem[/FONT]
[FONT=Menlo]smtpd_tls_loglevel = 1[/FONT]
[FONT=Menlo]smtpd_tls_received_header = yes[/FONT]
[FONT=Menlo]smtpd_tls_session_cache_timeout = 3600s[/FONT]
[FONT=Menlo]tls_random_source = dev:/dev/urandom[/FONT]
[FONT=Menlo]smtpd_recipient_limit = 100[/FONT]
[FONT=Menlo]smtpd_helo_restrictions = reject_invalid_hostname[/FONT]
[FONT=Menlo]smtpd_sender_restrictions = reject_unknown_address[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# appending .domain is the MUA's job.[/FONT]
[FONT=Menlo]append_dot_mydomain = no[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]myhostname = mail.infonuage.com[/FONT]
[FONT=Menlo]myorigin = mail.infonuage.com[/FONT]
[FONT=Menlo]mydestination =mailhost.infonuage.com, smtp.infonuage.com, imap.infonuage.com, mail.infonuage.com, localhost.mail.infonuage.com, localhost[/FONT]
[FONT=Menlo]relayhost =[/FONT]
[FONT=Menlo]mynetworks = 127.0.0.0/8, 184.170.128.38[/FONT]
[FONT=Menlo]mailbox_size_limit = 0[/FONT]
[FONT=Menlo]recipient_delimiter = +[/FONT]
[FONT=Menlo]inet_interfaces = all[/FONT]
[FONT=Menlo]mydomain=mail.infonuage.com[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf[/FONT]
[FONT=Menlo]virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf[/FONT]
[FONT=Menlo]virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf[/FONT]
[FONT=Menlo]virtual_uid_maps = static:5000
[/FONT]
[FONT=Menlo]virtual_gid_maps = static:5000[/FONT]
[FONT=Menlo]virtual_mailbox_base = /home/vmail[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]#relay[/FONT]
[FONT=Menlo]#smtpd_relay_restrictions =[/FONT]
[FONT=Menlo]#       permit_mynetworks,[/FONT]
[FONT=Menlo]#       permit_sasl_authenticated,[/FONT]
[FONT=Menlo]#       reject_unauth_destination,[/FONT]
[FONT=Menlo]#       reject_non_fqdn_recipient[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]#adresses d'expedition[/FONT]
[FONT=Menlo]smtpd_sender_restrictions =[/FONT]
[FONT=Menlo]        permit_mynetworks,[/FONT]
[FONT=Menlo]        permit_tls_clientcerts,[/FONT]
[FONT=Menlo]        permit_sasl_authenticated,[/FONT]
[FONT=Menlo]        warn_if_reject reject_unverified_sender[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]#adresses de destination[/FONT]
[FONT=Menlo]smtpd_recipient_restrictions=[/FONT]
[FONT=Menlo]        permit_mynetworks,[/FONT]
[FONT=Menlo]        permit_sasl_authenticated,[/FONT]
[FONT=Menlo]        permit_tls_clientcerts,[/FONT]
[FONT=Menlo]        reject_unauth_destination,[/FONT]
[FONT=Menlo]        reject_non_fqdn_recipient,[/FONT]
[FONT=Menlo]        reject_unknown_sender_domain,[/FONT]
[FONT=Menlo]        reject_non_fqdn_sender,[/FONT]
[FONT=Menlo]        reject_unknown_recipient_domain,[/FONT]
[FONT=Menlo]        reject_invalid_helo_hostname,[/FONT]
[FONT=Menlo]        reject_unlisted_recipient,[/FONT]
[FONT=Menlo]        reject_unlisted_sender,[/FONT]
[FONT=Menlo]        reject_non_fqdn_helo_hostname[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# client[/FONT]
[FONT=Menlo]smtpd_client_restrictions =[/FONT]
[FONT=Menlo]        permit_mynetworks,[/FONT]
[FONT=Menlo]        permit_sasl_authenticated,[/FONT]
[FONT=Menlo]        permit_tls_clientcerts


I'm using TLS security. Must need to pass to SSL ????[/FONT]

---

### Post by TheFu on 2013-11-03
teksavvy.com is rejecting your attempts to use them as an email relay.  Get the settings and requirements to use them as a relay from them.  Some ISPs do not allow relaying at all or they require an added service to be purchased.  My ISP doesnt require anything other than being on a specific subnet with static IPs - in fact, they do not require relaying at all. Sorry, that means I cannot directly help solve that part of the issue.

Unrelated, but probably NOT what you want
```
mydomain=mail.infonuage.com
``` - probably incorrect
should be 
```
mydomain=infonuage.com
```

I looked at your MX records ... seems odd to have 3 MX records all pointing to the same IP. Is that intentional?

This link [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html) seems to be around what you are asking. Hope it helps.

---

### Post by giroux.oli on 2013-11-03
Hi thank for your reply.

Must need to pass in a SSL if I want to log whatever the place... ?

I have write mai.infonuage.com in "mydomain=" option because infonuage.com pointing in to a other server....

If a put my IP of my home , that working. I don't want to have my email just at my home.... 

Sorry i'm a little noob with the mail server and DNS... 

Thank in advance....

---

### Post by TheFu on 2013-11-03
> **giroux.oli said:**
> Must need to pass in a SSL if I want to log whatever the place... ?

What does the ISP say?

> **giroux.oli said:**
> I have write mai.infonuage.com in "mydomain=" option because infonuage.com pointing in to a other server....  This mydomain setting is for email and needs to match the MX record. The prior correction is 99.9999% correct.

> **giroux.oli said:**
> If a put my IP of my home , that working. I don't want to have my email just at my home....  I dont understand this.  _put IP of home_ where?  There are differences between sending and receiving email. These do not need to be on the same server at all. In my company, the sending email server is different from the receiving email server ... security considerations.

> **giroux.oli said:**
> Sorry i'm a little noob with the mail server and DNS... 

We all were at some point.  I still am when it comes to using a relay host that demands authenticated connections.  Google found this: [https://bbs.archlinux.org/viewtopic.php?id=165665](https://bbs.archlinux.org/viewtopic.php?id=165665)

---

### Post by giroux.oli on 2013-11-03
Finally , 

The Post is solved. 

I fix the problem Just add 2 line in my main.cf file. 

[FONT=Menlo]smtpd_sasl_type = dovecot[/FONT]
[FONT=Menlo]smtpd_sasl_path = private/auth

with that postfix use the SSL authentification of Dovecot. Now I can connect, send and receive email everywhere. 

Thank You for your Help TheFu[/FONT]

---

### Post by giroux.oli on 2013-11-03
thank you

---

### Post by mörgæs on 2013-11-03
Please mark the thread 'solved' using 'thread tools'.

---

