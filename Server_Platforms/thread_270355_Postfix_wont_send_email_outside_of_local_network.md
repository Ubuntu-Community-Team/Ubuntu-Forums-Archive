---
title: "Postfix wont send email outside of local network"
date: 2006-10-03
forum: Server Platforms
---

### Post by murraymints on 2006-10-03
Hi,

For some reason I can only send emails to local email addresses using postfix as my smtp server.

I can successfully send emails to both local and internet addresses using the ISP smtp server but I would like emails from the internet and local addresses to be handled a little differently so I need postfix to work as a smpt server.

My mail server in on an internet connection using a non static-ip and downloads messages using fetchmail.

Here is the last few lines from my /var/log/mail.log

```

Oct  3 14:06:40 server postfix/smtp[18471]: connect to mail-r.hw.ac.uk[137.195.101.212]: Connection timed out (port 25)
Oct  3 14:06:44 server postfix/smtp[17523]: connect to mx3.hotmail.com[64.4.50.179]: Connection timed out (port 25)
Oct  3 14:07:09 server postfix/smtp[18470]: connect to mx1.hotmail.com[64.4.50.50]: Connection timed out (port 25)
Oct  3 14:07:10 server postfix/smtp[18471]: connect to mail-r.hw.ac.uk[137.195.101.219]: Connection timed out (port 25)
Oct  3 14:07:10 server postfix/smtp[18471]: AF45357D19A: to=<xxxx@hw.ac.uk>, relay=none, delay=2011, status=deferred (connect to mail-r.hw.ac.uk[137.195.101.219]: Connection timed out)
Oct  3 14:07:14 server postfix/smtp[17523]: connect to mx1.hotmail.com[65.54.244.8]: Connection timed out (port 25)
Oct  3 14:07:39 server postfix/smtp[18470]: connect to mx3.hotmail.com[65.54.245.72]: Connection timed out (port 25)
Oct  3 14:07:44 server postfix/smtp[17523]: connect to mx4.hotmail.com[65.54.244.232]: Connection timed out (port 25)
Oct  3 14:07:48 server courierpop3login: Connection, ip=[::ffff:192.168.0.2]
Oct  3 14:07:48 server courierpop3login: LOGIN, user=murray, ip=[::ffff:192.168.0.2]
Oct  3 14:07:48 server courierpop3login: LOGOUT, user=murray, ip=[::ffff:192.168.0.2], top=0, retr=0, time=0
Oct  3 14:08:06 server courierpop3login: Connection, ip=[::ffff:192.168.0.2]
Oct  3 14:08:06 server courierpop3login: LOGIN, user=dawa-sherpa, ip=[::ffff:192.168.0.2]
Oct  3 14:08:06 server courierpop3login: LOGOUT, user=dawa-sherpa, ip=[::ffff:192.168.0.2], top=0, retr=0, time=0
Oct  3 14:08:09 server postfix/smtp[18470]: connect to mx1.hotmail.com[65.54.245.8]: Connection timed out (port 25)
Oct  3 14:08:14 server postfix/smtp[17523]: connect to mx3.hotmail.com[65.54.244.72]: Connection timed out (port 25)
Oct  3 14:08:39 server postfix/smtp[18470]: connect to mx2.hotmail.com[65.54.245.40]: Connection timed out (port 25)
Oct  3 14:08:44 server postfix/smtp[17523]: connect to mx2.hotmail.com[65.54.244.40]: Connection timed out (port 25)
Oct  3 14:09:09 server postfix/smtp[18470]: connect to mx3.hotmail.com[65.54.244.200]: Connection timed out (port 25)
Oct  3 14:09:14 server postfix/smtp[17523]: connect to mx3.hotmail.com[65.54.244.200]: Connection timed out (port 25)
Oct  3 14:09:39 server postfix/smtp[18470]: connect to mx4.hotmail.com[65.54.245.104]: Connection timed out (port 25)
Oct  3 14:09:44 server postfix/smtp[17523]: connect to mx2.hotmail.com[65.54.190.50]: Connection timed out (port 25)
Oct  3 14:10:09 server postfix/smtp[18470]: connect to mx4.hotmail.com[65.54.244.232]: Connection timed out (port 25)
Oct  3 14:10:14 server postfix/smtp[17523]: connect to mx3.hotmail.com[65.54.245.72]: Connection timed out (port 25)
Oct  3 14:10:39 server postfix/smtp[18470]: connect to mx2.hotmail.com[65.54.190.50]: Connection timed out (port 25)
Oct  3 14:10:44 server postfix/smtp[17523]: connect to mx2.hotmail.com[65.54.244.168]: Connection timed out (port 25)
Oct  3 14:10:44 server postfix/smtp[17523]: CA87657D19B: to=<xxxxxxxxxxxxxx@hotmail.com>, relay=none, delay=519, status=deferred (connect to mx2.hotmail.com[65.54.244.168]: Connection timed out)
Oct  3 14:11:09 server postfix/smtp[18470]: connect to mx2.hotmail.com[65.54.244.40]: Connection timed out (port 25)
Oct  3 14:11:39 server postfix/smtp[18470]: connect to mx3.hotmail.com[65.54.244.72]: Connection timed out (port 25)
Oct  3 14:12:09 server postfix/smtp[18470]: connect to mx4.hotmail.com[65.54.244.104]: Connection timed out (port 25)
Oct  3 14:12:39 server postfix/smtp[18470]: connect to mx2.hotmail.com[65.54.244.168]: Connection timed out (port 25)
Oct  3 14:13:09 server postfix/smtp[18470]: connect to mx4.hotmail.com[65.54.190.179]: Connection timed out (port 25)
Oct  3 14:13:09 server postfix/smtp[18470]: A64F257D198: to=<xxxxxxxxxxxxxx@hotmail.com>, relay=none, delay=2886, status=deferred (connect to mx4.hotmail.com[65.54.190.179]: Connection timed out)
Oct  3 14:06:40 server postfix/smtp[18471]: connect to mail-r.hw.ac.uk[137.195.101.212]: Connection timed out (port 25)
Oct  3 14:06:44 server postfix/smtp[17523]: connect to mx3.hotmail.com[64.4.50.179]: Connection timed out (port 25)
Oct  3 14:07:09 server postfix/smtp[18470]: connect to mx1.hotmail.com[64.4.50.50]: Connection timed out (port 25)
Oct  3 14:07:10 server postfix/smtp[18471]: connect to mail-r.hw.ac.uk[137.195.101.219]: Connection timed out (port 25)
Oct  3 14:07:10 server postfix/smtp[18471]: AF45357D19A: to=<xxxx@hw.ac.uk>, relay=none, delay=2011, status=deferred (connect to mail-r.hw.ac.uk[137.195.101.219]: Connection timed out)
Oct  3 14:07:14 server postfix/smtp[17523]: connect to mx1.hotmail.com[65.54.244.8]: Connection timed out (port 25)
Oct  3 14:07:39 server postfix/smtp[18470]: connect to mx3.hotmail.com[65.54.245.72]: Connection timed out (port 25)
Oct  3 14:07:44 server postfix/smtp[17523]: connect to mx4.hotmail.com[65.54.244.232]: Connection timed out (port 25)
Oct  3 14:07:48 server courierpop3login: Connection, ip=[::ffff:192.168.0.2]
Oct  3 14:07:48 server courierpop3login: LOGIN, user=murray, ip=[::ffff:192.168.0.2]
Oct  3 14:07:48 server courierpop3login: LOGOUT, user=murray, ip=[::ffff:192.168.0.2], top=0, retr=0, time=0
Oct  3 14:08:06 server courierpop3login: Connection, ip=[::ffff:192.168.0.2]
Oct  3 14:08:06 server courierpop3login: LOGIN, user=dawa-sherpa, ip=[::ffff:192.168.0.2]
Oct  3 14:08:06 server courierpop3login: LOGOUT, user=dawa-sherpa, ip=[::ffff:192.168.0.2], top=0, retr=0, time=0
Oct  3 14:08:09 server postfix/smtp[18470]: connect to mx1.hotmail.com[65.54.245.8]: Connection timed out (port 25)
Oct  3 14:08:14 server postfix/smtp[17523]: connect to mx3.hotmail.com[65.54.244.72]: Connection timed out (port 25)
Oct  3 14:08:39 server postfix/smtp[18470]: connect to mx2.hotmail.com[65.54.245.40]: Connection timed out (port 25)
Oct  3 14:08:44 server postfix/smtp[17523]: connect to mx2.hotmail.com[65.54.244.40]: Connection timed out (port 25)
Oct  3 14:09:09 server postfix/smtp[18470]: connect to mx3.hotmail.com[65.54.244.200]: Connection timed out (port 25)
Oct  3 14:09:14 server postfix/smtp[17523]: connect to mx3.hotmail.com[65.54.244.200]: Connection timed out (port 25)
Oct  3 14:09:39 server postfix/smtp[18470]: connect to mx4.hotmail.com[65.54.245.104]: Connection timed out (port 25)
Oct  3 14:09:44 server postfix/smtp[17523]: connect to mx2.hotmail.com[65.54.190.50]: Connection timed out (port 25)
Oct  3 14:10:09 server postfix/smtp[18470]: connect to mx4.hotmail.com[65.54.244.232]: Connection timed out (port 25)
Oct  3 14:10:14 server postfix/smtp[17523]: connect to mx3.hotmail.com[65.54.245.72]: Connection timed out (port 25)
Oct  3 14:10:39 server postfix/smtp[18470]: connect to mx2.hotmail.com[65.54.190.50]: Connection timed out (port 25)
Oct  3 14:10:44 server postfix/smtp[17523]: connect to mx2.hotmail.com[65.54.244.168]: Connection timed out (port 25)
Oct  3 14:10:44 server postfix/smtp[17523]: CA87657D19B: to=<xxxxxxxxxxxxxx@hotmail.com>, relay=none, delay=519, status=deferred (connect to mx2.hotmail.com[65.54.244.168]: Connection timed out)
Oct  3 14:11:09 server postfix/smtp[18470]: connect to mx2.hotmail.com[65.54.244.40]: Connection timed out (port 25)
Oct  3 14:11:39 server postfix/smtp[18470]: connect to mx3.hotmail.com[65.54.244.72]: Connection timed out (port 25)
Oct  3 14:12:09 server postfix/smtp[18470]: connect to mx4.hotmail.com[65.54.244.104]: Connection timed out (port 25)
Oct  3 14:12:39 server postfix/smtp[18470]: connect to mx2.hotmail.com[65.54.244.168]: Connection timed out (port 25)
Oct  3 14:13:09 server postfix/smtp[18470]: connect to mx4.hotmail.com[65.54.190.179]: Connection timed out (port 25)
Oct  3 14:13:09 server postfix/smtp[18470]: A64F257D198: to=<xxxxxxxxxxxxxx@hotmail.com>, relay=none, delay=2886, status=deferred (connect to mx4.hotmail.com[65.54.190.179]: Connection timed out)

```

