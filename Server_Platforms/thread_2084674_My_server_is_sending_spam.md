---
title: "My server is sending spam"
date: 2012-11-16
forum: Server Platforms
---

### Post by AvengerX9 on 2012-11-16
Okay, I got a phone call from my ISP telling me that my server is sending spam. So I guess someone is using my server to spam. How can I troubleshoot and fix this before they cut me off the net for good? 

I appreciate all the help I can get on this matter.  Thanks for reading!

---

### Post by SlugSlug on 2012-11-16
Do you have a mail server installed? 

Test open relay here

[http://www.mailradar.com/openrelay/](http://www.mailradar.com/openrelay/)

---

### Post by HermanAB on 2012-11-16
First kill all email:
iptables -I -i eth0 -p tcp --dport 25 -j DROP

Now you can investigate things at your leasure.

---

### Post by AvengerX9 on 2012-11-16
> **SlugSlug said:**
> Do you have a mail server installed? 

Test open relay here

[http://www.mailradar.com/openrelay/](http://www.mailradar.com/openrelay/)

It says port 25 is closed and the command does not work. I'm looking in my mail logs and there are lots of stuff. Let me post it for you.


Here is one line out of thousands!
> Nov 12 06:44:10 roger-G31T-M7 postfix/error[8030]: 0A417145035: to=<avist@keytown.com>, relay=none, delay=2050, delays=1949/96/0/4.7, dsn=4.4.2, status=deferred (delivery temporarily suspended: lost connection with smtp.nenett.no[81.167.36.150] while sending RCPT TO)

---

### Post by AvengerX9 on 2012-11-16
I turned off my postfix mail server. It seems like the mail log have stopped getting new records now. How can I fix this to prevent it from being used to spam again ?

---

### Post by mlentink on 2012-11-16
Do not allow relays. 
You might want to read through [this]("http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.04-lts") for a solid mailserver configuration

---

### Post by AvengerX9 on 2012-11-16
how can I disable relays ?

---

### Post by lisati on 2012-11-16
> **AvengerX9 said:**
> how can I disable relays ?

Having something like [this]("http://www.spamcop.net/fom-serve/cache/349.html") in your main.cf file will often be a help:
```

smtpd_recipient_restrictions =
    reject_invalid_hostname, 
    reject_non_fqdn_sender, 
    reject_non_fqdn_recipient, 
    reject_unknown_sender_domain, 
    reject_unknown_recipient_domain, 
    reject_unauth_pipelining, 
    permit_mynetworks, 
    reject_unauth_destination, 
    reject_rbl_client bl.spamcop.net 
    permit

```
The important line is "reject_unauth_destination", which limits the incoming mail that doesn't arrive via your own network to destinations in Postfix's "mydestination =" line in the main.cf file.

---

### Post by AvengerX9 on 2012-11-16
Can I just add this to the bottom of my main.cf file or should I place it somewhere else in there ?

---

### Post by AvengerX9 on 2012-11-16
Now I'm also getting this in my mail log, but I don't know what it means

> postfix/postfix-script[####]warning: not owned by postfix: /var/lib/postfix/./verify_cache

---

### Post by lisati on 2012-11-16
> **AvengerX9 said:**
> Can I just add this to the bottom of my main.cf file or should I place it somewhere else in there ?
If you don't already have a smtpd_sender_restrictions section in your main.cf file, it can go just about anywhere.
> **AvengerX9 said:**
> Now I'm also getting this in my mail log, but I don't know what it means
Are you using some kind of [address verification]("http://www.postfix.org/ADDRESS_VERIFICATION_README.html")?

---

### Post by AvengerX9 on 2012-11-16
Here is my current main.cf

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

myhostname = mail.truckstop24.no
mydomain = truckstop24.no
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = $mydomain, $myhostname
myorigin = $mydomain
mynetworks = 0.0.0.0/0 [::/0]
relayhost = smtp.nenett.no
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_recipient_restrictions = reject_non_fqdn_recipient reject_unknown_recipient_domain permit_mynetworks permit_sasl_authenticated reject_unauth_destination reject_non_fqdn_hostname reject_invalid_hostname check_helo_access pcre:/etc/postfix/helo_checks check_sender_mx_access cidr:/etc/postfix/bogus_mx reject_rbl_client zen.spamhaus.org reject_rbl_client cbl.abuseat.org reject_rbl_client dnsbl-1.uceprotect.net permit

smtpd_recipient_restrictions =
    reject_invalid_hostname, 
    reject_non_fqdn_sender, 
    reject_non_fqdn_recipient, 
    reject_unknown_sender_domain, 
    reject_unknown_recipient_domain, 
    reject_unauth_pipelining, 
    permit_mynetworks, 
    reject_unauth_destination, 
    reject_rbl_client bl.spamcop.net 
    permit

```

---

### Post by lisati on 2012-11-16
OK. You already had a "smtpd_recipient_restrictions" entry. Postfix only uses one. You can probably safely remove the bit you added from my previous post. What I'd suggest for the line you already had is to add commas "," between the individual restrictions you have listed, so that it looks something like this:
```
smtpd_recipient_restrictions = reject_non_fqdn_recipient, reject_unknown_recipient_domain, permit_mynetworks permit_sasl_authenticated, reject_unauth_destination, reject_non_fqdn_hostname, reject_invalid_hostname check_helo_access pcre:/etc/postfix/helo_checks, check_sender_mx_access cidr:/etc/postfix/bogus_mx, reject_rbl_client zen.spamhaus.org, reject_rbl_client cbl.abuseat.org, reject_rbl_client dnsbl-1.uceprotect.net, permit

```

---

### Post by AvengerX9 on 2012-11-16
Thanks, fixed that now :) But to prevent others from using my mailserver to spam. Is there something I can do in the IPtables ?

---

### Post by cryptotheslow on 2012-11-16
Do you have any more recent logs of this spam being sent through your server?

It's certainly not acting as an open relay right now.

You might want to consider enforcing SMTP Auth and TLS. Your conf file suggests you have TLS configured already. SMTP Auth would require all users wanting to send via your server to authenticate.

I'm not really familiar with postfix so I'll just point at a googled how to: [http://postfix.state-of-mind.de/patrick.koetter/smtpauth/](http://postfix.state-of-mind.de/patrick.koetter/smtpauth/)

---

### Post by AvengerX9 on 2012-11-17
Thanks. I will check that out.

Here is the most recent mail.log

> 
Nov 17 02:36:58 roger-G31T-M7 postfix/cleanup[14379]: 15FF2143E3D: message-id=<20121117013658.15FF2143E3D@mail.truckstop24.no>
Nov 17 02:36:58 roger-G31T-M7 postfix/bounce[14384]: 9AC61143D8B: sender non-delivery notification: 15FF2143E3D
Nov 17 02:36:58 roger-G31T-M7 postfix/qmgr[9049]: 15FF2143E3D: from=<>, size=2458, nrcpt=1 (queue active)
Nov 17 02:36:58 roger-G31T-M7 postfix/qmgr[9049]: 9AC61143D8B: removed
Nov 17 02:36:58 roger-G31T-M7 postfix/smtp[14383]: 15FF2143E3D: to=<test@testie.com>, relay=smtp.nenett.no[81.167.36.150]:25, delay=0.18, delays=0.06/0/0.04/0.08, dsn=5.7.1, status=bounced (host smtp.nenett.no[81.167.36.150] said: 554 5.7.1 <test@testie.com>: Recipient address rejected: Policy Rejection- This ip has been blacklisted. Contact your service provider if you have questions. (in reply to RCPT TO command))
Nov 17 02:36:58 roger-G31T-M7 postfix/qmgr[9049]: 15FF2143E3D: removed
Nov 17 02:37:01 roger-G31T-M7 postfix/smtpd[14370]: disconnect from 87-194-210-230.bethere.co.uk[87.194.210.230]
Nov 17 02:40:53 roger-G31T-M7 postfix/smtpd[14481]: error: unsupported dictionary type: pcre
Nov 17 02:40:53 roger-G31T-M7 postfix/smtpd[14481]: error: open /etc/postfix/bogus_mx: No such file or directory
Nov 17 02:40:53 roger-G31T-M7 postfix/smtpd[14481]: connect from 87-194-210-230.bethere.co.uk[87.194.210.230]
Nov 17 02:41:38 roger-G31T-M7 postfix/smtpd[14481]: A7465140831: client=87-194-210-230.bethere.co.uk[87.194.210.230]
Nov 17 02:41:52 roger-G31T-M7 postfix/cleanup[14487]: A7465140831: message-id=<>
Nov 17 02:41:52 roger-G31T-M7 postfix/qmgr[9049]: A7465140831: from=<me@truckstop24.no>, size=244, nrcpt=1 (queue active)
Nov 17 02:41:53 roger-G31T-M7 postfix/smtp[14490]: A7465140831: to=<bzgigley@sharklasers.com>, relay=smtp.nenett.no[81.167.36.150]:25, delay=30, delays=30/0/0.05/0.08, dsn=5.7.1, status=bounced (host smtp.nenett.no[81.167.36.150] said: 554 5.7.1 <bzgigley@sharklasers.com>: Recipient address rejected: Policy Rejection- This ip has been blacklisted. Contact your service provider if you have questions. (in reply to RCPT TO command))
Nov 17 02:41:53 roger-G31T-M7 postfix/cleanup[14487]: 15535143E3D: message-id=<20121117014153.15535143E3D@mail.truckstop24.no>
Nov 17 02:41:53 roger-G31T-M7 postfix/bounce[14491]: A7465140831: sender non-delivery notification: 15535143E3D
Nov 17 02:41:53 roger-G31T-M7 postfix/qmgr[9049]: 15535143E3D: from=<>, size=2470, nrcpt=1 (queue active)
Nov 17 02:41:53 roger-G31T-M7 postfix/qmgr[9049]: A7465140831: removed
Nov 17 02:41:53 roger-G31T-M7 postfix/local[14492]: 15535143E3D: to=<me@truckstop24.no>, relay=local, delay=0.12, delays=0.05/0.02/0/0.05, dsn=5.1.1, status=bounced (unknown user: "me")
Nov 17 02:41:53 roger-G31T-M7 postfix/qmgr[9049]: 15535143E3D: removed
Nov 17 02:42:00 roger-G31T-M7 postfix/smtpd[14481]: disconnect from 87-194-210-230.bethere.co.uk[87.194.210.230]
Nov 17 07:45:47 roger-G31T-M7 postfix/pickup[16996]: 7FEC4143E40: uid=0 from=<root>
Nov 17 07:45:47 roger-G31T-M7 postfix/cleanup[17609]: 7FEC4143E40: message-id=<20121117064547.7FEC4143E40@mail.truckstop24.no>
Nov 17 07:45:47 roger-G31T-M7 postfix/qmgr[9049]: 7FEC4143E40: from=<root@truckstop24.no>, size=490, nrcpt=1 (queue active)
Nov 17 07:45:47 roger-G31T-M7 postfix/local[17611]: 7FEC4143E40: to=<Roger@truckstop24.no>, orig_to=<root>, relay=local, delay=0.35, delays=0.22/0.01/0/0.12, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Nov 17 07:45:47 roger-G31T-M7 postfix/qmgr[9049]: 7FEC4143E40: removed
Nov 17 08:16:11 roger-G31T-M7 postfix/postfix-script[17984]: warning: not owned by postfix: /var/lib/postfix/./verify_cache



---

### Post by cryptotheslow on 2012-11-17
That's interesting - those are the logs from the couple of tests I did to see if your server would relay (hope you don't mind! :D ).

The bad thing there is that your server accepted the mail and attempted to relay it - even though it doesn't know who I am. It was your ISP's mail relay that actually blocked it based on the recipient being @sharklasers.com which is a domain used for throwaway email addresses at guerrillamail.com - so no surpise that is in a blacklist somewhere.

I more used to exim than postfix, however from here [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html) this config section looks like it should be what is required:

```

# Relay control (Postfix 2.10 and later): local clients and     # authenticated clients may specify any destination domain.
[smtpd_relay_restrictions]("http://www.postfix.org/postconf.5.html#smtpd_relay_restrictions") = [permit_mynetworks]("http://www.postfix.org/postconf.5.html#permit_mynetworks"),  	[permit_sasl_authenticated]("http://www.postfix.org/postconf.5.html#permit_sasl_authenticated"), 	[reject_unauth_destination]("http://www.postfix.org/postconf.5.html#reject_unauth_destination")

```

That will allow anyone in your $mynetworks range and anyone who authenticates to use your server to send mail to any destination.

It will also allow any mail for @truckstop24.no addresses to be accepted from anywhere. 

One thing that concerns me is that you have $mynetworks set as:
```
mynetworks = 0.0.0.0/0 [::/0]
```

That looks to me to be a wildcard setting allowing any IP to send. I think you need to tighten that control up. See here:
[http://www.postfix.org/postconf.5.html#mynetworks](http://www.postfix.org/postconf.5.html#mynetworks)

---

### Post by AvengerX9 on 2012-11-17
Thanks. I will update my main.cf file. It should look like this now

> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

myhostname = mail.truckstop24.no
mydomain = truckstop24.no
#alias_maps = hash:/etc/aliases
alias_maps = hash:/etc/postfix/aliases
#alias_database = hash:/etc/aliases
alias_database = hash:/etc/postfix/aliases
mydestination = $mydomain, $myhostname
myorigin = $mydomain
#mynetworks = 0.0.0.0/0 [::/0]
mynetworks = 79.161.88.51/24, 127.0.0.1/8
#relayhost = smtp.nenett.no
relayhost = smtp.gmail.com
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

# SASL SUPPORT FOR CLIENTS
# The following options set parameters needed by Postfix to enable 
# Cyrus-SASL support for authentication of mail clients. 
# 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
#smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, check_relay_domains
smtpd_recipient_restrictions = reject_non_fqdn_recipient, reject_unknown_recipient_domain permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_non_fqdn_hostname, reject_invalid_hostname, check_helo_access, pcre:/etc/postfix/helo_checks, check_sender_mx_access, cidr:/etc/postfix/bogus_mx, reject_rbl_client, zen.spamhaus.org, reject_rbl_client, cbl.abuseat.org, reject_rbl_client, dnsbl-1.uceprotect.net, permit

# Relay control (Postfix 2.10 and later): local clients and     
# authenticated clients may specify any destination domain.
smtpd_relay_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination

I will check out the links you gave me too :)

---

### Post by cryptotheslow on 2012-11-17
That looks better :)

One thing though.....

You have two *smtpd_recipient_restrictions =* entries.

You should add the *check_relay_domains* option to the first one and remove the second instance (in the SASL section).

Just shout if you want me to test it for open relay once you have your new settings in place :)

Another question - will google allow you to relay through their smtp??

---

### Post by cryptotheslow on 2012-11-17
> **cryptotheslow said:**
> 
Another question - will google allow you to relay through their smtp??

The answer is NO unless you are somehow using authenticated SMTP using STARTTLS.

This is what happens when trying straight SMTP:
```
crypto@ubulaptop1204:~$ telnet smtp.gmail.com 25
Trying 173.194.66.109...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP gk9sm6755645wib.4
HELO google.com
250 mx.google.com at your service
MAIL FROM: tester@google.co.uk
530 5.7.0 Must issue a STARTTLS command first. gk9sm6755645wib.4

```

As it should be really - otherwise it would also be an open relay :D

---

### Post by AvengerX9 on 2012-11-17
I tried fix it. Looks like this now, but when I use the 

```
smtpd_relay_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
```

I get this error

> Failed to start Postfix : /usr/sbin/postconf: warning: /etc/postfix/main.cf: unused parameter: smtpd_relay_restrictions=permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination


Main.cf

> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

myhostname = mail.truckstop24.no
mydomain = truckstop24.no
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
mydestination = $mydomain, $myhostname
myorigin = $mydomain
mynetworks = 79.161.88.51/24, 127.0.0.1/8
relayhost = smtp.nenett.no
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

# SASL SUPPORT FOR CLIENTS
# The following options set parameters needed by Postfix to enable 
# Cyrus-SASL support for authentication of mail clients. 
# 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_non_fqdn_recipient, reject_unknown_recipient_domain permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_non_fqdn_hostname, reject_invalid_hostname, check_helo_access, pcre:/etc/postfix/helo_checks, check_sender_mx_access, cidr:/etc/postfix/bogus_mx, reject_rbl_client, zen.spamhaus.org, reject_rbl_client, cbl.abuseat.org, reject_rbl_client, dnsbl-1.uceprotect.net, check_relay_domains, permit
smtpd_client_restrictions = permit_mynetworks, reject
smtpd_relay_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination

---

### Post by lisati on 2012-11-17
[s]You now appear to have three entries for smtpd_recipient_restrictions. You'll need to either comment two of them out or find a way of combining them.[/s] (Edit: misread)

BTW, [noparse]```
 and 
``` works better for posting copies of configuration files than >  and [/noparse] because it preserves the formatting better. For some software (including postfix), the indentation can make a different.

---

### Post by AvengerX9 on 2012-11-17
Update
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

myhostname = mail.truckstop24.no
mydomain = truckstop24.no
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
mydestination = $mydomain, $myhostname
myorigin = $mydomain
mynetworks = 79.161.88.51/24, 127.0.0.1/8
relayhost = smtp.nenett.no
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

# SASL SUPPORT FOR CLIENTS
# The following options set parameters needed by Postfix to enable 
# Cyrus-SASL support for authentication of mail clients. 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_non_fqdn_recipient, reject_unknown_recipient_domain permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_non_fqdn_hostname, reject_invalid_hostname, check_helo_access, pcre:/etc/postfix/helo_checks, check_sender_mx_access, cidr:/etc/postfix/bogus_mx, reject_rbl_client, zen.spamhaus.org, reject_rbl_client, cbl.abuseat.org, reject_rbl_client, dnsbl-1.uceprotect.net, check_relay_domains, permit
smtpd_client_restrictions = permit_mynetworks, reject
smtpd_relay_restrictions = permit_mynetworks


```


> Failed to start Postfix : /usr/sbin/postconf: warning: /etc/postfix/main.cf: unused parameter: smtpd_relay_restrictions=permit_mynetworks



---

### Post by AvengerX9 on 2012-11-17
Seems like my postfix is v 2.9.3. Is the 2.10 not available for webmin ?

---

### Post by cryptotheslow on 2012-11-17
What version of postfix are you running?

smtpd_relay_restrictions was introduced in v2.10 before that relay permissions were combined into smtpd_recipient_restrictions

---

### Post by AvengerX9 on 2012-11-17
its 2.9.3 for webmin

---

### Post by cryptotheslow on 2012-11-17
Ahh - that appears to be the version available in the Ubuntu precise repos too.

So you can't use the smtpd_relay_restrictions directive.

Leave it out and test to see if your server flags as an open relay and can send receive as you would expect.

---

### Post by AvengerX9 on 2012-11-17
How can I test that. I used this site [http://www.mailradar.com/openrelay/](http://www.mailradar.com/openrelay/) but it says the port 25 is closed

---

### Post by cryptotheslow on 2012-11-17
Is postfix up and running?

That link you have should work as should [http://mxtoolbox.com/SuperTool.aspx?action=smtp%3amail.truckstop24.no](http://mxtoolbox.com/SuperTool.aspx?action=smtp%3amail.truckstop24.no)

As far as I can see your server is not listening on port 25 which suggests postfix is not up.

---

### Post by AvengerX9 on 2012-11-17
its running, but my ISP blocked my mail someway so I can't send any mails. Is that the reason ?

---

### Post by cryptotheslow on 2012-11-17
If they have blocked inbound port 25 connections to you - then yes, that would explain it.

Not very helpful as it means you can't test your new configuration properly :(

This may not be helping either:
```
smtpd_client_restrictions = permit_mynetworks, reject
```

That means only clients in the 79.161.88.51/24, 127.0.0.1/8 ranges can use the server to send. Is that what you need?

---

### Post by AvengerX9 on 2012-11-17
hmmm. I need to give them a call and open it up again. I will post back here once its open

---

### Post by cryptotheslow on 2012-11-17
If they are being awkward about opening it up again, you could suggest that you run postfix on an alternative port temporarily whilst you make sure the config is secure.

e.g. you could run the postfix SMTP service on port 25250 and use telnet to make sure it is not acting as an open relay. Once you are happy with that, put it back on port 25 and make sure it will still correctly receive mail for your domain and allow sending by your expected clients.

Moving it off port 25 will pretty much stop any spammers from finding and using it whilst you test.

---

### Post by AvengerX9 on 2012-11-17
How would I go about temporary moving it to another port ?

---

### Post by cryptotheslow on 2012-11-17
In file /etc/postfix/master.cf

Comment out or change this line:
```
smtp    inet    n       -       -       -       -       smtpd -o
```
 to
```
25250    inet    n       -       -       -       -       smtpd -o
```

Restart postfix and smtpd should now be listening on port 25250

---

### Post by dcstar on 2012-11-18
> **AvengerX9 said:**
> Update
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version
.........
mynetworks = **79.161.88.51/24**, 127.0.0.1/8
.........


```

If your server is directly connected to the Internet with a valid External IP address then that is (almost) valid, if your server is behind a NAT Firewall with Port Forwarding then that should be the Internal IP range.

I also seriously doubt that are using 255 IP addresses in that range.

---

### Post by lisati on 2012-11-18
*Thread moved to **Server Platforms**.*

---

### Post by AvengerX9 on 2012-11-18
*double post*

---

### Post by AvengerX9 on 2012-11-18
I tried that, but I get connection refused. Do I have to add it into my iptables too ?

[http://mxtoolbox.com/SuperTool.aspx?action=smtp%3amail.truckstop24.no](http://mxtoolbox.com/SuperTool.aspx?action=smtp%3amail.truckstop24.no)

---

### Post by SeijiSensei on 2012-11-18
May I ask a broader question?  Who uses this server?  Are you supporting multiple domains and multiple clients, or just one domain?  I'm not a Postfix user, but I'm certain there is a way to configure it to accept only mail intended for your domain and reject everything else.  That's what you want to have.  Mail for [noparse]you@example.com[/noparse] is accepted and mail for [noparse]someone@somewhere.com[/noparse] is rejected.

---

### Post by AvengerX9 on 2012-11-18
I just need my website to send out mail and to receive mails for that domain.

I have one website hosted there and I'm the only user :)

---

### Post by cryptotheslow on 2012-11-18
How are you getting on with your ISP unblocking you?

---

### Post by AvengerX9 on 2012-11-19
Just called them now. It will be open sometime today. :)

---

### Post by AvengerX9 on 2012-11-19
open now. lets try

---

### Post by cryptotheslow on 2012-11-19
Well there is now certainly something listening on port 25 of mail.truckstop24.no however whilst it accepts a connection it does not respond to any input. :confused:

At least it won't be relaying anything - but it also won't be accepting mail for your domain.

---

### Post by AvengerX9 on 2012-11-20
It used to work and the only changes I did was the ones to the main.cf file

---

### Post by cryptotheslow on 2012-11-20
Can you post up what your main.cf now contains?

---

### Post by AvengerX9 on 2012-11-20
```
  # See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

myhostname = mail.truckstop24.no
mydomain = truckstop24.no
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
mydestination = $mydomain, $myhostname
myorigin = $mydomain
mynetworks = 79.161.88.51/24, 127.0.0.1/8
relayhost = smtp.nenett.no
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

# SASL SUPPORT FOR CLIENTS
# The following options set parameters needed by Postfix to enable 
# Cyrus-SASL support for authentication of mail clients. 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_non_fqdn_recipient, reject_unknown_recipient_domain permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_non_fqdn_hostname, reject_invalid_hostname, check_helo_access, pcre:/etc/postfix/helo_checks, check_sender_mx_access, cidr:/etc/postfix/bogus_mx, reject_rbl_client, zen.spamhaus.org, reject_rbl_client, cbl.abuseat.org, reject_rbl_client, dnsbl-1.uceprotect.net, check_relay_domains, permit
smtpd_client_restrictions = permit_mynetworks, reject
smtpd_relay_restrictions = permit_mynetworks      
```

---

### Post by cryptotheslow on 2012-11-20
Apparently *smtpd_use_tls=yes* was depracated in v2.3.x and you should now use instead:
```
smtpd_tls_security_level = may
```

Also you have have reintroduced *smtpd_relay_restrictions = permit_mynetworks* which we earlier discovered only works on v2.10 and up, so that line needs removing.

---

### Post by AvengerX9 on 2012-11-23
Here it is, previous was wrong
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

myhostname = mail.truckstop24.no
mydomain = truckstop24.no
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
mydestination = $mydomain, $myhostname
myorigin = $mydomain
mynetworks = 79.161.88.51/24, 127.0.0.1/8
relayhost = smtp.nenett.no
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

# SASL SUPPORT FOR CLIENTS
# The following options set parameters needed by Postfix to enable 
# Cyrus-SASL support for authentication of mail clients. 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_non_fqdn_recipient, reject_unknown_recipient_domain permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_non_fqdn_hostname, reject_invalid_hostname, check_helo_access, pcre:/etc/postfix/helo_checks, check_sender_mx_access, cidr:/etc/postfix/bogus_mx, reject_rbl_client, zen.spamhaus.org, reject_rbl_client, cbl.abuseat.org, reject_rbl_client, dnsbl-1.uceprotect.net, check_relay_domains, permit
smtpd_client_restrictions = permit_mynetworks, reject
smtpd_recipient_restrictions = permit_mynetworks

```

---

### Post by SeijiSensei on 2012-11-23
I was going to test and see if it was still an open relay by trying to push a message through manually, but "telnet mail.truckstop24.no 25" just hangs.  Are you still blocked or is the server not accepting mail?

I could visit the web site, and an nmap scan showed FTP open as well.

One thing you might want to take up with your ISP is this:

rDNS record for 79.161.88.51: 51.79-161-88.customer.lyse.net

If you will be sending mail legitmately to other SMTP servers, many of them check that the forward and reverse DNS entries match.  You should ask your ISP to make 79.161.88.51 resolve to mail.truckstop24.no rather than the generic hostname you have now.

---

### Post by AvengerX9 on 2012-11-23
I thought I had my own IP, but I dont so I have to order that. I can't access emails and I can't telnet either. Dont know whats wrong :confused:

---

### Post by lisati on 2012-11-23
> **AvengerX9 said:**
> Here it is, previous was wrong
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

myhostname = mail.truckstop24.no
mydomain = truckstop24.no
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
mydestination = $mydomain, $myhostname
myorigin = $mydomain
mynetworks = 79.161.88.51/24, 127.0.0.1/8
relayhost = smtp.nenett.no
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

# SASL SUPPORT FOR CLIENTS
# The following options set parameters needed by Postfix to enable 
# Cyrus-SASL support for authentication of mail clients. 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_non_fqdn_recipient, reject_unknown_recipient_domain permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_non_fqdn_hostname, reject_invalid_hostname, check_helo_access, pcre:/etc/postfix/helo_checks, check_sender_mx_access, cidr:/etc/postfix/bogus_mx, reject_rbl_client, zen.spamhaus.org, reject_rbl_client, cbl.abuseat.org, reject_rbl_client, dnsbl-1.uceprotect.net, check_relay_domains, permit
smtpd_client_restrictions = permit_mynetworks, reject
smtpd_recipient_restrictions = permit_mynetworks

```

I'd suggest removing the second "smtpd_recopient_restrictions" entry, and inserting a comma "," between "reject_unknown_recipient_domain" and "permit_mynetworks"

---

### Post by AvengerX9 on 2012-11-24
Okay, updated it now

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

myhostname = mail.truckstop24.no
mydomain = truckstop24.no
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
mydestination = $mydomain, $myhostname
myorigin = $mydomain
mynetworks = 79.161.88.51/24, 127.0.0.1/8
relayhost = smtp.nenett.no
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

# SASL SUPPORT FOR CLIENTS
# The following options set parameters needed by Postfix to enable 
# Cyrus-SASL support for authentication of mail clients. 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_non_fqdn_recipient, reject_unknown_recipient_domain, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_non_fqdn_hostname, reject_invalid_hostname, check_helo_access, pcre:/etc/postfix/helo_checks, check_sender_mx_access, cidr:/etc/postfix/bogus_mx, reject_rbl_client, zen.spamhaus.org, reject_rbl_client, cbl.abuseat.org, reject_rbl_client, dnsbl-1.uceprotect.net, check_relay_domains, permit
smtpd_client_restrictions = permit_mynetworks, reject
```

---

### Post by cryptotheslow on 2012-11-24
Telnet to port 25 is still timing out. Unless you have changed something with your network configuration or iptables setup or port forwarding etc. - then it seems your ISP is blocking it again.

Can you *telnet 127.0.0.1 25* when logged into the server itself? If so what response do you get if you enter an EHLO command?

---

### Post by AvengerX9 on 2012-11-25
I suddenly got this problem yesterday and its not fixed yet 

[http://ubuntuforums.org/showthread.php?t=2087781](http://ubuntuforums.org/showthread.php?t=2087781)

---

### Post by AvengerX9 on 2012-11-25
Its up now

---

### Post by cryptotheslow on 2012-11-25
Still not responding on port 25 :/

---

### Post by AvengerX9 on 2012-11-25
Not sure how to fix that. I have not set up any port forwarding for that port in my router though. Maybe thats the problem ?

---

### Post by AvengerX9 on 2012-11-25
set up port forwarding and looks like it works 

[http://mxtoolbox.com/SuperTool.aspx?action=smtp%3amail.truckstop24.no#](http://mxtoolbox.com/SuperTool.aspx?action=smtp%3amail.truckstop24.no#)

---

### Post by AvengerX9 on 2012-11-25
hmmm, just hangs when I try to telnet

---

### Post by cryptotheslow on 2012-11-25
It is working from here:
```

crypto@ubulaptop1204:~$ telnet mail.truckstop24.no 25
Trying 79.161.88.51...
Connected to mail.truckstop24.no.
Escape character is '^]'.
220 mail.truckstop24.no ESMTP Postfix (Ubuntu)
EHLO test.com
250-mail.truckstop24.no
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH DIGEST-MD5 CRAM-MD5 NTLM LOGIN PLAIN
250-AUTH=DIGEST-MD5 CRAM-MD5 NTLM LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
MAIL FROM: test@test.com
250 2.1.0 Ok
RCPT TO: bogey@bogus.com
451 4.3.0 <87-194-210-nnn.bethere.co.uk[87.194.210.nnn]>: Temporary lookup failure
RSET
250 2.0.0 Ok

```

It's also not relaying any more which is good. Is it receiving mail for your domain OK?

Are you on the LAN side of the same router trying to connect to the external IP?

A lot of domestic broadband type routers will not function like that, i.e. you can't go from the LAN to the WAN and back in via the port forward.

---

### Post by AvengerX9 on 2012-11-26
Im still not receiving any mail. Also I set up a port forwarding on the router then it worked. Tried again with port 23 and that worked too.

I'm on another computer on the same network accessing the site through the domain name/IP

---

### Post by SeijiSensei on 2012-11-26
```

[root@smtp ~]# telnet mail.truckstop24.no 25
Trying 79.161.88.51...                                          
Connected to mail.truckstop24.no.          
Escape character is '^]'.                            
220 mail.truckstop24.no ESMTP Postfix (Ubuntu)
ehlo smtp.mydomain.com
250-mail.truckstop24.no
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH DIGEST-MD5 CRAM-MD5 NTLM LOGIN PLAIN
250-AUTH=DIGEST-MD5 CRAM-MD5 NTLM LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: test@example.com
250 2.1.0 Ok
rcpt to: root@truckstop24.no
451 4.3.0 <smtp.mydomain.com[1.2.3.4]>: Temporary lookup failure

```

I replaced my SMTP server's authentic hostname name and IP address with aliases above.  I did a little browsing on Google for the "Temporary lookup failure" error, but so far I only see discussions about cases where the recipient address appears in the angle brackets within the error message.  I wonder if you have DNS properly configured on the server.  If you SSH to the machine, can you correctly resolve addresses in both directions on it?  What do you get if you type "host 8.8.8.8"?  You should see the reply 
```
8.8.8.8.in-addr.arpa domain name pointer google-public-dns-a.google.com.
```

---

### Post by cryptotheslow on 2012-11-26
As well as the DNS suggestion above, the "Temporary lookup failure" message can be caused by Postfix not being able to determine whether a particular email address is a valid local address.

Have a look in your mail logs for warnings about not being able to connect to the database, or database related errors.

---

### Post by AvengerX9 on 2012-11-30
Here is some of the last lines in my mail.log file

```
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: extract_addr: input: <Articulate-ulikhky1jryhhihlik1r@createsend5.com>
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: smtpd_check_addr: addr=Articulate-ulikhky1jryhhihlik1r@createsend5.com
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: connect to subsystem private/rewrite
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: send attr request = rewrite
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: send attr rule = local
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: send attr address = [email]Articulate-ulikhky1jryhhihlik1r@createsend5.com[/email]
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: flags
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: flags
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute value: 0
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: address
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: address
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute value: [email]Articulate-ulikhky1jryhhihlik1r@createsend5.com[/email]
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: (list terminator)
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: (end)
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: rewrite_clnt: local: [email]Articulate-ulikhky1jryhhihlik1r@createsend5.com[/email] -> [email]Articulate-ulikhky1jryhhihlik1r@createsend5.com[/email]
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: send attr request = resolve
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: send attr sender = 
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: send attr address = [email]Articulate-ulikhky1jryhhihlik1r@createsend5.com[/email]
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: flags
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: flags
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute value: 0
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: transport
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: transport
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute value: smtp
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: nexthop
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: nexthop
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute value: smtp.nenett.no
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: recipient
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: recipient
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute value: [email]Articulate-ulikhky1jryhhihlik1r@createsend5.com[/email]
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: flags
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: flags
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute value: 4096
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: (list terminator)
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: (end)
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: resolve_clnt: `' -> `Articulate-ulikhky1jryhhihlik1r@createsend5.com' -> transp=`smtp' host=`smtp.nenett.no' rcpt=`Articulate-ulikhky1jryhhihlik1r@createsend5.com' flags= class=default
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: ctable_locate: install entry key [email]Articulate-ulikhky1jryhhihlik1r@createsend5.com[/email]
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: extract_addr: in: <Articulate-ulikhky1jryhhihlik1r@createsend5.com>, result: [email]Articulate-ulikhky1jryhhihlik1r@createsend5.com[/email]
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: smtpd_check_rewrite: trying: permit_inet_interfaces
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: permit_inet_interfaces: mx107.b.outbound.createsend.com 27.126.146.107
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: fsspace: .: block size 4096, blocks free 6906953
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: smtpd_check_queue: blocks 4096 avail 6906953 min_free 0 msg_size_limit 10240000
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: > mx107.b.outbound.createsend.com[27.126.146.107]: 250 2.1.0 Ok
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: < mx107.b.outbound.createsend.com[27.126.146.107]: RCPT TO:<roger@truckstop24.no> NOTIFY=FAILURE
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: extract_addr: input: <roger@truckstop24.no>
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: smtpd_check_addr: addr=roger@truckstop24.no
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: send attr request = rewrite
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: send attr rule = local
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: send attr address = [email]roger@truckstop24.no[/email]
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: flags
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: flags
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute value: 0
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: address
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: address
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute value: [email]roger@truckstop24.no[/email]
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: (list terminator)
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: (end)
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: rewrite_clnt: local: [email]roger@truckstop24.no[/email] -> [email]roger@truckstop24.no[/email]
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: send attr request = resolve
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: send attr sender = 
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: send attr address = [email]roger@truckstop24.no[/email]
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: flags
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: flags
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute value: 0
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: transport
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: transport
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute value: local
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: nexthop
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: nexthop
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute value: mail.truckstop24.no
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: recipient
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: recipient
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute value: [email]roger@truckstop24.no[/email]
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: flags
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: flags
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute value: 256
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: private/rewrite socket: wanted attribute: (list terminator)
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: input attribute name: (end)
Nov 30 20:33:05 roger-G31T-M7 postfix/smtpd[2935]: resolve_clnt: `' -> `roger@truckstop24.no' -> transp=`local' host=`mail.truckstop24.no' rcpt=`roger@truckstop24.no' flags= class=local
Nov 30 20:34:45 roger-G31T-M7 postfix/smtpd[2935]: idle timeout -- exiting
Nov 30 20:36:26 roger-G31T-M7 postfix/anvil[2937]: statistics: max connection rate 1/60s for (smtp:27.126.146.107) at Nov 30 20:33:05
Nov 30 20:36:26 roger-G31T-M7 postfix/anvil[2937]: statistics: max connection count 1 for (smtp:27.126.146.107) at Nov 30 20:33:05
Nov 30 20:36:26 roger-G31T-M7 postfix/anvil[2937]: statistics: max cache size 1 at Nov 30 20:33:05
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: name_mask: all
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: inet_addr_local: configured 2 IPv4 addresses
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: inet_addr_local: configured 2 IPv6 addresses
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: process generation: 60 (60)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: mynetworks ~? debug_peer_list
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: mynetworks ~? fast_flush_domains
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: mynetworks ~? mynetworks
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: relay_domains ~? debug_peer_list
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: relay_domains ~? fast_flush_domains
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: relay_domains ~? mynetworks
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: relay_domains ~? permit_mx_backup_networks
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: relay_domains ~? qmqpd_authorized_clients
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: relay_domains ~? smtpd_access_maps
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_list_match: relay_domains: no match
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: permit_mx_backup_networks ~? debug_peer_list
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: permit_mx_backup_networks ~? fast_flush_domains
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: permit_mx_backup_networks ~? mynetworks
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: permit_mx_backup_networks ~? permit_mx_backup_networks
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: connect to subsystem private/proxymap
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr request = open
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr table = unix:passwd.byname
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr flags = 0
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/proxymap socket: wanted attribute: status
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: status
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: 0
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/proxymap socket: wanted attribute: flags
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: flags
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: 16
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/proxymap socket: wanted attribute: (list terminator)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: (end)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: dict_proxy_open: connect to map=unix:passwd.byname status=0 server_flags=fixed
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: dict_open: proxy:unix:passwd.byname
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: Compiled against Berkeley DB: 5.1.25?
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: Run-time linked against Berkeley DB: 5.1.25?
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: error: open database /etc/postfix/aliases.db: No such file or directory
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: dict_open: hash:/etc/postfix/aliases
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: smtpd_access_maps ~? debug_peer_list
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: smtpd_access_maps ~? fast_flush_domains
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: smtpd_access_maps ~? mynetworks
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: smtpd_access_maps ~? permit_mx_backup_networks
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: smtpd_access_maps ~? qmqpd_authorized_clients
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: smtpd_access_maps ~? smtpd_access_maps
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: error: unsupported dictionary type: pcre
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: error: open /etc/postfix/bogus_mx: No such file or directory
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: dict_open: cidr:/etc/postfix/bogus_mx
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: unknown_helo_hostname_tempfail_action = defer_if_permit
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: unknown_address_tempfail_action = defer_if_permit
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: unverified_recipient_tempfail_action = defer_if_permit
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: unverified_sender_tempfail_action = defer_if_permit
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: xsasl_cyrus_server_init: SASL config file is smtpd.conf
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: name_mask: 0
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: auto_clnt_create: transport=local endpoint=private/tlsmgr
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: auto_clnt_open: connected to private/tlsmgr
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr request = seed
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr size = 32
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/tlsmgr: wanted attribute: status
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: status
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: 0
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/tlsmgr: wanted attribute: seed
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: seed
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: FT+PW3nTP4hNRZV6n2XvKk99I++tSfer/qt7tSEDlrA=
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/tlsmgr: wanted attribute: (list terminator)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: (end)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr request = policy
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr cache_type = smtpd
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/tlsmgr: wanted attribute: status
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: status
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: 0
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/tlsmgr: wanted attribute: cachable
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: cachable
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: 1
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/tlsmgr: wanted attribute: (list terminator)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: (end)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: fast_flush_domains ~? debug_peer_list
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_string: fast_flush_domains ~? fast_flush_domains
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: auto_clnt_create: transport=local endpoint=private/anvil
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: connection established
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: master_notify: status 0
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: name_mask: resource
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: name_mask: software
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: connect from mx107.b.outbound.createsend.com[27.126.146.107]
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_list_match: mx107.b.outbound.createsend.com: no match
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_list_match: 27.126.146.107: no match
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_list_match: mx107.b.outbound.createsend.com: no match
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_list_match: 27.126.146.107: no match
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: smtp_stream_setup: maxtime=300 enable_deadline=0
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_hostname: mx107.b.outbound.createsend.com ~? 79.161.88.51/24
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_hostaddr: 27.126.146.107 ~? 79.161.88.51/24
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: warning: non-null host address bits in "79.161.88.51/24", perhaps you should use "79.161.88.0/24" instead
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: auto_clnt_open: connected to private/anvil
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr request = connect
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr ident = smtp:27.126.146.107
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/anvil: wanted attribute: status
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: status
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: 0
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/anvil: wanted attribute: count
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: count
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: 1
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/anvil: wanted attribute: rate
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: rate
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: 1
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/anvil: wanted attribute: (list terminator)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: (end)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: > mx107.b.outbound.createsend.com[27.126.146.107]: 220 mail.truckstop24.no ESMTP Postfix (Ubuntu)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: xsasl_cyrus_server_create: SASL service=smtp, realm=mail.truckstop24.no
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: name_mask: noanonymous
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: < mx107.b.outbound.createsend.com[27.126.146.107]: EHLO mx107.b.outbound.createsend.com
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_list_match: mx107.b.outbound.createsend.com: no match
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: match_list_match: 27.126.146.107: no match
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: > mx107.b.outbound.createsend.com[27.126.146.107]: 250-mail.truckstop24.no
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: > mx107.b.outbound.createsend.com[27.126.146.107]: 250-PIPELINING
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: > mx107.b.outbound.createsend.com[27.126.146.107]: 250-SIZE 10240000
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: > mx107.b.outbound.createsend.com[27.126.146.107]: 250-VRFY
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: > mx107.b.outbound.createsend.com[27.126.146.107]: 250-ETRN
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: > mx107.b.outbound.createsend.com[27.126.146.107]: 250-STARTTLS
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: > mx107.b.outbound.createsend.com[27.126.146.107]: 250-AUTH DIGEST-MD5 CRAM-MD5 NTLM LOGIN PLAIN
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: > mx107.b.outbound.createsend.com[27.126.146.107]: 250-AUTH=DIGEST-MD5 CRAM-MD5 NTLM LOGIN PLAIN
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: > mx107.b.outbound.createsend.com[27.126.146.107]: 250-ENHANCEDSTATUSCODES
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: > mx107.b.outbound.createsend.com[27.126.146.107]: 250-8BITMIME
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: > mx107.b.outbound.createsend.com[27.126.146.107]: 250 DSN
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: < mx107.b.outbound.createsend.com[27.126.146.107]: MAIL FROM:<Articulate-ulikhky1jryhhihlik1r@createsend5.com> BODY=8BITMIME
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: extract_addr: input: <Articulate-ulikhky1jryhhihlik1r@createsend5.com>
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: smtpd_check_addr: addr=Articulate-ulikhky1jryhhihlik1r@createsend5.com
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: connect to subsystem private/rewrite
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr request = rewrite
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr rule = local
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr address = [email]Articulate-ulikhky1jryhhihlik1r@createsend5.com[/email]
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: flags
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: flags
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: 0
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: address
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: address
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: [email]Articulate-ulikhky1jryhhihlik1r@createsend5.com[/email]
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: (list terminator)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: (end)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: rewrite_clnt: local: [email]Articulate-ulikhky1jryhhihlik1r@createsend5.com[/email] -> [email]Articulate-ulikhky1jryhhihlik1r@createsend5.com[/email]
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr request = resolve
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr sender = 
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr address = [email]Articulate-ulikhky1jryhhihlik1r@createsend5.com[/email]
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: flags
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: flags
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: 0
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: transport
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: transport
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: smtp
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: nexthop
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: nexthop
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: smtp.nenett.no
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: recipient
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: recipient
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: [email]Articulate-ulikhky1jryhhihlik1r@createsend5.com[/email]
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: flags
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: flags
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: 4096
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: (list terminator)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: (end)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: resolve_clnt: `' -> `Articulate-ulikhky1jryhhihlik1r@createsend5.com' -> transp=`smtp' host=`smtp.nenett.no' rcpt=`Articulate-ulikhky1jryhhihlik1r@createsend5.com' flags= class=default
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: ctable_locate: install entry key [email]Articulate-ulikhky1jryhhihlik1r@createsend5.com[/email]
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: extract_addr: in: <Articulate-ulikhky1jryhhihlik1r@createsend5.com>, result: [email]Articulate-ulikhky1jryhhihlik1r@createsend5.com[/email]
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: smtpd_check_rewrite: trying: permit_inet_interfaces
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: permit_inet_interfaces: mx107.b.outbound.createsend.com 27.126.146.107
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: fsspace: .: block size 4096, blocks free 6906993
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: smtpd_check_queue: blocks 4096 avail 6906993 min_free 0 msg_size_limit 10240000
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: > mx107.b.outbound.createsend.com[27.126.146.107]: 250 2.1.0 Ok
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: < mx107.b.outbound.createsend.com[27.126.146.107]: RCPT TO:<roger@truckstop24.no> NOTIFY=FAILURE
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: extract_addr: input: <roger@truckstop24.no>
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: smtpd_check_addr: addr=roger@truckstop24.no
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr request = rewrite
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr rule = local
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr address = [email]roger@truckstop24.no[/email]
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: flags
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: flags
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: 0
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: address
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: address
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: [email]roger@truckstop24.no[/email]
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: (list terminator)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: (end)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: rewrite_clnt: local: [email]roger@truckstop24.no[/email] -> [email]roger@truckstop24.no[/email]
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr request = resolve
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr sender = 
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: send attr address = [email]roger@truckstop24.no[/email]
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: flags
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: flags
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: 0
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: transport
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: transport
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: local
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: nexthop
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: nexthop
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: mail.truckstop24.no
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: recipient
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: recipient
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: [email]roger@truckstop24.no[/email]
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: flags
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: flags
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute value: 256
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: private/rewrite socket: wanted attribute: (list terminator)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: input attribute name: (end)
Nov 30 20:43:06 roger-G31T-M7 postfix/smtpd[3087]: resolve_clnt: `' -> `roger@truckstop24.no' -> transp=`local' host=`mail.truckstop24.no' rcpt=`roger@truckstop24.no' flags= class=local
Nov 30 20:44:46 roger-G31T-M7 postfix/smtpd[3087]: idle timeout -- exiting
```

---

### Post by AvengerX9 on 2013-04-03
hmmm hope the thread is not to old to bring back. Still need help on this issue. I can send emails, but not receive

[http://mxtoolbox.com/SuperTool.aspx?action=mx%3amail.truckstop24.no#](http://mxtoolbox.com/SuperTool.aspx?action=mx%3amail.truckstop24.no#)

Here is the current mail.log file

```

Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: name_mask: all
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: inet_addr_local: configured 2 IPv4 addresses
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: inet_addr_local: configured 2 IPv6 addresses
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: process generation: 4 (4)
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: mynetworks ~? debug_peer_list
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: mynetworks ~? fast_flush_domains
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: mynetworks ~? mynetworks
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: relay_domains ~? debug_peer_list
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: relay_domains ~? fast_flush_domains
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: relay_domains ~? mynetworks
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: relay_domains ~? permit_mx_backup_networks
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: relay_domains ~? qmqpd_authorized_clients
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: relay_domains ~? smtpd_access_maps
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_list_match: relay_domains: no match
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: permit_mx_backup_networks ~? debug_peer_list
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: permit_mx_backup_networks ~? fast_flush_domains
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: permit_mx_backup_networks ~? mynetworks
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: permit_mx_backup_networks ~? permit_mx_backup_networks
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: connect to subsystem private/proxymap
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: send attr request = open
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: send attr table = unix:passwd.byname
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: send attr flags = 0
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/proxymap socket: wanted attribute: status
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: status
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 0
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/proxymap socket: wanted attribute: flags
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: flags
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 16
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/proxymap socket: wanted attribute: (list terminator)
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: (end)
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: dict_proxy_open: connect to map=unix:passwd.byname status=0 server_flags=fixed
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: dict_open: proxy:unix:passwd.byname
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: Compiled against Berkeley DB: 5.1.25?
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: Run-time linked against Berkeley DB: 5.1.25?
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: error: open database /etc/aliases.db: No such file or directory
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: dict_open: hash:/etc/aliases
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: smtpd_access_maps ~? debug_peer_list
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: smtpd_access_maps ~? fast_flush_domains
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: smtpd_access_maps ~? mynetworks
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: smtpd_access_maps ~? permit_mx_backup_networks
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: smtpd_access_maps ~? qmqpd_authorized_clients
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: smtpd_access_maps ~? smtpd_access_maps
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: unknown_helo_hostname_tempfail_action = defer_if_permit
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: unknown_address_tempfail_action = defer_if_permit
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: unverified_recipient_tempfail_action = defer_if_permit
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: unverified_sender_tempfail_action = defer_if_permit
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: name_mask: 0
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: auto_clnt_create: transport=local endpoint=private/tlsmgr
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: auto_clnt_open: connected to private/tlsmgr
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: send attr request = seed
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: send attr size = 32
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/tlsmgr: wanted attribute: status
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: status
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 0
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/tlsmgr: wanted attribute: seed
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: seed
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: iatwM+qSLJDAlVHc/aMM3EScIdlPeesMYyDURrzfziI=
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/tlsmgr: wanted attribute: (list terminator)
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: (end)
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: send attr request = policy
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: send attr cache_type = smtpd
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/tlsmgr: wanted attribute: status
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: status
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 0
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/tlsmgr: wanted attribute: cachable
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: cachable
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 1
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/tlsmgr: wanted attribute: (list terminator)
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: (end)
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: fast_flush_domains ~? debug_peer_list
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_string: fast_flush_domains ~? fast_flush_domains
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: auto_clnt_create: transport=local endpoint=private/anvil
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: connection established
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: master_notify: status 0
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: name_mask: resource
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: name_mask: software
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: connect from mxtb-pws3.mxtoolbox.com[64.20.227.133]
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_list_match: mxtb-pws3.mxtoolbox.com: no match
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_list_match: 64.20.227.133: no match
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_list_match: mxtb-pws3.mxtoolbox.com: no match
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_list_match: 64.20.227.133: no match
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: smtp_stream_setup: maxtime=300 enable_deadline=0
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_hostname: mxtb-pws3.mxtoolbox.com ~? 79.161.88.51/24
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_hostaddr: 64.20.227.133 ~? 79.161.88.51/24
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: warning: non-null host address bits in "79.161.88.51/24", perhaps you should use "79.161.88.0/24" instead
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: auto_clnt_open: connected to private/anvil
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: send attr request = connect
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: send attr ident = smtp:64.20.227.133
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/anvil: wanted attribute: status
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: status
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 0
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/anvil: wanted attribute: count
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: count
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 1
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/anvil: wanted attribute: rate
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: rate
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 1
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/anvil: wanted attribute: (list terminator)
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: (end)
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: > mxtb-pws3.mxtoolbox.com[64.20.227.133]: 220 mail.truckstop24.no ESMTP Postfix (Ubuntu)
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: < mxtb-pws3.mxtoolbox.com[64.20.227.133]: EHLO please-read-policy.mxtoolbox.com
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_list_match: mxtb-pws3.mxtoolbox.com: no match
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: match_list_match: 64.20.227.133: no match
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: > mxtb-pws3.mxtoolbox.com[64.20.227.133]: 250-mail.truckstop24.no
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: > mxtb-pws3.mxtoolbox.com[64.20.227.133]: 250-PIPELINING
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: > mxtb-pws3.mxtoolbox.com[64.20.227.133]: 250-SIZE 10240000
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: > mxtb-pws3.mxtoolbox.com[64.20.227.133]: 250-VRFY
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: > mxtb-pws3.mxtoolbox.com[64.20.227.133]: 250-ETRN
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: > mxtb-pws3.mxtoolbox.com[64.20.227.133]: 250-STARTTLS
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: > mxtb-pws3.mxtoolbox.com[64.20.227.133]: 250-ENHANCEDSTATUSCODES
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: > mxtb-pws3.mxtoolbox.com[64.20.227.133]: 250-8BITMIME
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: > mxtb-pws3.mxtoolbox.com[64.20.227.133]: 250 DSN
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: < mxtb-pws3.mxtoolbox.com[64.20.227.133]: MAIL FROM: <supertool@mxtoolbox.com>
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: extract_addr: input: <supertool@mxtoolbox.com>
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: smtpd_check_addr: addr=supertool@mxtoolbox.com
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: connect to subsystem private/rewrite
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: send attr request = rewrite
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: send attr rule = local
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: send attr address = [email]supertool@mxtoolbox.com[/email]
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: flags
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: flags
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 0
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: address
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: address
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: [email]supertool@mxtoolbox.com[/email]
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: (list terminator)
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: (end)
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: rewrite_clnt: local: [email]supertool@mxtoolbox.com[/email] -> [email]supertool@mxtoolbox.com[/email]
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: send attr request = resolve
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: send attr sender = 
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: send attr address = [email]supertool@mxtoolbox.com[/email]
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: flags
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: flags
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 0
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: transport
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: transport
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: smtp
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: nexthop
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: nexthop
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: smtp.nenett.no
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: recipient
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: recipient
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: [email]supertool@mxtoolbox.com[/email]
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: flags
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: flags
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 4096
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: (list terminator)
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: (end)
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: resolve_clnt: `' -> `supertool@mxtoolbox.com' -> transp=`smtp' host=`smtp.nenett.no' rcpt=`supertool@mxtoolbox.com' flags= class=default
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: ctable_locate: install entry key [email]supertool@mxtoolbox.com[/email]
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: extract_addr: in: <supertool@mxtoolbox.com>, result: [email]supertool@mxtoolbox.com[/email]
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: smtpd_check_rewrite: trying: permit_inet_interfaces
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: permit_inet_interfaces: mxtb-pws3.mxtoolbox.com 64.20.227.133
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: fsspace: .: block size 4096, blocks free 4971864
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: smtpd_check_queue: blocks 4096 avail 4971864 min_free 0 msg_size_limit 10240000
Apr  4 00:00:02 roger-G31T-M7 postfix/smtpd[29237]: > mxtb-pws3.mxtoolbox.com[64.20.227.133]: 250 2.1.0 Ok
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: < mxtb-pws3.mxtoolbox.com[64.20.227.133]: RCPT TO: <test@example.com>
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: extract_addr: input: <test@example.com>
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: smtpd_check_addr: addr=test@example.com
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: send attr request = rewrite
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: send attr rule = local
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: send attr address = [email]test@example.com[/email]
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: flags
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: flags
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 0
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: address
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: address
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: [email]test@example.com[/email]
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: (list terminator)
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: (end)
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: rewrite_clnt: local: [email]test@example.com[/email] -> [email]test@example.com[/email]
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: send attr request = resolve
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: send attr sender = 
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: send attr address = [email]test@example.com[/email]
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: flags
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: flags
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 0
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: transport
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: transport
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: smtp
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: nexthop
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: nexthop
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: smtp.nenett.no
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: recipient
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: recipient
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: [email]test@example.com[/email]
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: flags
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: flags
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 4096
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: (list terminator)
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: (end)
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: resolve_clnt: `' -> `test@example.com' -> transp=`smtp' host=`smtp.nenett.no' rcpt=`test@example.com' flags= class=default
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: ctable_locate: install entry key [email]test@example.com[/email]
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: extract_addr: in: <test@example.com>, result: [email]test@example.com[/email]
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: send attr request = rewrite
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: send attr rule = local
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: send attr address = double-bounce
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: flags
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: flags
Apr  4 00:00:03 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 0
Apr  4 00:00:08 roger-G31T-M7 postfix/smtpd[29237]: rewrite stream disconnect
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: connection established
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: master_notify: status 0
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: name_mask: resource
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: name_mask: software
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: connect from mail-ee0-f52.google.com[74.125.83.52]
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: match_list_match: mail-ee0-f52.google.com: no match
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: match_list_match: 74.125.83.52: no match
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: match_list_match: mail-ee0-f52.google.com: no match
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: match_list_match: 74.125.83.52: no match
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: smtp_stream_setup: maxtime=300 enable_deadline=0
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: match_hostname: mail-ee0-f52.google.com ~? 79.161.88.51/24
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: match_hostaddr: 74.125.83.52 ~? 79.161.88.51/24
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: warning: non-null host address bits in "79.161.88.51/24", perhaps you should use "79.161.88.0/24" instead
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr request = connect
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr ident = smtp:74.125.83.52
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/anvil: wanted attribute: status
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: status
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 0
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/anvil: wanted attribute: count
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: count
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 1
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/anvil: wanted attribute: rate
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: rate
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 1
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/anvil: wanted attribute: (list terminator)
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: (end)
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 220 mail.truckstop24.no ESMTP Postfix (Ubuntu)
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: < mail-ee0-f52.google.com[74.125.83.52]: EHLO mail-ee0-f52.google.com
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: match_list_match: mail-ee0-f52.google.com: no match
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: match_list_match: 74.125.83.52: no match
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250-mail.truckstop24.no
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250-PIPELINING
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250-SIZE 10240000
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250-VRFY
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250-ETRN
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250-STARTTLS
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250-ENHANCEDSTATUSCODES
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250-8BITMIME
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250 DSN
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: < mail-ee0-f52.google.com[74.125.83.52]: STARTTLS
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 220 2.0.0 Ready to start TLS
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: auto_clnt_open: connected to private/tlsmgr
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr request = seed
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr size = 32
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/tlsmgr: wanted attribute: status
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: status
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 0
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/tlsmgr: wanted attribute: seed
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: seed
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: /uOXNIn54/OXOzfgEvXAGQw3p0uLi1sgmFHAlzI+jR4=
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/tlsmgr: wanted attribute: (list terminator)
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: (end)
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: < mail-ee0-f52.google.com[74.125.83.52]: EHLO mail-ee0-f52.google.com
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: match_list_match: mail-ee0-f52.google.com: no match
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: match_list_match: 74.125.83.52: no match
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250-mail.truckstop24.no
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250-PIPELINING
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250-SIZE 10240000
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250-VRFY
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250-ETRN
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250-ENHANCEDSTATUSCODES
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250-8BITMIME
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250 DSN
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: < mail-ee0-f52.google.com[74.125.83.52]: MAIL FROM:<roger.andersen@gmail.com>
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: extract_addr: input: <roger.andersen@gmail.com>
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: smtpd_check_addr: addr=roger.andersen@gmail.com
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: connect to subsystem private/rewrite
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr request = rewrite
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr rule = local
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr address = [email]roger.andersen@gmail.com[/email]
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: flags
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: flags
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 0
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: address
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: address
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: [email]roger.andersen@gmail.com[/email]
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: (list terminator)
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: (end)
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: rewrite_clnt: local: [email]roger.andersen@gmail.com[/email] -> [email]roger.andersen@gmail.com[/email]
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr request = resolve
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr sender = 
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr address = [email]roger.andersen@gmail.com[/email]
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: flags
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: flags
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 0
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: transport
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: transport
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: smtp
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: nexthop
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: nexthop
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: smtp.nenett.no
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: recipient
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: recipient
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: [email]roger.andersen@gmail.com[/email]
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: flags
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: flags
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 4096
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: (list terminator)
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: (end)
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: resolve_clnt: `' -> `roger.andersen@gmail.com' -> transp=`smtp' host=`smtp.nenett.no' rcpt=`roger.andersen@gmail.com' flags= class=default
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: ctable_locate: install entry key [email]roger.andersen@gmail.com[/email]
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: extract_addr: in: <roger.andersen@gmail.com>, result: [email]roger.andersen@gmail.com[/email]
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: smtpd_check_rewrite: trying: permit_inet_interfaces
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: permit_inet_interfaces: mail-ee0-f52.google.com 74.125.83.52
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: fsspace: .: block size 4096, blocks free 4971848
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: smtpd_check_queue: blocks 4096 avail 4971848 min_free 0 msg_size_limit 10240000
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 250 2.1.0 Ok
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: < mail-ee0-f52.google.com[74.125.83.52]: RCPT TO:<roger@truckstop24.no>
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: extract_addr: input: <roger@truckstop24.no>
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: smtpd_check_addr: addr=roger@truckstop24.no
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr request = rewrite
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr rule = local
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr address = [email]roger@truckstop24.no[/email]
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: flags
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: flags
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 0
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: address
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: address
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: [email]roger@truckstop24.no[/email]
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: (list terminator)
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: (end)
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: rewrite_clnt: local: [email]roger@truckstop24.no[/email] -> [email]roger@truckstop24.no[/email]
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr request = resolve
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr sender = 
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr address = [email]roger@truckstop24.no[/email]
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: flags
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: flags
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 0
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: transport
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: transport
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: local
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: nexthop
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: nexthop
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: mail.truckstop24.no
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: recipient
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: recipient
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: [email]roger@truckstop24.no[/email]
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: flags
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: flags
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 256
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/rewrite socket: wanted attribute: (list terminator)
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: (end)
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: resolve_clnt: `' -> `roger@truckstop24.no' -> transp=`local' host=`mail.truckstop24.no' rcpt=`roger@truckstop24.no' flags= class=local
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: ctable_locate: install entry key [email]roger@truckstop24.no[/email]
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: extract_addr: in: <roger@truckstop24.no>, result: [email]roger@truckstop24.no[/email]
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: >>> START Recipient address RESTRICTIONS <<<
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: generic_checks: name=permit_mynetworks
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: permit_mynetworks: mail-ee0-f52.google.com 74.125.83.52
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: match_hostname: mail-ee0-f52.google.com ~? 79.161.88.51/24
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: match_hostaddr: 74.125.83.52 ~? 79.161.88.51/24
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: warning: non-null host address bits in "79.161.88.51/24", perhaps you should use "79.161.88.0/24" instead
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: generic_checks: name=permit_mynetworks status=-1
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: NOQUEUE: reject: RCPT from mail-ee0-f52.google.com[74.125.83.52]: 451 4.3.0 <roger@truckstop24.no>: Temporary lookup failure; from=<roger.andersen@gmail.com> to=<roger@truckstop24.no> proto=ESMTP helo=<mail-ee0-f52.google.com>
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 451 4.3.0 <roger@truckstop24.no>: Temporary lookup failure
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: < mail-ee0-f52.google.com[74.125.83.52]: QUIT
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: > mail-ee0-f52.google.com[74.125.83.52]: 221 2.0.0 Bye
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: match_hostname: mail-ee0-f52.google.com ~? 79.161.88.51/24
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: match_hostaddr: 74.125.83.52 ~? 79.161.88.51/24
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: warning: non-null host address bits in "79.161.88.51/24", perhaps you should use "79.161.88.0/24" instead
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr request = disconnect
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: send attr ident = smtp:74.125.83.52
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/anvil: wanted attribute: status
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: status
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute value: 0
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: private/anvil: wanted attribute: (list terminator)
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: input attribute name: (end)
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: disconnect from mail-ee0-f52.google.com[74.125.83.52]
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: master_notify: status 1
Apr  4 00:01:02 roger-G31T-M7 postfix/smtpd[29237]: connection closed
Apr  4 00:01:07 roger-G31T-M7 postfix/smtpd[29237]: auto_clnt_close: disconnect private/tlsmgr stream
Apr  4 00:01:07 roger-G31T-M7 postfix/smtpd[29237]: rewrite stream disconnect

```

---

### Post by lisati on 2013-04-03
Might not be relevant, but I spotted this:
```
error: open database /etc/aliases.db: No such file or directory
```
If you have a file */etc/aliases*, you might want to run:
```
sudo newaliases
```

I also saw this:
```
warning: non-null host address bits in "79.161.88.51/24", perhaps you should use "79.161.88.0/24" instead
```

---

### Post by AvengerX9 on 2013-04-03
I did the sudo newaliases now. I also checked the /etc/ and there is a file there called aliases. I also checked the previous setup which was /etc/postfix/aliases but there were nothing there. I also noticed the IP address issue, but the ip address I got is the first one. I dont know why it want me to change it.

Thanks :)

---

### Post by AvengerX9 on 2013-04-03
Here are some new stuff from the mail.log file

> 
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: name_mask: software
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: connect from mail-ea0-f180.google.com[209.85.215.180]
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: match_list_match: mail-ea0-f180.google.com: no match
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: match_list_match: 209.85.215.180: no match
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: match_list_match: mail-ea0-f180.google.com: no match
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: match_list_match: 209.85.215.180: no match
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: smtp_stream_setup: maxtime=300 enable_deadline=0
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: match_hostname: mail-ea0-f180.google.com ~? 79.161.88.51/24
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: match_hostaddr: 209.85.215.180 ~? 79.161.88.51/24
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: warning: non-null host address bits in "79.161.88.51/24", perhaps you should use "79.161.88.0/24" instead
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: auto_clnt_open: connected to private/anvil
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: send attr request = connect
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: send attr ident = smtp:209.85.215.180
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/anvil: wanted attribute: status
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: status
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute value: 0
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/anvil: wanted attribute: count
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: count
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute value: 1
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/anvil: wanted attribute: rate
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: rate
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute value: 1
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/anvil: wanted attribute: (list terminator)
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: (end)
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 220 mail.truckstop24.no ESMTP Postfix (Ubuntu)
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: < mail-ea0-f180.google.com[209.85.215.180]: EHLO mail-ea0-f180.google.com
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: match_list_match: mail-ea0-f180.google.com: no match
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: match_list_match: 209.85.215.180: no match
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250-mail.truckstop24.no
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250-PIPELINING
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250-SIZE 10240000
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250-VRFY
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250-ETRN
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250-STARTTLS
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250-ENHANCEDSTATUSCODES
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250-8BITMIME
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250 DSN
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: < mail-ea0-f180.google.com[209.85.215.180]: STARTTLS
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 220 2.0.0 Ready to start TLS
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: send attr request = seed
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: send attr size = 32
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/tlsmgr: wanted attribute: status
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: status
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute value: 0
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/tlsmgr: wanted attribute: seed
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: seed
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute value: y/0jVQsMQ9YtSnYDksLCtlW3A/ghNVmIY0MdgdSQ4yg=
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/tlsmgr: wanted attribute: (list terminator)
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: (end)
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: < mail-ea0-f180.google.com[209.85.215.180]: EHLO mail-ea0-f180.google.com
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: match_list_match: mail-ea0-f180.google.com: no match
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: match_list_match: 209.85.215.180: no match
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250-mail.truckstop24.no
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250-PIPELINING
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250-SIZE 10240000
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250-VRFY
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250-ETRN
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250-ENHANCEDSTATUSCODES
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250-8BITMIME
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250 DSN
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: < mail-ea0-f180.google.com[209.85.215.180]: MAIL FROM:<roger.andersen@gmail.com>
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: extract_addr: input: <roger.andersen@gmail.com>
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: smtpd_check_addr: addr=roger.andersen@gmail.com
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: connect to subsystem private/rewrite
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: send attr request = rewrite
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: send attr rule = local
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: send attr address = [email]roger.andersen@gmail.com[/email]
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/rewrite socket: wanted attribute: flags
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: flags
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute value: 0
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/rewrite socket: wanted attribute: address
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: address
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute value: [email]roger.andersen@gmail.com[/email]
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/rewrite socket: wanted attribute: (list terminator)
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: (end)
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: rewrite_clnt: local: [email]roger.andersen@gmail.com[/email] -> [email]roger.andersen@gmail.com[/email]
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: send attr request = resolve
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: send attr sender = 
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: send attr address = [email]roger.andersen@gmail.com[/email]
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/rewrite socket: wanted attribute: flags
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: flags
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute value: 0
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/rewrite socket: wanted attribute: transport
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: transport
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute value: smtp
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/rewrite socket: wanted attribute: nexthop
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: nexthop
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute value: smtp.nenett.no
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/rewrite socket: wanted attribute: recipient
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: recipient
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute value: [email]roger.andersen@gmail.com[/email]
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/rewrite socket: wanted attribute: flags
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: flags
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute value: 4096
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/rewrite socket: wanted attribute: (list terminator)
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: (end)
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: resolve_clnt: `' -> `roger.andersen@gmail.com' -> transp=`smtp' host=`smtp.nenett.no' rcpt=`roger.andersen@gmail.com' flags= class=default
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: ctable_locate: install entry key [email]roger.andersen@gmail.com[/email]
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: extract_addr: in: <roger.andersen@gmail.com>, result: [email]roger.andersen@gmail.com[/email]
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: smtpd_check_rewrite: trying: permit_inet_interfaces
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: permit_inet_interfaces: mail-ea0-f180.google.com 209.85.215.180
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: fsspace: .: block size 4096, blocks free 4970811
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: smtpd_check_queue: blocks 4096 avail 4970811 min_free 0 msg_size_limit 10240000
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: > mail-ea0-f180.google.com[209.85.215.180]: 250 2.1.0 Ok
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: < mail-ea0-f180.google.com[209.85.215.180]: RCPT TO:<roger@truckstop24.no>
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: extract_addr: input: <roger@truckstop24.no>
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: smtpd_check_addr: addr=roger@truckstop24.no
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: send attr request = rewrite
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: send attr rule = local
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: send attr address = [email]roger@truckstop24.no[/email]
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/rewrite socket: wanted attribute: flags
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: flags
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute value: 0
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/rewrite socket: wanted attribute: address
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: address
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute value: [email]roger@truckstop24.no[/email]
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/rewrite socket: wanted attribute: (list terminator)
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: (end)
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: rewrite_clnt: local: [email]roger@truckstop24.no[/email] -> [email]roger@truckstop24.no[/email]
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: send attr request = resolve
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: send attr sender = 
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: send attr address = [email]roger@truckstop24.no[/email]
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/rewrite socket: wanted attribute: flags
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute name: flags
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: input attribute value: 0
Apr  4 01:56:15 roger-G31T-M7 postfix/smtpd[3055]: private/rewrite socket: wanted attribute: transport


---

### Post by AvengerX9 on 2013-04-03
and my main.cf

> 
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific: Specifying a file name will cause the first
# line of that file to be used as the name. The Debian default
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

myhostname = mail.truckstop24.no
mydomain = truckstop24.no
alias_maps = hash:/etc/aliases
mydestination = $mydomain, $myhostname
myorigin = $mydomain
mynetworks = 79.161.88.51/24, 127.0.0.1/8
relayhost = smtp.nenett.no
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

# SASL SUPPORT FOR CLIENTS
# The following options set parameters needed by Postfix to enable 
# Cyrus-SASL support for authentication of mail clients. 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_non_fqdn_recipient, reject_unknown_recipient_domain, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_non_fqdn_hostname, reject_invalid_hostname, check_helo_access, pcre:/etc/postfix/helo_checks, check_sender_mx_access, cidr:/etc/postfix/bogus_mx, reject_rbl_client, zen.spamhaus.org, reject_rbl_client, cbl.abuseat.org, reject_rbl_client, dnsbl-1.uceprotect.net, check_relay_domains, permit



---

### Post by conradin on 2013-04-04
what firewall do you use?
evaluate how compromised your computer is. is it worth saving or should you start clean?
(choosing save the system:)
First: backup all your logs (and hope they didnt cook the logs)
2nd: disable outgoing and incoming connections on all ports (except what you need)
3: identify the services you should be running, and disable everything else.
4. harden / secure those services. 

you can get many pointers on system hardening on this forum if you tell us more about what services you should be running

---

### Post by AvengerX9 on 2013-04-05
I use iptables which I manager from within webmin. I also have a router where I manually forward the ports I need to use to this server. By starting over do you mean remove the postfix and do a new install of it ? Cause I dont think the rest of the computer is compromised. The spamming ended short time after I made the first post. The problem now is that I can't receive emails, just send them out.

---

### Post by SeijiSensei on 2013-04-05
Is the machine's IP address  79.161.88.51?  Or is that an upstream router?  Right now your mynetworks directive only allows mail sent from that address and the localhost address.  If you have an Internet-facing machine, I believe you need to use 0/0 for mynetworks to accept mail from all Internet addresses.  If you do that, you must make sure that you only accept mail for your own domain and no others.  Otherwise you will be running an open relay that spammers can exploit.  Have you read [this page of documentation]("http://www.postfix.org/BASIC_CONFIGURATION_README.html") thoroughly?

---

### Post by darkod on 2013-04-05
I'm no expert for the mail server but from networking point of view I also have problems with this: 79.161.88.51/24. If you use /24 that means it covers 256 addresses, and the most usual way to use it is replacing the whole range for the last section of the IP. Like 192.168.1.0/24 is the whole range 192.168.1.1 to 192.168.1.254.

I guess that is why the warning suggested maybe you should use 79.161.88.0/24.

I guess you put the /24 there by default but if you want to single out only one single IP, your IP, it would be like 79.161.88.51/32 I believe.

Anyway with what Sensei said you should use something like 0/0 so the discussion about the above is pointless.

---

### Post by AvengerX9 on 2013-04-05
> **SeijiSensei said:**
> Is the machine's IP address  79.161.88.51?  Or is that an upstream router?  Right now your mynetworks directive only allows mail sent from that address and the localhost address.  If you have an Internet-facing machine, I believe you need to use 0/0 for mynetworks to accept mail from all Internet addresses.  If you do that, you must make sure that you only accept mail for your own domain and no others.  Otherwise you will be running an open relay that spammers can exploit.  Have you read [this page of documentation]("http://www.postfix.org/BASIC_CONFIGURATION_README.html") thoroughly?

Thats the upstream router. There are multiple machines here and Im using port forward to the server on the router

---

### Post by AvengerX9 on 2013-04-05
> **darkod said:**
> I'm no expert for the mail server but from networking point of view I also have problems with this: 79.161.88.51/24. If you use /24 that means it covers 256 addresses, and the most usual way to use it is replacing the whole range for the last section of the IP. Like 192.168.1.0/24 is the whole range 192.168.1.1 to 192.168.1.254.

I guess that is why the warning suggested maybe you should use 79.161.88.0/24.

I guess you put the /24 there by default but if you want to single out only one single IP, your IP, it would be like 79.161.88.51/32 I believe.

Anyway with what Sensei said you should use something like 0/0 so the discussion about the above is pointless.

I changed to 79.161.88.0/24 now and I received some emails that were sent from the router. Still can't receive my test mails from gmail though. So we have moved a step forward :)

---

### Post by darkod on 2013-04-05
I would also try with the exact IP without the /24 part. That way you limit it to that IP only. Since that's your upstream router as you now explained, that should be fine.

What does the returned mail on gmail say? Usually undelivered mails have a good explanation message with error code you can google, etc.

---

### Post by AvengerX9 on 2013-04-05
This is what I get in return on gmail

> 
THIS IS A WARNING MESSAGE ONLY.

YOU DO NOT NEED TO RESEND YOUR MESSAGE.

Delivery to the following recipient has been delayed:

     [email]roger@truckstop24.no[/email]

Message will be retried for 2 more day(s)

Technical details of temporary failure:
Google tried to deliver your message, but it was rejected by the server for the recipient domain truckstop24.no by mail.truckstop24.no. [79.161.88.51].

The error that the other server returned was:
451 4.3.0 <roger@truckstop24.no>: Temporary lookup failure

----- Original message -----

DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/relaxed;
        d=gmail.com; s=20120113;
        h=mime-version:x-received:date:message-id:subject:from:to
         :content-type;
        bh=8IE5bH9zm+hgNducuxWFTS0mVHTRxClKMYkuXHGbgOY=;
        b=TANng1yjkjF0ScllUcVeH+Vs5UX0I2UC/lAPAVX1v8E3hCgZvoTn068doFqNH9ZRuv
         GER9EOjdI+BtsdJ7quGaEM811xcVQ+i4oTuFC8ZxbFW7PxC0V5dV0EVm3Tto9QWkwTwy
         HzqPB/sTgyL9xrJBpNauEHFrdLwUkWDwpgRhsWe8DZ+UXwIPvf3rn6uXQw1XVv6wfRKu
         8zfmx/QtppbwySonoD36kDEED0Cs1MB6hRzv+9J2OPjxXV7KmpdvTRSLX8a0v4fe+5ts
         dPgD9/IcxHfg+DUezE+oQ/bHosyD9p0E7J9LNugtq71h1o7Lv5YSLGj5WV8vajBGnD8f
         6irQ==
MIME-Version: 1.0
X-Received: by 10.15.45.136 with SMTP id b8mr1085725eew.11.1365035544800; Wed,
 03 Apr 2013 17:32:24 -0700 (PDT)
Received: by 10.15.25.5 with HTTP; Wed, 3 Apr 2013 17:32:24 -0700 (PDT)
Date: Thu, 4 Apr 2013 02:32:24 +0200
Message-ID: <CALtvZM_73i1B0BxhtvT-PjrQofLp+ZsvxaMmO1hkNvyRvODrVQ@mail.gmail.com>
Subject: hei roger
From: Roger Andersen <roger.andersen@gmail.com>
To: "roger@truckstop24.no" <roger@truckstop24.no>
Content-Type: multipart/alternative; boundary=089e016284a6c113e504d97e1a4d


---

### Post by AvengerX9 on 2013-04-05
I changed mynetworks to this and it works now.

```
mynetworks = 127.0.0.0/8 79.161.88.0/32
```

---

