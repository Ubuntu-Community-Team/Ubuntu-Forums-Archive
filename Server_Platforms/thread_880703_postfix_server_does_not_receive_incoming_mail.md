---
title: "postfix server does not receive incoming mail"
date: 2008-08-05
forum: Server Platforms
---

### Post by kofiernest on 2008-08-05
Hi all am kofiernest I am new at this and will apperciate all the help. Anyway I an trying to configure postfix from the house just a test and I am able to send me to let say yahoo.com but the yahoo client can not reply to the email. 

I wan using dyndns to resolve my hostname with my dynamic ip, I had my ISP open port 25 and 80 which I can telnet to. I think Im almost here but the fact that I can not receive messages from the outside world

Thanks in Advance for all the help.

---

### Post by MJN on 2008-08-06
Does the sender get a non-delivery report back? If so, what does it say?
 
We really need more info e.g. your Postfix config and an example e-mail address at the very least.
 
Mathew

---

### Post by kofiernest on 2008-12-13
Sorry MJN I did not not back to you soon. But answer to your question the sender does not receive any error. MY dydns hostname is ernestk.homelinux.net so the email address is [email]test@ernestk.homelinux.net[/email] but nothing happen. 

I have attach the postfix main.cf below if that will help. thank you in advance for your help.


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

myhostname = ernestk.homelinux.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = ernestk.homelinux.net, localhost.localdomain, localhost
relayhost = mail.optonline.net
mynetworks = 127.0.0.0/8, 192.168.1.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command =
virtual_alias_domains = ernestk.homelinux.net linuxelabs.com fossedu.org

---

### Post by MJN on 2008-12-13
Your DNS appears to be incorrectly configured.

Asking for the MX records for ernestk.homelinux.net (i.e. where to sent mail to) we get:

```
$ dig ernestk.homelinux.net mx

; <<>> DiG 9.3.2-P2.1 <<>> ernestk.homelinux.net mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 19895
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ernestk.homelinux.net.         IN      MX

;; ANSWER SECTION:
ernestk.homelinux.net.  60      IN      MX      10 mail.optonline.net.

;; Query time: 32 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Sat Dec 13 10:46:59 2008
;; MSG SIZE  rcvd: 70
```mail.optonline.net resolves to 167.206.5.250 which I am assuming is not your address.

Mathew

---

