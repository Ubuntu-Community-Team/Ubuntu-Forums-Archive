---
title: "no SASL authentication mechanims - Dovecot/SASLauthD/Postfix/PAM problem"
date: 2015-10-20
forum: Server Platforms
---

### Post by defaria on 2015-10-20
I've been running an email server for years but after about 3 months my server was no longer responding so sadly I had to reboot it. After coming back up my email client (Thunderbird) started prompting for my password again and would not take it. Investigating I find error messages such as

```
postfix/smtpd[28849]: fatal: no SASL authentication mechanisms
```

and 

```
dovecot: auth: Error: auth worker: Aborted request: Lookup timed out
```

I've done a lot of googling around but have not managed to find anything that's fixed this problem (why are error messages from these particular systems so bad and so unhelpful?). 

postconf -n

```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
canonical_maps = hash:/etc/postfix/canonical
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = ipv4
local_recipient_maps =
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot.conf -m "${EXTENSION}"
mailbox_size_limit = 0
message_size_limit = 0
mydestination = $myhostname, localhost, jupiter, mail.$myhostname, clearscm.com
myhostname = defaria.com
mynetworks = 74.62.25.170 66.160.163.2 127.0.0.0/8 192.168.1.0/24
myorigin = /etc/mailname
queue_directory = /var/spool/postfix
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:/var/lib/postfix/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_enforce_tls = no
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_relay_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = reject_unknown_sender_domain
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_dh1024_param_file = /etc/postfix/dh_1024.pem
smtpd_tls_dh512_param_file = /etc/postfix/dh_512.pem
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:/var/lib/postfix/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom

```

doveconf -n 

```

# 2.2.9: /etc/dovecot/dovecot.conf
# OS: Linux 3.13.0-65-generic i686 Ubuntu 14.04.3 LTS 
auth_mechanisms = plain login
disable_plaintext_auth = no
log_timestamp = "%Y-%m-%d %H:%M:%S "
mail_privileged_group = mail
passdb {
  driver = pam
}
protocols = imap
service auth {
  unix_listener /var/spool/postfix/private/auth {
    group = postfix
    mode = 0660
    user = postfix
  }
  user = root
}
ssl_cert = </etc/ssl/selfsigned/server.crt
ssl_key = </etc/ssl/selfsigned/server.key
userdb {
  driver = passwd
}
protocol pop3 {
  pop3_uidl_format = %08Xu%08Xv
}
protocol imap {
  imap_capability = IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE SORT SORT=DISPLAY THREAD=REFERENCES THREAD=REFS MULTIAPPEND UNSELECT CHILDREN NAMESPACE UIDP LUS LIST-EXTENDED I18NLEVEL=1 ESEARCH ESORT SEARCHRES WITHIN CONTEXT=SEARCH LIST-STATUS
  mail_max_userip_connections = 20
}

```

$ doveadm auth test <user>

```

Password: <password>
passdb: andrew auth failed
extra fields:
  user=andrew
  temp

```

When this happens I get a bunch of:

```

root      1163  1153  0 12:15 ?        00:00:00 dovecot/auth -w

```

which pile up filling the process table and then I have to reboot the server.

HELP!

---

### Post by defaria on 2015-10-21
Nobody?!? 111 views and nobody has a guess?

---

### Post by defaria on 2015-10-22
Answering my own question for the benefit of others... Note that there can be many reasons why this broke down so my solution may not be your solution.

Somehow I got the idea that perhaps my password changed. I don't know why it would but I decided to set it anyway to make sure it was what I thought it should be. When I did the passwd command it hung! Ok, so let's go research that. Turns out, since I use PAM, as does dovecot in my configuration I decided to look at PAM. Looking at /etc/pam.d I noticed that the files there that started with common (common-account, common-auth, etc.) were all modified about a week ago. I'm not sure why. Updates? 

In any event I tried the passwd command on my desktop instead of my server and it did not hang. So I took the /etc/pam.d/common* files and saved them away and then copied the /etc/pam.d/common* files from my desktop to my server and put them in place. Tried passwd and it no longer hung. Tried doveadm to test that and it worked and now my Thunderbird works fine. Odd.

Hope that helps somebody else.

---

### Post by Habitual on 2015-10-22
> **defaria said:**
> Nobody?!? 111 views and nobody has a guess?
People *look* to maybe see if they can help and we are all volunteers.

Be patient. :)

---

