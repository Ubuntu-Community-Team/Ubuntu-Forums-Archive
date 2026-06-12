---
title: "Postfix - Unable to receive e-mail from the public internet (ex. gmail)"
date: 2018-01-13
forum: Server Platforms
---

### Post by mvelez83 on 2018-01-13
Hello,

I'm very new to Ubuntu as well as postfix and dovecot so my apologies if I miss some information or miss something obvious. I was trying to create an e-mail server where I can send e-mail and receive e-mails for my domain [www.aevtech.com]("http://www.aevtech.com"). I used the following HowTo:

[https://www.cloudjojo.com/how-to-install-mail-server-on-ubuntu-16-04-part1/](https://www.cloudjojo.com/how-to-install-mail-server-on-ubuntu-16-04-part1/)

Long story short, I'm able to send and receive locally. I can only send when it comes to the outside world (Goes to the spam folder) but I can not receive e-mails from places such as gmail, yahoo etc.

These are some of the errors I've noticed in the mail.log file:

```
Jan 13 14:53:06 mail postfix/postfix-script[15040]: warning: unable to create missing queue directories
NOQUEUE: reject: RCPT from unknown[8.21.104.53]: 454 4.7.1 <spameri@tiscali.it>: Relay access denied; from=<spameri@tiscali.it> to=<spameri@tiscali.it> proto=ESMTP helo=<Server>
```

I haven't seen anything other errors when I try to send e-mails the log doesn't move for anything incoming when I have tested myself sending from a gmail account. Below is my postfix configuration:

```
alias_database = hash:/etc/aliasesalias_maps = hash:/etc/aliases
biff = no
command_directory = /usr/sbin
compatibility_level = 2
daemon_directory = /usr/lib/postfix/sbin
data_directory = /var/lib/postfix
debugger_command = PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin ddd $daemon_directory/$process_name $process_id & sleep 5
home_mailbox = Maildir/
html_directory = no
inet_interfaces = all
inet_protocols = ipv4
mail_owner = postfix
mailq_path = /usr/sbin/mailq
manpage_directory = /usr/share/man
mydestination = $myhostname, localhost.$mydomain, localhost
mydomain = mail.aevtech.com
myhostname = mail.aevtech.com
mynetworks = 45.77.0.0/16, 127.0.0.0/8
myorigin = mail.aevtech.com
newaliases_path = /usr/sbin/newaliases
queue_directory = /var/spool/postfix
readme_directory = no inet_protocols = all
recipient_delimiter = +
relayhost =
sample_directory = /etc/postfix
sendmail_path = /usr/sbin/sendmail
setgid_group = postdrop
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = private/auth
smtpd_sasl_type = dovecot
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/dovecot/mail_aevtech_com.pem
smtpd_tls_key_file = /etc/dovecot/private/mail_aevtech_com.pem
smtpd_use_tls = yes
unknown_local_recipient_reject_code = 550
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf,mysql:/etc/postfix/mysql-virtual-email2email.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_transport = lmtp:unix:private/dovecot-lmtp
```

Here are the ports I have open on the server:

```
Status: active

To                         Action      From
--                         ------      ----
25/tcp on ens3             ALLOW       Anywhere
465/tcp on ens3            ALLOW       Anywhere
587/tcp on ens3            ALLOW       Anywhere
110/tcp on ens3            ALLOW       Anywhere
995/tcp on ens3            ALLOW       Anywhere
143/tcp on ens3            ALLOW       Anywhere
993/tcp on ens3            ALLOW       Anywhere
80/tcp on ens3             ALLOW       Anywhere
```

I have tried to test port 25 but doesn't seem to connect:

```
(mvelez)-(jobs:0)-(~)(! 260)-> telnet mail.aevtech.com 25
Trying 45.77.146.115...
^C
```

I have the server with vultr.com and they confirmed they're not blocking port 25 (SMTP). Let me know if I can send any other information to help. Again, sorry if I didn't send enough information at first not sure what else to send. 

Thank You!

---

### Post by darkod on 2018-01-13
First, you have no MX record for the aevtech.com domain:
```
darko@nuc6:~$ dig mx aevtech.com

; <<>> DiG 9.10.3-P4-Ubuntu <<>> mx aevtech.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12004
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;aevtech.com.   IN	MX

;; AUTHORITY SECTION:
aevtech.com.  299	IN	SOA	ns1.vultr.com. dnsadm.choopa.com. 1515481568 10800 3600 604800 3600

;; Query time: 49 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Sat Jan 13 16:25:28 CET 2018
;; MSG SIZE  rcvd: 100
```

For any mail server on the internet to send you mail they need to know where to find your mail server. You need MX record pointing to mail.aevtech.com

---

### Post by mvelez83 on 2018-01-13
Hey Darkrod,

I added it now it works:

```
(mvelez)-(jobs:0)-(~)(! 261)-> dig mx aevtech.com


; <<>> DiG 9.9.7-P3 <<>> mx aevtech.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21616
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;aevtech.com.            IN    MX


;; ANSWER SECTION:
aevtech.com.        3600    IN    MX    10 45.77.146.115.


;; Query time: 91 msec
;; SERVER: 2001:558:feed::1#53(2001:558:feed::1)
;; WHEN: Sat Jan 13 13:18:56 EST 2018
;; MSG SIZE  rcvd: 69
```

I sent an email and it came in right away. I'll do some more testing and I don't think that was in the HowTo but THANK YOU!!!!!!!!

---

### Post by darkod on 2018-01-13
You did it slightly wrong. The MX should not point to a public IP. It should point to A record that is pointing to that IP.

For example if you have your record mail.aevtech.com pointing to 45.77.146.115, then the MX should have value of mail.aevtech.com, not the IP. That is why above I said to point it to that record, not to the IP.

You can mark the thread Solved if you have it resolved now. You can do that in Thread Tools above the first post.

---

### Post by mvelez83 on 2018-01-14
Hello,

I have updated the record so it uses a CNAME and not an A cord and it's working.

THANK YOU!!!

I'll mark as resolved.

---

