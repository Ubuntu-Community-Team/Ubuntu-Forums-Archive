---
title: "Ubuntu Karmic Postfix Server does not receive mail"
date: 2009-12-23
forum: Server Platforms
---

### Post by danushk on 2009-12-23
Hi Ubuntuers,

Title clearly describes my problem.  I can send from Squirrelmail installed in the mail server to my gmail account. But i cannot send mail from my gmail to the account i made in the mail server .  Gmail responds back after sometime with following response 

my mail server hostname = mail.onlinemeetings.tk

hostname -f on terminal is  domU-12-31-39-06-C6-05.compute-1.internal

which is amazon EC2 instance

What am i missing here ,  can anybody show me ?

cheers


> 
This is an automatically generated Delivery Status Notification

THIS IS A WARNING MESSAGE ONLY.

YOU DO NOT NEED TO RESEND YOUR MESSAGE.

Delivery to the following recipient has been delayed:

     [EMAIL="admin@onlinemeetings.tk"]admin@onlinemeetings.tk[/EMAIL]

Message will be retried for 2 more day(s)

Technical details of temporary failure:
The recipient server did not accept our requests to connect. Learn more at [http://mail.google.com/support/bin/answer.py?answer=7720](http://mail.google.com/support/bin/answer.py?answer=7720)
[[MAIL.onlinemeetings.tk]("http://mail.onlinemeetings.tk/"). (0): Connection timed out]

----- Original message -----

MIME-Version: 1.0
Received: by 10.220.89.221 with SMTP id f29mr8756252vcm.61.1261487252396; Tue,
        22 Dec 2009 05:07:32 -0800 (PST)
Date: Tue, 22 Dec 2009 18:37:32 +0530
Message-ID: <[EMAIL="e4916a00912220507r27d5e05ax77d8dd51fee52df2@mail.gmail.com"]e4916a00912220507r27d5e05ax77d8dd51fee52df2@mail.gmail.com[/EMAIL]>
Subject: test
From: danushka <[EMAIL="danushka@gmail.com"]danushka@gmail.com[/EMAIL]>
To: [EMAIL="admin@onlinemeetings.tk"]admin@onlinemeetings.tk[/EMAIL]
Content-Type: multipart/alternative; boundary=0016e6471b86915c31047b50e35e

test



---

### Post by oneloveamaru on 2009-12-23
The key to your issues is in your post.

"Connection timed out". Is port 25 open through a firewall if you have one? Is Postfix listening on your IP address on the server and not just localhost? Are you using NAT? Is it set up correctly?

---

### Post by danushk on 2009-12-23
> **oneloveamaru said:**
> The key to your issues is in your post.

"Connection timed out". Is port 25 open through a firewall if you have one? Is Postfix listening on your IP address on the server and not just localhost? Are you using NAT? Is it set up correctly?

Hi there , Thanks for a quick response.

yes  port 25 open and i can telnet on port 25 from my PC into the server

> 
 telnet onlinemeetings.tk 25
Trying 75.101.154.228...
Connected to onlinemeetings.tk.
Escape character is '^]'.
220 mail.onlinemeetings.tk ESMTP Postfix (Ubuntu)
ehlo onlinemeetings.tk
250-mail.onlinemeetings.tk
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH DIGEST-MD5 NTLM CRAM-MD5 LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN


This is why its so weird to experience this problem :(

---

### Post by oneloveamaru on 2009-12-23
Looks like a DNS problem. Where does the MX record for your domain point to? I assume it's pointing to MAIL.onlinemeetings.tk, which resolves to 94.103.151.195, while onlinemeetings.tk resolves to 75.101.154.228.

That sounds like your problem to me.

---

### Post by danushk on 2009-12-23
> **oneloveamaru said:**
> Looks like a DNS problem. Where does the MX record for your domain point to? I assume it's pointing to MAIL.onlinemeetings.tk, which resolves to 94.103.151.195, while onlinemeetings.tk resolves to 75.101.154.228.

That sounds like your problem to me.

Hi , ya i guess so ,  i am using this free domain service and free dns service to test the application before i move into real thing.   Here is how my dns records are listed

A    onlinemeetings.tk     75.101.154.228
MX  onlinemeetings.tk     mail.onlinemeetings.tk

I don't see anything wrong here either , so why does MAIL.onlinemeetings.tk not pointing to  75.101.154.228 ?  :confused:

---

### Post by oneloveamaru on 2009-12-23
Because you don't have an A record for MAIL.onlinemeetings.tk.

It's resolving to some IP address, that the top level domain is handing out most likely.

So either point your MX to onlinemeetings.tk or create an A record for mail.onlinemeetings.tk pointing to 75.101.154.228.

---

### Post by oneloveamaru on 2009-12-23
OR you could create wild card A record, *.onlinemeetings.tk and point it to 75.101.154.228, so anything not specifically defined for that domain is sent to 75.101.154.228.

---

### Post by danushk on 2009-12-24
> **oneloveamaru said:**
> OR you could create wild card A record, *.onlinemeetings.tk and point it to 75.101.154.228, so anything not specifically defined for that domain is sent to 75.101.154.228.

Thanks , your solution worked.

Now i can see in the log files that mail is trying to connect

> 
Dec 24 06:04:47 ubuntu postfix/smtpd[7533]: connect from mail-vw0-f190.google.com[209.85.212.190]
Dec 24 06:04:48 ubuntu postfix/smtpd[7533]: NOQUEUE: reject: RCPT from mail-vw0-f190.google.com[209.85.212.190]: 554 5.7.1 <admin@onlinemeetings.tk>: Relay access denied; from=<danushka@gmail.com> to=<admin@onlinemeetings.tk> proto=ESMTP helo=<mail-vw0-f190.google.com>
Dec 24 06:04:48 ubuntu postfix/smtpd[7533]: disconnect from mail-vw0-f190.google.com[209.85.212.190]


But this RELAY ACCESS DENIED problem stops the mail going to the incoming queue.

What do i need to do for that ?

---

### Post by danushk on 2009-12-24
> **danushk said:**
> Thanks , your solution worked.

Now i can see in the log files that mail is trying to connect



But this RELAY ACCESS DENIED problem stops the mail going to the incoming queue.

What do i need to do for that ?

problem solved by following another thread in this same forum 

Its located at [http://ubuntuforums.org/showthread.php?t=477590](http://ubuntuforums.org/showthread.php?t=477590)

thanks guys for your great help !

---

### Post by headhoncho on 2009-12-27
Have wrestled with this for some weeks after upgrade to Karmic which happened at same time as ISP problems. Having had a functioning mailer with postfix/dovecot/mysql/spamassassin/clmav for over a year I mistakenly thought there had been a glitch, and foolishly started to change things without backing up old settings. Now have got back to functioning postfix/dovecot/mysql without the spam/clam filters, except it will not now receive external mail but will send to internal, self and external.Logs do not show any evidence of external connection from say gmail. Can access port 25 using telnet and servername, but not using the no-ip allocated ip address. Any ideas - I have played aroud with eth MX records as well. woudl it be because there is no reverse DNS ? Many thanks.

---

### Post by headhoncho on 2009-12-27
ps Here is my main.cf

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 0
mydestination = 'servername'.oldfieldhillfarm.co.uk, localhost, localhost.localdomain, localdomain
mydomain = oldfieldhillfarm.co.uk
myhostname = 'servername'.oldfieldhillfarm.co.uk
mynetworks = 127.0.0.0/8, 192.168.1.0/24
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = smtp.orangehome.co.uk
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_alias_domains = 
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf, mysql:/etc/postfix/mysql-email2email.cf
virtual_gid_maps = static:5005
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_transport = dovecot
virtual_uid_maps = static:5005

---

### Post by headhoncho on 2010-01-12
It seems that the ISP had had problems with Spammers. I emailed them about opening port 25 incoming and, to be fair, shortly afterwards email has started to flow. SO must have been the port 25 incoming after all!!! :grin:

---

