---
title: "SASL AUTH Failure"
date: 2008-10-28
forum: Server Platforms
---

### Post by FawnOfFeist on 2008-10-28
I can not get SMTP SASL authentication to work properly with mysql.  I am not sure if it is even trying to login using the mysql database.  Any help with this would be greatly appreciated as I have been fighting this for a week now, and have no idea what I am missing.

Here are the errors I am getting.


Oct 28 16:55:14 AlbPostFix02 postfix/smtpd[4630]: warning: SASL authentication failure: no secret in database

Oct 28 16:55:14 AlbPostFix02 postfix/smtpd[4630]: warning: static-72-10-196-48.albyny.csvoip.net[72.10.196.48]: SASL NTLM authentication failed: authentication failure

Oct 28 16:55:14 AlbPostFix02 postfix/smtpd[4630]: warning: SASL authentication failure: realm changed: authentication aborted

Oct 28 16:55:14 AlbPostFix02 postfix/smtpd[4630]: warning: static-72-10-196-48.albyny.csvoip.net[72.10.196.48]: SASL DIGEST-MD5 authentication failed: authentication failure

Oct 28 16:55:14 AlbPostFix02 postfix/smtpd[4630]: warning: static-72-10-196-48.albyny.csvoip.net[72.10.196.48]: SASL LOGIN authentication failed: authentication failure


How can I make sure SASL is using the mysql database?  I have configured the smtpd.conf file in both /etc/postfix/sasl and in /usr/lib/sasl2

Below is that config.  Is there somewhere else I need to enable this?  Is it failing because I am using an encrypted password in the MySQL database?

sasl_pwcheck_method: authprop
sasl_auxprop_plugin: mysql
sasl_mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: localhost
sql_user: mailpostfix
sql_passwd: PasswordReplaced
sql_database: maildbpostfix
sql_select: select crypt from users where id='%u@%r' and enabled = 1


Also, I have squirrelmail working without issue sending and receiving on the server, but obviously that is not using SASL.

---

### Post by FawnOfFeist on 2008-10-30
Any authentication genius want to lend a hand?  Still can not get this figured out.

Would appreciate some help.  Thanks.

Let me know what other info you need and I will post.

---

### Post by FawnOfFeist on 2008-10-31
Ok, here is the other pertinent data you likely need.  If someone could please tell me what is wrong here, that would be great.  I have been trying to figure this out for quite some time.


Who has the magic answer?



Getting these auth.log errors:

Oct 31 00:00:49 AlbPostFix02 postfix/smtpd[5107]: sql_select option missing
Oct 31 00:00:49 AlbPostFix02 postfix/smtpd[5107]: auxpropfunc error no mechanism available
Oct 31 00:00:49 AlbPostFix02 postfix/smtpd[5107]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql




Here is saslfinger:
# saslfinger -s
saslfinger - postfix Cyrus sasl configuration Fri Oct 31 00:00:49 EDT 2008
version: 1.0.4
mode: server-side SMTP AUTH

-- basics --
Postfix: 2.5.1
System: Ubuntu 8.04.1 \n \l

-- smtpd is linked to --
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb7d8d000)

-- active SMTP AUTH and TLS parameters for smtpd --
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous


-- listing of /usr/lib/sasl2 --
total 808
drwxr-xr-x  2 root root  4096 2008-10-29 11:57 .
drwxr-xr-x 58 root root 20480 2008-10-29 12:20 ..
-rw-r--r--  1 root root 13568 2008-04-09 17:50 libanonymous.a
-rw-r--r--  1 root root   862 2008-04-09 17:49 libanonymous.la
-rw-r--r--  1 root root 12984 2008-04-09 17:50 libanonymous.so
-rw-r--r--  1 root root 12984 2008-04-09 17:50 libanonymous.so.2
-rw-r--r--  1 root root 12984 2008-04-09 17:50 libanonymous.so.2.0.22
-rw-r--r--  1 root root 15834 2008-04-09 17:50 libcrammd5.a
-rw-r--r--  1 root root   848 2008-04-09 17:49 libcrammd5.la
-rw-r--r--  1 root root 15320 2008-04-09 17:50 libcrammd5.so
-rw-r--r--  1 root root 15320 2008-04-09 17:50 libcrammd5.so.2
-rw-r--r--  1 root root 15320 2008-04-09 17:50 libcrammd5.so.2.0.22
-rw-r--r--  1 root root 46332 2008-04-09 17:50 libdigestmd5.a
-rw-r--r--  1 root root   871 2008-04-09 17:49 libdigestmd5.la
-rw-r--r--  1 root root 43020 2008-04-09 17:50 libdigestmd5.so
-rw-r--r--  1 root root 43020 2008-04-09 17:50 libdigestmd5.so.2
-rw-r--r--  1 root root 43020 2008-04-09 17:50 libdigestmd5.so.2.0.22
-rw-r--r--  1 root root 13574 2008-04-09 17:50 liblogin.a
-rw-r--r--  1 root root   842 2008-04-09 17:49 liblogin.la
-rw-r--r--  1 root root 13268 2008-04-09 17:50 liblogin.so
-rw-r--r--  1 root root 13268 2008-04-09 17:50 liblogin.so.2
-rw-r--r--  1 root root 13268 2008-04-09 17:50 liblogin.so.2.0.22
-rw-r--r--  1 root root 30016 2008-04-09 17:50 libntlm.a
-rw-r--r--  1 root root   836 2008-04-09 17:49 libntlm.la
-rw-r--r--  1 root root 29236 2008-04-09 17:50 libntlm.so
-rw-r--r--  1 root root 29236 2008-04-09 17:50 libntlm.so.2
-rw-r--r--  1 root root 29236 2008-04-09 17:50 libntlm.so.2.0.22
-rw-r--r--  1 root root 13798 2008-04-09 17:50 libplain.a
-rw-r--r--  1 root root   842 2008-04-09 17:49 libplain.la
-rw-r--r--  1 root root 13396 2008-04-09 17:50 libplain.so
-rw-r--r--  1 root root 13396 2008-04-09 17:50 libplain.so.2
-rw-r--r--  1 root root 13396 2008-04-09 17:50 libplain.so.2.0.22
-rw-r--r--  1 root root 22126 2008-04-09 17:50 libsasldb.a
-rw-r--r--  1 root root   873 2008-04-09 17:49 libsasldb.la
-rw-r--r--  1 root root 18080 2008-04-09 17:50 libsasldb.so
-rw-r--r--  1 root root 18080 2008-04-09 17:50 libsasldb.so.2
-rw-r--r--  1 root root 18080 2008-04-09 17:50 libsasldb.so.2.0.22
-rw-r--r--  1 root root 23696 2008-04-09 17:50 libsql.a
-rw-r--r--  1 root root   971 2008-04-09 17:49 libsql.la
-rw-r--r--  1 root root 23140 2008-04-09 17:50 libsql.so
-rw-r--r--  1 root root 23140 2008-04-09 17:50 libsql.so.2
-rw-r--r--  1 root root 23140 2008-04-09 17:50 libsql.so.2.0.22
drwxr-xr-x  2 root root  4096 2008-10-29 11:51 sasl2
-rw-r--r--  1 root root   250 2008-10-30 23:57 smtpd.conf

