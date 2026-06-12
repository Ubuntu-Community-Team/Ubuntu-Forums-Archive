---
title: "posfix send mail only from localhost"
date: 2009-11-03
forum: Server Platforms
---

### Post by manuel11g on 2009-11-03
Hello,

I have a big problem on my vps. 
I have Ubuntu 8.04 Hardy and I have installed EHCP. In the first week worked with out any trouble. A couple of days ago one of my users tell me that they can not send mail anymore using smtp. 

I've look on the server and I found that EHCP use postfix and when I try to connect and send a mail from the server - from webmail or from telnet - it works. I tried to solve the problem but I can't.

Please help.

Here are some infos about my server:

Linux avantajtour 2.6.18-028stab059.6 #1 SMP Fri Nov 14 14:01:22 MSK 2008 i686 GNU/Linux


```
root@avantajtour:/var/log# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```
```
root@avantajtour:/var/log# netstat --tcp --listening --programs
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:auth                  *:*                     LISTEN      13969/xinetd    
tcp        0      0 *:ftp                   *:*                     LISTEN      14225/vsftpd    
tcp        0      0 42.164.36.89.sta:domain *:*                     LISTEN      1839/named      
tcp        0      0 avantajtour:domain      *:*                     LISTEN      1839/named      
tcp        0      0 localhost.locald:domain *:*                     LISTEN      1839/named      
tcp        0      0 *:smtp                  *:*                     LISTEN      3767/master     
tcp        0      0 localhost.localdo:60000 *:*                     LISTEN      24250/postgrey.pid 
tcp        0      0 localhost.localdo:mysql *:*                     LISTEN      15985/mysqld    
tcp        0      0 *:www                   *:*                     LISTEN      10042/apache2   
tcp6       0      0 [::]:domain             [::]:*                  LISTEN      1839/named      
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      1867/sshd       
tcp6       0      0 [::]:imaps              [::]:*                  LISTEN      13531/couriertcpd
tcp6       0      0 [::]:pop3s              [::]:*                  LISTEN      13620/couriertcpd
tcp6       0      0 [::]:pop3               [::]:*                  LISTEN      13578/couriertcpd
tcp6       0      0 [::]:imap2              [::]:*                  LISTEN      13487/couriertcpd
tcp6       0      0 [::]:webcache           [::]:*                  LISTEN      16267/python   
```
main.cf :

```


root@avantajtour:/etc/postfix# cat main.cf
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

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = avantajtour
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = localhost, 89.36.164.42
relayhost =
mynetworks = 127.0.0.0/8, 192.168.0.0/16, 172.16.0.0/16, 10.0.0.0/8,  89.36.164.0/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, proxy:mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,check_client_access hash:/var/lib/pop-before-smtp/hosts,reject_unauth_destination
#smtpd_recipient_restrictions = permit_all
smtp_use_tls = yes
smtpd_tls_auth_only = no
smtpd_tls_CAfile = /etc/postfix/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $mynetworks $virtual_mailbox_limit_maps

```master.cf:

```



root@avantajtour:/etc/postfix# cat master.cf
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
    -o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


``````
root@avantajtour:/var/log# tail mail.warn
Nov  3 18:05:03 avantajtour postfix/smtpd[30325]: warning: unknown[92.83.252.4]: SASL LOGIN authentication failed: authentication failure
Nov  3 18:06:42 avantajtour postfix/smtpd[30325]: warning: unknown[92.83.252.4]: SASL LOGIN authentication failed: authentication failure
Nov  3 18:58:01 avantajtour postfix/smtpd[9380]: warning: 82.79.116.189: hostname 82-79-116-189-B-S.galati.rdsnet.ro verification failed: Name or service not known
Nov  3 20:20:09 avantajtour postfix/smtpd[10151]: warning: 82.79.116.189: hostname 82-79-116-189-B-S.galati.rdsnet.ro verification failed: Name or service not known
Nov  3 22:45:12 avantajtour postfix/smtpd[30383]: warning: 82.79.116.189: hostname 82-79-116-189-B-S.galati.rdsnet.ro verification failed: Name or service not known
Nov  3 23:23:22 avantajtour postfix/smtpd[8176]: warning: 82.79.116.189: hostname 82-79-116-189-B-S.galati.rdsnet.ro verification failed: Name or service not known
Nov  3 23:48:51 avantajtour postfix/smtpd[25681]: warning: 82.79.116.189: hostname 82-79-116-189-B-S.galati.rdsnet.ro verification failed: Name or service not known
Nov  4 00:05:09 avantajtour postfix/smtpd[32144]: warning: 82.79.116.189: hostname 82-79-116-189-B-S.galati.rdsnet.ro verification failed: Name or service not known
Nov  4 00:28:20 avantajtour postfix/smtpd[7653]: warning: 82.79.116.189: hostname 82-79-116-189-B-S.galati.rdsnet.ro verification failed: Name or service not known

```

---