Anyone have any ideas whats wrong?

Any help greatly appreciated,

Murray

---

### Post by sonic2000gr on 2006-10-03
Maybe if you could post the contents of your /etc/postfix/main.cf file we could work something out.
In any case you may wish to consider reading [this excellent tutorial]("http://www.howtoforge.com/perfect_setup_debian_sarge_p4") on postfix (it is based on debian, but the difference is minute), my postfix server works perfectly thanks to it.

---

### Post by murraymints on 2006-10-03
I followed a how-tu very similar to the one linked in the post above and I've got most things working. Just sending to outside internet address is the only thing not working.

Here's my /etc/postfix/main.cf

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

myhostname = server.example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost.localdomain, localhost, mydomain.com
relayhost = 
mynetworks = 127.0.0.0/8, 192.168.0.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mailbox_command = 
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/

```

---

### Post by sonic2000gr on 2006-10-03
Your main.cf looks correct, in fact looks almost exactly like mine.
There is only one more thing that comes to mind: The mail server is known to the outside world by the name specified in 

/etc/mailname

Now, this name should actually be resolvable from the outside world (it must exist beyond your local network).

For example my mail server is named diktia.dyndns.org and I have an account in dyndns.org (it is free) so that diktia.dyndns.org points to my ip.
If you are trying to send an email and your server identifies as e.g. mailserver.yourdomain.com and this does not exist, then good chances are the mail servers you talk to will not accept your connection.

---

### Post by murraymints on 2006-10-03
ok,

i've applied for mydomain.dyndns.org with wildcard enabled (ie. *.mydomain.dyndns.org allowed) but did specify a mail exchanger or enable backup MX. I then and enabled port-forwarding on port 25 on my router and set /etc/mailname to mydomain.dyndns.org.

but I'm still having problems, in my /var/log/mail.log I get:

```

