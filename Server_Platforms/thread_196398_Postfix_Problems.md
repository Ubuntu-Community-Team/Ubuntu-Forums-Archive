---
title: "Postfix Problems"
date: 2006-06-14
forum: Server Platforms
---

### Post by osmium on 2006-06-14
Hi, I'm not sure if this is in the right forum, I suppose it is as I am trying to create a server, but if it's not, sorry.

Currently, I host a server from home ([http://osmium.it.tt](http://osmium.it.tt)) and I have installed the packages so that I can have FTP, HTTP and SSH access. At the moment I am trying to install postfix for a mail server. I am using the following tutorial as a guide:

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p4](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p4)

Everything is working perfectly, I can connect to my SMTP and POP3 server without hassles. The only problem is when I am trying to send an email. Because I am hosting from home and I am using domain fowarding for the 'osmium.it.tt' address, the only genuine server address I have is obviously my IP. I was wondering what email address I would send an email to if I were to send an email to one of my users. I have tried sending an email to 'xenon@220.239.139.134' (xenon is my username and the IP address is my server) and it doesn't work. I have correctly set up port fowarding on my router so the problem isn't there.
I was basically wondering if I would have to register a domain or if there was another way that I could get an email to arrive at a users' inbox.

I don't know if I have given enough detail but I am more than happy to give more if it is needed to fix the problem.

Thanks in advance.

---

### Post by osmium on 2006-06-14
Hmm, do I have the wrong idea here? Postfix can be used as a normal email server, right? Just reading through the other posts seems to me like it is used in scripts for form mail. :confused:

---

### Post by LordHunter317 on 2006-06-14
Posting main.cf, which has probably been terribly corrupted by that guide, would be a good first start.

Another real possiblity is that your ISP blocks connections on port 25.

---

### Post by osmium on 2006-06-14
Here is my main.cf file. I don't think my ISP has ports blocked, I am able to connect, although I have only connected internally, using my ISP's address with port fowarding but of course it routes the data internally.


```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = server1.example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = 220.239.139.134, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtpd_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
mailbox_command = 

```

By looking at that file, may I need to change the 'myhostname' value or someting? :confused:

---

### Post by osmium on 2006-06-14
Hmm, that's a shame, you may be right, I just used an external shell account to test the connection and it just times out. Maybe they have blocked the port. I use OptusNet cable if you can advise me as to wether this is the case or not. :(

EDIT: Maybe I should test more before I post :P. I just changed the ports to 255 for SMTP and 1100 for POP3 to test them and I can connect externally. So with the server actually working, what should the address syntax be? Like because I don't have a .com or .net etc address Outlook Express and telnet both tell me that when I put my server's IP address (220.239.139.134) as the '@' domain, it is a bad address syntax. Which is fair enough, but I don't understand how to use it then. In reference to my initial question, may I need to purchase a domain?

---

### Post by LordHunter317 on 2006-06-14
You can't have mail delivered to that IP, period.  You might find an email-gateway service that will deliver to an SMTP server on a non-standard IP, but if port 25 is blocked, you're basically out of luck.

---

### Post by osmium on 2006-06-14
:( Well thanks for your help. I figured it would probably be harder to do than the tutorial made it sound.

---

