---
title: "Ubuntu 13.10 Mail server"
date: 2014-02-21
forum: Server Platforms
---

### Post by dave-stockinger on 2014-02-21
I am trying to setup a brand new Ubuntu 13.10 server to get emails working there.
I want to have two seperate mail-addresses (admin@foobar.com and [email]office@foobar.com[/email]).

Currently, I have dovecot and postfix installed and followed several different guides, none successfully.
Here is a list of all the guides I have followed: [http://www.rosehosting.com/blog/how-to-setup-simple-but-yet-powerful-mail-server-using-postfix-dovecot-and-sasl-in-debian-6-squeeze/](http://www.rosehosting.com/blog/how-to-setup-simple-but-yet-powerful-mail-server-using-postfix-dovecot-and-sasl-in-debian-6-squeeze/), [https://help.ubuntu.com/12.04/serverguide/email-services.html](https://help.ubuntu.com/12.04/serverguide/email-services.html), [http://wiki2.dovecot.org/HowTo/SimpleVirtualInstall](http://wiki2.dovecot.org/HowTo/SimpleVirtualInstall)

Please help me configure dovecot and postfix with those two virtual mailboxes.

---

### Post by SeijiSensei on 2014-02-21
First off, if this is going to be a production server with a long life span, do not use 13.10.  You should install a release with long-term support like 12.04LTS, or the forthcoming 14.04LTS that will be released in April.  All non-LTS versions of Ubuntu have relatively short support lifetimes; 12.04LTS will be supported through 2017; 14.04 even longer.

Did you read the [Ubuntu Server Guide]("https://help.ubuntu.com/lts/serverguide/email-services.html")?

---

### Post by Roswebnet on 2014-02-21
Hi
 
 Do you have DNS  (Bind) installed and configured?
 
 How many mail accounts you will use? If only two I believe homedir and simple sasl based on pam should be enough. IMHO

Please post your postfix (main master) and dovecot (dovecot, auth, ssl and etc..) configs. It will help us to give a better answer.

---

### Post by dave-stockinger on 2014-02-22
I have used the default dovecot config and just overwrote what I need in the local.conf:
```
protocols = imap imaps
disable_plaintext_auth = no


ssl_cert_file = /etc/ssl/certs/mail.crt
ssl_key_file = /etc/ssl/private/mail.key


mail_location = maildir:/var/mail/vhosts/%d/%n


auth default {
  mechanisms = plain login
  userdb {
    driver = passwd-file
    args = /home/vmail/foobar.com/passwd
    default_fields = uid=vmail gid=vmail home=/home/vmail/%d/%u
  }
  passdb {
    driver = passwd-file
    args = /home/vmail/foobar.com/passwd
  }
  socket listen {
    client {
      path = /var/spool/postfix/private/auth
      mode = 0660
      user = postfix
      group = vmail
    }
    master {
      path = /var/run/dovecot/auth-master
      mode = 0600
      user = vmail
      group = vmail
    }
  }
}

```

Here is my postfix' main.cf:
```
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
smtpd_tls_cert_file = /etc/dovecot/dovecot.pem
smtpd_tls_key_file = /etc/dovecot/private/dovecot.pem
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = foobar.com
mydomain = foobar.com
mydestination = foobar.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = foobar.com, localhost.lan, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot.conf -m "${EXTENSION}"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sender_restrictions = reject_unknown_sender_domain
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = yes
tls_random_source = dev:/dev/urandom


virtual_mailbox_base = /home/vmail
virtual_mailbox_maps = hash:/etc/postfix/vmailbox
virtual_mailbox_domains = foobar.com
virtual_minimum_uid = 100
virtual_uid_maps = static:2222
virtual_gid_maps = static:2222
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1


smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $mydomain
smtpd_tls_security_level = may
smtpd_tls_cert_file=/etc/ssl/certs/mail.crt
smtpd_tls_key_file=/etc/ssl/private/mail.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_received_header = yes
tls_random_source = dev:/dev/urandom
```

The vmailbox file has been postmap'd already, so that should be no problem.

---

### Post by nerdtron on 2014-02-23
For a beginner creating an full featured email server, one-click installer of iredmail works like a charm. All you need to do after the installation is to configure the DNS.
Install it on a fresh installation of Ubuntu 12.04 server. Do not choose any extra packages (relating to email) on the installation of the ubuntu server, iRedmail will install everything for you.
[http://www.iredmail.org/install_iredmail_on_ubuntu.html](http://www.iredmail.org/install_iredmail_on_ubuntu.html)

---

### Post by CharlesA on 2014-02-23
I'll leave this here:
[https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql](https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql)

:)

---

### Post by sandyd on 2014-02-24
> **dave-stockinger said:**
> I am trying to setup a brand new Ubuntu 13.10 server to get emails working there.
I want to have two seperate mail-addresses (admin@foobar.com and [email]office@foobar.com[/email]).

Currently, I have dovecot and postfix installed and followed several different guides, none successfully.
Here is a list of all the guides I have followed: [http://www.rosehosting.com/blog/how-to-setup-simple-but-yet-powerful-mail-server-using-postfix-dovecot-and-sasl-in-debian-6-squeeze/](http://www.rosehosting.com/blog/how-to-setup-simple-but-yet-powerful-mail-server-using-postfix-dovecot-and-sasl-in-debian-6-squeeze/), [https://help.ubuntu.com/12.04/serverguide/email-services.html](https://help.ubuntu.com/12.04/serverguide/email-services.html), [http://wiki2.dovecot.org/HowTo/SimpleVirtualInstall](http://wiki2.dovecot.org/HowTo/SimpleVirtualInstall)

Please help me configure dovecot and postfix with those two virtual mailboxes.

Note that iRedMail's upgrades can be a bit overwhelming at some cases.

There is also 
[LIST]
[*][Zimbra ]("http://www.zimbra.com/downloads/os-downloads.html")(which abiet its heaviness is quite nice, but might be overkill)
[*][Axigen]("http://www.axigen.com/mail-server/free/") (free for 100 users, provided that you register to get the free liscence)
[*]Exim
[*][Postfix+PostfixAdmin]("https://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/") - Guide includes postfixadmin setup, which allows you to manage postfix from the web. Reccomended that you use nginx instead of apache, and dovecot instead of horde
[/LIST]

---

### Post by brokenhachi on 2014-02-25
I agree with SeijiSensei, you should use 12.04 or if you can wait for 14.04 that might be better. Other than that, there are several turnkey solutions, but postfix is a great place to learn how linux works and what it does best. I say stick with postfix, you'll thank yourself later.

on to the problem though... can you tell us exactly what *doesn't work*? Is postfix working? How about trying a couple test messages (inbound/outbound) and posting the last bit of /var/log/maillog :)

just of the top of my head...
```


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
**myhostname = foobar.com <--- should be hostname without domain **
mydomain = foobar.com
mydestination = foobar.com
[B]alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases  <-- you don't need alias_maps and alias_database if you are using hash:/ [/b]
**myorigin = /etc/mailname <-- usually this is *$mydomain* **
mydestination = foobar.com, localhost.lan, localhost
relayhost =
**mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 <-- with this, you'll only be able to relay mail from localhost **


```

[http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html)

I don't know if that will fix the problem but maybe give it a look :D

---