Oct  3 17:58:29 server postfix/qmgr[6691]: A64F257D198: from=<murray@mydomain.com>, size=572, nrcpt=1 (queue active)
Oct  3 17:58:29 server postfix/qmgr[6691]: 3BD8957D19C: from=<murray@mydomain.com>, size=556, nrcpt=1 (queue active)
Oct  3 17:58:59 server postfix/smtp[15678]: connect to mx3.hotmail.com[65.54.244.72]: Connection timed out (port 25)
Oct  3 17:58:59 server postfix/smtp[15679]: connect to mx1.hotmail.com[65.54.244.8]: Connection timed out (port 25)
Oct  3 17:59:29 server postfix/smtp[15678]: connect to mx3.hotmail.com[65.54.245.72]: Connection timed out (port 25)
Oct  3 17:59:29 server postfix/smtp[15679]: connect to mx3.hotmail.com[65.54.244.200]: Connection timed out (port 25)
Oct  3 17:59:54 server postfix/smtpd[14809]: timeout after RCPT from unknown[202.166.220.218]
Oct  3 17:59:54 server postfix/smtpd[14809]: disconnect from unknown[202.166.220.218]
Oct  3 17:59:59 server postfix/smtp[15678]: connect to mx4.hotmail.com[65.54.190.179]: Connection timed out (port 25)
Oct  3 17:59:59 server postfix/smtp[15679]: connect to mx3.hotmail.com[65.54.245.72]: Connection timed out (port 25)
Oct  3 18:00:29 server postfix/smtp[15678]: connect to mx4.hotmail.com[65.54.244.104]: Connection timed out (port 25)
Oct  3 18:00:29 server postfix/smtp[15679]: connect to mx3.hotmail.com[65.54.244.72]: Connection timed out (port 25)
Oct  3 18:00:37 server courierpop3login: Connection, ip=[::ffff:192.168.0.2]
Oct  3 18:00:37 server courierpop3login: LOGIN, user=murray, ip=[::ffff:192.168.0.2]
Oct  3 18:00:37 server courierpop3login: LOGOUT, user=murray, ip=[::ffff:192.168.0.2], top=0, retr=0, time=0
Oct  3 18:00:59 server postfix/smtp[15678]: connect to mx2.hotmail.com[65.54.244.168]: Connection timed out (port 25)
Oct  3 18:00:59 server postfix/smtp[15679]: connect to mx4.hotmail.com[65.54.190.179]: Connection timed out (port 25)
Oct  3 18:01:29 server postfix/smtp[15678]: connect to mx2.hotmail.com[65.54.244.40]: Connection timed out (port 25)
Oct  3 18:01:29 server postfix/smtp[15679]: connect to mx4.hotmail.com[65.54.244.104]: Connection timed out (port 25)
Oct  3 18:01:54 server postfix/anvil[14408]: statistics: max connection rate 1/60s for (smtp:xxx.xxx.xxx.xxx) at Oct  3 17:51:54
Oct  3 18:01:54 server postfix/anvil[14408]: statistics: max connection count 1 for (smtp:xxx.xxx.xxx.xxx) at Oct  3 17:51:54
Oct  3 18:01:54 server postfix/anvil[14408]: statistics: max cache size 1 at Oct  3 17:51:54
Oct  3 18:01:59 server postfix/smtp[15678]: connect to mx4.hotmail.com[65.54.244.232]: Connection timed out (port 25)
Oct  3 18:01:59 server postfix/smtp[15679]: connect to mx4.hotmail.com[65.54.244.232]: Connection timed out (port 25)
Oct  3 18:02:29 server postfix/smtp[15678]: connect to mx2.hotmail.com[65.54.245.40]: Connection timed out (port 25)
Oct  3 18:02:29 server postfix/smtp[15679]: connect to mx2.hotmail.com[65.54.244.168]: Connection timed out (port 25)
Oct  3 18:02:59 server postfix/smtp[15678]: connect to mx3.hotmail.com[65.54.244.200]: Connection timed out (port 25)
Oct  3 18:02:59 server postfix/smtp[15679]: connect to mx2.hotmail.com[65.54.245.40]: Connection timed out (port 25)
Oct  3 18:03:29 server postfix/smtp[15678]: connect to mx2.hotmail.com[65.54.190.50]: Connection timed out (port 25)
Oct  3 18:03:29 server postfix/smtp[15679]: connect to mx1.hotmail.com[64.4.50.50]: Connection timed out (port 25)
Oct  3 18:03:59 server postfix/smtp[15678]: connect to mx1.hotmail.com[64.4.50.50]: Connection timed out (port 25)
Oct  3 18:03:59 server postfix/smtp[15679]: connect to mx4.hotmail.com[65.54.245.104]: Connection timed out (port 25)
Oct  3 18:04:29 server postfix/smtp[15678]: connect to mx4.hotmail.com[65.54.245.104]: Connection timed out (port 25)
Oct  3 18:04:29 server postfix/smtp[15679]: connect to mx1.hotmail.com[65.54.245.8]: Connection timed out (port 25)
Oct  3 18:04:59 server postfix/smtp[15678]: connect to mx1.hotmail.com[65.54.244.8]: Connection timed out (port 25)
Oct  3 18:04:59 server postfix/smtp[15679]: connect to mx3.hotmail.com[64.4.50.179]: Connection timed out (port 25)

