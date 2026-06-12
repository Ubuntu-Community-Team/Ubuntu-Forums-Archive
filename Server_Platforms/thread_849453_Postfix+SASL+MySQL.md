---
title: "Postfix+SASL+MySQL"
date: 2008-07-04
forum: Server Platforms
---

### Post by Sneaker on 2008-07-04
(Sorry for my bad english)

Hello,

Im trying to configure a mail server with Postfix(SMTP)+AUTH SASL+MySQL in ubuntu server 8.04TLS. I configure all well but i have a little problem in sasl authentication:

In the mail client i configure smtp with authentication required. When i try to send a mail don't have any problem, the mail sends well. If i type a bad user the mail not send, but if i clear the password or put a bad password then mail sends anyway.

(Sorry for my bad english, again)

Configuration and logs:

Postfix:

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
delay_warning_time = 1h
inet_interfaces = all
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination = $myhostname, localhost.$mydomain, inet.domain.com, domain.com, localhost
myhostname = inet.domain.com
mynetworks = 127.0.0.0/8, 192.168.123.0/24
mynetworks_style = host
myorigin = $mydomain
readme_directory = no
recipient_delimiter = +
relayhost = 
smtp_helo_timeout = 60s
smtpd_banner = inet ESMTP domain.com
smtpd_hard_error_limit = 12
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = reject_unknown_sender_domain
smtpd_soft_error_limit = 3
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
```

smtpd.conf

```
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: *******
sql_passwd: *******
sql_database: maildb
sql_select: select clear from users where id='%u@%r' and enabled = 1
```

mail.log

```
Jul  4 13:28:39 inet postfix/smtpd[9967]: 57197220785: client=XXX.Red-xx-XXX-XXX.staticIP.rima-tde.net[XX.XXX.XXX.XXX], sasl_method=LOGIN, sasl_username=USER@DOMAIN.com
Jul  4 13:28:39 inet postfix/cleanup[9971]: 57197220785: message-id=
Jul  4 13:28:39 inet postfix/qmgr[9212]: 57197220785: from=, size=2066, nrcpt=1 (queue active)
Jul  4 13:28:39 inet postfix/smtpd[9967]: disconnect from XXX.Red-XX-XXX-XXX.staticIP.rima-tde.net[XX.XXX.XXX.XXX]
Jul  4 13:28:46 inet postfix/smtp[9972]: 57197220785: to=, relay=xxxx.xxxxxx.xx[XXX.XX.XX.XXX]:25, delay=7.1, delays=0.37/0.01/3.3/3.5, dsn=2.6.0, status=sent (250 2.6.0   Queued mail for delivery)
Jul  4 13:28:46 inet postfix/qmgr[9212]: 57197220785: removed
```

auth.log

```
Jul  4 13:28:39 inet postfix/smtpd[9967]: sql plugin Parse the username danvi@domain.com 
Jul  4 13:28:39 inet postfix/smtpd[9967]: sql plugin try and connect to a host 
Jul  4 13:28:39 inet postfix/smtpd[9967]: sql plugin trying to open db 'maildb' on host '127.0.0.1' 
Jul  4 13:28:39 inet postfix/smtpd[9967]: sql plugin Parse the username danvi@domain.com 
Jul  4 13:28:39 inet postfix/smtpd[9967]: sql plugin try and connect to a host 
Jul  4 13:28:39 inet postfix/smtpd[9967]: sql plugin trying to open db 'maildb' on host '127.0.0.1' 
Jul  4 13:28:39 inet postfix/smtpd[9967]: sql plugin Parse the username danvi@domain.com 
Jul  4 13:28:39 inet postfix/smtpd[9967]: sql plugin try and connect to a host 
Jul  4 13:28:39 inet postfix/smtpd[9967]: sql plugin trying to open db 'maildb' on host '127.0.0.1' 
Jul  4 13:28:39 inet postfix/smtpd[9967]: begin transaction
Jul  4 13:28:39 inet postfix/smtpd[9967]: sql plugin create statement from userPassword danvi domain.com 
Jul  4 13:28:39 inet postfix/smtpd[9967]: sql plugin doing query select clear from users where id='danvi@domain.com' and enabled = 1; 
Jul  4 13:28:39 inet postfix/smtpd[9967]: sql plugin create statement from cmusaslsecretPLAIN danvi domain.com 
Jul  4 13:28:39 inet postfix/smtpd[9967]: sql plugin doing query select clear from users where id='danvi@domain.com' and enabled = 1; 
Jul  4 13:28:39 inet postfix/smtpd[9967]: commit transaction
Jul  4 13:28:39 inet postfix/smtpd[9967]: sql plugin Parse the username danvi@domain.com 
Jul  4 13:28:39 inet postfix/smtpd[9967]: sql plugin try and connect to a host 
Jul  4 13:28:39 inet postfix/smtpd[9967]: sql plugin trying to open db 'maildb' on host '127.0.0.1' 
```

Im trying to solve this problem for 2 weeks.

thx.

---

### Post by HermanAB on 2008-07-04
Hmm, good luck with that... ;)

Once you are totally fed-up with Postfix and willing to try an alternative, go to [http://www.citadel.org/doku.php](http://www.citadel.org/doku.php) run the Easy Install script and you should have a complete working groupware system with every protocol you can imagine in about 20 minutes.

Cheers,

Herman

---

### Post by Sneaker on 2008-07-07
Please, somewhere can help me?????? Thx.

---

### Post by Sneaker on 2008-07-15
Pleaseeeeeeeeee!!!!

---

### Post by dragonator on 2008-07-16
> **HermanAB said:**
> Hmm, good luck with that... ;)

Once you are totally fed-up with Postfix and willing to try an alternative, go to [http://www.citadel.org/doku.php](http://www.citadel.org/doku.php) run the Easy Install script and you should have a complete working groupware system with every protocol you can imagine in about 20 minutes.

Cheers,

Herman

Unless I'm missing something pretty basic the citadel "easy install" doesn't work all that easy.  I've had no luck with it. I've tried on 2 separate hardy server installs, one I built from CD in the process of building a mail server, the other was a VM instance I downloaded from the VMWare site.  Missing dependencies, all of which are supposedly handled by the script, but no go on either 8.04 server install.

I'm game to give it a try, but if it won't install...[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

