---
title: "karmic dovecot/postfix relay access denied"
date: 2009-10-31
forum: Server Platforms
---

### Post by notquitemichael on 2009-10-31
afternoon all,

i used the karmic server installation disc to install and setup the combined dovecot/postfix packages that ubuntu offers.

i have not touched the default settings and have got the system sending and recieving messages internally- however messages sent from outside the network disappear without a trace, and i get a 'relay access denied' error when i attempt to send e-mails out of the local network.

i've tried a host of different, working, external web addresses and am convinced the problems on my side. from some google'ing around the subject i can confirm that my client (evolution,) states that 'server requires authentication'

there are a few tutorials with talk about adding sasl_... terms to my postfix config files, but the ubuntu spiel on the dovecot/postfix package is that postfix should be using dovecot to authenticate.

 environment: 64bit karmic, server edition
 trac/apache/svn/ssh/telnet can all reach the machine so it's not a router issue.
 client: evolution

here is my postfix -n output:
> alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = my_domain.com, cefca, localhost.localdomain, localhost
myhostname = cefca
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = 
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes


where my_domain is my website.

thanks!

---

### Post by notquitemichael on 2009-10-31
well i sorted it- in the spirit of sharing: here goes.

 1 - you _do_ still need to configure sasl authentication; you can do this by adding the following lines to your /etc/postfix/main.cf

```

smtpd_sasl_auth_enable = yes
smtpd_sasl_path = auth-client
smtpd_sasl_type = dovecot
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

```

 2 - and this still needs to be manually linked into dovecot: do this via /etc/dovecot/dovecot.conf - this time you'll have to amend the following section to look as such:

```

socket listen {
    master {
    }
    client {
      path = /var/spool/postfix/auth-client
      mode = 0660
      user = postfix
      group = postfix
    }
  }

```

which can be found in the "auth_default {" block

 3 - now your client should ask for your user name and password and it should be your users.

n.b. (4) - i also got caught out setting up my domain; make sure you have you MX record pointing all mydomain.com (this might be shown as @) back to your smtp.mydomain.com or else some providers won't be able to e-mail you.

happy hunting.

---

