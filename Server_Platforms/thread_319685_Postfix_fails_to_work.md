---
title: "Postfix fails to work"
date: 2006-12-16
forum: Server Platforms
---

### Post by satimis on 2006-12-16
Hi folks,


ubuntu-6.06.1-LAMP-server-amd64


Postfix fails to work

$ sudo postconf -e 'inet_interfaces = all'
bash: postconf: command not found

$ which postconf
No printout

$ ls /usr/sbin/ | grep postconf
No printout

# dpkg -l | grep postfix
rc  postfix          2.2.10-1ubuntu0.1              
A high-performance mail transport agent
* end *

It is there.

$ sudo /etc/init.d/postfix restart
$ sudo /etc/init.d/postfix status
both no printout.


This happened after installing "sendmail" which was to satisfy another problem.  Now "sendmail" has been erased with;

$ sudo apt-get remove sendmail

postfix still fails to work.  Pls advise.  TIA


B.R.
Stephen

---

### Post by chrisfay on 2006-12-16
I would try purging both packages and reinstalling postfix:

```
sudo apt-get remove --purge postfix
```
```
sudo apt-get remove --purge sendmail
```

Then 'locate' any remaining files and delete them manually.

Then reinstall postfix....This solved a similar problem when I switched from sendmail 'to' postfix.

* If you have a customized main.cf file you better save it since purging removes all config files.

---

### Post by satimis on 2006-12-16
Hi chrisfay,

Before reading your posting I already ran;

$ sudo apt-get install postix

Postfix is now running.
$ dpkg -l | grep postfix```

iF  postfix                                          2.2.10-1ubuntu0.1              A high-performance mail transport agent
```
What is "iF"?

At booting text scrolling displayed some files of sendmail can't be removed.  Unfortunation it scrolled too fast.  I hardly read them.  I forget the key combination to hold text scrolling.  Neither I found them on message, kernl.log, etc.  Which file holds text scrolling log?  Tks.

> 
I would try purging both packages and reinstalling postfix:

```
sudo apt-get --purge remove postfix
```
```
sudo apt-get --purge remove sendmail
```

Shall I run them?

> 
Then 'locate' any remaining files and delete them manually.

Pls advise which files?

Others noted with tks.


B.R.
satimis

---

### Post by chrisfay on 2006-12-16
Are the Postfix services running?

```
ps aux | grep postifx
```

---

### Post by satimis on 2006-12-16
> **chrisfay said:**
> Are the Postfix services running?

```
ps aux | grep postifx
```
$ ps aux | grep postfix```

root      5109  0.0  0.1  19556  2020 ?        Ss   16:38   0:00 /usr/lib/postfix/master
root      5136  0.0  0.1  29248  1160 ?        Ss   16:38   0:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -r -a pam
root      5141  0.0  0.0  29248   740 ?        S    16:38   0:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -r -a pam
root      5143  0.0  0.0  29248   672 ?        S    16:38   0:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -r -a pam
root      5144  0.0  0.0  29248   672 ?        S    16:38   0:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -r -a pam
root      5145  0.0  0.0  29248   672 ?        S    16:38   0:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -r -a pam
postfix   5768  0.0  0.1  20588  1944 ?        S    16:38   0:00 pickup -l -t fifo -u -c
postfix   5769  0.0  0.1  20628  1976 ?        S    16:38   0:00 qmgr -l -t fifo -u
satimis   5992  0.0  0.0   3948   920 pts/0    S+   17:08   0:00 grep postfix

```
Tks


B.R.
satimis

---

### Post by chrisfay on 2006-12-16
The package looks like its running fine...are you still having problems?

---

### Post by satimis on 2006-12-16
> **chrisfay said:**
> The package looks like its running fine...are you still having problems?
Hi chrisfay,

Yes, I can't send mail.

New domain:-  satimis.homelinux.com

$ sudo telnet localhost 25```

Trying 127.0.0.1...
Connected to localhost.satimis.homelinux.com.
Escape character is '^]'.
ehlo satimis.homelinux.com
(it hangs here)

```

