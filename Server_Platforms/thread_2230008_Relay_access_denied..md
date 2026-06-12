---
title: "Relay access denied."
date: 2014-06-16
forum: Server Platforms
---

### Post by cthugha on 2014-06-16
I have a local discourse docker installation on my machine, and whenever it tries to send an email, the following information gets spat out:

```

Jun 16 15:33:42 hostname postfix/smtpd[19245]: connect from XXX-XXX-XXX.my-isp.com[XXX.XXX.XXX.XXX]
Jun 16 15:33:42 hostname postfix/smtpd[19245]: Anonymous TLS connection established from XXX-XXX-XXX.my-isp.com[XXX.XXX.XXX.XXX]: TLSv1.2 with cipher ECDHE-RSA-AES256-GCM-SHA384 (256/256 bits)
Jun 16 15:33:42 hostname postfix/smtpd[19245]: NOQUEUE: reject: RCPT from XXX-XXX-XXX.my-isp.com[XXX.XXX.XXX.XXX]: 554 5.7.1 <my.email@gmail.com>: Relay access denied; from=<admin@my.domain.us> to=<my.email@gmail.com> proto=ESMTP helo=<localhost.localdomain>
Jun 16 15:33:42 hostname postfix/smtpd[19245]: disconnect from XXX-XXX-XXX.my-isp.com[XXX.XXX.XXX.XXX]

```

I can send emails from my user account with the [email]admin@my.domain.us[/email] email using:
```

 echo "This is the main body of the mail" | mail -s "Subject of the Email" my.email@gmail.com -- -f admin@my.domain.us

```

It only seems to fail for discourse. Any ideas why?

---

### Post by CharlesA on 2014-06-16
Most ISP's mail servers only accept mail to or from that ISP's users.

You would have to set up your own mail server or use something like a gmail relay to send mail.

---

### Post by cthugha on 2014-06-16
Yes, I forgot to mention that this is more a question about my postfix install.

---

### Post by lisati on 2014-06-16
The error message reads to me as if the server is rejecting a message intended for gmail, throwing a hissy fit because it (the server) isn't one of gmail's servers.

If the message is originating on your own network, you might need to take a look at Postfix's main.cf settings, and make sure that it accepts email from your own internal network when required.

---

### Post by cthugha on 2014-06-17
Here is my main.cf for postfix (stripped of comments):
```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

append_dot_mydomain = no

readme_directory = no

smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

smtpd_relay_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
myhostname = mail.my.domain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = mail.my.domain, localhost.localdomain, localhost, my.domain
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command =
mailbox_size_limit = 51200000
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
myorigin = /etc/mailname
inet_protocols = all
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/ssl/certs/emailcert.pem
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

```

EDIT: your hypothesis seem to agree with everything that I've read so far about this. However, I have no idea which parameter is causing this.

---

### Post by CharlesA on 2014-06-18
The mydestination line looks.. off.

Here's what mine says.

```
smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no

readme_directory = no

smtpd_use_tls=yes
smtpd_tls_auth_only = yes

smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes

smtpd_recipient_restrictions =
        permit_sasl_authenticated,
        permit_mynetworks,
        sleep 3, reject_unauth_pipelining,
        reject_unknown_client_hostname,
        reject_unauth_destination,
        reject_rbl_client zen.spamhaus.org

myhostname = serenity
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4

#Handing off local delivery to Dovecot's LMTP, and telling it where to store mail
virtual_transport = lmtp:unix:private/dovecot-lmtp
#Virtual domains, users, and aliases
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf
content_filter = smtp-amavis:[127.0.0.1]:10024

```

Ignore the references to dovecot as I've got it set up to do authentication for sending mail.

---

### Post by lisati on 2014-06-18
If I've read the config files correctly, I think charlesa is using virtual mailboxes and cthugha isn't. 

You might want to have a look here for one possible solution: [http://ubuntuforums.org/showthread.php?t=1409112](http://ubuntuforums.org/showthread.php?t=1409112)

---

### Post by CharlesA on 2014-06-18
> **lisati said:**
> If I've read the config files correctly, I think charlesa is using virtual mailboxes and cthugha isn't. 

You might want to have a look here for one possible solution: [http://ubuntuforums.org/showthread.php?t=1409112](http://ubuntuforums.org/showthread.php?t=1409112)

You would be right. ;)

---

### Post by cthugha on 2014-06-18
> **lisati said:**
> If I've read the config files correctly, I think charlesa is using virtual mailboxes and cthugha isn't. 

You might want to have a look here for one possible solution: [http://ubuntuforums.org/showthread.php?t=1409112](http://ubuntuforums.org/showthread.php?t=1409112)

Thanks, changing my postfix conf to 
```
mynetworks = 127.0.0.0/8 192.168.0.0/16 172.16.0.0/12 XXX.XXX.XXX.XXX [::1]/128 [fe80::]/64

```
did it.

For people who may stumble upon this while attempting to solve their own problems the issue was that the connection to postfix was being made from XXX.XXX.XXX.XXX (my ip) and this IP did not appear in any of the network ranges specified in mynetworks. Since gmail is not in the mydestination configuration, it would not deliver this.

I attempted to circumvent this by adding the network range 172.16.0.0/12 (an internal network range) to the configuration and setting the mail server in discourse to 192.168.1.XXX (my internal IP) however, this caused a STARTTLS issue since the mail server's certificate is signed with my mail server's domain name (mail.mydomain.tld). I then tried to circumvent this issue by editing the container's /etc/hosts however the container would not allow that.

This is when I added my ip to the postfix conf, a less than ideal solution, but a solution nonetheless.

I'd like to thank CharlesA and lisati for their help with this issue. I was way beyond my depth.

---

### Post by CharlesA on 2014-06-18
Glad you got it sorted.

This might help you in the future:
[http://arstechnica.com/information-technology/2014/02/how-to-run-your-own-e-mail-server-with-your-own-domain-part-1/](http://arstechnica.com/information-technology/2014/02/how-to-run-your-own-e-mail-server-with-your-own-domain-part-1/)

---

### Post by lisati on 2014-06-18
> **CharlesA said:**
> Glad you got it sorted.

This might help you in the future:
[http://arstechnica.com/information-technology/2014/02/how-to-run-your-own-e-mail-server-with-your-own-domain-part-1/](http://arstechnica.com/information-technology/2014/02/how-to-run-your-own-e-mail-server-with-your-own-domain-part-1/)

+1

---

