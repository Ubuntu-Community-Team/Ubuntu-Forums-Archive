---
title: "Problems with couriertls"
date: 2007-05-26
forum: Server Platforms
---

### Post by Beamerboy on 2007-05-26
I am receiving the following error when I try to connect to my IMAP server over a secure connection with evolution:

May 26 06:57:47 mail imapd: Disconnected, ip=[::ffff:87.127.87.186], time=0, starttls=1
May 26 06:57:47 mail imapd: Connection, ip=[::ffff:87.127.87.186]
May 26 06:57:47 mail imapd: couriertls: connect: error:1408F10B:SSL routines:SSL3_GET_RECORD:wrong version number
May 26 06:57:47 mail imapd: Connection, ip=[::ffff:87.127.87.186]
May 26 06:57:47 mail imapd: couriertls: connect: error:1408F10B:SSL routines:SSL3_GET_RECORD:wrong version number
May 26 06:57:47 mail imapd: Disconnected, ip=[::ffff:87.127.87.186], time=0, starttls=1
May 26 06:57:47 mail imapd: Disconnected, ip=[::ffff:87.127.87.186], time=0, starttls=1
May 26 06:57:58 mail imapd: Connection, ip=[::ffff:87.127.87.186]
May 26 06:57:58 mail imapd: couriertls: connect: error:1408F10B:SSL routines:SSL3_GET_RECORD:wrong version number
May 26 06:57:58 mail imapd: Disconnected, ip=[::ffff:87.127.87.186], time=0, starttls=1

Seems to be an issue with the SSL version number but I don't have a clue what is going on, so if anyone could help me out I would appreciate it.

I used the following guide for installing Postfix+Courier+Mysql:

[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy)

The only thing I have done differently is I have ignored the quota side of things since this is a small mail server with oodles of hd space.

Thanks for any help.

Paladine

---

### Post by Beamerboy on 2007-05-26
Seems this is a SASL problem.  KMail tells me TLS is not supported on the server.

Is something monumentally borked with SASL in Feisty?  Seems odd, cos I had this running with a single domain earlier with no problems.  As soon as I switched to use MySQL and made the appropriate changes to /etc/postfix/sasl/smtpd.conf and /etc/pam.d/smtp everything broke.

Here are my configs:

/etc/postfix/main.cf
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

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.xxxxxxx.org.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.xxxxxxx.org.uk, localhost, localhost.localdomain
relayhost = 
mynetworks = 127.0.0.0/8,xx.xxx.xx.xxx/29
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = smtpd
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks

```

/etc/postfix/sasl/smtpd.conf

```

pwcheck_method: saslauthd
mech_list: plain login
allow_plaintext: true
auxprop_plugin: mysql
sql_hostnames: 127.0.0.1
sql_user: xxxxxxxx
sql_passwd: xxxxxxxx
sql_database: xxxxxxxx
sql_select: select password from users where email = '%u'

```

/etc/pam.d/smtp

```

auth    required   pam_mysql.so user=xxxxxxxx passwd=xxxxxxxx host=127.0.0.1 db=xxxxxxxx table=users usercolumn=email passwdcolumn=password crypt=1
account sufficient pam_mysql.so user=xxxxxxxx passwd=xxxxxxxx host=127.0.0.1 db=xxxxxxxx table=users usercolumn=email passwdcolumn=password crypt=1

```

Happy to post any other configs also here is the output from telnetting to port 25:

```


root@mail:/home/paladine# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 mail.paladine.org.uk ESMTP Postfix (Ubuntu)
ehlo localhost
250-mail.paladine.org.uk
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
quit
221 2.0.0 Bye
Connection closed by foreign host.
root@mail:/home/paladine#

```

All help appreciated, I am utterly stumped on this.

Paladine

---

### Post by Beamerboy on 2007-05-26
I just found another "warning" in /var/log/mail.warn

May 26 06:57:22 mail postfix/smtpd[21465]: warning: TLS library problem: 21465:error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca:s3_pkt.c:1057:SSL alert number 48:

Paladine

---

### Post by Beamerboy on 2007-05-26
OK, I fixed it finally (after 10 hours).

I regenerated my ssl certs, all seems good now.

Paladine

---

### Post by Beamerboy on 2007-05-26
Hmmm,

I just added a new domain and user, and all of a sudden I am getting these errors again:

May 26 10:42:35 mail imapd: couriertls: connect: error:1408F10B:SSL routines:SSL3_GET_RECORD:wrong version number

I regenerated my certificates again, but it has made no difference.  Definitely something very odd going on here.

Paladine

---

### Post by Beamerboy on 2007-05-26
Wish I had found this 13 hours ago:

[https://bugs.launchpad.net/evolution/+bug/59632](https://bugs.launchpad.net/evolution/+bug/59632)

I can confirm that the following solution worked for me (from the bug thread):

edit the file /etc/courier/imapd-ssl and make sure the following line is correct

[INDENT]TLS_STARTTLS_PROTOCOL=SSL3[/INDENT]

Then in Evolution edit the account profiles in the Receiving Emails tab and change Use Secure Connection to SSL

You need to do this for all accounts you have setup in evolution for your mail server.

Restart Evolution and everything should work again

It worked for me, so hopefully it will help others too.

Paladine

---