$cat /etc/postfix/main.cf```

#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

#myhostname = server1.example.com
#myhostname = mail.satimis.freeddns.com
myhostname = satimis.homelinux.com
#mydomain = satimis.freeddns.com
mydomain = satimis.homelinux.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
#myorigin = /etc/mailname
#mydestination = /etc/postfix/local-host-names
myorigin = $myhostname
mydestination = $myhostname, localhost.$mydomain, localhost
#relayhost = satimis.homelinux.com
relayhost = [ndsmtp.netvigator.com]
mynetworks = 127.0.0.0/8, 192.168.0.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reje$smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_type = cyrus

smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
mailbox_command =
home_mailbox = Maildir/
virtual_maps = hash:/etc/postfix/virtusertable

```

$ /etc/hosts```

127.0.0.1       localhost.satimis.homelinux.com  localhost
192.168.0.100   mail.satimis.homelinux.com mail

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

$ cat /etc/hostname```

satimis.homelinux.com

```

Tks


B.R.
satimis

---

### Post by chrisfay on 2006-12-16
You're blocked on port 25. Try telneting to any mail server on port 25 and you'll get the same response. That's what I had told you in an earlier post on my forum.

Have you configured a 3rd party service to accept and send mail on an alternative port as suggested? If so, have you changed your master.cf file to function on that new port?

---

### Post by satimis on 2006-12-16
Hi chrisfay,

> 
you're blocked on port 25. Try telneting to any mail server on port 25 and you'll get the same response. That's what I had told you in an earlier post on my forum.

Have you configured a 3rd party service to accept and send mail on an alternative port as suggested? If so, have you changed your master.cf file to function on that new port?

I send mails relayed via ISP mail server

$ cat /etc/postfix/main.cf```

....
relayhost = [ndsmtp.netvigator.com]
......
.....

```

This arrangement worked while running "satimis.freeddns.com" as domain previously.  After changing the domain as "satimis.freeddns.com" it failed to work.

"ping satimis.homelinux.com" worked.  "satimis.homelinux.com:8080" can visit the homepage on the server.  Port 80 is blocked by ISP, I suppose.


Edit:-

So I suspect there'll be problem on Postfix and the removed Sendmail


B.R.
satimis

---

### Post by chrisfay on 2006-12-16
> i send mails relayed via ISP mail server

So what happens if you:

```
telnet ndsmtp.netvigator.com 25
```

If you get:
> 220 wcppop01.icm.netvigator.com ESMTP Relay service (7.3.104) ready
Then you can rule out being blocked on 25, and should check your configuration files.

If it just hangs, then either your blocked, or you have a firewall/port routing issue.

Port 80 and 8080 have nothing to do with your postfix issue. Although as a side not, if you are blocked on 25, you may as well be on 80.

---

### Post by satimis on 2006-12-16
Hi chrisfay,

> 
So what happens if you:

```
telnet ndsmtp.netvigator.com 25
```

# telnet ndsmtp.netvitgator.com 25```

Trying 64.20.33.131...


Then you can rule out being blocked on 25, and should check your configuration files.

If it just hangs, then either your blocked, or you have a firewall/port routing issue.

Port 80 and 8080 have nothing to do with your postfix issue. Although as a side not, if you are blocked on 25, you may as well be on 80.[/QUOTE]


(It hung here)

```

# telnet ndpop.netvigator.com 25```

Trying 219.76.95.44...
Connected to ndpop.netvigator.com.
Escape character is '^]'.
220 wcppop03dat.icm.netvigator.com ESMTP Relay service (7.3.104) ready
(it also hung here.  Waiting for input???)

```

Before installing Sendmail.  It can send mails via relayhost=[ndsmtp.netvigator.com].  Strangely now it did work.

Neither I haven't touched anything on firewall.

# iptables -L```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/S YN tcpmss match 1400:1536 TCPMSS clamp to PMTU

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Others noted with tks.

B.R.
satimis

---

### Post by chrisfay on 2006-12-16
> 
# telnet ndpop.netvigator.com 25
Trying 219.76.95.44...
Connected to ndpop.netvigator.com.
Escape character is '^]'.
220 wcppop03dat.icm.netvigator.com ESMTP Relay service (7.3.104) ready
(it also hung here.  Waiting for input???)

Good, port 25 is open....

Can you try sending an email somewhere and post the resulting logs in /var/log/mail.log?
Also check /var/log/mail.err