```

and if I try sending mail through telnet I get:

```

root@server:/backup# telnet mydomain.dyndns.org smtp
Trying xxx.xxx.xxx.xxx...
Connected to mydomain.dyndns.org.
Escape character is '^]'.
220 server.example.com ESMTP Postfix (Ubuntu)
mail from: murray@mydomain.com
250 Ok
rcpt to: xxxxxxxxxxxxxx@hotmail.com
554 <xxxxxxxxxxxxxx@hotmail.com>: Relay access denied

```

is this anywhere close to working?
is there an easier alternative such as setting up postfix fix to forward all internet bound mail to ISP smtp server and send local mail through local smtp server?

---

### Post by sonic2000gr on 2006-10-03
```

root@server:/backup# telnet mydomain.dyndns.org smtp
Trying xxx.xxx.xxx.xxx...
Connected to mydomain.dyndns.org.
Escape character is '^]'.
220 server.example.com ESMTP Postfix (Ubuntu)
mail from: murray@mydomain.com
250 Ok
rcpt to: xxxxxxxxxxxxxx@hotmail.com
554 <xxxxxxxxxxxxxx@hotmail.com>: Relay access denied

```

Look the at the problem here: You are trying to send mail from [email]murray@mydomain.com[/email] while your domain is mydomain.dyndns.org. You email name should be [email]murray@mydomain.dyndns.org[/email] (not [email]murray@dyndns.org[/email] either since you don't own the dyndns.org domain, just the mydomain.dyndns.org). The server is right to reject this one. 

> is this anywhere close to working?
is there an easier alternative such as setting up postfix fix to forward all internet bound mail to ISP smtp server and send local mail through local smtp server?

It is possible to setup postfix for forwarding, I haven't done that, but you will find a guide for it somewhere. It is much better to run your own server though.

---

### Post by zitch on 2006-10-03
Actually, I think the real problem is that your ISP is blocking outbound port 25 connections.

Do the following from a command line:

```

