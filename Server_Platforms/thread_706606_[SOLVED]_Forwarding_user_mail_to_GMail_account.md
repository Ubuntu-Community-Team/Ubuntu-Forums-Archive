---
title: "[SOLVED] Forwarding user mail to GMail account"
date: 2008-02-24
forum: Server Platforms
---

### Post by SumnerBoy on 2008-02-24
Hi,

I am new to Linux and Ubuntu and have a (probably stupid) question re. user mail. I have Postfix installed and am getting mail generated and delivered to my user mailbox (mainly via crontab etc).

I would like this mail to actually be delivered or forwarded to my personal GMail account - is this possible? If so, how do I go about configuring Postfix etc?

Thanks in advance,
Ben

PS - I am running Ubuntu 7.10 Server Edition - i.e. no GUI bar Webmin.

---

### Post by astrotech226 on 2008-02-24
Depending on your setup, you can normally create a file in your home directory called ".forward" and simply put the email address you want it forwarded to.

---

### Post by SumnerBoy on 2008-02-25
Thanks Mark - that is half my problem solved. Adding a .forward file with my personal gmail account in it means any email sent to my user account is immediately forwarded to that address. However the mail is not being delivered - it is just sitting in my mail queue.

Anyone know how to configure Postfix to allow it to deliver mail to the gmail servers?

---

### Post by Mr. C. on 2008-02-25
Show the log messages for delivery attempts from /var/log/maillog.  Show output of:

postconf -n
mailq

MrC

---

### Post by SumnerBoy on 2008-02-25
Here is the output of /var/log/mail.log...i.e. connection timeout

Feb 25 21:01:32 weka postfix/qmgr[4136]: 10CEE7B57C: from=<ben@weka>, size=644, nrcpt=1 (queue active)
Feb 25 21:02:02 weka postfix/smtp[5914]: connect to smtp.gmail.com[209.85.199.111]: Connection timed out (port 25)
Feb 25 21:02:32 weka postfix/smtp[5914]: connect to smtp.gmail.com[209.85.199.109]: Connection timed out (port 25)
Feb 25 21:02:32 weka postfix/smtp[5914]: 10CEE7B57C: to=<<my email address - removed>>, orig_to=<ben>, relay=none, delay=3274, delays=3214/0.04/60/0, dsn=4.4.1, status=deferred (connect to smtp.gmail.com[209.85.199.109]: Connection timed out)

And my configuration...

ben@weka:~$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
disable_dns_lookups = yes
inet_interfaces = all
mailbox_size_limit = 0
mydestination = weka.com, weka, localhost.localdomain, localhost
myhostname = weka
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
recipient_delimiter = +
relayhost = [smtp.gmail.com]
smtp_generic_maps = hash:/etc/postfix/generic
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_tls_cert_file = /etc/postfix/FOO-cert.pem
smtp_tls_key_file = /etc/postfix/FOO-key.pem
smtp_tls_session_cache_database = btree:/var/run/smtp_tls_session_cache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_sasl_auth_enable = no
smtpd_sasl_local_domain = $myhostname
smtpd_tls_CAfile = /etc/postfix/cacert.pem
smtpd_tls_cert_file = /etc/postfix/FOO-cert.pem
smtpd_tls_key_file = /etc/postfix/FOO-key.pem
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:/var/run/smtpd_tls_session_cache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
transport_maps = hash:/etc/postfix/transport

ben@weka:~$ mailq
-Queue ID- --Size-- ----Arrival Time---- -Sender/Recipient-------
10CEE7B57C      644 Mon Feb 25 20:07:58  ben@weka
             (connect to smtp.gmail.com[209.85.199.109]: Connection timed out)
                                         <my email address - removed>

85E7F7B579      543 Sun Feb 24 12:04:26  ben@weka
             (connect to smtp.gmail.com[209.85.199.111]: Connection timed out)
                                         <my email address - removed>

-- 1 Kbytes in 2 Requests.

Hope this sheds some light on it!!
Thanks!

---

### Post by Mr. C. on 2008-02-25
Your ISP is blocking outbound port 25.  Test with :

```
telnet 209.85.199.111 25
```

and you will see no response.  You want to see:

```
Trying 209.85.199.111...
Connected to rv-in-f111.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP k19sm10919808rvb.18
```

If this is the case, you can attempt to use the submission port:

```
telnet 209.85.199.111 587
```

If this works, you will be able to relay email via Gmail.  If this port is blocked also, you cannot use your LAN to send mail via SMTP, and will instead have to configure your postfix installation to relay via your ISPs mail servers.

MrC

---

### Post by SumnerBoy on 2008-02-25
You are right - I cannot telnet to port 25 but 587 worked. Sorry but I am not sure how I am supposed to configure things to use this - is it a simple thing to setup?

Thanks again for your help.

---

### Post by Mr. C. on 2008-02-25
As we suspected.

In a nutshell, Gmail only allows encrypted, authenticated connections to submit email.  You will need to configure postfix to connect to the gmail server using TLS, and then to authenticate by presenting a key.  Here's a howto that will get you on your way.

[http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html](http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html)

Take it slowly, verifying you understand each step as you go along, so that you can troubleshoot along the way.

Post log entires, and learn to use saslfinger ([http://postfix.state-of-mind.de/patrick.koetter/saslfinger/](http://postfix.state-of-mind.de/patrick.koetter/saslfinger/)) when necessary.

MrC

---

### Post by SumnerBoy on 2008-02-25
Righto - will have a crack and see how I get on.

Thanks a heap for your assistance on this.

---

### Post by SumnerBoy on 2008-02-25
Update!! I had already completed all the steps outlined but was obviously trying to connect on port 25. As soon as I updated it to 587 emails started flying out the door!

Thanks once again.

---

### Post by Mr. C. on 2008-02-25
Nice!

Best of luck,
MrC

---

