---
title: "SASL to MySQL connection not working"
date: 2007-06-19
forum: Server Platforms
---

### Post by chrishoeppner on 2007-06-19
Hey there!

It would surely have been some kind of miracle if I'd was to get this done on my own at first shot. I've gotten pretty far however.

I'm "building" a mail server for a small office environment. So far, postfix is able to send and receive mail, and thanks to courier, I'm authing people with sasl against a mysql table. Neat. I've tested it from "inside" (eg. loopback) and everything works fine. Then from the "outside" (eg. another box, same network, not in mynetworks directive), pop3 auth works like a charm, but I'm unable to auth my user when sending (eg. smtp). Tailing some logs, I've found that SASL is *not* querying the database when a smtp connections comes in. I've revised the smtpd.conf file 50 times or more, and everything is fine. I've even manually tested a mysql connection with those params, and I get the expected result.

My guess is, postfix is not loading that smtpd.conf file, though it's placed where it's supposed to (eg. /etc/postfix/sasl/smtpd.conf), and I've made it look there explicitly with the smtpd_sasl_path directive, with no luck. Since there's a "default" smtpd.conf file in /usr/lib/sasl2/smtpd.conf, I've changed that one accordingly. No luck too.

I'm pretty clueless, since I do not know where postfix expects this file to be or even if it's looking for it at all.

Here are some snippets from my conf files:

postfix/main.cf
```

# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hos$
                reject_invalid_hostname, permit

# Requirements for the sender details
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks,
                reject_non_fqdn_sender, reject_unknown_sender_domain,
                reject_unauth_pipelining, permit

# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org,
                reject_rbl_client blackholes.easynet.nl,
                reject_rbl_client dnsbl.njabl.org

# Requirement for the recipient address
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks,
                permit_sasl_authenticated, reject_non_fqdn_recipient,
                reject_unauth_destination, check_policy_service inet:127.0.0.1:$
                permit

smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
# I was told postfix adds ".conf" to the below
smtpd_sasl_path = /etc/postfix/sasl/smtpd:/usr/lib/sasl2/smtpd
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

```

postfix/sasl/smtpd.conf
same as /usr/lib/sasl2/smtpd.conf
```

pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: <*>
sql_passwd: <*>
sql_database: maildb
sql_select: SELECT `clear` FROM `users` WHERE `id`='%u@%r' AND `enabled` ='1'

```

Most of this code I've taken from some online guides I've found with minor tweaks of mine. Auth for pop3 / imap works, and I've used the same params here. This discards a problem with SASL itself, and makes me wonder what the problem might be.

Thanks everyone for reading.
Chris Hoeppner
[www.pixware.org](www.pixware.org)

---

### Post by mneisen on 2007-12-07
Hi,

I have exactly the same problem. Postfix will not even try to connect to MySQL when doing SMTP AUTH. On the other hand, using a Berkely DB at /etc/sasldb2 work perfectly.

Has anybody any idea what is wrong here?

Thanks in advance!

Regards
Martin Eisenhardt

---

### Post by shuetrim on 2008-01-22
I am having a very similar problem.  I have been following a range of guides on how to set up Postfix with Courier, Cyrus SASL and MySQL to store information about the virtual domains and mailboxes.

I did manage to get this setup working using Feisty Fawn about 5 months ago but having recently tried to replicate the setup on Gutsy Gibbon I am running into problems.

Specifically, when I attempt to get an authenticated SMTP connection using authentication based on the MYSQL database tables, the connection is refused
and I get the following information in my /var/log/mail.log:

```

Jan 22 21:42:24 mail postfix/smtpd[13587]: connect from t43[192.168.0.4]
Jan 22 21:42:28 mail postfix/smtpd[13587]: warning: SASL authentication failure: Password verification failed
Jan 22 21:42:28 mail postfix/smtpd[13587]: warning: t43[192.168.0.4]: SASL PLAIN authentication failed: authentication failure
Jan 22 21:42:28 mail postfix/smtpd[13587]: warning: t43[192.168.0.4]: SASL LOGIN authentication failed: authentication failure
Jan 22 21:42:30 mail postfix/smtpd[13587]: disconnect from t43[192.168.0.4]

```

Keeping an eye on my /var/log/mysql/mysql.log (which has been enabled in the /etc/mysql/my.cnf configuration file), I notice that no queries are being triggered by this attempted SMTP authentication.

If I run saslfinger then I get:

