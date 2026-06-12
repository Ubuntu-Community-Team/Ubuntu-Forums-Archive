---
title: "Local mail not working"
date: 2011-03-10
forum: Server Platforms
---

### Post by jerome1232 on 2011-03-10
I feel dumb for not being able to figure this out but on my recently installed server local mail does not work for any user, the only reason this is a concern to me is I have a few security/monitoring programs configured to send mail to root which is then supposed to get delivered to my admin user.

If it helps during the install I selected mail server from the tasksel list and configured it as a local only mail server.

---

### Post by jerome1232 on 2011-03-11
Giving it the ole bump

---

### Post by jerome1232 on 2011-03-12
Bump

Any suggestions?

---

### Post by jerome1232 on 2011-03-13
Bump

---

### Post by SeijiSensei on 2011-03-14
What errors do you see in /var/log/mail.log?  We really can't help if you don't give us more details on exactly what's not working.

---

### Post by Demented ZA on 2011-03-14
Yes, the output of 
```
sudo tail /var/log/mail.log
```
would help.

Also, doing 
```
sudo mailq
```
Will show you if any messages are still unsent in the queue, with the destination as well as the source address.

Nice for solving problems like mail being sent to [email]user@host.domain.com[/email] when it should have been [email]user@domain.com[/email]

---

### Post by jerome1232 on 2011-03-14
Thank your for the suggestions, here is the requested output, if required I can try to do a few emails then repost the last 10 lines of /var/log/mail.log

```
jeremy@voiceserv:~$ tail /var/log/mail.log
Mar 13 22:42:28 voiceserv postfix/local[27003]: 9E17C11F70: to=<jeremy@localhost>, relay=local, delay=0.35, delays=0.15/0.19/0/0.02, dsn=2.0.0, status=sent (forwarded as E050E11F61)
Mar 13 22:42:28 voiceserv postfix/qmgr[26897]: 9E17C11F70: removed
Mar 13 22:42:28 voiceserv postfix/error[27004]: E050E11F61: to=<postmaster@voiceserv.gateway.2wire.net>, orig_to=<jeremy@localhost>, relay=none, delay=0.08, delays=0.01/0.03/0/0.04, dsn=5.0.0, status=bounced (voiceserv.gateway.2wire.net)
Mar 13 22:42:29 voiceserv postfix/error[27004]: E050E11F61: to=<root@voiceserv.gateway.2wire.net>, orig_to=<jeremy@localhost>, relay=none, delay=0.09, delays=0.01/0.03/0/0.05, dsn=5.0.0, status=bounced (voiceserv.gateway.2wire.net)
Mar 13 22:42:29 voiceserv postfix/cleanup[27001]: 0336C11F71: message-id=<20110314054229.0336C11F71@voiceserv.gateway.2wire.net>
Mar 13 22:42:29 voiceserv postfix/qmgr[26897]: 0336C11F71: from=<>, size=2833, nrcpt=1 (queue active)
Mar 13 22:42:29 voiceserv postfix/bounce[27006]: E050E11F61: sender non-delivery notification: 0336C11F71
Mar 13 22:42:29 voiceserv postfix/qmgr[26897]: E050E11F61: removed
Mar 13 22:42:29 voiceserv postfix/error[27004]: 0336C11F71: to=<jeremy@voiceserv.gateway.2wire.net>, relay=none, delay=0.02, delays=0.01/0/0/0.01, dsn=5.0.0, status=bounced (voiceserv.gateway.2wire.net)
Mar 13 22:42:29 voiceserv postfix/qmgr[26897]: 0336C11F71: removed
jeremy@voiceserv:~$ mailq
Mail queue is empty
jeremy@voiceserv:~$ sudo mailq
[sudo] password for jeremy:
Mail queue is empty
jeremy@voiceserv:~$

```

I'm not sure why my server is picking up gateway.2wire.net,

