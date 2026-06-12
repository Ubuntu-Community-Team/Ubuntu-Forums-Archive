---
title: "Postfix + Mysql + Dovecot"
date: 2011-02-21
forum: Server Platforms
---

### Post by NamiJason on 2011-02-21
I've got a working solution with no SSL.  Im having trouble getting SSL working on both the incoming and outgoing side.  Im using virtual domains in mysql.  Auth.log is showing this:

saslauthd[31383]: pam_mysql - required option "db" is not set
saslauthd[31383]: DEBUG: auth_pam: pam_authenticate failed: Error in service module
saslauthd[31383]: do_auth         : auth failure: [user=test@site.com] [service=smtp] [realm=site.com] [mech=pam] [reason=PAM auth error]

My */etc/default/saslauthd *looks like:
START=yes
DESC="SASL Authentication Daemon"
NAME="saslauthd"
MECHANISMS="pam"
MECH_OPTIONS=""
THREADS=5
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd -r"
and  [I]/etc/pam.d/smtp:

[/I]auth    required   pam_mysql.so user=mail_admin passwd=password host=127.0.0.1 db=mail table=users usercolumn=email passwdcolumn=password crypt=1
account sufficient pam_mysql.so user=mail_admin passwd=password host=127.0.0.1 db=mail table=users usercolumn=email passwdcolumn=password crypt=1

---

### Post by elico on 2011-02-21
i have what you need:
instead using sasl daemon use dovecot  as sasl auth agent

smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
smtpd_tls_security_level = may

you can use the 
> [http://workaround.org/ispmail/lenny](http://workaround.org/ispmail/lenny)
to understand the whole picture better.

---

### Post by NamiJason on 2011-02-22
[SIZE=2]Great tutorial [/SIZE][FONT=Verdana][SIZE=2][elico]("http://ubuntuforums.org/member.php?u=1130241")[/SIZE][/FONT][SIZE=2] but this still isn't working. Figured out for the PAM auth error was due to an incorrect password.  I've got this working for TLS now but Outlook 2002 still can't send mail.  It can recieve over TLS but it looks like it is getting a timeout error according to outlook.

> 'Sending and           Receiving' reported error (0x8004210B) : 'The operation timed out waiting for a           response from the sending (SMTP) server. If you continue to receive this           message, contact your server administrator or Internet service provider (ISP).           Here is my postconf -n

[/SIZE]```
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 0
message_size_limit = 30720000
milter_default_action = accept
milter_protocol = 2
mydestination = localhost, localhost.localdomain
myhostname = mydomain.com
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
non_smtpd_milters = inet:localhost:8892
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
relayhost =
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_milters = inet:localhost:8892
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_path = private/auth
smtpd_sasl_type = dovecot
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/postfix.pem
smtpd_tls_key_file = /etc/ssl/private/postfix.pem
smtpd_tls_security_level = may
smtpd_use_tls = yes
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_transport = dovecot
virtual_uid_maps = static:5000

```

---

### Post by Parama on 2011-02-22
Have you tried testing with Thunderbird or Outlook 2007/2010. I have had a couple of customers in the same situation (Dovecot server, Outlook 2003 clients), and it seemed like a combination of Outlook 2003 not having a good SMTP TLS implementation and the lack of certain hotfixes.

It was just a thought...

---

### Post by NamiJason on 2011-02-25
Yes.  Thunderbird detects everything and comes up with green lights on STARTTLS and SSL/TLS for imap, smtp and pop.  

I have it configured incoming POP SSL/TLS and outgoing SMTP SSL/TLS.  It has no problem retreiving email, but when it tries to send it gets the following error:

Thunderbird says, "Sending of message failed. The message could not be sent because the connection to SMTP server mail.domain.com timed out. Try again or contact your network administrator."

I don't see anything partiular in the mail log.


```
postfix/smtpd[15138]: connect from hsd1.mn.comcast.net[clientip]
dovecot: auth(default): new auth connection: pid=15138
dovecot: auth(default): client in: AUTH#0111#011PLAIN#011service=pop3#011secured#011lip=serverip#011rip=clientip#011lport=995#011rport=1243
dovecot: auth(default): client out: CONT#0111#011
dovecot: auth(default): new auth connection: pid=15140
dovecot: auth(default): client in: CONT<hidden>
dovecot: auth-worker(default): sql(test@domain.com,clientip): query: SELECT email as user, password FROM users WHERE email='test@domain.com';
dovecot: auth(default): client out: OK#0111#011user=test@vividiridium.com
dovecot: auth(default): master in: REQUEST#011234#01115137#0111
dovecot: auth(default): master out: USER#011234#011test@domain.com#011uid=5000#011gid=5000#011home=/home/vmail/domain.com/test
dovecot: pop3-login: Login: user=<test@domain.com>, method=PLAIN, rip=clientip, lip=serverip, TLS
dovecot: POP3(test@domain.com): Disconnected: Logged out top=0/0, retr=0/0, del=0/1, size=1675
postfix/smtpd[15138]: lost connection after UNKNOWN from hsd1.mn.comcast.net[clientip]
postfix/smtpd[15138]: disconnect from hsd1.mn.comcast.net[clientip]
```

---

