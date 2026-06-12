---
title: "Mail Server issues: 554 relay access denied"
date: 2011-09-01
forum: Server Platforms
---

### Post by rsain on 2011-09-01
Greetings all,

I have followed the instructions on [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) to establish a mail server on top of my existing web server. I'm running into some odd problems - and at odd times. 

If I telnet locally into the server: ```
telnet localhost 25 
```

I can send email without an error to my work account. (well kinda, but I dont get the access denied error)

If I telnet into the server from an outside machine: ```
telnet XXX.XXX.XX.XXX 25
```

Then I get the following error:

```
rcpt to: <rsain@yyy.yyy>
554 5.7.1 <rsain@yyy.yyy>: Relay access denied
```

Been tailing the mail.log and the mysql.log. Mysql is ok. mail is giving this:

```
ubuntu postfix/qmgr[3244]: DC0119015C9: from=<rsain@newserver.xxx>, size=804, nrcpt=1 (queue active)
ubuntu postfix/smtp[3280]: connect to mail.messaging.microsoft.com[xxx.xxx.xx.xxx]:25: Connection refused
ubuntu postfix/smtp[3280]: DC0119015C9: to=<rsain@workemail.xxx>, relay=none, delay=1089, delays=1089/0.01/0/0, dsn=4.4.1, status=deferred (connect to mail.messaging.microsoft.com[xxx.xxx.xx.xxx]:25: Connection refused)
```

I've been looking through many many threads on this but haven't seen this particular issue. There are many other problems, but I think this is at the core. Not sure what I should post to help make more sense of this. I have not tried to use an outside client yet - just getting telnet to work.

Help please!

- ryan

---

### Post by lisati on 2011-09-01
A couple of ideas to start the ball rolling.

Usually Postfix throws a "Relay access denied" error when it doesn't recognize the email address as belonging to a valid destination. One way of controlling incoming mail is through the "mydestination" configuration option in postfix's main.cf

