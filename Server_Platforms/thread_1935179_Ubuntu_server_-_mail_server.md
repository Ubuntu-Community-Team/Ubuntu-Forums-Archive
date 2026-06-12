---
title: "Ubuntu server - mail server"
date: 2012-03-03
forum: Server Platforms
---

### Post by Jguy on 2012-03-03
hi all,

I am trying to use courier and postfix, along with squirrelmail to provide some mail services for the 4 domains on my ubuntu server 11.04 64-bit machine. I would be the only one accessing them from a locked installation of squirrelmail.

for simplicity and private sake, they are:

domain1.com
domain2.net
domain3.net
domain4.net

domain1.com is my primary domain for everything (I access webmin, SSH and such from that domain). It also has mail.domain1.com, smtp.domain1.com and imap.domain1.com as subdomains through DNS.

All the relevent information (for note: ramuh is the machine's hostname (i.e. machine name):

/etc/hosts
```
  
127.0.0.1       localhost localhost.localdomain
69.147.230.138  domain1.com domain2.net domain3.net domain4.net ramuh

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

/etc/postfix/main.cf
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.domain1.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = /etc/mailname
mynetworks = all
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
home_mailbox = Maildir/
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_unauth_pipelining,reject_non_fqdn_recipient,reject_unknown_recipient_domain, permit
smtpd_sender_restrictions = reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

smtpd_sasl+security_options = noanonymous
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

# Virtual Mailbox Domain Settings

virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual_mailbox_limit = 5120000
virtual_minimum_uid = 5000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_transport = virtual

# Additional for quota support

virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql_virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = Sorry, the your maildir has overdrawn your diskspace quota, please free up some of spaces of your m$
virtual_overquota_bounce = yes
content_filter = smtp-amavis:[localhost]:10024
spf-policyd_time_limit = 3600s
mydomain = mail.domain1.com
```

Basically, I followed the guide here: [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto) to the letter.

for starters, no mail incoming is being delivered. I have checked my DNS settings to make sure my mx records are OK. I tried to send to [email]jguy@domain1.com[/email] and got this back:

> 
This is the mail system at host mail.domain1.com.

I'm sorry to have to inform you that your message could not be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can delete your own text from the attached returned message.

                   The mail system

<jguy@domain1.com>: Host or domain name not found. Name service error for
    name=localhost type=AAAA: Host not found

As for sending email out, when I try through squirrelmail, it takes a REALLY log time to send a message, and then it (maybe times out) shows this error: 
```

ERROR:
Message not sent. Server replied:


```

(error message blank)

MySQL connections are good, but for some reason ,the server doesn't want to send or receive mail properly. any ideas? Let me know if you have any quetions or need any information from my server.

thanks for you assistance, it is much appreciated.

---

### Post by ksudbury on 2012-03-03
Can you provide the actual domain or IP address of the mail server please?

---

### Post by volkswagner on 2012-03-03
How did you check your DNS?

What do you get when you run the following from your workstation.

```
host domain1.com
```

Can you telnet into the server on port 25?

---

### Post by Jguy on 2012-03-03
> Can you provide the actual domain or IP address of the mail server please?

Didn't think it was allowed. Domain is jemstuff.com

> 

How did you check your DNS?

What do you get when you run the following from your workstation.

```

host domain1.com
```
Can you telnet into the server on port 25?

DNS was checked by pinging mail.jemstuff.com and it returning the proper IP.

I'm not in a Linux terminal right now. doesn't seem like I can telnet from the outside of the server on port 25, though. there are no firewalls blocking port 25 on the machine. I can telnet on the server to jemstuff.com port 25 and get through, though.

---

### Post by volkswagner on 2012-03-04
it appears from the domain you mention that port 25 is open and connecting to your mail server.  It seems that the mail server does not properly respond.  You should check for some hints in your logs.

---

### Post by Jguy on 2012-03-04
Looks like I have just one issue. Mail is getting delivered from gmail, but I'm not able to send to anyone outside my server. Everything internal works. I have a feeling it's the smtpd_recipient_restrictions and smtpd_sender_resttrictions in main.cf What should those be set at? If I set them to the parameters in the guide: [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)
 It doesn't allow me to send or receive email.

Now, with both of those settings blank, I am able to send from my gmail account to 2/4 of my domains on my server (the only two I have MX records setup for at the moment), but I'm not able to send anything from either domain on my server to the outside world. I get the following in my /var/log/mail.log (by the way, [email]user@gmail.com[/email] is my gmail.com account):

> 

2141 Mar  4 14:05:42 srv124 postfix/smtpd[15133]: connect from jemstuff.com[69.147.230.138]
2142 Mar  4 14:05:42 srv124 postfix/smtpd[15133]: NOQUEUE: reject: RCPT from jemstuff.com[69.147.230.138]: 554 5.7.1 <user     @gmail.com>: Relay access denied; from=<jguy@jemstuff.com> to=<user@gmail.com> proto=ESMTP helo=<jemstuff.com>
2143 Mar  4 14:05:42 srv124 postfix/smtpd[15133]: lost connection after RCPT from jemstuff.com[69.147.230.138]
2144 Mar  4 14:05:42 srv124 postfix/smtpd[15133]: disconnect from jemstuff.com[69.147.230.138]
2145 Mar  4 14:08:09 srv124 postfix/smtpd[15142]: connect from jemstuff.com[69.147.230.138]
2146 Mar  4 14:08:09 srv124 postfix/smtpd[15142]: 3B7693A02F6: client=jemstuff.com[69.147.230.138]
2147 Mar  4 14:08:09 srv124 postfix/cleanup[15145]: 3B7693A02F6: message-id=<ef3bf058055ba5b35486abbb9ba05c87.squirrel@jemstuff     .com>
2148 Mar  4 14:08:09 srv124 postfix/qmgr[14974]: 3B7693A02F6: from=<jguy@jemstuff.com>, size=711, nrcpt=1 (queue active)
2149 Mar  4 14:08:09 srv124 postfix/smtpd[15142]: disconnect from jemstuff.com[69.147.230.138]


If I get this issue working, I'd finally have a working email server. Right now my two settings, smtpd_recipient_restrictions and smtpd_sender_restrictions in /etc/postfix/main.cf are NOT set to anything (they don't even exist). Any idea on what to throw in there?