if any of this is relevant: My router does have a dns entry setup for itself as home.gateway.2wire.net, I have this server placed in DMZ+ mode by the router which actually gives it the routers external ip, I have ddclient setup updating the hostname voiceserv.dyndns.org with the ip of eth0(currently 75.15.228.161) every time the ip changes.

---

### Post by Demented ZA on 2011-03-14
Does your isp allocate dynamic(non fixed) ip addresses? Whats the reason for running ddclient?

I'm still trying to understand exactly what is happening in that log file. Your messages have left the que, but they havn't reached you, because they were malformed it seems. Although, I think something like jeremy @ localhost should still be delivered to the user jeremy's inbox under his user account, but I see the message was bounced, and then cleaned, with two subsequent e-mails generated possibly by postfix to let postmaster know of the bounce, but that too failed, as well as the error e-mail sent back to you to notify you of the error.

---

### Post by Demented ZA on 2011-03-14
Again, I'm assuming postfix is your MTA. Please do a
```
sudo service postfix status
```

If you have postfix, it'll tell you its running or something along those lines. If not, it'll tell you unknown process.

If you have postfix, please output the /etc/postfix/main.cf file here (minus personal/private information)

---

### Post by rubylaser on 2011-03-14
Have you tried creating test emails by hand, and seeing what happens?  Send both to a local user, and then on an external host.

```
echo "This is only a test" | mail -s "Test email sent to local root user" root
echo "This is only a test" | mail -s "Test email sent to external" user@gmail.com
```

---

### Post by jerome1232 on 2011-03-14
Yes I am using postfix, I have a dynamically allocated ip address, I use a dyndns account (hence ddclient) to setup a hostname that users of my voice server can connect with a name that doesn't change. I don't think that's really relevant though.


Here is the config file and postfix status.

```

jeremy@voiceserv:~$ sudo service postfix status
[sudo] password for jeremy:
 * postfix is running
jeremy@voiceserv:~$ cat /etc/postfix/main.cf
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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = voiceserv.gateway.2wire.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = voiceserv.dyndns.org, localhost.dyndns.org, localhost, voicserv.gateway.2wire.net, localhost.gateway.2wire.net
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
default_transport = error
relay_transport = error
inet_protocols = ipv4

```

I have those redundant destinations out of, me just trying to get something to work. Maybe I should also add just "voiceserv" as a destination?

---