telnet mx2.hotmail.com 25
telnet mx4.hotmail.com 25

```

Post your results from these.  This is what I get:

```

$ telnet mx2.hotmail.com 25
Trying 65.54.245.40...
Connected to mx2.hotmail.com.
Escape character is '^]'.
220 bay0-mc10-f7.bay0.hotmail.com Sending unsolicited commercial or bulk e-mail to Microsoft's computer network is prohibited. Other restrictions are found at http://privacy.msn.com/Anti-spam/. Violations will result in use of equipment located in California and other states. Tue, 3 Oct 2006 09:46:41 -0700

$ telnet mx4.hotmail.com 25
Trying 65.54.244.232...
Connected to mx4.hotmail.com.
Escape character is '^]'.
220 bay0-mc8-f18.bay0.hotmail.com Sending unsolicited commercial or bulk e-mail to Microsoft's computer network is prohibited. Other restrictions are found at http://privacy.msn.com/Anti-spam/. Violations will result in use of equipment located in California and other states. Tue, 3 Oct 2006 09:46:09 -0700

```
Keep in mind that these took a while.  You can also try other service's mail servers too:

```

smtp1.google.com
smtp2.google.com
smtp3.google.com
smtp4.google.com
mx1.mail.yahoo.com
mx2.mail.yahoo.com
mx3.mail.yahoo.com

