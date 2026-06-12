---
title: "PostFix Doesn't accept mail"
date: 2009-04-30
forum: Server Platforms
---

### Post by PJDouglas on 2009-04-30
Hi,

I have just set up Postfix as a relay server which is going to be used for rewriting the domain address on all mail before mail delivery.

Our exchange server has a smtp connector pointing to postfix as the smarthost.

Our postfix server is in the same ip subnet as our exchange but for some reason the connection to postfix keeps timing out.

I have ran network monitor and confirmed that our exchange is attempting mail delivery to postfix.

My understanding is that postfix will trust any server in the same ip subnet and no relay permissions need to be set.

Not sure why I can't deliver mail to postfix and the connection seems to be refused.

Any help would be appreciated.

Many Thanks

Paul.

---

### Post by ephmanjmm on 2009-05-01
It might help if you posted your main.cf and some of the mail logs showing the connections.

---

### Post by Dy1anW on 2009-05-01
I had a similar problem earlier, but it turned out to be overzealous smtpd_*_restrictions in main.cf

---

### Post by PJDouglas on 2009-05-01
> **Dy1anW said:**
> I had a similar problem earlier, but it turned out to be overzealous smtpd_*_restrictions in main.cf

Thanks for your reply.

Here is the contents of main.cf,

smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_client_restrictions = permit_ mynetworks
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = test.domain.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = test.domain.co.uk, localhost.domain.co.uk, localhost
relayhost = 172.16.255.251
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks = 10.0.0.0/16
remote_header_rewrite_domain = pjdouglas.co.uk
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only

I'm new to Ubuntu and Postfix and pretty much just finding my feet.

I've just entered 'smtpd_client_restrictions = permit_ mynetworks' which has made no difference. Not sure whether I got the syntax right?

/var/log/mail.log

Apr 30 10:43:29 test postfix/master[3918]: daemon started -- version 2.5.5, configuration /etc/postfix
Apr 30 10:43:29 test dovecot: Dovecot v1.1.4 starting up
Apr 30 10:43:29 test dovecot: Generating Diffie-Hellman parameters for the first time. This may take a while..
Apr 30 10:44:05 test dovecot: ssl-build-param: SSL parameters regeneration completed
Apr 30 10:53:51 test postfix/master[3918]: reload configuration /etc/postfix
Apr 30 10:53:52 test postfix/master[3918]: reload configuration /etc/postfix
Apr 30 12:54:38 test postfix/master[3918]: reload configuration /etc/postfix
Apr 30 14:51:30 test postfix/master[3918]: terminating on signal 15
Apr 30 14:52:04 test postfix/master[3928]: daemon started -- version 2.5.5, configuration /etc/postfix
Apr 30 14:52:04 test dovecot: Dovecot v1.1.4 starting up
Apr 30 15:26:42 test postfix/postfix-script[4531]: refreshing the Postfix mail system
Apr 30 15:26:42 test postfix/master[3928]: reload configuration /etc/postfix
Apr 30 15:29:47 test postfix/postfix-script[4540]: refreshing the Postfix mail system
Apr 30 15:29:47 test postfix/master[3928]: reload configuration /etc/postfix
May  1 12:41:05 test postfix/postfix-script[16599]: refreshing the Postfix mail system
May  1 12:41:05 test postfix/master[3928]: reload configuration /etc/postfix
May  1 12:44:21 test postfix/master[3928]: reload configuration /etc/postfix
May  1 12:44:22 test postfix/master[3928]: reload configuration /etc/postfix
May  1 13:13:53 test postfix[16985]: fatal: /etc/postfix/main.cf, line 38: missing '=' after attribute name: "permit_mynetworks"
May  1 13:51:39 test postfix[17371]: fatal: /etc/postfix/main.cf, line 29: missing '=' after attribute name: "smtpd client restrictions = permit mynetwork$
May  1 13:54:24 test postfix/postfix-script[17375]: refreshing the Postfix mail system
May  1 13:54:24 test postfix/master[3928]: reload configuration /etc/postfix
May  1 13:54:34 test postfix/postfix-script[17383]: refreshing the Postfix mail system
May  1 13:54:34 test postfix/master[3928]: reload configuration /etc/postfix

Don't know of any other error logs I can look at being new to all this. What other logs should I be looking at?

Many Thanks for your help.


Paul.

---

### Post by Dy1anW on 2009-05-01
Hi!  I'm still learning this too, so I really can't help too much.

Here's a snippet of my smtpd statements:

```

# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_invalid_hostname, permit
# Requirements for the recipient address
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org

```

I can receive and send via webmail using this configuration, but have problems just sending with a client on another machine, so this'll likely work for you too.  When I was testing I had all restrictions as "permit" (as in permit everything) and that did the trick, but naturally you wouldn't want to be operating like that.

You can ignore check_policy_service inet: 127.0.0.1:60000, permit in the above code, as that's for spam & virus checking.

I think the biggest issue is that there's no line for smtpd_sender_restrictions in your file as that handles mail that gets accepted, I could be wrong though, but just copy the code above, and let us know how it works out :P

---

### Post by PJDouglas on 2009-05-05
Thanks Dy1anW,

Tried entering the smtpd_sender_restrictions and smtpd_*_restrictions and restarting postfix.

Unfortunately neither have made any difference.

Are there any postfix logs that show the connection being rejected and why??

Thanks for your help.


Paul.

---

