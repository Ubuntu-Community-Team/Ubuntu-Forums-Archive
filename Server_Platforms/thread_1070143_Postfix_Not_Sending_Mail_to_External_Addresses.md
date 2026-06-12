---
title: "Postfix Not Sending Mail to External Addresses"
date: 2009-02-14
forum: Server Platforms
---

### Post by blendmaster on 2009-02-14
Hello!

I made a thread yesterday describing some trouble I had with the default Ubuntu Mail server. Now I've made a lot of progress, but no amount of tweaks seems to let me send mail from my server to an external account (my GMail account was tested). I can receive emails from external addresses just fine however.

Since I'm not sure what the problem might be, I'll post some info here to see if you guys can help (I'm lost :P ). Assume that I own the domain 'example.com' (I have an actual domain that I'm using).

Here's my main.cf (/etc/postfix/main.cf):

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
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.example.com, localhost.localdomain, localhost, example.com
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
mail_location = maildir:/home/%u/Maildir
virtual_alias_domains = example.com
virtual_alias_maps = hash:/etc/postfix/virtual


```
hostname
```

and

```
hostname -f
```

Returns:

> MyServer

Edit:

More info:

Using telnet to send mail results in:

> 250 2.0.0 Ok: queued as 3993B90567

Checking the log in /var/log/messages shows:

> Feb 14 18:26:45 MyServer sudo: pam_sm_authenticate: Called
Feb 14 18:26:45 MyServer sudo: pam_sm_authenticate: username = [user]
Feb 14 18:26:45 MyServer sudo: Error attempting to parse .ecryptfsrc file; rc = [-5]
Feb 14 18:26:45 MyServer sudo: Unable to read salt value from user's .ecryptfsrc file; using default
Feb 14 18:26:47 MyServer sudo: Passphrase key already in keyring
Feb 14 18:26:47 MyServer sudo: There is already a key in the user session keyring for the given passphrase.


Don't know if that helps...

---

### Post by HermanAB on 2009-02-14
Some common things I can think of:
Your mail server must have a FQDN.  HOSTNAME is defined in /etc/sysconfig/network.
Test your DNS with 'dig'.  Ensure that you have a PTR record.  
Check at Spamhaus to see whether your IP range is black listed.

Cheers,

Herman

---

### Post by blendmaster on 2009-02-14
No /etc/sysconfig directory.

I assume I should create /etc/sysconfig/network and put

> mail.example.com

in the file?

Edit:

Also, Spamhaus says

> xx.xxx.xxx.0/20 is listed on the Policy Block List (PBL)

Outbound Email Policy of The Spamhaus Project for this IP range:

This IP range has been identified by Spamhaus as not meeting our policy for IPs which should deliver 'direct-to-mx' mail to PBL users.

Important: If you are using any normal email software such as Outlook, Entourage, Thunderbird, Apple Mail, and you are being blocked by this Spamhaus PBL listing when you try to send email, the reason is simply that you need to turn on "SMTP Authentication" in your email software settings (Tools : Accounts : Properties : Outgoing Mail Server : check "My server requires authentication").
If you do not know how to do this, ask your Internet Service Provider for help with "SMTP Authentication".

That seems it could be a problem...

---

### Post by HermanAB on 2009-02-14
Hmm, it looks like you need to talk to your ISP and get a new IP address.

Cheers,

Herman

---

### Post by blendmaster on 2009-02-15
> **HermanAB said:**
> Hmm, it looks like you need to talk to your ISP and get a new IP address.

Cheers,

Herman

Yeah, I guess so.

Thanks for the help though!

---