```

---

### Post by murraymints on 2006-10-04
looks like your right zitch:

```

murray@server:~$ telnet mx2.hotmail.com 25
Trying 65.54.245.40...
Trying 65.54.190.50...
Trying 65.54.244.40...
Trying 65.54.244.168...
telnet: Unable to connect to remote host: Connection timed out

murray@server:~$ smtp1.google.com smtp
bash: smtp1.google.com: command not found
murray@server:~$ telnet smtp1.google.com smtp
Trying 216.239.57.25...
telnet: Unable to connect to remote host: Connection timed out

murray@server:~$ telnet mx1.mail.yahoo.com smtp
Trying 4.79.181.14...
Trying 4.79.181.15...
Trying 4.79.181.168...
Trying 67.28.113.73...
Trying 67.28.113.19...
Trying 67.28.113.71...
telnet: Unable to connect to remote host: Connection timed out

murray@server:~$ telnet mx4.hotmail.com smtp
Trying 65.54.244.232...
Trying 65.54.245.104...
Trying 65.54.190.179...
Trying 65.54.244.104...
telnet: Unable to connect to remote host: Connection timed out

murray@server:~$ telnet smtp3.google.com smtp
Trying 64.233.183.25...
telnet: Unable to connect to remote host: Connection timed out

```

but i'm trying the email forwaring idea, the first example in man transport looked particulary hopefull, saying that the follwoing would deliver local mail directly while sending other mail through a mail relay (sounds like exactly what I want) only it doesn'nt work.

my /etc/postfix/transport looks like 

```

mydomain.com      :
.mydomain.com     :
*               smtp:smtp.wlink.com.np

```

any ideas what wrong with this? (I'm remebering to run "sudo postmap /etc/postfix/transport" after editing the file)

EDit: almost solved :???: 

I visited this page: [http://www.ussg.iu.edu/index75cd.html?option=articles&task=viewarticle&artid=26&Itemid=3](http://www.ussg.iu.edu/index75cd.html?option=articles&task=viewarticle&artid=26&Itemid=3)

I found that i need to run this line:
# postmap hash:/etc/postfix/transport

add this line to my /etc/postfix/main.cf:
transport_maps = hash:/etc/postfix/transport

and then run this line:
 # postfix reload
and it now send local mai locally and internet mail through the isp server.

But I've just noticed another problem, if I try to reply to an internet sent email it fails with te error message "murray@localhost: 511 no such email address here" obviously I need to edit my postfix conf so that any replies goto [email]murray@mydomain.com[/email] not murray@localhost.

how do I do this?

---

### Post by murraymints on 2006-10-04
Hi, I've edited my last comment a few times as I thought I fixed everything but had'nt. Just incase its confusing at all I want to know how to change emails that are sent to internet addresses through my ISP server from trying to return to murray@localhost to trying to return to [email]murray@mydomain.com[/email].

Thanks in advance for any help (the various tips I've had so far have been great),

Murray

---

### Post by murraymints on 2006-10-05
ok its all working now :D

I added this to my /var/postfix/main.cf
masquerade_domains = asian-trekking.com

and also added to the top of my /etc/postfix/transport:
localhost            :

perhap someone should update the transport manual to include that in ti's example :D

---

