---
title: "virtual-users-and-domains-with-postfix-ubuntu-7.10"
date: 2007-12-03
forum: Server Platforms
---

### Post by jmazaredo on 2007-12-03
Hello I used this guide [http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10)
to setup a mail server. It somewhat working.
I can use the mail server using squirrelmail weblogin. Can send and receive via web. Also I can send and receive if i use the server as the medium.

The problem is i can **only** get mail **not send** via email clients outside the network. (accessing via internet)

When I look at the /etc/var/log/mail.log i see the client LOGIN and LOG OFF, but no error of any sort.

I followed the guide step by step i know it is working since i can send/receive via web interface.

Also I have no active firewall of any sort on the server and i use a router that port forwards port 110 25 80 143


anyone have encountered this matter?

---

### Post by jmazaredo on 2007-12-04
my logs

```

Dec  4 16:45:03 mail courierpop3login: Connection, ip=[::ffff:xxx.xxx.xxx.xxx]
Dec  4 16:45:06 mail courierpop3login: LOGIN, user=jeff@mail.domain.com.xx, ip=[::ffff:xxx.xxx.xxx.xxx]
Dec  4 16:45:11 mail courierpop3login: LOGOUT, user=jeff@mail.domain.com.xx, ip=[::ffff:xxx.xxx.xxx.xxx], top=0, retr=0, rcvd=24, sent=96, time=5
Dec  4 16:45:29 mail courierpop3login: Connection, ip=[::ffff:xxx.xxx.xxx.xxx]
Dec  4 16:45:33 mail courierpop3login: LOGIN, user=jeff@mail.domain.com.xx, ip=[::ffff:xxx.xxx.xxx.xxx]
Dec  4 16:45:36 mail courierpop3login: LOGOUT, user=jeff@mail.domain.com.xx, ip=[::ffff:xxx.xxx.xxx.xxx], top=0, retr=0, rcvd=24, sent=96, time=3
Dec  4 16:46:02 mail courierpop3login: Connection, ip=[::ffff:xxx.xxx.xxx.xxx]
Dec  4 16:46:05 mail courierpop3login: LOGIN, user=jeff@mail.domain.com.xx, ip=[::ffff:xxx.xxx.xxx.xxx]
Dec  4 16:46:08 mail courierpop3login: LOGOUT, user=jeff@mail.domain.com.xx, ip=[::ffff:xxx.xxx.xxx.xxx], top=0, retr=0, rcvd=24, sent=96, time=3
Dec  4 16:47:26 mail courierpop3login: Connection, ip=[::ffff:xxx.xxx.xxx.xxx]
Dec  4 16:47:28 mail courierpop3login: LOGOUT, ip=[::ffff:xxx.xxx.xxx.xxx]
Dec  4 16:47:28 mail courierpop3login: Disconnected, ip=[::ffff:xxx.xxx.xxx.xxx]


```

---

### Post by MJN on 2007-12-04
Is Postfix running?
 
Those log entries are your IMAP/POP logging entries - the mail.log should also contain Postfix log entries.
 
Post your /etc/postfix/main.cf file, and your Squirrelmail config.php file too (the latter will be useful as you it is working so we can verify what it is using as its mail server).
 
Mathew

---

### Post by jmazaredo on 2007-12-04
output when i try to get and send mail using thunderbird just plain login and logout

```
login as: root
root@mail.some.com.no's password:
Last login: Wed Dec  5 02:40:18 2007 from 111.111.111.111
Linux mail 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
root@mail:~# tail -f /var/log/mail.log
Dec  5 02:47:18 mail courierpop3login: LOGIN, user=jeff@mail.some.com.no, ip=[::ffff:111.111.111.111]
Dec  5 02:47:18 mail courierpop3login: LOGOUT, user=jeff@mail.some.com.no, ip=[::ffff:111.111.111.111], top=0, retr=0, rcvd=12, sent=39, time=0
Dec  5 02:48:16 mail courierpop3login: Connection, ip=[::ffff:64.233.182.191]
Dec  5 02:48:16 mail courierpop3login: Disconnected, ip=[::ffff:64.233.182.191]
Dec  5 02:48:16 mail courierpop3login: Connection, ip=[::ffff:64.233.182.191]
Dec  5 02:48:16 mail courierpop3login: LOGIN FAILED, user=sabrina, ip=[::ffff:64.233.182.191]
Dec  5 02:48:22 mail courierpop3login: Disconnected, ip=[::ffff:64.233.182.191]
Dec  5 02:50:42 mail courierpop3login: Connection, ip=[::ffff:xxx.xxx.xxx.xx]
Dec  5 02:50:42 mail courierpop3login: LOGIN, user=jmazaredo@mail.some.com.no, ip=[::ffff:xxx.xxx.xxx.xx]
Dec  5 02:50:42 mail courierpop3login: LOGOUT, user=jmazaredo@mail.some.com.no, ip=[::ffff:xxx.xxx.xxx.xx], top=0, retr=0, rcvd=12, sent=39, time=0
Dec  5 02:53:19 mail courierpop3login: Connection, ip=[::ffff:111.111.111.111]
Dec  5 02:53:20 mail courierpop3login: LOGIN, user=jeff@mail.some.com.no, ip=[::ffff:111.111.111.111]
Dec  5 02:53:21 mail courierpop3login: LOGOUT, user=jeff@mail.some.com.no, ip=[::ffff:111.111.111.111], top=0, retr=0, rcvd=12, sent=39, time=1
```