---

### Post by satimis on 2006-12-16
Hi chrisfay

> Good, port 25 is open....

Is "ndpop" the outgoing port on ISP mail server?

> 
Can you try sending an email somewhere and post the resulting logs in /var/log/mail.log?
Also check /var/log/mail.err

# telnet ndpop.netvigator.com 25```

Trying 219.76.95.44...
Connected to ndpop.netvigator.com.
Escape character is '^]'.
220 wcppop03dat.icm.netvigator.com ESMTP Relay service (7.3.104) ready
ehlo satimis.homelinux.com
250-wcppop03dat.icm.netvigator.com
250-DSN
250-8BITMIME
250-PIPELINING
250-HELP
250-AUTH=LOGIN
250-AUTH LOGIN CRAM-MD5 DIGEST-MD5 PLAIN
250-X-CP-DELIVER-AFTER
250-DELIVERBY 300
250 SIZE
mail from: satimis@satimis.homelinux.com
501 Syntax error in parameters or arguments to MAIL command
(it hung here)

```

# telnet localhost 25```

Trying 127.0.0.1...
Connected to localhost.satimis.homelinux.com.
Escape character is '^]'.
ehlo satimis.homelinus.com
(it hung here)

```

# tail -f /var/log/mail.err```

Dec 16 19:41:23 mail postfix/smtpd[7012]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 19:42:24 mail postfix/smtpd[7013]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 19:43:25 mail postfix/smtpd[7018]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 19:44:26 mail postfix/smtpd[7019]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 19:45:27 mail postfix/smtpd[7034]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 19:46:28 mail postfix/smtpd[7040]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 19:47:29 mail postfix/smtpd[7041]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 19:48:30 mail postfix/smtpd[7042]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 19:49:31 mail postfix/smtpd[7077]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 19:50:32 mail postfix/smtpd[7078]: fatal: open database /etc/aliases.db: No such file or directory

```

B.R.
satimis

---

### Post by chrisfay on 2006-12-16
Your Postfix server took a crap...:p 

> Is "ndpop" the outgoing port on ISP mail server?

From the name of it I would say no, but it accepts connections on port 25 which was all you needed to prove your port was open.

As far as your logs are concerned, its pretty apparent you're missing some postfix files, specifically the aliases.db. There may be more and Postfix just locked at that one.

I would purge remove and reinstall postfix to get all your files back. Again, saving any custom config files you've created. (ie. main.cf, master.cf)



**EDIT**: After re-reading your logs and your main.cf file, I would comment out both:

```
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
```

Restart Postfix and see if you get a new error when sending mail.

---

### Post by satimis on 2006-12-16
Hi chrisfay,


# cp /etc/postfix/main.cf /home/satimis/
# cp /etc/postfix/master.cf /home/satimis/


# apt-get remove --purge postfix```

Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  courier-imap* courier-imap-ssl* courier-pop* courier-pop-ssl* postfix*
  sensible-mda*
0 upgraded, 0 newly installed, 6 to remove and 7 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7033kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 93174 files and directories currently installed.)
Removing courier-pop-ssl ...
 * Stopping Courier POP3-SSL server...                                   [ ok ]
Purging configuration files for courier-pop-ssl ...
Removing courier-pop ...
 * Stopping Courier POP3 server...                                       [ ok ]
Purging configuration files for courier-pop ...
Removing courier-imap-ssl ...
 * Stopping Courier IMAP-SSL server...                                   [ ok ]
Purging configuration files for courier-imap-ssl ...
Removing courier-imap ...
 * Stopping Courier IMAP server...                                       [ ok ]
Purging configuration files for courier-imap ...
Removing sensible-mda ...
Purging configuration files for sensible-mda ...
Removing postfix ...
 * Stopping Postfix Mail Transport Agent postfix                         [ ok ]
Purging configuration files for postfix ...

```

# apt-get remove --purge sendmail```

Reading package lists... Done
Building dependency tree... Done
Package sendmail is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

