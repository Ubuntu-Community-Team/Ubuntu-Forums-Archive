---
title: "Postfix &amp; Dovecot: No &quot;login&quot; mechanism"
date: 2009-12-01
forum: Server Platforms
---

### Post by tentacleguy on 2009-12-01
Hi, 

for my Palm Pre, I need to enable the login mechanism "login", but it doesn't work:

(I'm using Hardy with some dovecot-debs from jaunty)

dovecot -n (extract):
> 
auth default:
  mechanisms: plain login
  user: vmail
  verbose: yes
  debug: yes
  passdb:
    driver: sql
    args: /etc/dovecot/dovecot-sql.conf
  userdb:
    driver: sql
    args: /etc/dovecot/dovecot-sql.conf
  socket:
    type: listen
    client:
      path: /var/spool/postfix/private/auth
      mode: 432
      user: postfix
      group: postfix
    master:
      path: /var/run/dovecot/auth-master
      mode: 432
      user: dovecot
      group: vmail


postconf -n:
> 
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot


But telnet mailserver 25 gives:
> 
ehlo test

250-PIPELINING
250-SIZE 35240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN
250-AUTH=PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN


Why is there no AUTH PLAIN LOGIN?

---