As for the "Connection refused" issue, it could be anything at your end, including using the "wrong" server as a smarthost or maybe having a typo in postfix's transport maps. Possibly the Microsoft server just doesn't like your server connecting. :(

*Edit: Thread moved to "Server platforms"*

---

### Post by rsain on 2011-09-02
> **lisati said:**
> A couple of ideas to start the ball rolling.

Usually Postfix throws a "Relay access denied" error when it doesn't recognize the email address as belonging to a valid destination. One way of controlling incoming mail is through the "mydestination" configuration option in postfix's main.cf


The two errors are concurrent - one is what is happening in the telnet window the other is what is happening in the log at the same time. 

Further - the issue isn't with incoming mail. It is when I'm trying to send mail using the new domain. If I tunnel into the machine on ssh then use telnet locally to send mail to my work email addy - it doesn't kick an error. 

However, if I do not tunnel in first and just telnet into the ip of the machine I get the errors I mentioned. 


> **lisati said:**
> 
As for the "Connection refused" issue, it could be anything at your end, including using the "wrong" server as a smarthost or maybe having a typo in postfix's transport maps. Possibly the Microsoft server just doesn't like your server connecting. :(


I'm not using any relay - I'm allowing my server to handle that task as I'm not going to be hosting a ton of mail. I'll definitely look into the transport map issue that very well could be a problem. 

It may also be that because not everything is matching up (server is behind a firewall at work - university) and the domain isn't the same (organization domain hides behind a firewall of the uni) that the spam filters are not allowing a connection.

Would It help if I posted the main.cf file?

Thanks for your thoughts!

- ryan

---

### Post by SeijiSensei on 2011-09-02
```
mail.messaging.microsoft.com[xxx.xxx.xx.xxx]:25
```

Can you telnet to port 25 at this address and conduct a manual SMTP transaction?

---

### Post by rsain on 2011-09-02
Sadly, no. Just says connection refused. 

```
~$ telnet 2xx.3x.1xx.1xx 25
Trying 2xx.3x.1xx.1xx...
telnet: Unable to connect to remote host: Connection refused
```

I'm just at a loss here. Everything is working locally so to speak (on localhost) but not getting outside and nothing from the outside is getting in. 

What is the chances this is a port issue on the firewall at work (i.e., port 25 is closed)? Wouldn't it kick a general error like this?

- ryan

---

### Post by rsain on 2011-09-02
main.cf content - ips and comments stripped:

```
myorigin = mydomain.net
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
relayhost =
inet_interfaces = all
mynetworks_style = host
local_recipient_maps =
mydestination =
append_dot_mydomain = no
delay_warning_time = 4h
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12

smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
readme_directory = no
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
myhostname = mail.mydomain.net
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
content_filter = amavis:[127.0.0.1]:10024
```

I wonder if I buggered something in mynetworks? I want to be able to send and receive email from anywhere in the world - using authentication. 

- ryan

---

### Post by Entilza on 2011-09-02
Add your local network to mynetworks  for example 10.1.16.0/24

Relaying is disabled by default outside the local network.

And you can't telnet to 25 from the outside world probably because your ISP is blocking it but don't worry mail servers will be able to connect.

---

### Post by rsain on 2011-09-02
> **Entilza said:**
> Add your local network to mynetworks  for example 10.1.16.0/24


Just to make sure i'm getting this right...

the IP where my mail server sits should be included here? followed by a /24 ?

Do I separate by a comma after the local IP?

- ryan

---

### Post by e79 on 2011-09-02
> **Entilza said:**
> Add your local network to mynetworks  for example 10.1.16.0/24

Relaying is disabled by default outside the local network.

And you can't telnet to 25 from the outside world probably because your ISP is blocking it but don't worry mail servers will be able to connect.

+ 1 for that

and make sure that your server doesn't accept relay and stays like that, you don't want all the spammers in the world to use your mail server  ;)

---

### Post by Entilza on 2011-09-02
Sorry that would allow relaying messages from other computers within your network, if you want to allow relaying from the outside world via external IPS then I am not too sure.  This would solve your issue from other PC's within your network to email.

It's probably something similar perhaps some wildcard or something, why do you want to allow SMTP from the outside world?  As I mentioned some ISP's don't even allow telneting out on 25 so it may not even work as you are trying.

---

### Post by rsain on 2011-09-02
I guess I'm a bit confused here.

"my network" is a university. I have a non-profit that I host stuff for. Now they want email. Since the non-profit is not located on campus, people will be checking their mail using email clients from anywhere in the world. Further, they will send emails to anyone. I will require SSL (next step after I get the bugs out here).

Right now - I cannot send a mail to even my gmail account. Heck, I cant even send an email to my own university account.

- ryan

---

### Post by rsain on 2011-09-02
Additional info:

The ONLY thing that works right now is telnet. 
1. I can send a message from [email]user1@mynewdomain.net[/email] to [email]user2@mynewdomain.net[/email]
1.2. I can see that the messages are sent and delivered by tailing /var/log/mail.log
1.3. I can see that mysql is working by tailing it

2.1 on TELNET only I can send a message from [email]myname@myuni.edu[/email] to [email]user1@mynewdomain.net[/email]
2.2 I cannot send a message from [email]user1@mydomain.net[/email] to any outside address including [email]myname@myuni.edu[/email]

3.1 using my university email and a client I can send from [email]myname@myuni.edu[/email] to [email]user1@mynewdomain.net[/email]
3.2 using my google email I CANNOT send an email from [email]myname@gmail.com[/email] to [email]user1@mynewdomain.net[/email] 

What I expect it should do:

1. Use a client (say Thunderbird) to receive and send email from and to any location - while physically sitting at any location.
2. of course the caveat here is all the stuff that should be filtered will be...(which seems to be working)

- ryan

---

### Post by rsain on 2011-09-02
Here's the mail.log when I try to send from telnet to gmail:

```
Sep  2 10:53:49 ubuntu postfix/smtpd[3055]: connect from localhost[127.0.0.1]
Sep  2 10:54:22 ubuntu postfix/smtpd[3055]: 2877A9015EF: client=localhost[127.0.0.1]
Sep  2 10:54:38 ubuntu postfix/cleanup[3057]: 2877A9015EF: message-id=<20110902175422.2877A9015EF@mail.mynewdomain.net>
Sep  2 10:54:38 ubuntu postfix/qmgr[2377]: 2877A9015EF: from=<root@mynewdomain.net>, size=405, nrcpt=1 (queue active)
Sep  2 10:54:38 ubuntu amavis[1681]: (01681-03) ESMTP::10024 /var/lib/amavis/tmp/amavis-20110902T091259-01681: <root@mynewdomain.net> -> <myemail@gmail.com> SIZE=405 Received: from mail.mynewdomain.net ([127.0.0.1]) by localhost (ubuntu.unidomain.uni.edu [127.0.0.1]) (amavisd-new, port 10024) with ESMTP for <myemail@gmail.com>; Fri,  2 Sep 2011 10:54:38 -0700 (PDT)
Sep  2 10:54:38 ubuntu amavis[1681]: (01681-03) Checking: c0527P3Ki-Ci [127.0.0.1] <root@mynewdomain.net> -> <myemail@gmail.com>
Sep  2 10:54:38 ubuntu amavis[1681]: (01681-03) p001 1 Content-Type: text/plain, size: 31 B, name: 
Sep  2 10:54:38 ubuntu postfix/smtpd[3060]: connect from localhost[127.0.0.1]
Sep  2 10:54:38 ubuntu postfix/smtpd[3060]: 250BB9015F0: client=localhost[127.0.0.1]
Sep  2 10:54:38 ubuntu postfix/cleanup[3057]: 250BB9015F0: message-id=<20110902175422.2877A9015EF@mail.globalnetworksusa.net>
Sep  2 10:54:38 ubuntu postfix/smtpd[3060]: disconnect from localhost[127.0.0.1]
Sep  2 10:54:38 ubuntu postfix/qmgr[2377]: 250BB9015F0: from=<root@mynewdomain.net>, size=813, nrcpt=1 (queue active)
Sep  2 10:54:38 ubuntu amavis[1681]: (01681-03) FWD via SMTP: <root@mynewdomain.net> -> <myemail@gmail.com>,BODY=7BIT 250 2.0.0 Ok, id=01681-03, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 250BB9015F0
Sep  2 10:54:38 ubuntu amavis[1681]: (01681-03) Passed CLEAN, LOCAL [127.0.0.1] [127.0.0.1] <root@mynewdomain.net> -> <myemail@gmail.com>, Message-ID: <20110902175422.2877A9015EF@mail.mynewdomain.net>, mail_id: c0527P3Ki-Ci, Hits: -, size: 405, queued_as: 250BB9015F0, 143 ms
Sep  2 10:54:38 ubuntu postfix/smtp[3061]: connect to gmail-smtp-in.l.google.com[74.125.53.27]:25: Connection refused
Sep  2 10:54:38 ubuntu postfix/smtp[3061]: connect to alt1.gmail-smtp-in.l.google.com[74.125.159.27]:25: Connection refused
Sep  2 10:54:38 ubuntu postfix/smtp[3058]: 2877A9015EF: to=<myemail@gmail.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=30, delays=30/0/0/0.14, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=01681-03, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 250BB9015F0)
Sep  2 10:54:38 ubuntu postfix/qmgr[2377]: 2877A9015EF: removed
Sep  2 10:54:38 ubuntu postfix/smtp[3061]: connect to alt2.gmail-smtp-in.l.google.com[74.125.93.27]:25: Connection refused
Sep  2 10:54:38 ubuntu amavis[1681]: (01681-03) TIMING [total 145 ms] - SMTP greeting: 1 (1%)1, SMTP EHLO: 0 (0%)1, SMTP pre-MAIL: 0 (0%)1, SMTP pre-DATA-flush: 1 (1%)2, SMTP DATA: 36 (25%)26, check_init: 0 (0%)26, digest_hdr: 0 (0%)27, digest_body_dkim: 0 (0%)27, gen_mail_id: 0 (0%)27, mime_decode: 2 (2%)29, get-file-type1: 4 (3%)31, parts_decode: 0 (0%)31, check_header: 0 (0%)32, update_cache: 1 (0%)32, decide_mail_destiny: 0 (0%)32, fwd-connect: 7 (5%)37, fwd-mail-pip: 1 (1%)38, fwd-rcpt-pip: 0 (0%)38, fwd-data-chkpnt: 0 (0%)38, write-header: 0 (0%)38, fwd-data-contents: 0 (0%)38, fwd-end-chkpnt: 84 (58%)96, prepare-dsn: 0 (0%)96, main_log_entry: 4 (3%)99, update_snmp: 1 (1%)100, SMTP pre-response: 0 (0%)100, SMTP response: 0 (0%)100, unlink-1-files: 0 (0%)100, rundown: 0 (0%)100
Sep  2 10:54:38 ubuntu postfix/smtp[3061]: connect to alt3.gmail-smtp-in.l.google.com[74.125.113.27]:25: Connection refused
Sep  2 10:54:38 ubuntu postfix/smtp[3061]: connect to alt4.gmail-smtp-in.l.google.com[209.85.143.27]:25: Connection refused
Sep  2 10:54:38 ubuntu postfix/smtp[3061]: 250BB9015F0: to=<myemail@gmail.com>, relay=none, delay=0.09, delays=0.08/0/0/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[209.85.143.27]:25: Connection refused)
Sep  2 10:54:39 ubuntu postfix/smtpd[3055]: disconnect from localhost[127.0.0.1]
```

This to me looks like the outside world is thinking i'm spamming them. I did read somewhere that if not everything matches up in terms of domains, etc. that it will reject. It's an issue if you are not using an relay server (iirc). So here's what really stands out to me from the above log:

```
Received: from mail.mynewdomain.net ([127.0.0.1]) by localhost (ubuntu.unidomain.uni.edu [127.0.0.1])
```

Any ideas?

- ryan

---

### Post by rsain on 2011-09-02
Rebooted server.

Now I can send email from my university account and receive it at my [email]user1@mynewdomain.net[/email] account. I was able to get this email on my Entourage client. However, I still cannot send to the outside world. I get the same error that is the title of this thread.

I also cannot receive from gmail. 

- ryan

---

### Post by SeijiSensei on 2011-09-02
My advice is to stop trying to do this from within a university network and rent a virtual machine  with a public IP address from some place like [Linode]("http://www.linode.com/"). The university network probably blocks outbound connections to SMTP port 25 to prevent infected student computers from sending spam.  Linode servers start at $20/month.  The nonprofit can then have complete web and email services accessible from anywhere on the Internet.

Another plausible option is something like [Google Apps for Business]("http://www.google.com/apps/intl/en/business/smbs.html").

While the intent to provide free services from your dorm room is noble, it's not easy to implement.  Better to exist outside the university entirely.

---

### Post by rsain on 2011-09-02
I'm actually not a student. I'm a professor. It's part of my requirements to offer services to the community. If my university was any more inclined to do email services that didn't involve proprietary software I wouldn't be on here asking for help. I already have approval from the university to open port 25 and other necessary ports (i.e., 143, 587, 465). I'm waiting for the ticket to be pushed through now. I did bring up the port issue in a previous post - not sure if you saw it. 

I've been doing web hosting for entire university systems for the last 8 years and know a bit about that side of things. However, I'm new to this part of the game (email).  The non-profit is not going to pay 20 bucks a month for email access that they will use only occasionally. 

If anything this is a learning experience for me - and less of a service for them. So if you don't have any advice as to how to solve my problem - then please, dont reply.  I'm here to get help - not be told that I shouldn't do it. I spent good money on these Sun servers and the NAS to make this happen and I will make it happen.

- ryan

---

### Post by e79 on 2011-09-03
Some randoms thoughts about telnet using a real life configuration (the values has been changed though, and I used and Exchange server but the behavior should be about the same):

```

telnet mail.testdomain.com 25      [COLOR=Red]<-- Telnet'ing into the real mail server[/COLOR]
Trying X.X.X.X...                          [COLOR=Red]<-- Mail Server IP address[/COLOR]
Connected to mail.testdomain.com.
Escape character is '^]'.
220 MAIL.testdomain.com Microsoft ESMTP MAIL Service, Version: 6.0.3790.4675 ready at  Sat, 3 Sep 2011 08:39:16 -0700
ehlo xyz.com                               [COLOR=Red]<-- Random mail domain name for the handshake[/COLOR]
250-MAIL.testdomain.com Hello [X.X.X.X]    [COLOR=Red]<-- My own external IP address[/COLOR]
250-TURN
250-SIZE
250-ETRN
250-PIPELINING
250-DSN
250-ENHANCEDSTATUSCODES
250-8bitmime
250-BINARYMIME
250-CHUNKING
250-VRFY
250-X-EXPS GSSAPI NTLM LOGIN
250-X-EXPS=LOGIN
250-AUTH GSSAPI NTLM LOGIN
250-AUTH=LOGIN
250-X-LINK2STATE
250-XEXCH50
250 OK
mail from:user1@testdomain.com          [COLOR=Red]<-- Testing sender with an internal user (hosted by your postfix domain)[/COLOR]
250 2.1.0 user1@testdomain.com....Sender OK
rcpt to:user1@hotmail.com                    [COLOR=Red]<-- Trying to send to any external email address[/COLOR]
550 5.7.1 Unable to relay for user1@hotmail.com      [COLOR=Red]<-- The relay is being denied, this is a normal behavior[/COLOR]
rcpt to:user1@testdomain.com           [COLOR=Red]<-- Now trying to send to an internal email user[/COLOR]
250 2.1.5 user1@testdomain.com        [COLOR=Red]<-- That is accepted by the mail server, nomal behavior here as well[/COLOR]
data
354 Start mail input; end with <CRLF>.<CRLF>
This is a test.
.
..
250 2.6.0 <MAILeRaNgEpTX5V3Gyk0000005d@MAIL.testdomain.com> Queued mail for delivery

```So you should not be able to send email to the outside world when testing from telnet, even if an internal username is implied, this is a normal behavior. You can only send within your domain.

On another hand, I might be wrong but, in you 'main.cf' file, at the line :

```
mydestination =
```The value should not be empty but contain the domain(s) you are responsible for as stated here :

[http://postfix.eu.org/basic.html](http://postfix.eu.org/basic.html)

>  ** What domains to receive mail for **

   The **mydestination** parameter specifies what domains this machine will deliver locally, instead of forwarding to another machine. The default is to receive mail for the machine itself.    You can specify zero or more domain names, */file/name* patterns and/or *type:name* lookup tables, separated by whitespace and/or commas.  A */file/name* is replaced by its contents; *type:name* requests that a table lookup is done.  
  If your machine is a mail server for its entire domain, you must list **$mydomain** as well.  
  
 Examples:    
 Default setting:   **mydestination = $myhostname localhost.$mydomain**    
 Domain-wide mail server:   **mydestination = $myhostname localhost.$mydomain $mydomain **    
 Host with multiple DNS A records:   **mydestination = $myhostname localhost.$mydomain www.$mydomain ftp.$mydomain**    Caution: in order to avoid mail delivery loops, you must list all hostnames of the machine, including $myhostname, and localhost.$mydomain.  
I hope this shed a bit of light.

---

### Post by rsain on 2011-09-03
It does help! Thank you. 

I left the mydestination value blank because I'm following the [http://flurdy.com/docs/postfix/#test-postfix-send](http://flurdy.com/docs/postfix/#test-postfix-send) instructions. It says to keep it open as the setup is using virtual domains. 

This is one value that I was thinking of changing and I cant see why it would hurt to give it a shot. So I will. 

As I mentioned before I'm sure one issue I have is the port issue on the uni firewall, but that will be fixed on monday. 

I'll make the change - test within the network and go from there. 

Thanks for the detailed explanation.

- ryan

---

### Post by rsain on 2011-09-03
Interesting. Once I set it up with values in the mydestination I get the following warning in my mail.log


Sep  3 09:30:50 ubuntu postfix/trivial-rewrite[2573]: warning: do not list domain mynewdomain.net in BOTH mydestination and virtual_mailbox_domains

Still going to test to see if it changes any behavior but it looks like it's already specified in the virtual domains.

- ryan

---

### Post by e79 on 2011-09-03
Indeed if you have a firewall blocking access to port 25, it doesn't help ;)

> Sep  3 09:30:50 ubuntu postfix/trivial-rewrite[2573]: warning: do not  list domain mynewdomain.net in BOTH mydestination and  virtual_mailbox_domains
As stated in the error, you can list mynewdomain.net either in virtual_mailbox_domains **or** in mydestination, but not in both.

written here :
[http://www.howtoforge.com/postfix-do-not-list-domain-example.com-in-both-mydestination-and-virtual_mailbox_domains](http://www.howtoforge.com/postfix-do-not-list-domain-example.com-in-both-mydestination-and-virtual_mailbox_domains)

---

### Post by e79 on 2011-09-05
Let us know how it goes !

---

### Post by rsain on 2011-09-05
I've done everything I can do until that port gets opened. Holiday today so no work for the IT folk. Given what you described as expected behavior - then I think all is going well. I'll surely report back once that port is cleared.

- ryan

---

