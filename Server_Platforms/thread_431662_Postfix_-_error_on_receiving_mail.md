---
title: "Postfix - error on receiving mail"
date: 2007-05-03
forum: Server Platforms
---

### Post by wadesmart on 2007-05-03
I really have a problem here with postfix and I cant seem to get the postfix guys to help and posts on other postfix forums have gone unanswered.  

I have a hosted email account at GoDaddy. My domain name is wadesmart.com. 
I use fetchmail to get my mail from wadesmart.com and from my gmail account.
I setup postfix and dovecot and my mail is located in  /home/wadesmart/Maildir. 

wadesmart@wadesmart:~$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
mailbox_size_limit = 0
mydestination = wadesmart, localhost.localdomain, localhost
mydomain = wadesmart.com
myhostname = mail.wadesmart.com
mynetworks = 127.0.0.0/8 192.168.0.0/6
recipient_delimiter = +
relayhost = [smtpout.secureserver.net]:3535
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes

This is who I currently have things setup:
I use evolution to access dovecot to access my mail an I use evolution to send it directly. Reason being is I never could get postfix setup properly to send mail.  Right now I cant get most of my mail. When fetchmail is getting mail I can see postfix processing it and then bouncing it.

Here is one of the error messages:
May  2 18:33:33 wadesmart postfix/smtp[17898]: 0F2D8142854E: to=<ubuntulinux@yahoogroups.com>, 
relay=smtpout.secureserver.net[64.202.165.58]:3535, 
conn_use=112, 
delay=24, 
delays=0.07/23/0.13/0.26, 
dsn=5.0.0, 
status=bounced (host smtpout.secureserver.net[64.202.165.58] 
said: 553 Sorry, that domain isn't in my list of allowed rcpthosts. (in reply to RCPT TO command))

I tried not putting a value for relayhost because Im not sending anything just receiving - but that didnt help. 

At this point Im really lost. Any help is greatly appreciated.

---

### Post by gjtoth on 2007-05-03
Don't know how much time you have invested in this but, have you looked at Axigen?  It's REALLY easy to set up and configure, the tech support is free for the first year.  The ONLY problem I had with it was that anything I sent through it got classified as spam from quite a few ISPs and users (probably because they saw it as a relay).  If I had more time to play with it I probably could've worked it out.  However, if you're just receiving, this could be a good way to go for you.

Hope this helps a little.

---

### Post by rsermilik on 2007-05-04
> I tried not putting a value for relayhost because Im not sending anything just receiving - but that didnt help. 

The 553 message is coming from smtpout.secureserver.net when your Postfix is trying to send the mail to it so you are sending - not just receiving.

I'm not sure why you have the described setup with Postfix and dovecot. Can you please describe your setup?. Do you have a LAN with an internal mailserver and a client computer or? Do you want webmail because you access it from other (outside) computers? From where do you use fetchmail?
Edit: Is the computer with Postfix, dovecot standing at GoDaddy?

---