### Post by jerome1232 on 2011-03-14
here is that test, no go, I also don't want to be able to send mail to external hosts, so I don't expect that to work (gmail would reject mail from my dyndns account's hostname anyways)

```
jeremy@voiceserv:~$ echo "this is only a test" | mail -s "Test email sent to local root user" root
jeremy@voiceserv:~$ echo "this is only a test" | mail -s "Test email sent to external" j.jones1232@gmail.com
jeremy@voiceserv:~$ mail
No mail for jeremy
jeremy@voiceserv:~$ sudo -i
root@voiceserv:~# mail
No mail for root
root@voiceserv:~# exit
logout
jeremy@voiceserv:~$ tail -n 20 /var/log/mail.log
Mar 14 11:30:24 voiceserv postfix/pickup[3396]: 9921111F70: uid=1000 from=<jeremy>
Mar 14 11:30:24 voiceserv postfix/cleanup[3505]: 9921111F70: message-id=<20110314183024.9921111F70@voiceserv.gateway.2wire.net>
Mar 14 11:30:24 voiceserv postfix/qmgr[3397]: 9921111F70: from=<jeremy@voiceserv.gateway.2wire.net>, size=419, nrcpt=1 (queue active)
Mar 14 11:30:24 voiceserv postfix/error[3507]: 9921111F70: to=<root@voiceserv.gateway.2wire.net>, relay=none, delay=0.04, delays=0.03/0/0/0.01, dsn=5.0.0, status=bounced (voiceserv.gateway.2wire.net)
Mar 14 11:30:24 voiceserv postfix/cleanup[3505]: 9FA0411F71: message-id=<20110314183024.9FA0411F71@voiceserv.gateway.2wire.net>
Mar 14 11:30:24 voiceserv postfix/qmgr[3397]: 9FA0411F71: from=<>, size=2334, nrcpt=1 (queue active)
Mar 14 11:30:24 voiceserv postfix/bounce[3509]: 9921111F70: sender non-delivery notification: 9FA0411F71
Mar 14 11:30:24 voiceserv postfix/qmgr[3397]: 9921111F70: removed
Mar 14 11:30:24 voiceserv postfix/error[3507]: 9FA0411F71: to=<jeremy@voiceserv.gateway.2wire.net>, relay=none, delay=0.02, delays=0.01/0/0/0.01, dsn=5.0.0, status=bounced (voiceserv.gateway.2wire.net)
Mar 14 11:30:24 voiceserv postfix/qmgr[3397]: 9FA0411F71: removed
Mar 14 11:30:25 voiceserv postfix/pickup[3396]: 7959711F70: uid=1000 from=<jeremy>
Mar 14 11:30:25 voiceserv postfix/cleanup[3505]: 7959711F70: message-id=<20110314183025.7959711F70@voiceserv.gateway.2wire.net>
Mar 14 11:30:25 voiceserv postfix/qmgr[3397]: 7959711F70: from=<jeremy@voiceserv.gateway.2wire.net>, size=401, nrcpt=1 (queue active)
Mar 14 11:30:25 voiceserv postfix/error[3507]: 7959711F70: to=<j.REALLYNOSPAMjonNOSPAMes1232@NOSPAMgmail.com>, relay=none, delay=0.04, delays=0.02/0/0/0.01, dsn=5.0.0, status=bounced (gmail.com)
Mar 14 11:30:25 voiceserv postfix/cleanup[3505]: 809EC11F71: message-id=<20110314183025.809EC11F71@voiceserv.gateway.2wire.net>
Mar 14 11:30:25 voiceserv postfix/qmgr[3397]: 809EC11F71: from=<>, size=2258, nrcpt=1 (queue active)
Mar 14 11:30:25 voiceserv postfix/bounce[3508]: 7959711F70: sender non-delivery notification: 809EC11F71
Mar 14 11:30:25 voiceserv postfix/qmgr[3397]: 7959711F70: removed
Mar 14 11:30:25 voiceserv postfix/error[3507]: 809EC11F71: to=<jeremy@voiceserv.gateway.2wire.net>, relay=none, delay=0.03, delays=0.01/0/0/0.01, dsn=5.0.0, status=bounced (voiceserv.gateway.2wire.net)
Mar 14 11:30:25 voiceserv postfix/qmgr[3397]: 809EC11F71: removed


```


edit: longer output of log file

---

### Post by rubylaser on 2011-03-14
Your config file looks okay for local delivery.  Can you post the output of the last few lines of your mail.log?
```
tail -n 20 /var/log/mail.log
```
I want to make sure that postfix is using postfix/local instead of postfix/smtp.

Durr, I needed to read above.. :)

---

### Post by jerome1232 on 2011-03-14
Here it is