-- listing of /usr/local/lib/sasl2 --
total 12
drwxr-xr-x 2 root root 4096 2008-10-29 11:51 .
drwxr-xr-x 4 root root 4096 2008-10-29 11:50 ..
-rw-r--r-- 1 root root  231 2008-10-30 23:58 smtpd.conf

-- listing of /etc/postfix/sasl --
total 20
drwxr-xr-x 3 root root 4096 2008-10-30 18:37 .
drwxr-xr-x 3 root root 4096 2008-10-29 11:45 ..
drwxr-xr-x 2 root root 4096 2008-10-30 09:55 lala
-rw-r--r-- 1 root root  470 2008-10-30 23:56 smtpd.conf
-rw------- 1 root root  211 2008-10-30 18:37 smtpd.conf.save




-- content of /usr/lib/sasl2/smtpd.conf --
pwcheck_method: authprop
auxprop_plugin: mysql
mech_list: sql plain login
sql_engine: mysql
sql_hostnames: localhost
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select clear from users where id='%u@%r' and enabled = 1


-- content of /usr/local/lib/sasl2/smtpd.conf --
pwcheck_method: auxprop
auxprop_plugin: mysql
sql_engine: mysql
mech_list: sql plain login
sql_hostnames: localhost
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select clear from users where id='%u@%r'


-- content of /etc/postfix/sasl/smtpd.conf --
#pwcheck_method: auxprop
#auxprop_plugin: mysql
#sql_engine: mysql
#mech_list: sql plain login
#sql_hostnames: localhost
sql_user: --- replaced ---
sql_passwd: --- replaced ---
#sql_database: maildb
#sql_select: select crypt from users where id='%u@%r'

pwcheck_method: saslauthd
mech_list: plain login
allow_plaintext: true
auxprop_plugin: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select clear from users where id='%u@%r'


-- content of /etc/postfix/sasl/smtpd.conf --
#pwcheck_method: auxprop
#auxprop_plugin: mysql
#sql_engine: mysql
#mech_list: sql plain login
#sql_hostnames: localhost
sql_user: --- replaced ---
sql_passwd: --- replaced ---
#sql_database: maildb
#sql_select: select crypt from users where id='%u@%r'

pwcheck_method: saslauthd
mech_list: plain login
allow_plaintext: true
auxprop_plugin: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select clear from users where id='%u@%r'



-- active services in /etc/postfix/master.cf --
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
smtp      inet  n       -       -       -       -       smtpd
587       inet  n       -       n       -       -       smtpd
        -o smtpd_enforce_tls=yes
        -o smtpd_sasl_auth_enable=yes
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       n       300     1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
        -o smtp_fallback_relay=
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

-- mechanisms on localhost --
250-AUTH LOGIN PLAIN NTLM CRAM-MD5 DIGEST-MD5
250-AUTH=LOGIN PLAIN NTLM CRAM-MD5 DIGEST-MD5


-- end of saslfinger output --



And here in postconf -n:


# postconf -n

alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
delay_warning_time = 4h
disable_vrfy_command = yes
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
local_recipient_maps =
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination =
myhostname = albpostfix02.domain.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = domain.com
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
relayhost =
smtp_helo_timeout = 60s
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
#

---

