---
title: "Postfix/Dovecot Server Headaches"
date: 2013-08-13
forum: Server Platforms
---

### Post by danielgroves on 2013-08-13
Hi,

I'm attempting to setup a postfix/dovecot mail server with ViMbAdmin as a front end to allow other to easily manage accounts on their own domains (I host quite a few sites on one VPS, and am setting up a second as a mail server). The mail server is running Ubuntu 12.04 LTS. I've been following this guide: [http://pietervogelaar.nl/ubuntu-12-04-install-postfix-dovecot-and-vimbadmin/](http://pietervogelaar.nl/ubuntu-12-04-install-postfix-dovecot-and-vimbadmin/)

I have IMAP working in Apple Mail, box currently cannot get SMTP working. These are my SMTP settings:

[img]http://cloud.danielgroves.net/5Yt2+[/img]

And this is what 'Mail Connection Doctor' says with Apple Mail:

[img]http://cloud.danielgroves.net/KLrp+[/img]

I am currently running postfix with the -v option for debugging, and this is what it is outputting in /var/log/mail.log

```
Aug 13 11:32:59 odinson postfix/smtpd[13405]: connect from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]
Aug 13 11:33:00 odinson postfix/smtpd[13405]: SSL_accept error from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]: lost connection
Aug 13 11:33:00 odinson postfix/smtpd[13405]: lost connection after STARTTLS from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]
Aug 13 11:33:00 odinson postfix/smtpd[13405]: disconnect from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]
Aug 13 11:33:15 odinson postfix/smtpd[13411]: connect from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]
Aug 13 11:33:15 odinson postfix/smtpd[13405]: connect from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]
Aug 13 11:33:15 odinson postfix/smtpd[13411]: SSL_accept error from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]: lost connection
Aug 13 11:33:15 odinson postfix/smtpd[13411]: lost connection after STARTTLS from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]
Aug 13 11:33:15 odinson postfix/smtpd[13411]: disconnect from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]
Aug 13 11:33:15 odinson postfix/smtpd[13405]: SSL_accept error from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]: lost connection
Aug 13 11:33:15 odinson postfix/smtpd[13405]: lost connection after STARTTLS from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]
Aug 13 11:33:15 odinson postfix/smtpd[13405]: disconnect from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]
Aug 13 11:33:15 odinson postfix/smtpd[13411]: connect from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]
Aug 13 11:33:15 odinson postfix/smtpd[13411]: SSL_accept error from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]: lost connection
Aug 13 11:33:15 odinson postfix/smtpd[13411]: lost connection after STARTTLS from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]
Aug 13 11:33:15 odinson postfix/smtpd[13411]: disconnect from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]
Aug 13 11:33:15 odinson postfix/smtpd[13405]: connect from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]
Aug 13 11:33:16 odinson postfix/smtpd[13405]: SSL_accept error from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]: lost connection
Aug 13 11:33:16 odinson postfix/smtpd[13405]: lost connection after STARTTLS from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]
Aug 13 11:33:16 odinson postfix/smtpd[13405]: disconnect from host86-139-156-206.range86-139.btcentralplus.com[86.139.156.206]
```

And my Postfix Configuration:

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
smtpd_tls_auth_only = yes
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous, noplaintext
smtpd_sasl_tls_security_options = noanonymous
smtpd_recipient_restrictions =
    permit_mynetworks,
    permit_sasl_authenticated,
    reject_unauth_destination,
    reject_invalid_hostname,
    reject_unauth_pipelining,
    reject_non_fqdn_sender,
    reject_unknown_sender_domain,
    reject_non_fqdn_recipient,
    reject_unknown_recipient_domain,
    reject_rbl_client sbl.spamhaus.org,
    permit

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = odinson.danielgroves.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = odinson.danielgroves.net, localhost, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all


virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_alias_maps = mysql:/etc/postfix/mysql/virtual-aliases.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql/virtual-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql/virtual-mailboxes.cf
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1
```


I'd really appreciate any help with solving this. I've not setup a mail server before, and am somewhat stuck at the moment. 

Thanks in advance, 

Dan.

---

### Post by TheFu on 2013-08-13
Recommend you change the title to include "ViMbAdmin" - since that is REALLY what your question is about.
I know lots about postfix - ZERO about ViMbAdmin.

---

### Post by danielgroves on 2013-08-13
> **TheFu said:**
> Recommend you change the title to include "ViMbAdmin" - since that is REALLY what your question is about.
I know lots about postfix - ZERO about ViMbAdmin.

As I understand it, ViMbAdmin is simply a utility for configuring mailboxes in Dovecot. All it allows me to do as add domains, mailboxes and aliases — and doesn't deal with the login process. Surely this would be an issue with Dovecot or Postfix?

---

### Post by TheFu on 2013-08-13
Postfix is the MTA. It only knows about logins when a user "sends" email.  Usually, I do that on port 465 with SMTP/TLS (to force encryption). Normal mail transfer happens on port 25 server-to-server.  

Haven't used dovecot in years, but don't remember anything funny about getting it working.  
* [https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)
* [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3)
Might be helpful.  I never used anything but local accounts for my dovecot deployments - no mysql for users. Also, I stopped using POP3 in the mid-1990s. IMAP or nothing here, but I run corporate email systems, not ISPs. In a corporate environment, we want to encourage users to leave email on the server for access from smartphones, desktops and other integrated services (vTiger, Alfresco, ... )  anyway. For an ISP, getting users to pull email is critical, so POP3s makes sense.

The "Perfect Server" link appears to setup an ISP server just like nearly every ISP runs in my country.

Anyway - hope those links help and sorry I wasn't any use.

---

### Post by danielgroves on 2013-08-13
> Usually, I do that on port 465 with SMTP/TLS (to force encryption)

This is exactly what I want. I'm not interested in POP3 in the slightest. I won't be running any webmail either, so people will be required to use a mail client. 

I'll take a look over your links now, and hopefully I start to get somewhere. Thanks for the help.

---

### Post by TheFu on 2013-08-13
> **danielgroves said:**
> This is exactly what I want. I'm not interested in POP3 in the slightest. I won't be running any webmail either, so people will be required to use a mail client. 

I'll take a look over your links now, and hopefully I start to get somewhere. Thanks for the help.

Glad to help. Just be aware that email and DNS are the most likely UNIX services to be hacked. If you run DNS, do it chroot'd and do not make it accessible on the internet.  $20/yr pays for DNS run by pros.  Last time I was hacked was through DNS.

As to postfix, be certain you aren't an "open relay."  Definitely look for an email testing service to validate that.

Apache gets hacked a bunch these days too. I stopped using it externally about 5 yrs ago; using nginx instead. Very happy with the change for static and apps. Love the reverse proxy capabilities.

I am not a fan of web-based apps for any administrative needs. Even the most reputable have had security issues. With those, when someone breaks in, they often gain full root access. So, if you must run a webGUI for admin stuff - please, please, please, lock it down to as few IPs as possible and definitely block IPs outside countries that you don't sell services. A whitelist is probably best for you, your clients, and security.

---

### Post by danielgroves on 2013-08-14
> Glad to help. Just be aware that email and DNS are the most likely UNIX services to be hacked. If you run DNS, do it chroot'd and do not make it accessible on the internet. $20/yr pays for DNS run by pros. Last time I was hacked was through DNS.

Exactly what I'm doing now, last thing I want to do is start faffing with my own DNS server. 

> Apache gets hacked a bunch these days too. I stopped using it externally about 5 yrs ago; using nginx instead. Very happy with the change for static and apps. Love the reverse proxy capabilities.

Made this switch on my web server myself recently, haven't regretted it for a second. 

> I am not a fan of web-based apps for any administrative needs. Even the most reputable have had security issues. With those, when someone breaks in, they often gain full root access. So, if you must run a webGUI for admin stuff - please, please, please, lock it down to as few IPs as possible and definitely block IPs outside countries that you don't sell services. A whitelist is probably best for you, your clients, and security.

Again, exactly what I shall do. Incidentally I wrote a server security blog post just yesterday, would be great if you have anything to contribute to it: [http://danielgroves.net/notebook/2013/08/server-security/](http://danielgroves.net/notebook/2013/08/server-security/)


On the chance that anyone else stumbles by here, I think I'm making progress now. The TLS issues seems to be a duff SSL certificate. Used this to aid in generating a new one: [http://www.e-rave.nl/create-a-self-signed-ssl-key-for-postfix](http://www.e-rave.nl/create-a-self-signed-ssl-key-for-postfix)

Now got these errors being thrown in the logs to deal with:

```
Aug 14 11:41:45 odinson postfix/smtpd[20371]: fatal: no SASL authentication mechanisms
Aug 14 11:41:46 odinson postfix/master[20367]: warning: process /usr/lib/postfix/smtpd pid 20371 exit status 1
Aug 14 11:41:46 odinson postfix/master[20367]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
```

---

### Post by TheFu on 2013-08-14
Nice start to an article.  I won't use Disqus, so can't comment there. I dislike large, centralized services. Don't get me started on google, gmail, twitter, linkedin, ... Sorry.

No mention of backups?  **Backups are job #1 for security.** There are too many reasons to list them all. Without a backup, you'll always wonder, but with a backup, you can KNOW what happened by comparing the hacked system with the backed up files.

I write about security at my blog [http://blog.jdpfu.com/tag/security](http://blog.jdpfu.com/tag/security) too - lots. Servers, ssh, backups, encryption, best practices, nginx ... lots of stuff that I've learned over the last 15+ yrs running servers. Much of it since joining dc404 - a defcon security group.

---

### Post by danielgroves on 2013-08-14
Good shout on adding backups to it&#8230; I'll mention that in a follow-up article I'm starting to plan. I'll take a look at your security blog too &#8212; thanks!

---

