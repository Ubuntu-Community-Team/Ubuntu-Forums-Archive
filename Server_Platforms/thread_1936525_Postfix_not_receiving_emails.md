---
title: "Postfix not receiving emails ?"
date: 2012-03-06
forum: Server Platforms
---

### Post by Nailox on 2012-03-06
Hi. Im using this tutorial to setup my mail server [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

I send an email from yahoo to [email]email@mydomain.com[/email] - it doesnt bounce but its not delivered either.

this is my postconf -n:
> :~# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = 199.59.62.52
mailbox_command =
mailbox_size_limit = 0
mydestination = mail.mydomain.info, localhost.localdomain, localhost, mydomain.info
myhostname = goldenblog.info
mynetworks = 127.0.0.0/8, 192.168.1.0/24
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes


In the mail.log I see only entries of postfix and none of imapd and pop3d - does it mean they're not running ? When I try to reload pop3 i get :

"pop3d restart
/etc/courier/pop3d-ssl does not exist, forgot make install-configure?"

---

### Post by HermanAB on 2012-03-06
Howdy,

Check your DNS with 'dig' and make sure that you have A, MX and PTR records.

---

### Post by Nailox on 2012-03-06
> **HermanAB said:**
> Howdy,

Check your DNS with 'dig' and make sure that you have A, MX and PTR records.

I do have mx, A records and PTR. My DNS is hosted at my registrar - Godaddy

---

### Post by Nailox on 2012-03-07
bump ?

---

### Post by Doug S on 2012-03-07
> In the mail.log I see only entries of postfix and none of imapd and pop3d - does it mean they're not running ? When I try to reload pop3 i get :

Did the mail.log entries indicate that the test e-mail was recieved? Is it in /var/mail?

---

### Post by Nailox on 2012-03-07
yes its in /var/mail. I couldnt find a log specific for postfix so I was checking the one in /var/mail
I couldn't understand from the log if the mail is delivered but I couldn't see it in /home/user/Maildir/new

---

### Post by Doug S on 2012-03-07
So it appears as though postfix is working fine. That the e-mail is not making the next leg of its journey is probably due to the error you noted in your original posting. I don't use pop3d, so can not help with that part.

---

### Post by HermanAB on 2012-03-08
> In the mail.log I see only entries of postfix and none of imapd and pop3d - does it mean they're not running ?

# ps -e|grep pop
# ps -e|grep imap
# telnet localhost 143
# telnet localhost 993

---

