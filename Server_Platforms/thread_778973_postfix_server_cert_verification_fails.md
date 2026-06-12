---
title: "postfix server cert verification fails"
date: 2008-05-02
forum: Server Platforms
---

### Post by dbaron on 2008-05-02
I'm trying to migrate from Fedora 8 on my old laptop to Ubuntu 8.04 on my new laptop, and I'm getting stuck configuring postfix.  (Fedora 8 uses postfix 2.4.5; Ubuntu 8.0.4 uses 2.5.1.)

I'm trying to set up mandatory-encrypted connections to a single relay host, mail.sonic.net:587.  On both systems, I can connect successfully (with "Verify return code: 0 (ok)") using
```
openssl s_client -CApath /etc/ssl/certs/ -starttls smtp -connect mail.sonic.net:587
```
(though the CApath / CAfile varies between the systems).  This shows that the server's cert should verify against the CA certs on both systems (i.e., that it's not differences between the root cert set on Fedora vs. Ubuntu).  (And I note that I don't get the "Verify return code: 0 (ok)" if I don't provide the CApath / CAfile argument to openssl.)

The problem is when I'm actually setting it up in postfix.  On my old Fedora system (where this works), when I set smtp_tls_loglevel = 2 in /etc/postfix/main.cf, it shows the cert verification in maillog like this:

```
May  2 15:43:02 ridley postfix/smtp[28558]: certificate verification depth=2 subject=/C=US/ST=UT/L=Salt Lake City/O=The USERTRUST Network/OU=http://www.usertrust.com/CN=UTN-USERFirst-Hardware
May  2 15:43:02 ridley postfix/smtp[28558]: verify return: 1
May  2 15:43:02 ridley postfix/smtp[28558]: certificate verification depth=1 subject=/C=SE/O=AddTrust AB/OU=AddTrust External TTP Network/CN=AddTrust External CA Root
May  2 15:43:02 ridley postfix/smtp[28558]: verify return: 1
May  2 15:43:02 ridley postfix/smtp[28558]: certificate verification depth=0 subject=/C=US/postalCode=95402/ST=California/L=Santa Rosa/streetAddress=2260 Apollo Way/O=Sonic.net, Inc/OU=Security/OU=InstantSSL/CN=mail.sonic.net
May  2 15:43:02 ridley postfix/smtp[28558]: verify return: 1

```

However, on my new Ubuntu system what I end up with is this:

```
May  2 09:08:04 pickering postfix/smtp[17933]: mail.sonic.net[64.142.7.162]:587:
 certificate verification depth=1 verify=0 subject=/C=SE/O=AddTrust AB/OU=AddTru
st External TTP Network/CN=AddTrust External CA Root
May  2 09:08:04 pickering postfix/smtp[17933]: certificate verification failed f
or mail.sonic.net[64.142.7.162]:587: untrusted issuer /C=US/ST=UT/L=Salt Lake Ci
ty/O=The USERTRUST Network/OU=http://www.usertrust.com/CN=UTN-USERFirst-Hardware
May  2 09:08:04 pickering postfix/smtp[17933]: mail.sonic.net[64.142.7.162]:587:
 certificate verification depth=1 verify=0 subject=/C=SE/O=AddTrust AB/OU=AddTru
st External TTP Network/CN=AddTrust External CA Root
May  2 09:08:04 pickering postfix/smtp[17933]: mail.sonic.net[64.142.7.162]:587:
 certificate verification depth=0 verify=1 subject=/C=US/postalCode=95402/ST=Cal
ifornia/L=Santa Rosa/streetAddress=2260 Apollo Way/O=Sonic.net, Inc/OU=Security/
OU=InstantSSL/CN=mail.sonic.net

```

which then leads to the mail not being delivered:

```
May  2 09:08:05 pickering postfix/smtp[17933]: 46CB93A0C3: to=<real@address.removed>, relay=mail.sonic.net[64.142.7.162]:587, delay=40121, delays=40120/0.02/0.49/0, dsn=4.7.5, status=deferred (Server certificate not trusted)

```

This makes it look like postfix for some reason isn't verifying the cert past a depth of 1, although I'm really not sure if that's the problem.

My complete /etc/postfix/main.cf is the following:
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

myhostname = pickering
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = dbaron.org, pickering, localhost.localdomain, localhost
##relayhost = [smtp.comcast.net]:587
##relayhost = [smtp.dreamhost.com]:587
#relayhost = [smtp.gmail.com]:587
relayhost = [mail.sonic.net]:587
#relayhost = [smtp.mozilla.org]:587 # doesn't work
# mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = host
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

mailbox_command = /usr/bin/procmail

smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl/auth_table
smtp_sasl_security_options = noplaintext, noanonymous, nodictionary, noactive

smtp_tls_CApath = /etc/ssl/certs/
# smtp_use_tls = yes
# smtp_enforce_tls = yes
smtp_tls_security_level = secure
#smtp_tls_security_level = encrypt
smtp_tls_secure_cert_match = mail.sonic.net
smtp_tls_loglevel = 2
smtp_tls_mandatory_protocols = TLSv1
smtp_tls_scert_verifydepth = 5

```
... though the last 4 lines were all added during debugging of this problem (and it occurred without them).

---

### Post by dbaron on 2008-05-02
Ah, I found the answer in [https://help.ubuntu.com/community/GmailPostfixFetchmail#head-1486e0007b80d2c2bbbf7c731139a73ea3bb0570](https://help.ubuntu.com/community/GmailPostfixFetchmail#head-1486e0007b80d2c2bbbf7c731139a73ea3bb0570)

I didn't realize postfix was running inside a chroot, so the certs needed to be in /var/spool/postfix/certs and the path to them in the config needed to be /certs.

---

### Post by Kepesk on 2010-07-12
Okay, I fixed this by adding the certificate it was complaining about to /etc/postfix/cacert.pem

Try looking up the certificate your postfix is complaining about and adding it to yours.

---

### Post by konti on 2011-03-24
I's having the same problem. Where do you get the certificate from? I'm trying to connect with the smtp.live.com:578 server.

---