So, at the moment, I have the following:

/etc/postfix/main.cf:

```


# See /usr/share/postfix/main.cf.dist for a commented, more complete version
# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.jemstuff.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination =
mynetworks = all
recipient_delimiter = +
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
home_mailbox = Maildir/
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes

smtpd_sasl+security_options = noanonymous
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
disable_dns_lookups = yes

# Virtual Mailbox Domain Settings

virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual_minimum_uid = 5000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_transport = virtual

# Additional for quota support

virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql_virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = Sorry, the your maildir has overdrawn your diskspace quota, please free up some of space$
virtual_overquota_bounce = yes
content_filter = smtp-amavis:[localhost]:10024
spf-policyd_time_limit = 3600s
mydomain = mail.jemstuff.com

```

and, for reference, in /etc/mailname:

```

ramuh
jemstuff.com
rathena.net
ro-world.net
vanir-online.net
rathena.org

```

...which are all the domain names that this server will handle mail for.

Again, thank you dearly for the help, it is much appreciated.

Thanks,

---

### Post by acc61287 on 2012-03-04
So your problem is you cannot send to gmail or yahoo right?

I have the same issue. I setup mail server lately, I use postfix dovecot and postfixadmin.

Your ISP blocking your outgoing port 25, basically ISP blocked outgoing port 25 because of spam and virus send by mail.

---

### Post by Jguy on 2012-03-04
> **acc61287 said:**
> So your problem is you cannot send to gmail or yahoo right?

I have the same issue. I setup mail server lately, I use postfix dovecot and postfixadmin.

Your ISP blocking your outgoing port 25, basically ISP blocked outgoing port 25 because of spam and virus send by mail.

Nah, I checked with my hosting provider, they have tons of mail servers on VPS's and dedicated servers on their network. they're not blocking port 25.

---

### Post by HermanAB on 2012-03-05
Howdy,

In general, if you can send mail to some people and not to others, then you have a DNS problem.  Check your DNS with 'dig' and ensure that the A, MX and PTR records are defined properly.

---

### Post by Jguy on 2012-03-05
> **HermanAB said:**
> Howdy,

In general, if you can send mail to some people and not to others, then you have a DNS problem.  Check your DNS with 'dig' and ensure that the A, MX and PTR records are defined properly.

I don't think it's a DNS problem...my server uses google's DNS servers (8.8.8.8 and 4.4.4.4) and I'm having issues sending to anyone not on my server, not just gmail or yahoo. I send send, say, from [email]user@rathena.net[/email] to [email]user@jemstuff.com[/email] and vise versa, and delivery and relaying work fine, but sending to anyone outside my server and I get relay access denied, pointing me to the main.cf file.

---