```
jeremy@voiceserv:~$ tail -n 50 /var/log/mail.log
Mar 14 11:20:57 voiceserv postfix/cleanup[3275]: F157B11F71: message-id=<20110314182057.F157B11F71@voiceserv.gateway.2wire.net>
Mar 14 11:20:57 voiceserv postfix/qmgr[3271]: F157B11F71: from=<>, size=2399, nrcpt=1 (queue active)
Mar 14 11:20:57 voiceserv postfix/bounce[3279]: DF1C411F70: sender non-delivery notification: F157B11F71
Mar 14 11:20:57 voiceserv postfix/qmgr[3271]: DF1C411F70: removed
Mar 14 11:20:58 voiceserv postfix/local[3277]: warning: required alias not found: postmaster
Mar 14 11:20:58 voiceserv postfix/local[3277]: F157B11F71: to=<postmaster@voiceserv.dyndns.org>, orig_to=<jeremy@voiceserv.dyndns.org>, relay=local, delay=0.01, delays=0.01/0/0/0, dsn=2.0.0, status=sent (discarded)
Mar 14 11:20:58 voiceserv postfix/local[3277]: F157B11F71: to=<root@voiceserv.dyndns.org>, orig_to=<jeremy@voiceserv.dyndns.org>, relay=local, delay=0.04, delays=0.01/0/0/0.03, dsn=5.3.0, status=bounced (Command died with status 127: "procmail -a "$EXTENSION"". Command output: sh: procmail: not found )
Mar 14 11:20:58 voiceserv postfix/qmgr[3271]: F157B11F71: removed
Mar 14 11:21:18 voiceserv postfix/master[3268]: terminating on signal 15
Mar 14 11:21:19 voiceserv postfix/master[3394]: daemon started -- version 2.7.1, configuration /etc/postfix
Mar 14 11:28:57 voiceserv postfix/pickup[3396]: F30A511F70: uid=1000 from=<jeremy>
Mar 14 11:28:58 voiceserv postfix/cleanup[3505]: F30A511F70: message-id=<20110314182857.F30A511F70@voiceserv.gateway.2wire.net>
Mar 14 11:28:58 voiceserv postfix/qmgr[3397]: F30A511F70: from=<jeremy@voiceserv.gateway.2wire.net>, size=440, nrcpt=1 (queue active)
Mar 14 11:28:58 voiceserv postfix/error[3507]: F30A511F70: to=<root@voiceserv.gateway.2wire.net>, relay=none, delay=0.09, delays=0.05/0.02/0/0.02, dsn=5.0.0, status=bounced (voiceserv.gateway.2wire.net)
Mar 14 11:28:58 voiceserv postfix/cleanup[3505]: 0E15111F71: message-id=<20110314182858.0E15111F71@voiceserv.gateway.2wire.net>
Mar 14 11:28:58 voiceserv postfix/qmgr[3397]: 0E15111F71: from=<>, size=2355, nrcpt=1 (queue active)
Mar 14 11:28:58 voiceserv postfix/bounce[3508]: F30A511F70: sender non-delivery notification: 0E15111F71
Mar 14 11:28:58 voiceserv postfix/qmgr[3397]: F30A511F70: removed
Mar 14 11:28:58 voiceserv postfix/error[3507]: 0E15111F71: to=<jeremy@voiceserv.gateway.2wire.net>, relay=none, delay=0.02, delays=0.01/0/0/0.01, dsn=5.0.0, status=bounced (voiceserv.gateway.2wire.net)
Mar 14 11:28:58 voiceserv postfix/qmgr[3397]: 0E15111F71: removed
Mar 14 11:29:33 voiceserv postfix/pickup[3396]: 5FD7711F70: uid=1000 from=<jeremy>
Mar 14 11:29:33 voiceserv postfix/cleanup[3505]: 5FD7711F70: message-id=<20110314182933.5FD7711F70@voiceserv.gateway.2wire.net>
Mar 14 11:29:33 voiceserv postfix/qmgr[3397]: 5FD7711F70: from=<jeremy@voiceserv.gateway.2wire.net>, size=422, nrcpt=1 (queue active)
Mar 14 11:29:33 voiceserv postfix/error[3507]: 5FD7711F70: to=<j.jones1232@gmail.com>, relay=none, delay=0.04, delays=0.02/0/0/0.01, dsn=5.0.0, status=bounced (gmail.com)
Mar 14 11:29:33 voiceserv postfix/cleanup[3505]: 6862211F71: message-id=<20110314182933.6862211F71@voiceserv.gateway.2wire.net>
Mar 14 11:29:33 voiceserv postfix/qmgr[3397]: 6862211F71: from=<>, size=2279, nrcpt=1 (queue active)
Mar 14 11:29:33 voiceserv postfix/bounce[3509]: 5FD7711F70: sender non-delivery notification: 6862211F71
Mar 14 11:29:33 voiceserv postfix/qmgr[3397]: 5FD7711F70: removed
Mar 14 11:29:33 voiceserv postfix/error[3507]: 6862211F71: to=<jeremy@voiceserv.gateway.2wire.net>, relay=none, delay=0.02, delays=0.01/0/0/0.01, dsn=5.0.0, status=bounced (voiceserv.gateway.2wire.net)
Mar 14 11:29:33 voiceserv postfix/qmgr[3397]: 6862211F71: removed
Mar 14 11:30:24 voiceserv postfix/pickup[3396]: 9921111F70: uid=1000 from=<jeremy>
Mar 14 11:30:24 voiceserv postfix/cleanup[3505]: 9921111F70: message-id=<20110314183024.9921111F70@voiceserv.gateway.2wire.net>
Mar 14 11:30:24 voiceserv postfix/qmgr[3397]: 9921111F70: from=<jeremy@voiceserv.gateway.2wire.net>, size=419, nrcpt=1 (queue active)
Mar 14 11:30:24 voiceserv postfix/error[3507]: 9921111F70: to=<root@voiceserv.gateway.2wire.net>, relay=none, delay=0.04, delays=0.03/0/0/0.01, dsn=5.0.0, status=bounced (voiceserv.gateway.2wire.net)
Mar 14 11:30:24 voiceserv postfix/cleanup[3505]: 9FA0411F71: message-id=<20110314183024.9FA0411F71@voiceserv.gateway.2wire.net>
Mar 14 11:30:24 voiceserv postfix/qmgr[3397]: 9FA0411F71: from=<>, size=2334, nrcpt=1 (queue active)
Mar 14 11:30:24 voiceserv postfix/bounce[3509]: 9921111F70: sender non-delivery notification: 9FA0411F71
Mar 14 11:30:24 voiceserv postfix/qmgr[3397]: 9921111F70: removed
Mar 14 11:30:24 voiceserv postfix/error[3507]: 9FA0411F71: to=<jeremy@voiceserv.gateway.2wire.net>, relay=none, delay=0.02, delays=0.01/0/0/0.01, dsn=5.0.0, status=bounced (voiceserv.gateway.2wire.net)
Mar 14 11:30:24 voiceserv postfix/qmgr[3397]: 9FA0411F71: removed
Mar 14 11:30:25 voiceserv postfix/pickup[3396]: 7959711F70: uid=1000 from=<jeremy>
Mar 14 11:30:25 voiceserv postfix/cleanup[3505]: 7959711F70: message-id=<20110314183025.7959711F70@voiceserv.gateway.2wire.net>
Mar 14 11:30:25 voiceserv postfix/qmgr[3397]: 7959711F70: from=<jeremy@voiceserv.gateway.2wire.net>, size=401, nrcpt=1 (queue active)
Mar 14 11:30:25 voiceserv postfix/error[3507]: 7959711F70: to=<j.jones1232@gmail.com>, relay=none, delay=0.04, delays=0.02/0/0/0.01, dsn=5.0.0, status=bounced (gmail.com)
Mar 14 11:30:25 voiceserv postfix/cleanup[3505]: 809EC11F71: message-id=<20110314183025.809EC11F71@voiceserv.gateway.2wire.net>
Mar 14 11:30:25 voiceserv postfix/qmgr[3397]: 809EC11F71: from=<>, size=2258, nrcpt=1 (queue active)
Mar 14 11:30:25 voiceserv postfix/bounce[3508]: 7959711F70: sender non-delivery notification: 809EC11F71
Mar 14 11:30:25 voiceserv postfix/qmgr[3397]: 7959711F70: removed
Mar 14 11:30:25 voiceserv postfix/error[3507]: 809EC11F71: to=<jeremy@voiceserv.gateway.2wire.net>, relay=none, delay=0.03, delays=0.01/0/0/0.01, dsn=5.0.0, status=bounced (voiceserv.gateway.2wire.net)
Mar 14 11:30:25 voiceserv postfix/qmgr[3397]: 809EC11F71: removed
jeremy@voiceserv:~$

```

