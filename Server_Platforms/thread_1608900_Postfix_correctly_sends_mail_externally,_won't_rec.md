---
title: "Postfix correctly sends mail externally, won't receive it"
date: 2010-10-29
forum: Server Platforms
---

### Post by joosebuck on 2010-10-29
Alright guys, I've looked over every thread regarding this issue on this forum, and many others; yet I cannot find out why my mail is being bounced without error from my external gmail account.

From what I've seen, you guys need to start off by seeing my postconf -n

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = 10.1.254.2
inet_protocols = all
mailbox_command =
mailbox_size_limit = 0
mydestination = [edited]
myhostname = [edited]
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 10.1.254.0/24
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom

```Thanks in advance for all of your help.

---

### Post by joosebuck on 2010-11-22
Bump.... still have been unable to fix this.

---

### Post by clay7 on 2010-11-22
When you say "without error" do you mean that your log files show no problems? For example, awhile back I had some mail problems with a VPS. It turns out that Gmail and Yahoo among others had marked me as Spam because my IP had formerly belonged to a spammer. My /var/log/mail.log made this very clear. Check this log for something like this (my IP has been replaced with xxx here)

refused to talk to me: 553 Mail from xxx.xxx.xxx.xxx not allowed - 5.7.1 [BL21] Connections not accepted from IP addresses on Spamhaus PBL; see [http://postmaster.yahoo.com/errors/550-bl21.html](http://postmaster.yahoo.com/errors/550-bl21.html) [550]

---

### Post by joosebuck on 2010-11-29
Nothing resembling that in mail.log
Nothing except a login/logout when i use thunderbird, too; though thunderbird returns an SMTP error when I try to send from that client.



edit:
just found this in my log after trying to send from my gmail account to my domain name again, but nothing comes up when i log in to check my mail.

Nov 29 12:52:39 radiusfront postfix/qmgr[20831]: D0F962101255: from=<xxxxxxxxxxxxx>, size=1881, nrcpt=2 (queue active)
Nov 29 12:52:39 radiusfront postfix/local[16409]: D0F962101255: to=<xxxxxxxxx>, relay=local, delay=0.51, delays=0.44/0.01/0/0.06, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Nov 29 12:52:39 radiusfront postfix/local[16410]: D0F962101255: to=<xxxxxxxxxx>, relay=local, delay=0.55, delays=0.44/0.01/0/0.1, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")

Nov 29 12:52:39 radiusfront postfix/qmgr[20831]: D0F962101255: removed

---

### Post by joosebuck on 2010-12-08
Bump.  I'm quite the postfix novice, and have unfortunately run out of things to try based on guides I've read on installing/configuring postfix...

---

### Post by Nunnsby on 2010-12-21
Hi Joosebuck

You get this working? I'm having the same issue, and have noticed that what is actually happening is that mail is being delivered to the **/var/mail/%user%/** directory, and NOT **/home/%user%/Maildir** as specified in Postfix.

I can't seem to get this fixed, so wondering if you actually got a fix for it?

Regards

---

### Post by joosebuck on 2010-12-31
Unfortunately, I haven't found a fix for this as of yet.  I'm working on getting my reverse dns pointers set correctly with my upstream, but I don't think that would be the reason why -all- mail is undelivered.

---

### Post by James78 on 2010-12-31
It could also be related to port forwarding and related network issues.

Some things for you to check:
Are your port numbers forwarded correctly (25)? [http://portforward.com/](http://portforward.com/)
Is your ISP blocking port 25 (most do if you're not using a business account)?
Is your router blocking anonymous ping requests? (Turn off option "Block Anonymous WAN Requests (ping)" and "Filter WAN NAT Redirection")
Check your Postfix configuration, specifically the directives my_networks, my_hostname, my_destination, etc etc. if they're setup wrong, Postfix won't send, receive, or both.

Check if you can access your IP/host from your own computer (inside the network, but using a local loopback; using telnet below)
Now check if you can access your IP/host externally (you can use the methods I did below, using telnet)
Does the DNS have correct MX entries and does the IP returned work, and does it connect fine?
Yes, DNS is more than a reason for mail to not get delivered too you.
E.g. (example of a successful try)```
toonarmy@opti-hacker:~$ dig google.com MX

; <<>> DiG 9.7.1-P2 <<>> google.com MX
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2988
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.                    IN      MX

