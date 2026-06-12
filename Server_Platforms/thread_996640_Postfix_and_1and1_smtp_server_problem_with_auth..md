---
title: "Postfix and 1and1 smtp server problem with auth."
date: 2008-11-29
forum: Server Platforms
---

### Post by Twizzle on 2008-11-29
My system - Ubuntu 8.04 sever edition (LAMP install), Zarafa, fetchmail and postfix.

My Problem - I am trying to have my server send email through my ISP.

I installed postfix and chose the internet option. My main.cf looks like this:

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = **mydomain.co.uk**
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = **mydomain.co.uk**
mydestination = **mydomain.co.uk** , localhost
relayhost = **auth.smtp.1and1.co.uk**
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host


```

I have set up a password maps file (/etc/postfix/sasl_passwd)
```
auth.smtp.1and1.co.uk    me@1and1.co.uk:password
```

I then

```
chown root:root /etc/postfix/sasl_passwd
chmod 600 /etc/postfix/sasl_passwd
postmap /etc/postfix/sasl_passwd
```
   
restarted postfix and tried to send an email through Zarafa web interface. It bounced back to my inbox with:

```
The following recipient(s) could not be reached:

	the@email.address on Sat 11/29/08 07:17:19
		550 must be authenticated

```

My /var/log/mail.log file is empty of anything to do with trying to send an email. (It will receive mail just fine)

My /var/log/zarafa/spooler.log file:

```
Sat 29 Nov 2008 07:17:17 GMT: 0xb74f7b90: Sending e-mail for user john, subject: 'Test', size: 2474
Sat 29 Nov 2008 07:17:19 GMT: SMTP: Error while executing command 'DATA'. Response: 550 must be authenticated
Sat 29 Nov 2008 07:17:19 GMT: 0xb74f7b90: E-mail for user john could not be sent, notifying user
Sat 29 Nov 2008 07:17:20 GMT: 0xb74f7b90: Removing failed message from queue

```


I am assuming that there is a problem authenticating myself to the 1and1 server for some reason. I know that there is not a problem with the server as if I send direct through Thunderbird, for example, it works.

---

### Post by MJN on 2008-11-29
> **Twizzle said:**
> My /var/log/mail.log file is empty of anything to do with trying to send an email.

Really? That means Postfix isn't the one sending the mail - it must be Zarafa in which case that's the config you need to be looking at.

(unfortunately I've never used Zarafa so cannot help with the specifics)

Mathew

---

### Post by Twizzle on 2008-11-29
Ah, ok. Thankyou - in that case I will do digging else where.
Just in case it is causing a problem and I did not realise, my mail log does contain:

```
Nov 29 17:29:49 mydomain fetchmail[4825]: Server certificate verification error: unable to get local issuer certificate 
Nov 29 17:29:49 mydomain fetchmail[4825]: Server certificate verification error: certificate not trusted 
Nov 29 17:29:49 mydomain fetchmail[4825]: Server certificate verification error: unable to verify the first certificate 

```

but that started when I was getting fetchmail working and as it does collect main, I did not think it a problem - I take it this is not something that could be affecting postfix?

---

### Post by MJN on 2008-11-29
> **Twizzle said:**
> I take it this is not something that could be affecting postfix?Unlikely. As you say, it's a Fetchmail error and indeed it may not be fatal given that many default configurations tend to ignore (and just warn about) certificate verification errors.

Mathew

---

### Post by jamiesdomain on 2009-06-14
Hi
 
[COLOR=black][FONT=Verdana]I use 1and1 for all my email accounts and have just configured one of my email accounts to work in Evolution Mail.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Receiving Mail needs to be setup like this:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Server Type &#8211; IMAP[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Configuration:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Server: imap.1and1.co.uk[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Username: your email address[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Security: No encryption[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Sending Email[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Server Type: SMTP[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Server Configuration:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Server: smtp.orangehome.co.uk (Orange being my broadband provider)[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Verdana]That will work for all 1and1 email accounts and will work in Thundermail.[/FONT][/COLOR]

---