```

saslfinger - postfix Cyrus sasl configuration Tue Jan 22 21:45:34 CET 2008
version: 1.0.2
mode: server-side SMTP AUTH

-- basics --
Postfix: 2.4.5
System: Ubuntu 7.10 \n \l

-- smtpd is linked to --
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb7ce5000)

-- active SMTP AUTH and TLS parameters for smtpd --
smtpd_sasl_auth_enable = yes


-- listing of /usr/lib/sasl2 --
total 752
drwxr-xr-x   2 root root  4096 2008-01-22 13:13 .
drwxr-xr-x 177 root root 69632 2008-01-22 13:13 ..
-rw-r--r--   1 root root 13640 2007-10-02 15:58 libanonymous.a
-rw-r--r--   1 root root   862 2007-10-02 15:58 libanonymous.la
-rw-r--r--   1 root root 13208 2007-10-02 15:58 libanonymous.so
-rw-r--r--   1 root root 13208 2007-10-02 15:58 libanonymous.so.2
-rw-r--r--   1 root root 13208 2007-10-02 15:58 libanonymous.so.2.0.22
-rw-r--r--   1 root root 15974 2007-10-02 15:58 libcrammd5.a
-rw-r--r--   1 root root   848 2007-10-02 15:58 libcrammd5.la
-rw-r--r--   1 root root 15672 2007-10-02 15:58 libcrammd5.so
-rw-r--r--   1 root root 15672 2007-10-02 15:58 libcrammd5.so.2
-rw-r--r--   1 root root 15672 2007-10-02 15:58 libcrammd5.so.2.0.22
-rw-r--r--   1 root root 47348 2007-10-02 15:58 libdigestmd5.a
-rw-r--r--   1 root root   871 2007-10-02 15:58 libdigestmd5.la
-rw-r--r--   1 root root 43916 2007-10-02 15:58 libdigestmd5.so
-rw-r--r--   1 root root 43916 2007-10-02 15:58 libdigestmd5.so.2
-rw-r--r--   1 root root 43916 2007-10-02 15:58 libdigestmd5.so.2.0.22
-rw-r--r--   1 root root 13650 2007-10-02 15:58 liblogin.a
-rw-r--r--   1 root root   842 2007-10-02 15:58 liblogin.la
-rw-r--r--   1 root root 14036 2007-10-02 15:58 liblogin.so
-rw-r--r--   1 root root 14036 2007-10-02 15:58 liblogin.so.2
-rw-r--r--   1 root root 14036 2007-10-02 15:58 liblogin.so.2.0.22
-rw-r--r--   1 root root 30516 2007-10-02 15:58 libntlm.a
-rw-r--r--   1 root root   836 2007-10-02 15:58 libntlm.la
-rw-r--r--   1 root root 29876 2007-10-02 15:58 libntlm.so
-rw-r--r--   1 root root 29876 2007-10-02 15:58 libntlm.so.2
-rw-r--r--   1 root root 29876 2007-10-02 15:58 libntlm.so.2.0.22
-rw-r--r--   1 root root 13938 2007-10-02 15:58 libplain.a
-rw-r--r--   1 root root   842 2007-10-02 15:58 libplain.la
-rw-r--r--   1 root root 14036 2007-10-02 15:58 libplain.so
-rw-r--r--   1 root root 14036 2007-10-02 15:58 libplain.so.2
-rw-r--r--   1 root root 14036 2007-10-02 15:58 libplain.so.2.0.22
-rw-r--r--   1 root root 22150 2007-10-02 15:58 libsasldb.a
-rw-r--r--   1 root root   863 2007-10-02 15:58 libsasldb.la
-rw-r--r--   1 root root 18356 2007-10-02 15:58 libsasldb.so
-rw-r--r--   1 root root 18356 2007-10-02 15:58 libsasldb.so.2
-rw-r--r--   1 root root 18356 2007-10-02 15:58 libsasldb.so.2.0.22




-- content of /etc/postfix/sasl/smtpd.conf --
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login
sql_engine: mysql
log_level: 7
sql_verbose: yes
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: postfix
sql_select: select password from mailbox where username='%u'



-- active services in /etc/postfix/master.cf --
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
smtp      inet  n       -       -       -       -       smtpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
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
250-AUTH LOGIN PLAIN


-- end of saslfinger output --


```

Note, in particular, that the /etc/postfix/sasl/smtpd.conf file provides what I think are correct parameters to at least get an attempted query run against MySQL.

Any help identifying why the MySQL interaction is not occurring would be very much appreciated.

---

### Post by cyracks on 2008-02-25
since I have exatly the same problem I would just ask if any of you find the solution ?

---

### Post by mneisen on 2008-02-26
> **cyracks said:**
> since I have exatly the same problem I would just ask if any of you find the solution ?

Yes, and a very simple one.

I just switched to dovecot for IMAP, POP3 and SASL. I never had any problems since, and the setup was a matter of minutes. Although courier+cyrus-sasl has served me well a couple of years, I now say: R.I.P., old friend, or get better soon ... :-D

I know, this is not exactly the answer you were looking for. Nevertheless, it relieved me from a royal PITA, and it works perfectly for me. Additionally, dovecot uses a lot less RAM and CPU, so on the same iron, you can handle more users/connections.

Regards
mneisen

---

### Post by dibble5504 on 2008-03-05
I have the same problem.  As I run the server for just my wife and me, I have resorted to adding the users to the sasl DB instead.  It's a bit of a cop-out but it will do until a solution is found.

Paul

---

### Post by dibble5504 on 2008-03-07
[http://ubuntuforums.org/archive/index.php/t-329843.html](http://ubuntuforums.org/archive/index.php/t-329843.html) fixes it!

Just remove smtpd_sasl_path from /etc/postfix/main.cf and restart postfix.

Paul

[http://www.paulmccormack.com](http://www.paulmccormack.com)

---

### Post by mcdee on 2008-06-02
Just for future reference, I had the same problem with SASL failing to authenticate with SQL.  Turned out I was missing the package libsasl2-modules-sql which is required for SQL authentication.

---

