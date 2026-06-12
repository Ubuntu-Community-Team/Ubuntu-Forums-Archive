---
title: "Issues with Postfix Sending Mail to Certain Address and VPS Server"
date: 2013-05-26
forum: Server Platforms
---

### Post by jakek on 2013-05-26
So here's my issue: I have a domain with namecheap.com (bitknight.com) where I have paid for their email services, so I check my mail using their web portal. I also have a VPS at digital ocean that has the proper DNS records for resolution to point to my VPS, and mail setup which I have confirmed with standard emailing between another account and the bitknight.com account. Everything their seems to work fine. On the VPS I have postfix installed and it works fine to send emails to all other addresses except my email which is [EMAIL="jake@bitknight.com"]jake@bitknight.com[/EMAIL], so attempting to have PHP and Ruby scripts send me logging messages at this address is currently failing. I suspect something in my main.cf is not appropriately setup, but I'm not sure what exactly. I'm concerned as I add domains to route to this server I will encounter the same problem with many email addresses associated with it. Any advice would be appreciated.

My /etc/hosts contains two entries
127.0.0.1          localhost
198.199.91.180   bitknight.com

This is my current mail.cf file contents:
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


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = localhost
local_recipient_maps =
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
# mydestination = bitknight.com, localhost, localhost.localdomain, localhost
mydestination = localhost, localhost.localdomain, krypton
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all



```

I've attached the results of the mail.log when attempting to send to [EMAIL="jake@bitknight.com"]jake@bitknight.com[/EMAIL] from a PHP script.
[ATTACH]243089[/ATTACH]

Hopefully this is enough info to help suggest a solution. Thanks.

---

### Post by sanderj on 2013-05-26
```
sander@flappie:~$ host bitknight.com
bitknight.com has address 198.199.91.180
bitknight.com mail is handled by 10 oxmail2.registrar-servers.com.
bitknight.com mail is handled by 10 oxmail1.registrar-servers.com.
sander@flappie:~$ 

sander@flappie:~$ host oxmail2.registrar-servers.com
oxmail2.registrar-servers.com has address 198.187.29.233
sander@flappie:~$ 
```

So mail is delivered to 198.187.29.233. If that is not your mail server, you have found what is going on. Solution: correct the MX record for your domain: MX should point to bitknight.com

---

### Post by jakek on 2013-05-26
Is this true when I only want postfix to send email not intercept incoming mail to users on the VPS? Right now my MX records are setup as instructed by namecheap. I would prefer postfix to ignore all emails to  [email]user@bitknight.com[/email], or any domain I add in the future for that matter, so I'm not viewing mail on the server or needing something like dovecot to read them outside of ssh.

---

### Post by sanderj on 2013-05-26
What do want? Only send mail from your VPS?

---

### Post by jakek on 2013-05-26
Yes exactly. Currently mail sent from scripts on my server to any user email like [email]user1@bitknight.com[/email], [email]user2@bitknight.com[/email], etc. are only working if I make the appropriate user on the server itself, at which point I can read them through ssh as normal. This isn't what I want. I use the mailing service associated with my domain at namecheap.com so I don't want postfix to try handle incoming mail. Externally form the server everything works great, sending from hotmail, gmail, etc to these accounts works just fine. Hopefully that's a little clearer as to what I'm after.

---

