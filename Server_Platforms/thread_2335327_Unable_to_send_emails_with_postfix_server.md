---
title: "Unable to send emails with postfix server"
date: 2016-08-27
forum: Server Platforms
---

### Post by ferguson.stewart on 2016-08-27
I am running a new install of Ubuntu server 16.04.1 LTS with nothing installed except a postfix/dovecot mail server.  I installed it via this guide:
[https://help.ubuntu.com/lts/serverguide/postfix.html](https://help.ubuntu.com/lts/serverguide/postfix.html)

I can receive mail (Only IMAP in thunderbird tested) but I cannot send mail.  I think I am having trouble establishing an SMTP connection between client and server.  Can someone offer troubleshooting advice so that I can send mail with my mail server?

I have not found any errors in logs on the server side.  However the following is the output from Thunderbird as it tries to send mail: 
```
Sending of the message failed. 
The message could not be sent because connecting to the Outgoing Server (SMTP) mail.example.com failed.  The server may be unavailable or is refusing SMTP connections.  Please verify that your Outgoing server (SMTP) settings are correct and try again.
```

Client (thunderbird) settings:
```
Incomming Server Settings
  Server Type: IMAP Mail Server
  Server Name: mail.example.com  (mail.example.com resolves to the appropriate machine on the LAN using /etc/hosts).
  Server Port: 993
  User Name: stew
  Connection security: SSL/TLS
  Authentication Method: Normal Password
Outgoing Server (SMTP Settings): 
  Server name: mail.example.com
  Server Port: 465
  Connection security: SSL/TLS (Also tried STARTTLS)
  Authentication method: Normal password
  User Name: stew

```

Server settings: 
```
stew@mail:~$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot.conf -m "${EXTENSION}"
mailbox_size_limit = 0
mydestination = $myhostname, mail.example.com, localhost.example.com, , localhost, example.com
myhostname = mail.example.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.0/24
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_relay_domains
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = reject_unknown_sender_domain
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/dovecot/dovecot.pem
smtpd_tls_key_file = /etc/dovecot/private/dovecot.pem
smtpd_tls_loglevel = 1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
```

Sever logs:
```
stew@mail:~$ telnet mail.example.com 25
Trying 127.0.1.1...
Connected to mail.example.com.
Escape character is '^]'.
220 mail.example.com ESMTP Postfix (Ubuntu)
ehlo mail.example.com
250-mail.example.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

stew@mail:~$ tail -f /var/log/mail.err
Aug 24 10:15:02 mail postfix/smtpd[2398]: fatal: no SASL authentication mechanisms
Aug 25 01:04:34 mail dovecot: imap-login: Error: Timeout waiting for handshake from auth server. my pid=2654, input bytes=0
Aug 25 01:04:34 mail dovecot: imap-login: Error: Timeout waiting for handshake from auth server. my pid=2655, input bytes=0
Aug 25 20:53:35 mail dovecot: imap-login: Error: Timeout waiting for handshake from auth server. my pid=2307, input bytes=0
Aug 27 22:08:04 mail dovecot: imap-login: Error: Timeout waiting for handshake from auth server. my pid=2327, input bytes=0

stew@mail:~$ tail -f /var/log/mail.log
Aug 27 23:08:25 mail postfix/smtp[2656]: 496D1C11E8: to=<example@gmail.com>, relay=none, delay=1471, delays=1381/0.02/90/0, dsn=4.4.1, status=deferred (connect to alt2.gmail-smtp-in.l.google.com[74.125.23.27]:25: Connection timed out)
Aug 27 23:16:03 mail postfix/pickup[2325]: 1453EC11EE: uid=1000 from=<stew@mail.example.com>
Aug 27 23:16:03 mail postfix/cleanup[2663]: 1453EC11EE: message-id=<20160827211603.1453EC11EE@mail.example.com>
Aug 27 23:16:03 mail postfix/qmgr[2326]: 1453EC11EE: from=<stew@mail.example.com>, size=361, nrcpt=1 (queue active)
Aug 27 23:16:33 mail postfix/smtp[2665]: connect to gmail-smtp-in.l.google.com[74.125.136.27]:25: Connection timed out
Aug 27 23:16:33 mail postfix/smtp[2665]: connect to gmail-smtp-in.l.google.com[2a00:1450:4013:c01::1b]:25: Network is unreachable
Aug 27 23:17:03 mail postfix/smtp[2665]: connect to alt1.gmail-smtp-in.l.google.com[74.125.200.27]:25: Connection timed out
Aug 27 23:17:03 mail postfix/smtp[2665]: connect to alt1.gmail-smtp-in.l.google.com[2404:6800:4003:c00::1a]:25: Network is unreachable
Aug 27 23:17:33 mail postfix/smtp[2665]: connect to alt2.gmail-smtp-in.l.google.com[74.125.23.27]:25: Connection timed out
Aug 27 23:17:33 mail postfix/smtp[2665]: 1453EC11EE: to=<example@gmail.com>, relay=none, delay=90, delays=0.13/0.02/90/0, dsn=4.4.1, status=deferred (connect to alt2.gmail-smtp-in.l.google.com[74.125.23.27]:25: Connection timed out)

```

Another interesting part is that the following commands on the server will help me to test the send functionality.  Sending mail works internally, but not externally here.  So I think I have a few issues.  The one I want to deal with in this thread is why I can't use thunderbird to send internal emails.  I'll get to the external troubleshooting later.
```
stew@mail:~$ echo "Test mail from postfix" | mail -s "Test Postfix" stew@example.com  <-- Arrives
stew@mail:~$ echo "Test mail from postfix" | mail -s "Test Postfix" admin@example.com <-- Arrives
stew@mail:~$ echo "Test mail from postfix" | mail -s "Test Postfix" example@gmail.com <-- Does not arrive
```

Network config: 
I have a domain (example.com) with A and MX records pointing to my modem.  The mail server is located behind that modem in a LAN with ports 143 (IMAP), 993 (IMAP secure), 110 (POP3), 995 (POP3 secure), 25 (SMTP), and 587 (SMTP secure) forwarded to the server.  I am testing from inside of the LAN so I don't expect the port forwarding to be an issue.

Could this perhaps be an ssl certificate error?  I've self-signed the certs, so perhaps I need to get a CA to sign it to get this working.

---

### Post by TheFu on 2016-08-27
* Not all ISPs allow direct SMTP email in and out. For outbound, they usually require a relay be configured.
* example.com isn't a valid domainname. You must configure the domain that you bought with a registrar and configured with MX records in DNS.
* If the public IP for the WAN connection is DHCP, almost nobody will accept email from your system. DHCP subnets are blocked by everyone. I block them too.

To help any more, real IPs, real ISPs, and real domains are needed. Sorry.

Testing locally is fun, but really need to test from an outside provider to verify that the ISP, router, and server each aren't blocking inbound SMTP, DNS is configured correctly and that the entire pipeline is working.

And when you think everything is working, be certain to test that you are not an open relay. That will get your IP banned in less than 24 hrs. Don't know of anyway to get off that list. Friends have conveyed horror stories about trying to get off a block list. Most usually give up and have to move their email to an external provider - at least as a gateway.

If you just want to send email to one external userid, like gmail, then there are smaller programs designed just for this, of course, postfix can be used for that too.

---

### Post by ferguson.stewart on 2016-08-28
* I'll check with my ISP about SMTP email out.  So far, SMTP-in is working great so that makes me think I'll be okay. 
* I have a valid domain name.  I just replaced that name with "example.com" everywhere in the post above for the purpose of the post.  I wasn't comfortable with putting the real domain out there as I'm sure I'm revealing security holes in my architecture.
* I still need to contact my ISP to get on a static block.  Glad to know that could be an issue.

Regarding being an open-relay, I'm not sure whether my configuration is open.  I assume that the following lines in my postconf describe that the relay is closed. Am I wrong?
```
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_relay_domains
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
```

I know that testing on a LAN is not enough, however with troubleshooting I need to take it one step at a time.  There are too many variables here to do end-to-end testing right away.  If I can get it working on the LAN, then I'm ready to take it a step further externally.  Right now, the biggest problem I'm trying to debug is getting Thunderbird (on another machine in the LAN) to establish an SMTP connection with postfix.  If I can get that working, then I'm one step closer to a full solution.

---

### Post by ferguson.stewart on 2016-08-28
Re: Blacklisting
Good news.  So far, I don't appear to be on any blacklists.  I'm not sure if that means I'm not in a residential/DHCP block, 
[http://mxtoolbox.com/blacklists.aspx](http://mxtoolbox.com/blacklists.aspx)

---

### Post by lisati on 2016-08-28
One thing to check is that if your domain is "example.com" and you've configured Thunderbird to send through "mail.example.com" you might need to configure your DNS records to include "mail.example.com" as a valid destination.

---

### Post by TheFu on 2016-08-28
Without the real domainname, we can't look at DNS records - those are usually where folks make mistakes. It isn't like the data isn't published.

There are multiple blacklists. I use about 5. Some are dynamic, to block active spammers.

There are online tests for open-relays. Sometimes the settings we think are being used, aren't or aren't understood (for some subtle reason).

BTW, I use an email gateway which is actively maintained with constant patches. It runs on a tiny VM.  My real email server is also maintained, but not directly available on the internet. All inbound/outbound emails go through the gateway which has DKIM and SPF capabilities. It drops about 90% of all inbound email attempts. You'd be amazed at the crap thrown at a mail server. Outbound, it helps me catch infected systems inside our network, since only this gateway is authorized by SFP to send emails from us.  Email is very risky and deserves the extra layer of security, IMHO.  Plus, it is a way to have a relatively tiny front-end box that can be moved anywhere without having to touch many settings on the real email boxes, which is more complicated.

Anyway - good luck.

---

### Post by SeijiSensei on 2016-08-28
Quick test.  Enter the command "telnet gmail-smtp-in.l.google.com 25" at a terminal prompt.  If you don't see this
```

Trying 74.125.22.26...
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP x190si20618868qkd.102 - gsmtp

```
your ISP is blocking outbound SMTP traffic.

(To leave the telnet client, hold down Ctrl and type the "]" character.  Then enter "quit".)

---

### Post by ferguson.stewart on 2016-08-29
Thanks, it looks like my ISP does block port 25.

---

### Post by TheFu on 2016-08-29
> **ferguson.stewart said:**
> Thanks, it looks like my ISP does block port 25.

That just means you need to use their SMTP gateway. It may or may not require authentication. Depends on the ISP. If you shared the ISP name with us, perhaps someone here has experience with them and can help.  Just use the relayhost setting, if authentication isn't needed.  If auth is needed, think you'll need to setup a transport hash/db. I haven't dealt with this for about a decade, so don't remember the details now.

---

### Post by SeijiSensei on 2016-08-31
Not all ISPs provide a relay host, especially those that ban servers on residential accounts.

---

### Post by loualbertlaurel on 2016-10-13
I'm having the same problem and below is the result of my test:
```
@smtp:/# telnet gmail-smtp-in.l.google.com 25
Trying 74.125.204.26...
Trying 2404:6800:4008:c04::1b...
telnet: Unable to connect to remote host: Network is unreachable

```
but after raising this to our isp. email tests that i have done only came to the gmail recipient after almost 12 hours..

---

### Post by SeijiSensei on 2016-10-13
When you said you raised this with your ISP, what was the response?

---

### Post by loualbertlaurel on 2016-10-14
they said that our firewall must be filtering it. and asked to do a traceroute from our server to yahoo and google;

---

### Post by loualbertlaurel on 2016-10-16
as of yesterday, sending to external recipients is already working but receiving is still a problem. isp said they did some modifications on their end but have not provided the information on what exactly they did.

---

### Post by loualbertlaurel on 2016-10-17
[COLOR=#333333][FONT=Verdana][COLOR=#000000][FONT=&quot]Good morning,

I've checked with some rbl sites and found this upon checking:

[B]DNS request failed: The name server was unable to process this query due to a problem with the name server.
[/B][/FONT][/COLOR]
[/FONT][/COLOR]

---

