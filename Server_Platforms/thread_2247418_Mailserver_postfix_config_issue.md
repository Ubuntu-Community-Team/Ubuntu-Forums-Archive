---
title: "Mailserver postfix config issue"
date: 2014-10-07
forum: Server Platforms
---

### Post by Oliver_Edwards on 2014-10-07
Hi,

I am having some issues with sending mail to the specified [EMAIL="admin@xxmydomain.zonexx"]admin@xxmydomain.zonexx[/EMAIL] e-mail address and the reply e-mail error is;

[COLOR=#000000][FONT=Consolas]          Remote server replied: 554 5.7.1 <[EMAIL="oliver@edwardsltd.co.uk"]xxx@mydomain.co.uk[/EMAIL]>: Sender address rejected: Access denied

I have tried a plethora of different settings with no luck. Can anyone take that error message and tie it to a config line below so I can go away and trial and error something more specific? 

It would be worth mentioning the Ubuntu server sits behind a firewall with a local IP address. When the mail ports are called from the internet IP address they are forwarded onto the local IP.

I can send e-mail from outside the network ok but when I reply to that mail I get the rejected mail.

Any help would be much appreciated.[/FONT][/COLOR]

myhostname = mail.xxmydomain.zonexx
mydomain = xxmydomain.zonexx
myorigin = /etc/mailname
smtpd_banner = $myhostname ESMTP $mail_name
biff = no
append_dot_mydomain = no
readme_directory = no
mydestination =
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
# mynetworks = 127.0.0.1/32
mynetworks_style = host
mailbox_size_limit = 0
virtual_mailbox_limit = 0
recipient_delimiter = +
inet_interfaces = all
message_size_limit = 0


# SMTP Authentication (SASL)


smtpd_sasl_auth_enable = no
broken_sasl_auth_clients = no
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =


# Encrypted transfer (SSL/TLS)


smtp_use_tls = yes
smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/ssl/private/mail.xxmydomain.zonexx.crt
smtpd_tls_key_file = /etc/ssl/private/mail.xxmydomain.zonexx.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# Basic SPAM prevention


smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject


# Force incoming mail to go through Amavis


content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings


# Virtual user mappings


alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/maps/user.cf
virtual_uid_maps = static:5000
virtual_gid_maps =  static:5000
virtual_alias_maps = mysql:/etc/postfix/maps/alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/maps/domain.cf

---

### Post by TheFu on 2014-10-07
Let's start with the basics.
* does your ISP allow direct SMTP outbound connections?  Must you use their smtp gateway server?
* Is your domain properly registered with DNS for both forward and reverse lookups?
* Does your domain DNS have an MX record?
* Is your public IP in a DHCP range?
* firewall blocking outbound email?  This is a standard practice on corporate networks.

On my email systems, we reject emails if any of those things are not setup correctly.  We also use public block lists for currently active spammers.  Any residential ISP subnet is blocked too - there is just too much spam from those subnets.  Sorry, but that's the way of the world.

So - after all those questions are answered, then we can look deeper, check log files, try manual connections, etc.

---

### Post by Oliver_Edwards on 2014-10-08
Hi,

Thank you for the response TheFu.

To confirm my setup: I have a dedicated server running HyperV with 16 odd internet IP addresses. The connection is 100/100 with no restrictions. I have two Linux firewall VPS servers that forward traffic to the relevant internal IP address.

 - SMTP is unrestricted - I can telnet to port 25 and receive the SMTP banner of the VPS. I can also connect to my mail server and send e-mails out as the admin account to other mail server e.g. Gmail.
 - To the best of my knowledge the domain in question is set up correctly. I am reasonably savvy with DNS *cough* and believe it is correct - [http://mxtoolbox.com/diagnostic.aspx](http://mxtoolbox.com/diagnostic.aspx) reports everything as ok.
 - I have two MX records with corresponding A records - MX0 reports fine but I am having a problem with MX1 as the firewall in question is not playing ball. Another issues I am working through. To my knowledge I should still be able to use the mail server it is just less than ideal in a production environment?
 - Public IP is on of 16 odd that are static and provided by my host.
 - From the mail server I can telnet out to another mail server of mine running 2008 / Hmail server.

One thing I have noticed is whilst telnetting out on the mail server to check 25 is not being blocked it says;

 >Telnet mx1.myoldmailserver.co.uk 25
 >trying mx1.myoldmailserver.co.uk
 >Connected to mx1.myoldmailserver.co.uk.mynewmailserver.co.uk

It looks like it it appending the old mail server to the new mail server hostname. Is this normal or something to investigate?

Also using [http://www.emailsecuritygrader.com](http://www.emailsecuritygrader.com) it gave me 88%. It mentioned that the second MX record is not responding ( a separate firewall issue I am dealing with ) and POP3 is not allowed. I have not permitted POP3 as I don't want clients to use it in error.

Thanks in advance

Olly

---

### Post by TheFu on 2014-10-08
Sorry for all the questions - sometimes folks posting here are really new and don't know all the things needed.

I suspect the DNS issue is because a '.' is missing at the end of a DNS A or MX record. This is a common error.
[http://help.dnsmadeeasy.com/spry_menu/mx-record/](http://help.dnsmadeeasy.com/spry_menu/mx-record/)
That error could cause the other server to refuse email.

---

### Post by slickymaster on 2014-10-08
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by Oliver_Edwards on 2014-10-08
Not a problem -  I understand the need to check the fundamentals.

I can confirm at the end of the MX records there is a dot (the registrar actually does this for you). I can't add a dot to the end of the corresponding A records as it is invalid (I have not heard of this before).

I am still at a loss of where to go next. Can I PM you the domain name, perhaps if you give it a dig you might notice something I have missed. Short of that I must have stuffed up the configuration somewhere.

Thanks
Olly

---

