---
title: "Problems with Postfix+SASL"
date: 2008-04-23
forum: Server Platforms
---

### Post by werdan on 2008-04-23
Okay, I've been working on this for a while now and I've run out of idea,s I followed the directions for setting Postfix up with SASL at [https://help.ubuntu.com/community/Postfix#head-f68719942640e75877d23519c0bfe557f1b45b5d](https://help.ubuntu.com/community/Postfix#head-f68719942640e75877d23519c0bfe557f1b45b5d) and I've gotten it accepting my connection, but I can't for the life of me get it to accept my username and password, it just keeps asking over and over (so it's not being accepted). 

I want this going off of the passwd file and I assumed the tutorial I followed was for this type, but I'm unsure. 

Content of /etc/postfix/main.cf
```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no


append_dot_mydomain = no


smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache


myhostname = tiberath.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = tiberath.com, Tibbius, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated permit_mynetworks permit_inet_interfaces

```

Content of /etc/default/saslauthd
```

START=yes


PWDIR="/var/spool/postfix/var/run/saslauthd"
PARAMS="-m ${PWDIR}"
PIDFILE="${PWDIR}/saslauthd.pid"


MECHANISMS="pam" 
# I've tried 'shadow' here too.


OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd"

```

I think these are the only two files I need to post, as I noted I did try 'shadow' instead of 'pam' and 'pam shadow' as well.

Any help with be greatly appreciated, I'm so close to having this working =P.

---

### Post by hyper_ch on 2008-04-23
[http://www.howtoforge.com/perfect_server_ubuntu7.10_p5](http://www.howtoforge.com/perfect_server_ubuntu7.10_p5)

---

### Post by geertn on 2008-04-23
Any output in "/var/log/mail.log"? Do you happen to plan running an imap server? There are certain advantages of using dovecot authentication instead of saslauthd.

---

### Post by werdan on 2008-04-23
```

Apr 23 21:51:16 Tibbius postfix/smtpd[23203]: TLS connection established from dialup-4.244.138.212.Dial1.StLouis1.Level3.net[4.244.138.212]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
Apr 23 21:51:21 Tibbius postfix/smtpd[23203]: warning: SASL authentication failure: no secret in database
Apr 23 21:51:21 Tibbius postfix/smtpd[23203]: warning: dialup-4.244.138.212.Dial1.StLouis1.Level3.net[4.244.138.212]: SASL CRAM-MD5 authentication failed: authentication failure
Apr 23 21:51:22 Tibbius postfix/smtpd[23203]: warning: SASL authentication failure: no secret in database
Apr 23 21:51:22 Tibbius postfix/smtpd[23203]: warning: dialup-4.244.138.212.Dial1.StLouis1.Level3.net[4.244.138.212]: SASL NTLM authentication failed: authentication failure
Apr 23 21:51:22 Tibbius postfix/smtpd[23203]: warning: SASL authentication failure: Password verification failed
Apr 23 21:51:22 Tibbius postfix/smtpd[23203]: warning: dialup-4.244.138.212.Dial1.StLouis1.Level3.net[4.244.138.212]: SASL PLAIN authentication failed: authentication failure
Apr 23 21:51:25 Tibbius postfix/smtpd[23203]: warning: dialup-4.244.138.212.Dial1.StLouis1.Level3.net[4.244.138.212]: SASL LOGIN authentication failed: authentication failure
Apr 23 21:51:28 Tibbius postfix/smtpd[23203]: lost connection after AUTH from dialup-4.244.138.212.Dial1.StLouis1.Level3.net[4.244.138.212]
Apr 23 21:51:28 Tibbius postfix/smtpd[23203]: disconnect from dialup-4.244.138.212.Dial1.StLouis1.Level3.net[4.244.138.212]

```

But now I don't seem to be getting any errors (I cleared out the logs to get new information now nothing new is coming in).

I do have dovecot installed and it's working fine, and I don't plan to support IMAP here. I'm just wondering why it's not grabbing the authentication information properly.

---

### Post by geertn on 2008-04-24
Did you install /etc/postfix/sasl/smtpd.conf as written in the howto?

If you want, you can use dovecot authentication. This way you don't need to use saslauthd. These are my sasl settings in main.cf:
```

## sasl settings
smtpd_sasl_authenticated_header = yes

# Use Dovecot's SASL interface.
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
##

```

Relevant dovecot config:
```

auth_verbose = yes

auth default {
  mechanisms = plain login
  passdb pam {
  }

  userdb passwd {
  }

  user = root

  socket listen {
    client {
      path = /var/spool/postfix/private/auth
      mode = 0660
      user = postfix
      group = postfix
    }
  }
}



```

---

### Post by werdan on 2008-04-24
Dovecot got it, thanks a ton.

---

### Post by zazuge on 2008-04-24
If your problem is solved then change the thread title or close it.

---

### Post by excalq on 2009-08-13
Thank you!!!! Dovecot worked after two evenings dealing with sasl annoyances.

---