---

### Post by rubylaser on 2011-03-14
Can you telnet to localhost on port 25, and make sure postfix is the mail server that's replying, not sendmail.

```
telnet localhost 25
```

And, have you tried reconfiguring postfix, or re-installing it?  Also, what do you have in /var/log/mail.err and /var/log/mail.info

---

### Post by Demented ZA on 2011-03-14
Well if its local delivery only you want, then that doesn't matter.

I agree with rubylaser, try see if sendmail isn't maybe listening on port 25 instead of postfix.

---

### Post by rubylaser on 2011-03-14
His problem, is that even the local delivery is failing if you read the log files.  I'm not sure why at this point as frankly everything looks okay.  I'm grasping at straws at this point to see if sendmail is getting in the way somehow.

---

### Post by jerome1232 on 2011-03-14
Okay so I noticed an error in that log about not finding procmail, I installed procmail, error no longer appears in log.


I reconfigured postfix using sudo dpkg-reconfigure postfix

the resulting main.cf
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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = voiceserv.dyndns.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = voiceserv.dyndns.org, localhost.dyndns.org, localhost, voicserv.gateway.2wire.net, localhost.gateway.2wire.net, voiceserv
relayhost =
mynetworks = 127.0.0.0/8 192.168.1.0/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
default_transport = error
relay_transport = error
inet_protocols = ipv4

