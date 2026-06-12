---
title: "Mail server relay access denied"
date: 2008-11-21
forum: Server Platforms
---

### Post by kami_iwinaru on 2008-11-21
Ok, so I set up my mail server, and as far as I know, it works fine. I can send email to another user on my server, but I can't send anything out, and I also can't receive anything from another email. I've tried sending and receiving something from my gmail, and that didn't work either. (I tried that because another post I read said that he could send email to his gmail). Anytime I try to send an email to another email, it sends message back saying that Relay Access is Denied. Anything someone can tell me to get it going? The server name is fibercorp.mcccanntech.org. I'm working through my school right now for a project, and will soon have a public IP to use.

And someone also said to post the */etc/postfix/main.cf* file, so here it is, hope it helps (Not edited):

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

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = fibercorp.mccanntech.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = fibercorp.mccanntech.org, localhost.mccanntech.org, , localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reje$
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/

```

---

### Post by cdenley on 2008-11-21
Where are you trying to send mail from? Are you trying to have a client computer send mail through your server?
[http://www.postfix.org/postconf.5.html#mynetworks](http://www.postfix.org/postconf.5.html#mynetworks)
Also, what address are you expecting people to e-mail you at? I can't find any DNS record for fibercorp.mcccanntech.org, let alone an MX record.

---

### Post by kami_iwinaru on 2008-11-21
Uhm, I'm trying to send mail from an account on my mail server. (Using root for now). I'm using MS Outlook to do that. The accounts are set up fine (as far to my knowledge), and MS Outlook has sent a test message and I've gotten it. I'm just trying to get it so that I can send mail from an account on my server, to another account on gmail or some other one, and vice versa. And I guess for now they would email me at [email]root@fibercorp.mccanntech.org[/email]. And I don't think there would be a DNS record for it, like I said, it doesn't have a public IP address yet, it's running through the school.

---

### Post by cdenley on 2008-11-21
> **kami_iwinaru said:**
> Uhm, I'm trying to send mail from an account on my mail server. (Using root for now). I'm using MS Outlook to do that. The accounts are set up fine (as far to my knowledge), and MS Outlook has sent a test message and I've gotten it. I'm just trying to get it so that I can send mail from an account on my server, to another account on gmail or some other one, and vice versa. And I guess for now they would email me at [email]root@fibercorp.mccanntech.org[/email]. And I don't think there would be a DNS record for it, like I said, it doesn't have a public IP address yet, it's running through the school.

I doubt you have MS Outlook on your mail server. Are you trying to send e-mail from a client on your LAN, with Outlook configured to use your mail server as an SMTP server? If that is the case, your LAN needs to be added to "mynetworks" in the postfix configuration. This setting is explained in the link I posted.

If your server doesn't have a public IP address, how do you expect e-mail to reach it? This is the way e-mail works:

-user1 sends an e-mail to [email]user2@server2.com[/email]
-the e-mail is recieved by user1's smtp server (smtp.server1.com)
-smtp.server1.com looks up the MX record for server2.com, which may be, for example smtp.server2.com
-smtp.server1.com resolves the IP address for smtp.server2.com, which may be 123.123.123.123
-smtp.server1.com connects to 123.123.123.123, and sends the e-mail

So you see, if you have no MX record for server2.com, or in your case fibercorp.mccanntech.org, then how is any mail server supposed to be able to find yours? Even if you had an MX record, and it pointed to fibercorp.mccanntech.org, how is gmail or any e-mail server supposed to connect to it? It has no A record, and doesn't resolve to any IP.

---

### Post by kami_iwinaru on 2008-11-21
Yea, I'm using MS Outlook on my laptop, and using Putty to do whatever on my server. And I suppose I'll just wait until I get a public IP, a week >_<

---