(sabrina is not me someone trying to login :lolflag: t)


main.cf 

```

root@mail:~# vi /etc/postfix/main.cf
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

myhostname = mail.somewhere.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.somewhere.com, localhost, localhost.localdomain
relayhost =
mynetworks = 127.0.0.0/8
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
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
~
```


mail.err log 

```
root@mail:/var/log# tail mail.err
Dec  4 17:24:19 mail amavis[11805]: (11805-01) (!!) TROUBLE in process_request: Error writing a SMTP response to the socket: Broken pipe at (eval 51) line 788, <GEN25> line 27.
root@mail:/var/log# tail mail.err -f
Dec  4 17:24:19 mail amavis[11805]: (11805-01) (!!) TROUBLE in process_request: Error writing a SMTP response to the socket: Broken pipe at (eval 51) line 788, <GEN25> line 27.

```


Log when i use Squirrelmail and it is working just fine

```

Dec  5 03:11:14 mail postfix/qmgr[13252]: 7F63326819C: from=<jmazaredo@mail.some.com.no>, size=1235, nrcpt=1 (queue active)
Dec  5 03:11:14 mail postfix/smtpd[13353]: disconnect from localhost[127.0.0.1]
Dec  5 03:11:14 mail amavis[13159]: (13159-01) Passed CLEAN, LOCAL [127.0.0.1] [xxx.xxx.xxx.xxx] <jmazaredo@mail.some.com.no> -> <jeff@mail.some.com.no>, Message-ID: <1963.xxx.xxx.xxx.xxx.1196795469.squirrel@mail.some.com.no>, mail_id: KBqVyKxfRX3B, Hits: 1.459, queued_as: 7F63326819C, 4859 ms
Dec  5 03:11:14 mail postfix/smtp[13346]: A1C1C26811B: to=<jeff@mail.some.com.no>, relay=127.0.0.1[127.0.0.1]:10024, delay=4.9, delays=0.06/0.01/0.01/4.9, dsn=2.6.0, status=sent (250 2.6.0 Ok, id=13159-01, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 7F63326819C)
Dec  5 03:11:14 mail postfix/qmgr[13252]: A1C1C26811B: removed
Dec  5 03:11:14 mail postfix/virtual[13354]: 7F63326819C: to=<jeff@mail.some.com.no>, relay=virtual, delay=0.07, delays=0.05/0.01/0/0.01, dsn=2.0.0, status=sent (delivered to maildir)
Dec  5 03:11:14 mail postfix/qmgr[13252]: 7F63326819C: removed
```

I can send and receive via squirrel mail, i can receive via pop client but cant send via smtp. :confused: :confused: :confused:

---

### Post by jmazaredo on 2007-12-04
Also antivirus scanner is working since i get logs that i quarantine trojan also it shows in mail.log but its archive now

---