```

# apt-get install postfix```

Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  postfix-mysql postfix-pgsql postfix-ldap postfix-pcre
Recommended packages:
  resolvconf
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B/1002kB of archives.
After unpacking 2499kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package postfix.
(Reading database ... 92947 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.2.10-1ubuntu0.1_amd64.deb) ...
Setting up postfix (2.2.10-1ubuntu0.1) ...
Adding group `postfix' (113)...
Done.
Adding system user `postfix'...
Adding new user `postfix' (108) with group `postfix'.
Not creating home directory `/var/spool/postfix'.
Creating /etc/postfix/dynamicmaps.cflocalhost 25
Adding tcp map entry to /etc/postfix/dynamicmaps.cf
Adding group `postdrop' (114)...
Done.

Postfix was not set up.  Start with
  cp /usr/share/postfix/main.cf.debian /etc/postfix/main.cf
.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

```


# cp /home/satimis/main.cf /etc/postfix/
# cp /home/satimis/master.cf /etc/postfix/master.cf


commented out;
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
on /etc/postfix/main.cf


# /etc/init.d/postfix start
 * Starting Postfix Mail Transport Agent postfix                         [ ok ]

# telnet localhost 25```

Trying 220.246.239.14...
telnet: Unable to connect to remote host: Connection refused
root@mail:/home/satimis# telnet satimis.homelinux.com 25
Trying 220.246.239.14...
Connected to satimis.homelinux.com.
Escape character is '^]'.
ehlo satimis.homelinux.com
(it hung here)

```

# tail -f /var/log/mail.err```

Dec 16 20:37:34 mail postfix/smtpd[7897]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 20:38:35 mail postfix/smtpd[7932]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 20:39:36 mail postfix/smtpd[7970]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 20:40:01 mail postfix/cleanup[7990]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Dec 16 20:40:37 mail postfix/smtpd[7993]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 20:41:02 mail postfix/cleanup[7994]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Dec 16 20:41:38 mail postfix/smtpd[7995]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 20:42:01 mail postfix/cleanup[8102]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Dec 16 20:42:34 mail postfix/smtpd[8106]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 20:43:02 mail postfix/cleanup[8108]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory

```

# telnet ndpop.netvigator.com 25```

Trying 219.76.95.44...
Connected to ndpop.netvigator.com.
Escape character is '^]'.
220 wcppop03dat.icm.netvigator.com ESMTP Relay service (7.3.104) ready
ehlo satimis.homelinux.com
250-wcppop03dat.icm.netvigator.com
250-DSN
250-8BITMIME
250-PIPELINING
250-HELP
250-AUTH=LOGIN
250-AUTH LOGIN CRAM-MD5 DIGEST-MD5 PLAIN
250-X-CP-DELIVER-AFTER
250-DELIVERBY 300
250 SIZE
mail from: satimis@satimis.homelinux.com
501 Syntax error in parameters or arguments to MAIL command
(it hung here)

```

$ tail -f /var/log/mail.err```

Dec 16 20:42:34 mail postfix/smtpd[8106]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 20:43:02 mail postfix/cleanup[8108]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Dec 16 20:43:35 mail postfix/smtpd[8115]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 20:44:03 mail postfix/cleanup[8116]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Dec 16 20:44:36 mail postfix/smtpd[8117]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 20:45:04 mail postfix/cleanup[8119]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Dec 16 20:45:37 mail postfix/smtpd[8122]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 20:46:05 mail postfix/cleanup[8123]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Dec 16 20:46:38 mail postfix/smtpd[8124]: fatal: open database /etc/aliases.db: No such file or directory
Dec 16 20:47:06 mail postfix/cleanup[8145]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory

```


B.R.
satimis

---

### Post by chrisfay on 2006-12-17
Run:

```
sudo newaliases
```
...to recreate the aliases db in the correct format.

> Dec 16 20:40:01 mail postfix/cleanup[7990]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory

Does /etc/postfix/virtusertable exist? If so, run:
```
sudo postmap /etc/postfix/virtusertable
```

Restart Postfix and check again...

---

### Post by satimis on 2006-12-17
Hi chrisfay,

$ sudo newaliases```

sudo: unable to lookup #mail.satimis.freeddns.com
satimis.homelinux.com via gethostbyname()
Password:

```

> 
Does /etc/postfix/virtusertable exist?

$ ls /etc/postfix/ | grep virtusertable
No printout

satimis

---