```

Reloaded postfix with new configuration. Still no go, same type of error messages in /var/log/mail.log (mainly bounced mail).

testing telnet 25

```
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 voiceserv.dyndns.org ESMTP Postfix (Ubuntu)
quit
221 2.0.0 Bye
Connection closed by foreign host.

```

I tried reconfiguring procmail with dpkg but it didn't have anything to ask me.

Thanks for all the help so far](*,)

edit: sendmail is also not installed, should it be?

---

### Post by rubylaser on 2011-03-14
No, postfix is a replacement for sendmail, so you don't need it.

---

### Post by rubylaser on 2011-03-14
Here's another stab, what do you have in /etc/aliases? And, have you tried to edit your /etc/hosts file to make voiceserv.gateway.2wire.net resolve to 127.0.0.1 rather than it's internal ip? I'm wondering if it's resolving to the wrong ip, or to your public ip, and not making it back to your machine.  Again, grasping at more straws :)

---

### Post by jerome1232 on 2011-03-14
As an update, I removed postfix with the --purge option and installed exim4.

Mail works, with the exception that mail for postmaster wasn't getting forwarded to my regular user so after seeing rubylaser's post I looked at /etc/aliases and changed from this:

```

root:    jeremy, postmaster

root:    jeremy
```

to this

```

root: jeremy
postmaster: jeremy
```

saved reloaded exim4, mail works. 

I removed exim4, reinstalled postfix.


It works! So either my aliases file was malformed or something was errant in my old postfix config. I'm leaning towards something wrong with config since exim4 partially worked with the bad aliases file.


Here is the new config for comparison.
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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = voiceserv.gateway.2wire.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = voiceserv.dyndns.org, voiceserv.gateway.2wire.net, localhost.gateway.2wire.net, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
default_transport = error
relay_transport = error

```

I don't know why both postfix and exim4 are picking up voiceserv.gateway.2wire.net as my FQDN, I would like it to be voiceserv.dyndns.org but things are working atm and I'm afraid to investigate it.

Marking as solved. Thanks for leading me towards a resolution guys!

---

### Post by rubylaser on 2011-03-14
Glad you got it figured out :)  The main change in your main.cf is the my_networks line...

```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
```

---

