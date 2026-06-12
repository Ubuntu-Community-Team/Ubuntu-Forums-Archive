---
title: "Postfix + relay access denied 554 5.7.1"
date: 2007-07-17
forum: Server Platforms
---

### Post by nothingelse on 2007-07-17
Dear everybody,
Postfix had a problem. In my company, I sent mail to *@yahoo.com everything ok but i went to home i use outlook express i only sent *@domain.com no sent *@yahoo.com. postconf -n

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = scan:127.0.0.1:10026
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = ipv4
mailbox_size_limit = 0
mydestination = mail.domain.com, localhost.localdomain, , localhost, mail
myhostname = localhost
mynetworks = 127.0.0.0/8, 10.10.10.0/24
myorigin = localhost
receive_override_options = no_address_mappings
recipient_delimiter = +
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
virtual_alias_maps = hash:/etc/postfix/virtual
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000

file /var/log/mail.log

Jul 17 02:15:55 localhost postfix/smtpd[12446]: NOQUEUE: reject: RCPT from unkno                                             wn[10.10.10.1]: 554 5.7.1 <user@yahoo.com>: Relay access denied;from=<user@domain.com> to=<user@yahoo.com> proto=SMTP helo=<sptcdc8a4a5b85>
Jul 17 02:15:55 localhost postfix/smtpd[12446]: disconnect from unknown[10.10.10.1]

Sorry about not real domain. I scared spam mail. 
Please troubleshoot for me. Thank you so much.

---

### Post by MJN on 2007-07-17
Your mail client is probably not authenticating with the server - have you set it to? If you don't authenticate then, hopefully, your server won't relay to offsite domains otherwise your server would be acting as an open relay and be abused by spammers.
 
What configuration in Outlook Express have you set?
 
Mathew

---

### Post by Mr. C. on 2007-07-17
Older outlook and outlook express require using the smtps port 465.

You will have to add an entry to master.cf:

```
smtps     inet  n       -       n       -       -       smtpd
  ...

```
which looks like your other smtpd entries.  Show your master.cf if you need help with this part.

You will have to open port 465 on your firewall, and set an entry in /etc/services if there isn't already one:

```
smtps           465/tcp                         # SMTP over SSL (TLS)
```

Alternatively, you can setup an SSH server, and tunnel port 25 (smtp) from your local machine to the mail server.  Then outlook express will send email on port 25 to localhost.

MrC

---

### Post by nothingelse on 2007-07-17
Thanks everybody answer to me !
I use Outlook Express vession 6.

Hi Matthew, I agree with your question. 
"Your mail client is probably not authenticating with the server - have you set it to? If you don't authenticate then, hopefully, your server won't relay to offsite domains otherwise your server would be acting as an open relay and be abused by spammers."
I have trouble with smtp authenticate. Authenticate of POP3 is ok but athenticate of SMTP i don't understand.

Configuration in Outlook Express :
Email address : [email]user@domain.com[/email]
Incoming mail (POP3) : mail.domain.com
Outgoing mail (SMTP) : mail.domain.com
Account name : [email]user@domain.com[/email]
Password : password

Thanks,

---

### Post by Mr. C. on 2007-07-17
You need to set the Server requires authentication checkbox for the SMTP server.

Then you need to see via which port OE is connecting to your server (your firewall logs, or tcpdump can help with this).

MrC

---

### Post by johng4 on 2007-07-18
SMTP Authentication is only needed if you are using an outgoing mail server that is not the same as your ISP's.

Example...

Bill uses Comcast for his ISP.

Bill sends out an e-mail using an outgoing server of mail.ubuntu.org, with the mail address of [email]bill@ubuntu.org[/email].  The message will bounce because his ISP does not allow relaying for addresses outside of its domain.

Bill corrects his settings and with the same account (bill@ubuntu.org) using mail.comcast.net, and now it works.

Bill could also send mail out by using SMTP Authentication to the mail.ubuntu.org SMTP server so long as he uses the appropriate login information.  We'll assume that mail.ubuntu.org will require him to use his full e-mail address as his account name, so he sets up authentication like so...

User Name: [email]bill@ubuntu.org[/email]
Password: helloworld

Edit:  Even with authentication, it will be port 25 unless your mail client says otherwise.  The error you got is more than likely your ISP, and NOT your postfix server.

---

### Post by Mr. C. on 2007-07-18
> **johng4 said:**
> SMTP Authentication is only needed if you are using an outgoing mail server that is not the same as your ISP's.


This is not true.  Many ISPs require SMTP AUTH regardless of the network.

> **johng4 said:**
> Even with authentication, it will be port 25 unless your mail client says otherwise.

This is not true.  Many mail servers utilize the submission port 587.  I do as well.

MrC

---

### Post by nothingelse on 2007-07-23
Thank everybody !
Thank Mr. C
> 
You need to set the Server requires authentication checkbox for the SMTP server.
 
Everything is ok.

---

