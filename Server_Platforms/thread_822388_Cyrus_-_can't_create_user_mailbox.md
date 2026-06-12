---
title: "Cyrus - can't create user mailbox"
date: 2008-06-08
forum: Server Platforms
---

### Post by satimis on 2008-06-08
Hi folks,


Ubuntu 6.06 drake amd64


I'm following;

Cyrus
[https://help.ubuntu.com/community/Cyrus](https://help.ubuntu.com/community/Cyrus)

building IMAP/POP servers.


Packages installed;```


postfix

cyrus-admin-2.2 
cyrus-clients-2.2 
cyrus-imapd-2.2 
sasl2-bin
cyrus-pop3d-2.2

libc-client-dev
gamin

```


Everything is going on smoothly w/o problem.


Coming to creating Mailbox I can't proceed further;


$ cyradm -u cyrus localhost```

Password: 
localhost> cm user.satimiscyrus
createmailbox: Permission denied

```


$ tail /var/log/mail.log ```

Jun  8 18:09:16 lampserver cyrus/imap[4478]: executed
Jun  8 18:09:16 lampserver cyrus/imap[4478]: accepted connection
Jun  8 18:09:16 lampserver cyrus/imap[4478]: badlogin: localhost [127.0.0.1] plaintext satimis SASL(-1): generic failure: checkpass failed
Jun  8 18:10:19 lampserver cyrus/master[3881]: process 4478 exited, status 0
Jun  8 18:11:04 lampserver cyrus/master[4480]: about to exec /usr/lib/cyrus/bin/imapd
Jun  8 18:11:04 lampserver cyrus/imap[4480]: executed
Jun  8 18:11:04 lampserver cyrus/imap[4480]: accepted connection
Jun  8 18:11:13 lampserver cyrus/imap[4480]: badlogin: localhost [127.0.0.1] DIGEST-MD5 [SASL(-13): authentication failure: client response doesn't match what we generated]
Jun  8 18:11:16 lampserver cyrus/imap[4480]: login: localhost [127.0.0.1] anonymous ANONYMOUS User logged in
Jun  8 18:12:54 lampserver cyrus/master[3881]: process 4480 exited, status 0

```


$ su - cyrus -c cyradm localhost```

Password: 
localhost> cm user.satimiscyrus
createmailbox: Permission denied

```


$ tail /var/log/mail.log ```

Jun  8 18:27:14 lampserver cyrus/ctl_cyrusdb[4497]: archiving log file: /var/lib/cyrus/db/log.0000000001
Jun  8 18:27:14 lampserver cyrus/ctl_cyrusdb[4497]: archiving database file: /var/lib/cyrus/mailboxes.db
Jun  8 18:27:14 lampserver cyrus/ctl_cyrusdb[4497]: archiving log file: /var/lib/cyrus/db/log.0000000001
Jun  8 18:27:14 lampserver cyrus/ctl_cyrusdb[4497]: done checkpointing cyrus databases
Jun  8 18:27:14 lampserver cyrus/master[3881]: process 4497 exited, status 0
Jun  8 18:42:51 lampserver cyrus/master[4511]: about to exec /usr/lib/cyrus/bin/imapd
Jun  8 18:42:51 lampserver cyrus/imap[4511]: executed
Jun  8 18:42:51 lampserver cyrus/imap[4511]: accepted connection
Jun  8 18:43:00 lampserver cyrus/imap[4511]: badlogin: localhost [127.0.0.1] DIGEST-MD5 [SASL(-13): authentication failure: client response doesn't match what we generated]
Jun  8 18:43:03 lampserver cyrus/imap[4511]: login: localhost [127.0.0.1] anonymous ANONYMOUS User logged in

```


I can't resolve```

badlogin: localhost [127.0.0.1] DIGEST-MD5 [SASL(-13): authentication failure: client response doesn't match what we generated

```


I have been trying a day w/o breakthrough


$ sudo grep "^partition-" /etc/imapd.conf```

partition-default: /var/spool/cyrus/mail
partition-news: /var/spool/cyrus/news

```


$ sudo ls -ld /var/spool/cyrus/mail```

drwxr-x--- 29 cyrus mail 4096 2008-05-24 21:46 /var/spool/cyrus/mail

```


$ sudo ls -ld /var/spool/cyrus/news```

drwxr-x--- 29 cyrus mail 4096 2008-05-24 21:46 /var/spool/cyrus/news

```


Please help.  TIA


B.R.
satimis

---

### Post by dcroxton on 2008-07-09
I was having a permission problem (not the same as yours, though), and my permissions looked the same.  I think there must be some issue further down the directory hierarchy.  Anyway, I solved my problem with (found at [http://blog.cottee.org/2008/05/cyrus-imap-on-hardy-heron.html):](http://blog.cottee.org/2008/05/cyrus-imap-on-hardy-heron.html):)

chown -R cyrus:mail /var/spool/cyrus
chown -R cyrus:mail /var/lib/cyrus

Now I have a mailbox.  The server keeps telling the client that it doesn't exist, but it is definitely there when I issue the "lm" command...

Sincerely,
Derek

---

### Post by satimis on 2008-07-09
> **dcroxton said:**
> I was having a permission problem (not the same as yours, though), and my permissions looked the same.  I think there must be some issue further down the directory hierarchy.  Anyway, I solved my problem with (found at [http://blog.cottee.org/2008/05/cyrus-imap-on-hardy-heron.html):](http://blog.cottee.org/2008/05/cyrus-imap-on-hardy-heron.html):)

chown -R cyrus:mail /var/spool/cyrus
chown -R cyrus:mail /var/lib/cyrus

Now I have a mailbox.  The server keeps telling the client that it doesn't exist, but it is definitely there when I issue the "lm" command...

Hi Derek,


Thanks for your advice.


$ ls -ld /var/spool/cyrus/```

drwxr-xr-x 4 cyrus mail 4096 2008-06-07 16:44 /var/spool/cyrus/
```


$ sudo ls -l /var/spool/cyrus/```

total 8
drwxr-x--- 28 cyrus mail 4096 2008-06-16 14:23 mail
drwxr-x--- 29 cyrus mail 4096 2008-05-24 21:46 news

```


$ ls -ld /var/lib/cyrus/```

drwxr-x--- 11 cyrus mail 4096 2008-07-10 01:05 /var/lib/cyrus/
```


$ sudo ls -l /var/lib/cyrus/```

Password:
total 68
-rw-------  1 cyrus mail  144 2008-07-10 01:05 annotations.db
drwx------  2 cyrus mail 4096 2008-07-10 01:05 db
drwx------  2 cyrus mail 4096 2008-07-10 01:05 db.backup1
drwx------  2 cyrus mail 4096 2008-07-10 01:00 db.backup2
-rw-------  1 cyrus mail 8192 2008-07-09 18:54 deliver.db
drwx------  2 cyrus mail 4096 2008-05-24 21:46 log
-rw-------  1 cyrus mail 8896 2008-07-10 01:05 mailboxes.db
drwx------  2 cyrus mail 4096 2008-05-24 21:46 msg
drwx------  2 cyrus mail 4096 2008-07-10 01:06 proc
drwx------ 28 cyrus mail 4096 2008-05-24 21:46 quota
drwxr-x---  2 cyrus mail 4096 2008-06-11 08:30 socket
-rw-------  1 cyrus mail 8192 2008-05-24 21:46 tls_sessions.db
drwx------ 28 cyrus mail 4096 2008-05-24 21:46 user

```


Before reading your posting I performed following test:-


on /etc/imapd.conf

sasl_pwcheck_method: saslauthd

It worked previously without problem.


Then I changed it to;
sasl_pwcheck_method: auxprop


Still failed unable to login cyradm as cyrus


and then again changed it to;
sasl_pwcheck_method: pwcheck


$ sudo /etc/init.d/cyrus2.2 restart```

Stopping Cyrus IMAPd: cyrmaster.
Waiting for complete shutdown....
Starting Cyrus IMAPd: cyrmaster.
```


$ cyradm -user cyrus --auth plain localhost```

Password: 
IMAP Password: 
              Login failed: no mechanism available at /usr/lib/perl5/Cyrus/IMAP/Admin.pm line 118
cyradm: cannot authenticate to server with plain as cyrus

```


line 117    }	
line 118     my $rc = $self->{cyrus}->authenticate(@_);
line 119    if($rc && $self->{support_referrals}) {


changed it back to;
sasl_pwcheck_method: saslauthd


On running;
$ sudo /etc/init.d/cyrus2.2 stop```

Stopping Cyrus IMAPd: .

```


$ sudo /etc/init.d/cyrus2.2 start```

Starting Cyrus IMAPd: /etc/init.d/cyrus2.2: line 153: !check_status: command not found

```


line 152	else
line 153           if !check_status ; then
line 154		echo "(failed)."
line 155		exit 1


$ ps ax | grep cyrus```

 4566 pts/0    S+     0:00 grep cyrus

```

$ sudo netstat -tap | grep cyrus
No printout


$ tail /var/log/syslog```

Jul 10 07:35:01 satimis /USR/SBIN/CRON[4528]: (root) CMD (cd /var/www/SugarCE-Fu
ll-5.0.0e; php -f cron.php > /dev/null 2>&1)
Jul 10 07:36:01 satimis /USR/SBIN/CRON[4531]: (root) CMD (cd /var/www/SugarCE-Fu
ll-5.0.0e; php -f cron.php > /dev/null 2>&1)
Jul 10 07:37:01 satimis /USR/SBIN/CRON[4534]: (root) CMD (cd /var/www/SugarCE-Fu
ll-5.0.0e; php -f cron.php > /dev/null 2>&1)
Jul 10 07:38:01 satimis /USR/SBIN/CRON[4537]: (root) CMD (cd /var/www/SugarCE-Fu
ll-5.0.0e; php -f cron.php > /dev/null 2>&1)
Jul 10 07:39:01 satimis /USR/SBIN/CRON[4540]: (root) CMD (  [ -d /var/lib/php5 ]
 && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xa
rgs -r -0 rm)
Jul 10 07:39:01 satimis /USR/SBIN/CRON[4542]: (root) CMD (cd /var/www/SugarCE-Fu
ll-5.0.0e; php -f cron.php > /dev/null 2>&1)
Jul 10 07:40:01 satimis /USR/SBIN/CRON[4555]: (root) CMD (cd /var/www/SugarCE-Fu
ll-5.0.0e; php -f cron.php > /dev/null 2>&1)
Jul 10 07:41:01 satimis /USR/SBIN/CRON[4558]: (root) CMD (cd /var/www/SugarCE-Fu
ll-5.0.0e; php -f cron.php > /dev/null 2>&1)
Jul 10 07:42:01 satimis /USR/SBIN/CRON[4561]: (root) CMD (cd /var/www/SugarCE-Fu
ll-5.0.0e; php -f cron.php > /dev/null 2>&1)
Jul 10 07:43:01 satimis /USR/SBIN/CRON[4570]: (root) CMD (cd /var/www/SugarCE-Fu
ll-5.0.0e; php -f cron.php > /dev/null 2>&1)

```


$ tail /var/log/messages```

Jul 10 07:25:48 satimis kernel: [   95.854465] IPv6 over IPv4 tunneling driver
Jul 10 07:25:49 satimis kernel: [   98.253304] ppdev: user-space parallel port driver
Jul 10 07:26:25 satimis kernel: [  134.448066] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Jul 10 07:26:25 satimis kernel: [  134.557300] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jul 10 07:26:25 satimis kernel: [  134.557318] NFSD: recovery directory /var/lib/nfs/v4recovery doesn't exist
Jul 10 07:26:25 satimis kernel: [  134.557321] NFSD: starting 90-second grace period
Jul 10 07:26:28 satimis squid[4299]: Squid Parent: child process 4301 started
Jul 10 07:26:30 satimis kernel: [  139.652747] ip_tables: (C) 2000-2002 Netfilter core team
Jul 10 07:26:30 satimis kernel: [  139.854519] Netfilter messages via NETLINK v0.30.
Jul 10 07:26:30 satimis kernel: [  139.879396] ip_conntrack version 2.4 (4095 buckets, 32760 max) - 312 bytes per conntrack

```


$ sudo ls -l /var/lib/cyrus/log/
total 0


$ sudo ls -l /var/lib/cyrus/msg
total 0


Please advise how to revoke it to its previous state?  TIA


B.R.
satimis

---

### Post by satimis on 2008-07-09
Hi Derek and folks,


Problem solved as follow;


$ sudo nano /etc/imapd.conf
comment out
#sasl_minimum_layer and allowapop below, too.

uncomment
sasl_mech_list: PLAIN

sasl_pwcheck_method: saslauthd


$ sudo /etc/init.d/cyrus2.2 restart```

Stopping Cyrus IMAPd: .
Waiting for complete shutdown...
Starting Cyrus IMAPd: cyrmaster.

```

$ cyradm -user cyrus localhost```

IMAP Password: 
localhost.localdomain> cm user.aaa
localhost.localdomain> lm user.aaa*
user.aaa (\HasNoChildren)  

```

only top level mailbox created.  However on the arrival of the first email the other default mailboxes such Trash, Sent, etc. are created automatically.


Thanks again for your assistance


B.R.
satimis

---