;; ANSWER SECTION:
google.com.             900     IN      MX      400 google.com.s9b2.psmtp.com.
google.com.             900     IN      MX      100 google.com.s9a1.psmtp.com.
google.com.             900     IN      MX      200 google.com.s9a2.psmtp.com.
google.com.             900     IN      MX      300 google.com.s9b1.psmtp.com.

;; Query time: 60 msec
;; SERVER: 192.168.1.120#53(192.168.1.120)
;; WHEN: Fri Dec 31 17:23:08 2010
;; MSG SIZE  rcvd: 162

toonarmy@opti-hacker:~$ telnet google.com.s9b2.psmtp.com 25
Trying 74.125.148.14...
Connected to google.com.s9b2.psmtp.com.
Escape character is '^]'.
220 Postini ESMTP 244 y6_35_1c0 ready.  CA Business and Professions Code Section 17538.45 forbids use of this system for unsolicited electronic mail advertisements.
```

---

### Post by lisati on 2010-12-31
Just an observation which might point us in the direction of a solution. When my server accepts an email, it leaves a note similar to this:
> status=sent (delivered to maildir)
The log entries shown earlier in this thread have the following note instead:
> status=sent (delivered to command: procmail -a "$EXTENSION")
Are you using some filtering based around procmail?

---

### Post by t4thfavor on 2010-12-31
Don't know about yours, but I can post mail to gmail, and pretty much everywhere else with this config.

I also had my isp setup reverse dns.

```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = ipv4
mailbox_command = 
mailbox_size_limit = 0
mydestination = fultonit.local, ION, localhost.localdomain, localhost, fultonit.net
myhostname = ION
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = 
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,    permit_mynetworks,    check_relay_domains
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_security_options = noanonymous
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_alias_maps = hash:/etc/postfix/virtual

```

---

### Post by xathras1982 on 2011-01-01
Hi,
I know this was originally posted a long time ago but did you fix this?
If you didn't have does your ISP filter on port 25? I had the same problem but was wise enough to check on that and got my smtp relay information online.
 
That might help?
 
One way of testing this is send an email to yourself and check /var/log/mail.log, go to the bottom - in mine I could see connection timed out in the logs. 
 
If your ISP is filtering Port 25, you can simply add the following to your main.cf file in /etc/postfix/main.cf
 
> relayhost = relay.yourisp.co.uk
 
Where yourisp is the relayhost provided by your ISP. If a relayhost isn't publicly available services like dyndns/no-ip over it (at a cost i think)

---

### Post by James78 on 2011-01-01
And to add upon xathras post, you can go here to find a list of ISP's and their mail servers for which you can use as the relay host. The list is huge, so you're bound to find your ISP in there.

[http://www.e-eeasy.com/SMTPServerList.aspx](http://www.e-eeasy.com/SMTPServerList.aspx)

---

### Post by Nunnsby on 2011-01-03
Hey Joosebuck

I had a similar issue, and fixed it, but my config had both the procmail and the maildir lines in it. I commented out (#'d) the procmail line and it started working. I'm kind of tending to lean towards the same with your setup as it definitely mentions that is was processed by procmail in the logs, which would mean it has been received and processed by your system:

[FONT="Courier New"]delivered to command: procmail -a "$EXTENSION"[/FONT]

I think by default that what is happening is that procmail is managing the mail and pushing it to the location, Maildir, even though there is no mention of procmail. I think I remember reading somewhere that procmail is the default delivery agent for postfix?

Are you using Dovecot or Courier for pop3/imap? I can't see any configs for that. I've got a virtual transport which pushes mail to Dovecot, which then handles the local delivery, so that bypasses Postfix processing it.

I had loads of issues myself and landed up trashing my entire mail setup, and restarting it. Have learnt loads since then about configs, but not that much about the actual systems! :)

Try this tutorial for an overview....it really helped me:
[http://workaround.org/ispmail/lenny](http://workaround.org/ispmail/lenny)

I did land up doing it line by line, and that gave a better understanding of what was happening. Also made it easier to troubleshoot.

I am also using virtual domains as I am hosting multiple family member sites, so it kinda makes sense to go that route. Think about it. More work to setup in the long run, but maybe easier to manage.

Good luck, and let us know how you come on.

Nunnsby

---

