---
title: "Mail server relay access denied with virtual users"
date: 2012-03-04
forum: Server Platforms
---

### Post by nat45928 on 2012-03-04
Hi,

I have a mail server set up with virtual users and domains, using postfix, courier-IMAP, MySQL, SASL, and SquirrelMail. I followed this guide: [http://flurdy.com/docs/postfix](http://flurdy.com/docs/postfix)

I am logged into my server via outlook on the domains smtp and imap ports. I am not logging into my SMTP server however, when i set Outlook to log in i receive an error that the server does not have this type of authentication.

When i try and send mail i get a "Relay access denied" error in my log. i can send fine through SquirrelMail.

Here is my mail.conf (any blank spaces are filled out with sensitive information):

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = truefoodlooks.com

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h

readme_directory = no

unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=no
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

#myhostname = truefoodlooks.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = (set to my static IP)
mydestination =
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
local_recipient_maps =


# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth$
# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
# Requirement for the recipient address
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_d$
smtpd_data_restrictions = reject_unauth_pipelining

smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf

virtual_uid_maps = static:5000
virtual_gid_maps = static:5000

# SASL smtpd_sasl_auth_enable = yes
# If your potential clients use Outlook Express or other older clients
# this needs to be set to yes
broken_sasl_auth_clients = no
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

```

any help would be appreciated.

Nat

---

### Post by nsnidanko on 2012-03-06
Hi Nat,

Part of config:

smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks,...

When you send email via webmail it looks at a host as localhost, at it defined in [B]mynetworks

[/B]When you send via Outlook, it tries to get authenticated, which it fails to do, so than it looks at **mynetworks**, but the client is not listed there so therefore it rejects it.[B]

Outlook -> HELO -> authentication fails -> Not listed in mynetworks -> Reject

[/B]Looks like your main.cf is ok; your best bet would be to look into why Outlook client fails to authenticate. Check Outlook for type of encrypted connection, etc. Also try some sort of smtp tester to check that your authentication works.

---

### Post by nat45928 on 2012-03-07
OK, thanks for the reply, ill do some digging and see what i find.

---

### Post by nat45928 on 2012-03-10
There was an error in my mail.conf file this block:

```
# SASL smtpd_sasl_auth_enable = yes 
# If your potential clients use Outlook Express or other older clients 
# this needs to be set to yes 
broken_sasl_auth_clients = no 
smtpd_sasl_security_options = noanonymous 
smtpd_sasl_local_domain =
```Should have been:

```
# SASL 
smtpd_sasl_auth_enable = yes 
# If your potential clients use Outlook Express or other older clients 
# this needs to be set to yes 
broken_sasl_auth_clients = no 
smtpd_sasl_security_options = noanonymous 
smtpd_sasl_local_domain =
```So once that was fixed i started getting a password prompt from outlook but the password was never accepted. tailing the mail.log gave this error:

Mar 10 21:41:35 SJ-Linux-1 postfix/smtpd[1948]: connect from 
Mar 10 21:41:35 SJ-Linux-1 postfix/smtpd[1948]: warning: SASL authentication failure: unable to canonify user and get auxprops
Mar 10 21:41:35 SJ-Linux-1 postfix/smtpd[1948]: warning:  SASL DIGEST-MD5 authentication failed: no mechanism available
Mar 10 21:41:35 SJ-Linux-1 postfix/smtpd[1948]: warning:  SASL LOGIN authentication failed: no mechanism available
Mar 10 21:41:35 SJ-Linux-1 postfix/smtpd[1948]: disconnect from 

My smtpd.conf for postfix/sasl is :

```

pwcheck_method: saslauthd
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: 
sql_passw: 
sql_database: maildb
sql_select: select crypt from users where id='%u'@'%r' and enabled = 1

```with user and passw fields filled in.

What is happening?

Nat

---

### Post by Vishal Agarwal on 2012-03-11
add your server ip to 

mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128  xxx.xxx.xxx.xxx

I hope it should work.

---

### Post by nat45928 on 2012-03-12
that did not solve the problem, i tried both the local IP and my External IP and got the same error. When i remove the cram-md5 and digest-md5 mech's from smtpd.conf i get this error:

Mar 12 17:57:28 SJ-Linux-1 postfix/smtpd[25060]: connect from
Mar 12 17:57:28 SJ-Linux-1 postfix/smtpd[25060]: warning SASL LOGIN authentication failed: no mechanism available
Mar 12 17:57:28 SJ-Linux-1 postfix/smtpd[25060]: disconnect from

Any other ideas?

---

### Post by nsnidanko on 2012-03-13
It seems like mysql credentials doen't have permissions to access database. try granting permissions

Chers,
Naz

---

### Post by nat45928 on 2012-03-13
I'm using the same credentials that put the tables and information in place when the email account is created so that cant be the issue.

---

### Post by nsnidanko on 2012-03-14
Nat,

I am not sure what version you have but try following some things (i.e replacing libraries, etc) outlined in the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/cyrus-sasl2/+bug/875440](https://bugs.launchpad.net/ubuntu/+source/cyrus-sasl2/+bug/875440)

---

### Post by nat45928 on 2012-03-15
i used this article here to solve the problem, thanks for the help!

[https://bugs.launchpad.net/ubuntu/+source/cyrus-sasl2/+bug/875440](https://bugs.launchpad.net/ubuntu/+source/cyrus-sasl2/+bug/875440)

---

### Post by tpinet on 2012-06-13
Nat,

I am having the same problems with smtp (ie: "warning: SASL authentication failure: unable to canonify user and get auxprops") when following the Flurdy install in 12.04. How did you resolve your problem?

---

