---
title: "Postfix and Hotmail"
date: 2007-09-29
forum: Server Platforms
---

### Post by kenmiles on 2007-09-29
Can anyone please help with this problem.
I am running Ubuntu 6.10 with the Postfix mail server, apache2 and my own web site.
I have no problems sending mail from postfix except if I try to send to a Hotmail account, i then get the following failure notice -

<someone@hotmail.com>: host mx4.hotmail.com[65.54.245.104] said: 550 Your
    e-mail was rejected for policy reasons on this gateway.  Reasons for
    rejection may be related to content with spam-like characteristics or
    IP/domain reputation problems.  If you are not an e-mail/network admin
    please contact your E-mail/Internet Service Provider for help.  For e-mail
    delivery information, please go to [http://postmaster.live.com](http://postmaster.live.com) (in reply to
    MAIL FROM command)

My Postfix main.cf file is -

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
delay_warning_time = 4h
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
myhostname = kmiles.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = kmiles.co.uk, kenneth-desktop, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

My ip address is 86.133.44.177

Thanks in advance for any help, Kenneth.

---

### Post by MJN on 2007-09-29
As the 'error' says your message was rejected as it was suspected as being spam. It is likely that this is because you have a dynamic IP address and Hotmail have opted to not allow mail sent directly from such addresses given that they are commonly the source of a lot of spam (being compromised home machines).

Put your address into [http://www.kloth.net/services/dnsbl.php](http://www.kloth.net/services/dnsbl.php) and you can see that it is listed in at least one list of known-dynamic ranges (the SORBS one in particular is widely used) and so this is likely the problem.

The usual solutions to this are to either a) obtain a static IP address from your ISP (usually costs, assuming it's even available), or b) relay outgoing mail via your ISPs mail server (using **relayhost = [your.isps.mail.server]** - see [http://www.postfix.org/postconf.5.html#relayhost](http://www.postfix.org/postconf.5.html#relayhost) for details).

Mathew

---

### Post by kenmiles on 2007-09-29
Thanks for that info, I have submitted a request to have the address removed from the database and will see how that works out.
Regards, Kenneth.

---

### Post by MJN on 2007-09-29
That's not going to get you anywhere.... your IP is dynamic hence is rightfully listed on the database.

Mathew

---