### Post by jmazaredo on 2007-12-04
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:10024         *:*                     LISTEN     13156/amavisd (mast
tcp        0      0 localhost:10025         *:*                     LISTEN     13247/master
tcp        0      0 localhost:mysql         *:*                     LISTEN     5119/mysqld
tcp        0      0 *:webmin                *:*                     LISTEN     6452/perl
tcp        0      0 *:www                   *:*                     LISTEN     6364/apache2
tcp        0      0 localhost:ipp           *:*                     LISTEN     5011/cupsd
tcp        0      0 *:smtp                  *:*                     LISTEN     13247/master
tcp6       0      0 *:imaps                 *:*                     LISTEN     5743/couriertcpd
tcp6       0      0 *:pop3s                 *:*                     LISTEN     5787/couriertcpd
tcp6       0      0 *:5900                  *:*                     LISTEN     7866/vino-server
tcp6       0      0 *:pop3                  *:*                     LISTEN     5759/couriertcpd
tcp6       0      0 *:imap2                 *:*                     LISTEN     5720/couriertcpd
tcp6       0      0 *:ssh                   *:*                     LISTEN     4757/sshd
tcp6       0     28 ::ffff:192.168.1.1:5900 ::ffff:xxx.xx.243.:1832 ESTABLISHED7866/vino-server
tcp6       0   2128 ::ffff:192.168.1.10:ssh ::ffff:xxx.xx.243.:1946 ESTABLISHED13279/3

```

i just followed the howto by [http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10)

---

### Post by MJN on 2007-12-04
Your telnet command should be **telnet localhost 25**

Also try from outside your network (using your public IP/name instead of localhost).

Mathew

---

### Post by jmazaredo on 2007-12-04
```
root@mail:~# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 mail.xxxxx ESMTP Postfix (Ubuntu)
ehlo localhost
250-mail.xxxxx.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
quit
221 2.0.0 Bye
Connection closed by foreign host.
root@mail:~#

```

```
root@mail:~# telnet localhost 110
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
+OK Hello there.
quit
+OK Better luck next time.
Connection closed by foreign host.
root@mail:~#

```

```
Dec  5 03:41:13 mail postfix/smtpd[6722]: connect from localhost[127.0.0.1]
Dec  5 03:41:26 mail postfix/smtpd[6722]: disconnect from localhost[127.0.0.1]
Dec  5 03:41:30 mail postfix/smtpd[6722]: connect from localhost[127.0.0.1]
Dec  5 03:41:35 mail postfix/smtpd[6722]: disconnect from localhost[127.0.0.1]
Dec  5 03:41:50 mail postfix/smtpd[6722]: connect from localhost[127.0.0.1]
Dec  5 03:42:01 mail postfix/smtpd[6722]: disconnect from localhost[127.0.0.1]
Dec  5 03:43:49 mail courierpop3login: Connection, ip=[::ffff:127.0.0.1]
Dec  5 03:43:53 mail courierpop3login: LOGOUT, ip=[::ffff:127.0.0.1]
Dec  5 03:43:53 mail courierpop3login: Disconnected, ip=[::ffff:127.0.0.1]

```

---

### Post by jmazaredo on 2007-12-04
```
421 Cannot connect to SMTP server 203.xxx.xxx.97 (203.xxx.xxx.97:25), connect
ror 10060


Connection to host lost.

C:\Documents and Settings\jmazaredo>
```

```
+OK Hello there.
quit
+OK Better luck next time.


C:\Documents and Settings\jmazaredo>
```

using telnet outside

i have no firewall
i m using a router i have port forwarded smtp,imap,http,ssh, and all services i can think i can use

---

### Post by MJN on 2007-12-04
I think you've found your problem - you can't connect to port 25 from the outside.

But you say you are receiving e-mail okay? As in receiving from other people on the Internet? That requires port 25 to be open (and working!) so if you can clarify...

Mathew

P.S. Hiding your domain name really doesn't help sorting this problem out - it stops any form of diagnosis from this end hence why all the questions!

---

### Post by jmazaredo on 2007-12-04
yes port 25 is open i can send and receive mail via web using squirrel. but sending mail via a client like thunderbird and outlook cant

---

### Post by MJN on 2007-12-04
No, Squirrelmail is presumably hosted on the same server as Postfix hence it is accessing port 25 locally.

You're going to have to post your domain/IP (PM me if you prefer) otherwise we're not going to get anywhere fast diagnosing this one!

Alternatively, post the **full** output of a telnet session to port 25 from the Internet so we can see exactly what is failing (if anything). What you've posted looks more like an Outlook error transcript.

Mathew

---

### Post by jmazaredo on 2007-12-05
i think my isp is blocking port 25............ il try to check again

---

### Post by MJN on 2007-12-05
If you tell us your IP we can tell you! Why hide it?

Mathew

---

### Post by jmazaredo on 2007-12-07
sent message to you mjn

---

### Post by MJN on 2007-12-08
Got the message - much easier now!

As you've probably spottted I managed to successfully connect okay and deliver you a message. Furthermore, I tried to use your server to relay offsite and it failed (as it should do) so no worries there.

So, I'm not sure why you're not having any joy... How exactly are you testing this? Is your client on the same machine (server)? Or same LAN? Or out on the Internet (via another connection)?

Mathew

P.S. In your PM you touched on the reasons for hiding your IP, and it is indeed a very common practice to do by many, however it should be highlighted that keeping it secret is no really defence against the 'bad guys' as they tend to run bots that pick IP's at random, or sequentially within netblocks, and so even if you never told a sole what your address was these bots will still find you. Hence, you need to be secure either way - indeed if you assume your address is well known and start your security from that premise then you won't go far wrong.

---

