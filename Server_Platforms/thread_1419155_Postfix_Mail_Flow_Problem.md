---
title: "Postfix Mail Flow Problem"
date: 2010-03-01
forum: Server Platforms
---

### Post by ScatterBrain on 2010-03-01
I've got several Ubuntu 8.04 servers inside my LAN doing various things - but they all share two things in common: 1). They use postfix to handle e-mail and 2). They all run logwatch.
 
Over the past couple of weeks I've been replacing an Exchange 2003 server with an Exchange 2007 server. This process is complete and the Exchange 07 machine is doing everything for us now. (No stabs please, I have no choice.)
 
Cyan = Exchange 03 Server
Shale = Exchange 07 Server
Black = Ubuntu 8.04 Server
 
I've only got one minor problem - the Ubuntu boxes inside my LAN are still trying to pass e-mail to the old mail server. Here is a copy of the "postqueue -p" command on one of the servers:
 
```
root@black:~# postqueue -p
-Queue ID- --Size-- ----Arrival Time---- -Sender/Recipient-------
04A1B14F61A      328 Mon Mar  1 14:10:05  root@black.nei-ky.com
                (connect to cyan.nei.local[10.200.8.205]:25: No route to host)
                                         kcollins@nei-ky.com
 
-- 0 Kbytes in 1 Request.

```
 
Obviously, if I turn the Cyan back on, the mail goes through without problem.
 
Here are the kickers:
 
1). None of these machines are configured to "relay" mail to Cyan (the Exchange 03 box).
 
[COLOR=seagreen]/etc/postfix/main.cf:[/COLOR]
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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
 
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
 
myhostname = black.nei-ky.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = black.nei-ky.com, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

```
 
[COLOR=seagreen]/etc/postfix/master.cf is the default configuration as installed by "apt-get install postfix"[/COLOR]
 
2). The MX entry for Cyan was removed from DNS nearly 4 days ago.
3). "dig nei.local mx" only reports one mail server - the Exchange 07 machine.
 
```
root@black:~# dig nei.local mx
 
; <<>> DiG 9.3.2-P2.1 <<>> nei.local mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 34137
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1
 
;; QUESTION SECTION:
;nei.local.                     IN      MX
 
;; ANSWER SECTION:
nei.local.              3600    IN      MX      10 shale.nei.local.
 
;; ADDITIONAL SECTION:
shale.nei.local.        1200    IN      A       10.200.8.221
 
;; Query time: 8 msec
;; SERVER: 10.200.8.201#53(10.200.8.201)
;; WHEN: Mon Mar  1 14:17:25 2010
;; MSG SIZE  rcvd: 65

```
 
4). I've restarted networking and even restarted the Linux machines.
 
None of these things work. The only solution is turn Cyan back on. I can do that - but I need to remove Cyan soon. I know I can force the Linux boxes to relay through Shale by making a change in /etc/postfix/main.cf - I've tried that and it works. But I'd prefer to have the machines depend on DNS so that as the servers change in the future they can get updated.
 
Anyone have an idea as to how I might be able to fix this?
 
Any help is appreciated.

---

### Post by ScatterBrain on 2010-03-01
Just a bit more information...
 
I found this command in the Postfix Troubleshooting/Debugging Howto:
 
```
sendmail -bv <address>
```
 
And when I used it, I recieved an e-mail with these contents:
 
 
```
This is the mail system at host black.nei-ky.com.

Enclosed is the mail delivery report that you requested.

                   The mail system

<kcollins@nei-ky.com>: delivery via cyan.nei.local[10.200.8.205]:25: 250 2.1.5
    kcollins@nei-ky.com

```

```
Reporting-MTA: dns; black.nei-ky.com
X-Postfix-Queue-ID: 73A4414F61B
X-Postfix-Sender: rfc822; root@black.nei-ky.com
Arrival-Date: Mon,  1 Mar 2010 15:43:55 -0500 (EST)

Final-Recipient: rfc822; kcollins@nei-ky.com
Action: deliverable
Status: 2.1.5
Remote-MTA: dns; cyan.nei.local
Diagnostic-Code: smtp; 250 2.1.5 kcollins@nei-ky.com
```

I think the key line here is this:  [COLOR="Red"]**Remote-MTA: dns; cyan.nei.local**[/COLOR]

If I'm reading this correctly, this line says that DNS is still telling Postfix to deliver mail to Cyan.  In my mind this means that the Linux box is caching that DNS entry, because Cyan doesn't exist with an MX record anymore.

So how can I clear this cache?  Is it being cached by Postfix or by Ubuntu?  Why wouldn't the restart have cleared that cache?

HELP!!!!

---

### Post by ScatterBrain on 2010-03-05
OK, for the record, my forum handle is ScatterBrain for a reason.  Looking back at the issue I can see how much of an idiot I am.  But just so no one else makes the same mistake that I did here's the problem and the solution:
 
**Problem:** Postfix on several Ubuntu machines kept trying to send e-mail bound for "nei-ky.com" to a sever called "cyan.nei.local" - an Exchange 2003 server that I had recently replaced and removed.
 
**Solution**:  While I thought I had correctly set the MX records so that e-mail should flow through the new Exchange 2007 machine, I had forgotten that I used **[COLOR=red]an internal split-brain DNS server[/COLOR]**.  This server hosted the zones for both "nei.local" and "nei-ky.com".  I had corrected the MX record for "nei.local" but had not corrected the MX record for "nei-ky.com".  Hence when Postfix did a DNS call for the MX record on "nei-ky.com" it was told the wrong server...and there in lies my problem.
 
I corrected the MX record in the other DNS zone and all is well now.

---

