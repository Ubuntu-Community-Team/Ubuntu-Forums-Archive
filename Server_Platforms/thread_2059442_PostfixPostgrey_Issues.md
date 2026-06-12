---
title: "Postfix/Postgrey Issues"
date: 2012-09-18
forum: Server Platforms
---

### Post by AnubisXVIII on 2012-09-18
Okay, I created a mail server following this guide:
[http://flurdy.com/docs/postfix](http://flurdy.com/docs/postfix)

Now I can telnet to port 587 and send email internally but when I try to do it externally I get this error

```
rcpt to: webmaster@pharaohinc.com
451 4.3.5 Server configuration problem
quit

```So I check my mail.log..../var/log/mail.log...and it gives me this

```
Sep 18 09:04:52 server postfix/smtpd[32213]: warning: connect to 127.0.0.1:10023: Connection refused
Sep 18 09:04:52 server postfix/smtpd[32213]: warning: problem talking to server 127.0.0.1:10023: Connection refused
Sep 18 09:04:53 server postfix/smtpd[32213]: warning: connect to 127.0.0.1:10023: Connection refused
Sep 18 09:04:53 server postfix/smtpd[32213]: warning: problem talking to server 127.0.0.1:10023: Connection refused
Sep 18 09:04:53 server postfix/smtpd[32213]: NOQUEUE: reject: RCPT from unknown[24.244.154.174]: 451 4.3.5 Server configuration problem; from=<isjunkz@gmail.com> to=<webmaster@pharaohinc.com> proto=ESMTP helo=<webmail.pharaohinc.com>

```Now I googled and it was supposed to be a conflict with postgrey I tested to see if it was listening on the port and it was, I restarted postgrey, along with postfix and mysql but no success....below is my main.cf

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
smtpd_tls_cert_file=/etc/postfix/postfix.cert
smtpd_tls_key_file=/etc/postfix/postfix.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
myhostname = webmail.pharaohinc.com
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
#myorigin = /etc/mailname
myorigin = pharaohinc.com
#mydestination = pharaohinc.com, server.pharaohinc.com, localhost.pharaohinc.com, localhost
mydestination =
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
local_recipient_maps =
mynetworks_style= host

#Requirements for the HELO statement
smtpd_helo_restrictions= permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
#Requirements for the sender details
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
#Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
#Requirements for the recipient address
smtpd_recipient_restrictions= reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain,reject_unauth_destination,check_policy_service inet:127.0.0.1:10023, permit
smtpd_data_restrictions= reject_unauth_pipelining

# this specifies wher ethe virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual
#this is for the location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
#and this is for the aliases
virtual_alias_maps= mysql:/etc/postfix/mysql_alias.cf
#and this is for the domain lookups
virtual_mailbox_domains= mysql:/etc/postfix/mysql_domains.cf
#this is how to connect to the domains (all virtual, but the option is thre) not used yet
#transport_maps= mysql:/etc/postfix/mysql_transport.cf

virtual_uid_maps = static:5000
virtual_gid_maps= static:5000

content_filter= amavis:[127.0.0.1]:10024
```Any assistance will be greatly appreciated...I'm at my wits end with this

---

### Post by Hammi on 2012-10-05
FWIW, I'm having the same issue. Did you manage to solve it already?

Later:

The issue appears the be the following:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=656046](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=656046)

I think I just fixed that on my system by telling postfix to check with postgrey through ipv6:

```
[...]
smtpd_recipient_restrictions =
   permit_mynetworks,
   permit_sasl_authenticated, 
   reject_unauth_destination,
   reject_non_fqdn_sender,
   reject_non_fqdn_recipient,
   reject_unknown_sender_domain,
   reject_unknown_recipient_domain,
   reject_unauth_pipelining,
   reject_invalid_hostname,
   reject_non_fqdn_hostname,
   reject_rbl_client zen.spamhaus.org,
   check_policy_service inet:::1:10023,
   check_sender_access hash:/etc/postfix/sender_access,
   permit
[...]

```

---

### Post by bmatthewshea on 2012-12-13
PostGrey now binds to IP6 by default.

First thing: Make sure hostnames (and ip6 hostnames) (/etc/hosts) isn't the problem. If not, then this could be your issue:

IP4 was only protocol allowed/enabled as per older main.cf configuration when I upgraded my ubuntu server. Postgrey was working fine before upgrade..


Solution:

**main.cf:**

```

#ip6 proper syntax:
smtpd_recipient_restrictions =
# [...]
check_policy_service inet:[::1]:10023
#(and):
inet_protocols = all

```


Make sure all protocols are enabled. not *just* ip4 or ip6.
No changes to default/installed '/etc/default/postgrey' were needed. ( '--inet=10023' is fine - but it binds to ip6 now by default (only!). )
```

# sudo netstat -pln | grep postgrey

tcp6       0      0 ::1:10023               :::*                    LISTEN      1648/postgrey.pid -

```

ref: [https://bugs.launchpad.net/ubuntu/+source/postgrey/+bug/884743](https://bugs.launchpad.net/ubuntu/+source/postgrey/+bug/884743)


> **Hammi said:**
> FWIW, I'm having the same issue. Did you manage to solve it already?

Later:

The issue appears the be the following:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=656046](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=656046)

I think I just fixed that on my system by telling postfix to check with postgrey through ipv6:

```
[...]
smtpd_recipient_restrictions =
   permit_mynetworks,
   permit_sasl_authenticated, 
   reject_unauth_destination,
   reject_non_fqdn_sender,
   reject_non_fqdn_recipient,
   reject_unknown_sender_domain,
   reject_unknown_recipient_domain,
   reject_unauth_pipelining,
   reject_invalid_hostname,
   reject_non_fqdn_hostname,
   reject_rbl_client zen.spamhaus.org,
   check_policy_service inet:::1:10023,
   check_sender_access hash:/etc/postfix/sender_access,
   permit
[...]

```

---

### Post by bmatthewshea on 2012-12-13
.

---

### Post by lisati on 2012-12-13
It would be also be a good idea to make sure that Postgrey is actually running, otherwise Postfix won't be able to connect.

---

