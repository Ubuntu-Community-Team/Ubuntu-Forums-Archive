---
title: "Postfix Problems"
date: 2007-11-01
forum: Server Platforms
---

### Post by Keef on 2007-11-01
I've been trying to get a working mail server up for a few days now, wasting hours with no luck.

I used this guide to try to get postfix up and running:
[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

When I telnet to the mail server and send mail to the server everything looks fine.

```
$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 monkey ESMTP Sendmail 8.14.1/8.14.1/Debian-8ubuntu1; Thu, 1 Nov 2007 17:27:16 +1000; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
```

But the messages stay in the queue and when I try to "flush" them all  using:

```
/usr/sbin/postqueue -c /etc/postfix -f
```

I get this error:

```
postqueue: fatal: Cannot flush mail queue - mail system is down
```

This is my **/etc/postfix/main.cf**:
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
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = cmonkey.ath.cx
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = cmonkey.ath.cx, localhost.localdomain, localhost
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
smtpd_sasl_local_domain =
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated permit_mynetworks reject_unauth_destination permit_inet_interfaces
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
smtpd_use_tls = yes
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
inet_interfaces = all
smtpd_sasl_security_options =
```

Oh and...
[LIST]
[*]I've tried restarting postfix.
[*]I've tried reinstalling it.
[*]My ISP doesn't seem to block ports.
[*]Firewall is configured properly.
[*]Ports are forwarded.
[/LIST]

---

### Post by MJN on 2007-11-01
Post your log (/var/log/mail.log) as this will likely contain some vital clues.
 
Mathew

---

### Post by Keef on 2007-11-01
The log file is huge, this is just a part of it, but it should suffice: 

```
Nov  1 20:34:56 monkey sm-mta[11979]: l9VECf29011468: to=<xxxxxx@gmail.com>, ctl                                                                              addr=<www-data@monkey> (33/33), delay=20:22:14, xdelay=00:47:16, mailer=esmtp, p                                                                              ri=2100292, relay=gsmtp163.google.com. [64.233.163.27], dsn=4.0.0, stat=Deferred                                                                              : Connection timed out with gsmtp163.google.com.
Nov  1 20:44:56 monkey sm-mta[11983]: l9VDBhdC011343: to=<xxxxxx@gmail.com>, ctl                                                                              addr=<mark@monkey> (1000/1000), delay=21:33:13, xdelay=00:47:17, mailer=esmtp, p                                                                              ri=2280294, relay=gsmtp183.google.com. [64.233.183.27], dsn=4.0.0, stat=Deferred                                                                              : Connection timed out with gsmtp183.google.com.
Nov  1 21:01:52 monkey sm-mta[12004]: lA14h6ir013364: to=<xxxxxx@gmail.com>, ctl                                                                              addr=<www-data@monkey> (33/33), delay=06:18:45, xdelay=00:44:12, mailer=esmtp, p                                                                              ri=660292, relay=gsmtp163.google.com. [64.233.163.27], dsn=4.0.0, stat=Deferred:                                                                               Connection timed out with gsmtp163.google.com.
Nov  1 21:21:53 monkey sm-mta[12011]: l9VECf29011468: to=<xxxxxx@gmail.com>, ctl                                                                              addr=<www-data@monkey> (33/33), delay=21:09:11, xdelay=00:44:13, mailer=esmtp, p                                                                              ri=2190292, relay=gsmtp163.google.com. [64.233.163.27], dsn=4.0.0, stat=Deferred                                                                              : Connection timed out with gsmtp163.google.com.
Nov  1 21:28:38 monkey sm-mta[12026]: l9VDBhdC011343: to=<xxxxxx@gmail.com>, ctl                                                                              addr=<mark@monkey> (1000/1000), delay=22:16:55, xdelay=00:40:58, mailer=esmtp, p                                                                              ri=2370294, relay=gsmtp163.google.com. [64.233.163.27], dsn=4.0.0, stat=Deferred                                                                              : Connection timed out with gsmtp163.google.com.
Nov  1 21:48:38 monkey sm-mta[12063]: lA14h6ir013364: to=<xxxxxx@gmail.com>, ctl                                                                              addr=<www-data@monkey> (33/33), delay=07:05:31, xdelay=00:40:58, mailer=esmtp, p                                                                              ri=750292, relay=gsmtp163.google.com. [64.233.163.27], dsn=4.0.0, stat=Deferred:                                                                               Connection timed out with gsmtp163.google.com.
Nov  1 22:08:49 monkey sm-mta[12084]: l9VECf29011468: to=<xxxxxx@gmail.com>, ctl                                                                              addr=<www-data@monkey> (33/33), delay=21:56:07, xdelay=00:41:04, mailer=esmtp, p                                                                              ri=2280292, relay=gsmtp163.google.com. [64.233.163.27], dsn=4.0.0, stat=Deferred                                                                              : Connection timed out with gsmtp163.google.com.
Nov  1 22:25:02 monkey sm-mta[12087]: l9VDBhdC011343: to=<xxxxxx@gmail.com>, ctl                                                                              addr=<mark@monkey> (1000/1000), delay=23:13:19, xdelay=00:47:17, mailer=esmtp, p                                                                              ri=2460294, relay=gsmtp183.google.com. [64.233.183.27], dsn=4.0.0, stat=Deferred                                                                              : Connection timed out with gsmtp183.google.com.
Nov  1 22:41:53 monkey sm-mta[12106]: lA14h6ir013364: to=<xxxxxx@gmail.com>, ctl                                                                              addr=<www-data@monkey> (33/33), delay=07:58:46, xdelay=00:44:13, mailer=esmtp, p                                                                              ri=840292, relay=gsmtp183.google.com. [64.233.183.27], dsn=4.0.0, stat=Deferred:                                                                               Connection timed out with gsmtp183.google.com.
```

(I edited out my email address so it doesn't get picked up my spambots)

I do have a working (and fast) internet connection, also http, ftp, sql servers are already installed if this helps. Oh and I tried sending to other email addresses not listed here.

---

### Post by MJN on 2007-11-01
Uh? It looks like you're using Sendmail as your MTA, yet the HowTo is for Postfix. (I didn't spot the Sendmail banner line in your first post but the logs give it away)
 
Remove Sendmail and then see how you do...
 
(I'm surprised Postfix was even able to start given Sendmail will have been hogging port 25, althought the 'mail system is down' warning suggests it actually didn't)
 
Mathew

---

### Post by Keef on 2007-11-01
It doesn't seem to be installed:

```

root@monkey:~# apt-get remove sendmail
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package sendmail is not installed, so not removed
The following packages were automatically installed and are no longer required:
  sendmail-base sensible-mda sendmail-cf
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by ronald.higgins on 2007-11-01
It is bizarre "sm-mta" is sendmail ....

---

### Post by MJN on 2007-11-01
The 'sendmail' package is likely to be just a meta package which depends on various sendmail components and supporting packages. So, whilst you may not have the 'sendmail' (meta)package installed you do have a large chunk of its dependents, which are no longer required by other packages (or indeed by you!).
 
Remove those packages it mentioned (sendmail-base sensible-mda sendmail-cf) or use the autoremove directive as advised.
 
Mathew

---

### Post by Keef on 2007-11-01
Sorry my bad, I cleared the logs then tried to send a couple emails:

```
Nov  1 23:24:24 monkey postfix/postqueue[12430]: warning: Mail system is down -- accessing queue directly
Nov  1 23:24:29 monkey postfix/postqueue[12436]: warning: Mail system is down -- accessing queue directly
```

---

### Post by MJN on 2007-11-01
Our last posts may have collided - have you removed the sendmail 'sub'packages?
 
Mathew

---

### Post by Keef on 2007-11-01
Yes I have.

---

### Post by ronald.higgins on 2007-11-01
Do a 'sudo netstat -ntap' and let's see if anything is hogging port 25.

rH

---

### Post by Keef on 2007-11-01
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:51234           0.0.0.0:*               LISTEN     12160/server_linux
tcp        0      0 0.0.0.0:14534           0.0.0.0:*               LISTEN     12160/server_linux
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     4891/mysqld
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN     6315/sendmail: MTA:
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     5055/smbd
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN     7542/perl
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     5076/vsftpd
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     6315/sendmail: MTA:
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     5055/smbd
tcp        0      0 192.168.1.105:10000     192.168.1.100:2499      ESTABLISHED12898/perl
tcp        0      1 192.168.1.105:55172     66.249.93.114:25        SYN_SENT   12239/l9VECf2901146
tcp        0      0 192.168.1.105:445       192.168.1.100:4426      ESTABLISHED6229/smbd
tcp        0      1 192.168.1.105:59983     64.233.183.27:25        SYN_SENT   12198/lA14h6ir01336
tcp        0      0 192.168.1.105:445       192.168.1.104:3126      ESTABLISHED11879/smbd
tcp6       0      0 :::80                   :::*                    LISTEN     5205/apache2
tcp6       0      0 :::22                   :::*                    LISTEN     4797/sshd
tcp6       0      1 ::ffff:192.168.1.:49432 ::ffff:72.14.247.27:25  SYN_SENT   12275/l9VDBhdC01134
tcp6       0      0 ::ffff:192.168.1.105:22 ::ffff:192.168.1.1:4969 ESTABLISHED12200/sshd: mark [p
```

Ok sendmail seems to still be running, so I killed the processes and restarted postfix now this is what I have:

```
tcp        0      0 0.0.0.0:51234           0.0.0.0:*               LISTEN     12160/server_linux
tcp        0      0 0.0.0.0:14534           0.0.0.0:*               LISTEN     12160/server_linux
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     4891/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     5055/smbd
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN     7542/perl
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     5076/vsftpd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     13028/master
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     5055/smbd
tcp        0      1 192.168.1.105:51445     209.85.199.27:25        SYN_SENT   13037/smtp
tcp        0      1 192.168.1.105:51444     209.85.199.27:25        SYN_SENT   13035/smtp
tcp        0      0 192.168.1.105:10000     192.168.1.100:2499      ESTABLISHED12898/perl
tcp        0      0 192.168.1.105:445       192.168.1.100:4426      ESTABLISHED6229/smbd
tcp        0      0 192.168.1.105:445       192.168.1.104:3126      ESTABLISHED11879/smbd
tcp6       0      0 :::80                   :::*                    LISTEN     5205/apache2
tcp6       0      0 :::22                   :::*                    LISTEN     4797/sshd
tcp6       0      0 :::25                   :::*                    LISTEN     13028/master
tcp6       0    148 ::ffff:192.168.1.105:22 ::ffff:192.168.1.1:4969 ESTABLISHED12200/sshd: mark [p

```

I tried sending a couple more emails (with no luck) and I'm still getting errors in my mail log:

```
Nov  1 23:36:18 monkey postfix/smtp[13037]: connect to alt1.gmail-smtp-in.l.google.com[66.249.83.114]: Connection timed out (port 25)
```

---

### Post by ronald.higgins on 2007-11-01
:) 

Getting there.

From the host itself can you telnet to alt1.gmail-smtp-in.l.google.com on port 25?

---

### Post by Keef on 2007-11-01
I can't through either my server or my main computer, I did try another email address also with no luck:

```
Nov  1 23:51:32 monkey postfix/pickup[13031]: E5BDE2950005: uid=33 from=<www-data>
Nov  1 23:51:32 monkey postfix/cleanup[13185]: E5BDE2950005: message-id=<20071101135132.E5BDE2950005@cmonkey.ath.cx>
Nov  1 23:51:32 monkey postfix/qmgr[13032]: E5BDE2950005: from=<www-data@cmonkey.ath.cx>, size=320, nrcpt=1 (queue active)
Nov  1 23:51:43 monkey postfix/smtp[13178]: connect to mx1.hotmail.com[65.54.245.8]: Connection timed out (port 25)
Nov  1 23:51:47 monkey postfix/smtp[13179]: connect to alt1.gmail-smtp-in.l.google.com[66.249.83.114]: Connection timed out (port 25)
Nov  1 23:51:47 monkey postfix/smtp[13179]: 7C4662950033: to=<xxxxxx@gmail.com>, relay=none, delay=747, delays=596/0.02/152/0, dsn=4.4.1, status=deferred (connect to alt1.gmail-smtp-in.l.google.com[66.249.83.114]: Connection timed out)
Nov  1 23:51:47 monkey postfix/qmgr[13032]: warning: qmgr_active_corrupt: save corrupt file queue active id 7C4662950033: No such file or directory
Nov  1 23:51:49 monkey postfix/smtp[13190]: connect to mx2.hotmail.com[65.54.244.40]: Connection timed out (port 25)
Nov  1 23:52:03 monkey postfix/smtp[13438]: connect to mx2.hotmail.com[65.54.245.40]: Connection timed out (port 25)
Nov  1 23:52:13 monkey postfix/smtp[13178]: connect to mx2.hotmail.com[65.54.244.168]: Connection timed out (port 25)
Nov  1 23:52:19 monkey postfix/smtp[13190]: connect to mx2.hotmail.com[65.54.245.40]: Connection timed out (port 25)
Nov  1 23:52:33 monkey postfix/smtp[13438]: connect to mx3.hotmail.com[65.54.245.72]: Connection timed out (port 25)
Nov  1 23:52:43 monkey postfix/smtp[13178]: connect to mx2.hotmail.com[65.54.244.40]: Connection timed out (port 25)
Nov  1 23:52:44 monkey postfix/smtp[13178]: 4D821295003D: to=<xxxxxx@hotmail.com>, relay=none, delay=151, delays=0.03/0/151/0, dsn=4.4.1, status=deferred (connect to mx2.hotmail.com[65.54.244.40]: Connection timed out)
Nov  1 23:52:44 monkey postfix/qmgr[13032]: warning: qmgr_active_corrupt: save corrupt file queue active id 4D821295003D: No such file or directory
Nov  1 23:52:49 monkey postfix/smtp[13190]: connect to mx1.hotmail.com[65.54.244.136]: Connection timed out (port 25)
Nov  1 23:52:49 monkey postfix/smtp[13190]: D19BF295003E: to=<xxxxxx@hotmail.com>, relay=none, delay=151, delays=0.03/0.01/151/0, dsn=4.4.1, status=deferred (connect to mx1.hotmail.com[65.54.244.136]: Connection timed out)
Nov  1 23:52:49 monkey postfix/qmgr[13032]: warning: qmgr_active_corrupt: save corrupt file queue active id D19BF295003E: No such file or directory
Nov  1 23:53:03 monkey postfix/smtp[13438]: connect to mx4.hotmail.com[65.54.244.232]: Connection timed out (port 25)
```

---

### Post by ronald.higgins on 2007-11-01
Cool.

Ok, 

All the hosts that you are getting time-outs on( Connection timed out) .

Check and see if you can ping them from your mailserver, and then secondly manually try to telnet: 

```


telnet mx4.hotmail.com 25


```

and you should get a response like below

```


Trying 65.54.244.232...
Connected to mx4.hotmail.com (65.54.244.232).
Escape character is '^]'.



```


If it fails to connect then IMO you're looking at a Firewall issues on the below points: 

A.) The Mailserver (local firewall software / iptables)
B)  Your Router
C) Your ISP

that is blocking outbound TCP/IP traffic on port 25.

IMO.

rH

---

### Post by MJN on 2007-11-01
[Edit: I'll bow out here as we're overlapping so I'll leave you in Ronald's capable hands!]
 
It looks like your outgoing port 25 is being blocked.
 
Try connecting manually to, say, my machine with **telnet mail.newtonnet.co.uk 25**
 
Mathew

---

### Post by Keef on 2007-11-01
Thanks a lot for your help, it does look like it's the only port blocked by my ISP, can either of you suggest a solution or work around for this?

Oh I tried changing the port to 125 in master.cf by changing this line, but the connection still times out:

```
smtp      inet  n       -       -       -       -       smtpd
```
to:
```
125      inet  n       -       -       -       -       smtpd
```

(I don't mind even if it's a temporary solution, all I'm using the server for is php coding and I need the php mail function with the account control panel I'm working on.)

---

### Post by MJN on 2007-11-01
(I know I said I'd go but I'm sat here with spare time on my hands!)
 
You need to make the distinction between incoming and outgoing port 25.
 
Incoming port 25 is used to accept from the Internet - we have not ascertained whether yours is blocked yet as without knowing your IP address or DNS name we can't do the required tests. There are *some* solutions involving 3rd party services which will accept mail on your behalf and redirect it to another port but its far from elegant.
 
Outoing port 25 is used to send mail out to the Internet and, from what we've send, it's looking like your ISP blocks this. The best solution for this is for you to relay outgoing mail via your ISPs mail server using the **relayhost = [isp.mail.server]** directive where isp.mail.server is the name of your ISP's mail server (funnily enough!). Note you must use the square brackets to ensure the correct DNS queries are made by Postfix. Try adding this directive and reloading/restarting Postfix.
 
Don't go changing any ports yet - we're not in a position to determine that this is the right course of action.
 
Mathew

---

### Post by ronald.higgins on 2007-11-01
Have a chat with your ISP, perhaps they have a SMTP server that they will allow you to relay via and you'll also get to confirm whether or not they are blocking the traffic outgoing.

rH

Perhaps MJN or another forumite can think of an alternative.

PS. Port 125 wont work unless the receiving MailServer is configured to listen on port 125 for incoming email. Suprised Postfix didnt  about that change when you restarted it.

[EDIT: lol ... back again MJN :) , cool, i'm heading off home soon so the more the merrier]

---

### Post by MJN on 2007-11-01
> **ronald.higgins said:**
> [EDIT: lol ... back again MJN :) , cool, i'm heading off home soon so the more the merrier]
 
Indeed - I'm sure between the three of us (and anyone that might care to chip in!) we'll get it sorted!

---

### Post by Keef on 2007-11-01
Thanks a lot! :)

I added the line MJN suggested to main.cf and now it works fine.

---

### Post by ronald.higgins on 2007-11-01
Awesome stuff!

Kudos to Keef & MJN!

Have a rocking evening gents :)

rH

---

### Post by MJN on 2007-11-01
It's just too friendly around here!
 
Must go and hunt down a Linux/Windows thread - that'll redress the balance! ;)
 
Have a good 'un,
 
Mathew

---

