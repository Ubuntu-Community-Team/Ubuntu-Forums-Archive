---
title: "Huge amounts of mail traffic"
date: 2008-01-26
forum: Server Platforms
---

### Post by showe1966 on 2008-01-26
I'm getting a ton of messages and server traffic in my mail log of the format:-

Jan 26 06:25:54 server1 postfix/qmgr[22538]: 9FA7D1012703: to=<leugchi@ms36.hinet.net>, relay=none, delay=73243, delays=73066/176/0/0, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to ms36a.hinet.net[168.95.5.36]: Connection timed out)
Jan 26 06:25:54 server1 postfix/qmgr[22538]: 9A5B91012018: to=<dahjiaah@ms36.hinet.net>, relay=none, delay=77803, delays=77626/176/0/0, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to ms36a.hinet.net[168.95.5.36]: Connection timed out)
Jan 26 06:25:54 server1 postfix/qmgr[22538]: 9A5B91012018: to=<g4635388@ms36.hinet.net>, relay=none, delay=77803, delays=77626/176/0/0, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to ms36a.hinet.net[168.95.5.36]: Connection timed out)
Jan 26 06:25:54 server1 postfix/smtp[8031]: 1F7B0101140D: to=<m9300909@knight.fcu.edu.tw>, relay=none, delay=111829, delays=111641/158/31/0, dsn=4.4.1, status=deferred (connect to knight.fcu.edu.tw[140.134.4.20]: Connection timed out)


What is going on ?
Is my mail server an open replay or is this an attempted flooding attack ?
Should I try blocking this ip address 168.95.5.36 ?

I do a lot of business in China and taiwan and I suspect someone is trying to hack onto my server.

---

### Post by keithweddell on 2008-01-26
Looks like someone is trying to use you as a relay.  But it isn't working so I don't think you need to worry.  I see this on my mail server as well and I think as long as you're getting relay=none you don't need to worry.  You could try blocking the ip address but they tend to change from time to time - probably just spoofed anyway.

Keith.

---

### Post by showe1966 on 2008-01-26
Thanks for your reply.
Do you know any good article on the web about how to read and interpret the postfix mail log ?

---

### Post by HermanAB on 2008-01-26
Here you go:

$ sudo iptables -I INPUT -p tcp -s w.x.y.z -j DROP

A few of those can do wonders to calm a mail server down.

---

### Post by FakeOutdoorsman on 2008-01-26
Just as a side note, I monitor a server with [projecthoneypot.org]("http://projecthoneypot.org/").  You will receive an email message telling you if your ip addess(es) are being used for spamming, e-mail harvesting, comment spamming, etc.  You don't need to install anything.  Also good for making sure a family member's Windows computer isn't infected.

---

### Post by showe1966 on 2008-01-30
oh dear things aren't getting better and there is huge amounts of postfix traffic being bounced.
i will try some of those netfilters i guess.
i installed snort and the snort log says:-

[**] [1:2590:3] SMTP MAIL FROM overflow attempt [**]
[Classification: Attempted Administrator Privilege Gain] [Priority: 1]
01/30-16:22:49.785718 xxxxxxxxxxxxx:48100 -> 168.95.5.73:25
TCP TTL:240 TOS:0x10 ID:0 IpLen:20 DgmLen:3961
***AP*** Seq: 0xE61D71BC  Ack: 0x970AB8DB  Win: 0xBCB7  TcpLen: 20
[Xref => [http://www.guninski.com/exim1.html]](http://www.guninski.com/exim1.html])[Xref => [http://cve.mitre.org/cgi-bin/cvename.cgi?name=2004-0399]](http://cve.mitre.org/cgi-bin/cvename.cgi?name=2004-0399])[Xref => [http://www.securityfocus.com/bid/10290]](http://www.securityfocus.com/bid/10290])[Xref => [http://www.securityfocus.com/bid/7506]](http://www.securityfocus.com/bid/7506])

does anyone have any top tips about how i can stop these nice people from clogging up my postfix server ?

---

### Post by MJN on 2008-01-30
Something doesn't look right here. Post more of your logs (unedited) and identify which connections you know nothing about.

The log snippets in your first post are attempted outbound connections, not inbound, and hence are connections *from* your machine. Do you recognise those destination e-mail addresses? If they are bounces why are you generating them? If they are in response to non-existant mailboxes (e.g. from random spamming) then why aren't you rejecting such undeliverable mail during the SMTP stage?

What's your IP address and the domain you accept mail for? (PM it if you prefer) Have you configured Postfix to not act as an open relay?

Mathew

---

### Post by showe1966 on 2008-02-02
Sorry for the slow reply.
I was out of the country.

My webserver is set up using the ispconf.org proceedure on version 6.06 LTS.

So, the post server uses passwords and encyption so it should not be possible for anyone else to send mail with it.

I will check the logs again and post more when I see what is happening.

---

### Post by showe1966 on 2008-02-03
Looks like I f***ked up setting my postfix up.

I used following instructions to modify my /etc/postfix/main.cf
file:-

[http://www.cyberciti.biz/tips/postfix-spam-filtering-with-blacklists-howto.html](http://www.cyberciti.biz/tips/postfix-spam-filtering-with-blacklists-howto.html)

The file now looks as follows:-

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

myhostname = server1.xxxxxx.com
alias_maps = hash:/etc/aliases

alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = server1.xxxxxxxxxxx.com, localhost.xxxxxxxxxxxxx.com, , localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination,
   reject_invalid_hostname,
   reject_non_fqdn_hostname,
   reject_non_fqdn_sender,
   reject_non_fqdn_recipient,
   reject_unknown_sender_domain,
   reject_unknown_recipient_domain,
   reject_rbl_client list.dsbl.org,
   reject_rbl_client sbl.spamhaus.org,
   reject_rbl_client cbl.abuseat.org,
   reject_rbl_client dul.dnsbl.sorbs.net,
   permit

smtpd_error_sleep_time = 1s
smtpd_soft_error_limit = 10
smtpd_hard_error_limit = 20

smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

virtual_maps = hash:/etc/postfix/virtusertable

mydestination = /etc/postfix/local-host-names
disable_vrfy_command = yes
smtpd_delay_reject = yes
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks,
     reject_non_fqdn_hostname,
     reject_invalid_hostname,
     permit


Can anyone tell me if the above is OK now.
Anyway, there is still a lot of c**p coming in on the logs, but at least it all seems to be bouncing now. I am getting connects from unknowns, but I guess that is one of the hazards of allowing people to send mail to you !


Feb  3 17:57:45 server1 postfix/smtpd[15260]: NOQUEUE: reject: RCPT from pool-72-89-82-167.nycmny.fios.verizon.net[72.89.82.167]: 504 5.5.2 <Wireless_Broadband_Router>: Helo command rejected: need fully-qualified hostname; from=<linhofkammermet@hofkammer.de> to=<chris.detrick@xxxxxxxxxx.com> proto=ESMTP helo=<Wireless_Broadband_Router>
Feb  3 17:57:46 server1 postfix/smtpd[15260]: lost connection after DATA from pool-72-89-82-167.nycmny.fios.verizon.net[72.89.82.167]
Feb  3 17:57:46 server1 postfix/smtpd[15260]: disconnect from pool-72-89-82-167.nycmny.fios.verizon.net[72.89.82.167]
Feb  3 17:57:54 server1 postfix/smtpd[15266]: warning: 77.205.38.48: hostname 48.38.205-77.rev.gaoland.net verification failed: Name or service not known
Feb  3 17:57:54 server1 postfix/smtpd[15266]: connect from unknown[77.205.38.48]
Feb  3 17:57:54 server1 postfix/smtpd[15266]: lost connection after CONNECT from unknown[77.205.38.48]
Feb  3 17:57:54 server1 postfix/smtpd[15266]: disconnect from unknown[77.205.38.48]
Feb  3 17:57:55 server1 postfix/smtpd[15263]: connect from a166180.upc-a.chello.nl[62.163.166.180]
Feb  3 17:57:57 server1 postfix/smtpd[15263]: NOQUEUE: reject: RCPT from a166180.upc-a.chello.nl[62.163.166.180]: 554 5.7.1 Service unavailable; Client host [62.163.166.180] blocked using cbl.abuseat.org; Blocked - see [http://cbl.abuseat.org/lookup.cgi?ip=62.163.166.180;](http://cbl.abuseat.org/lookup.cgi?ip=62.163.166.180;) from=<spasmodicqr2@trcarr.com> to=<brandon@xxxxxxxxxx.com> proto=ESMTP helo=<pc-2d92f25f2e3b.arnhem.chello.nl>
Feb  3 17:57:57 server1 postfix/smtpd[15263]: lost connection after DATA from a166180.upc-a.chello.nl[62.163.166.180]
Feb  3 17:57:57 server1 postfix/smtpd[15263]: disconnect from a166180.upc-a.chello.nl[62.163.166.180]
Feb  3 17:58:44 server1 postfix/smtpd[15268]: connect from pool-72-89-82-167.nycmny.fios.verizon.net[72.89.82.167]
Feb  3 17:58:46 server1 postfix/smtpd[15268]: NOQUEUE: reject: RCPT from pool-72-89-82-167.nycmny.fios.verizon.net[72.89.82.167]: 504 5.5.2 <Wireless_Broadband_Router>: Helo command rejected: need fully-qualified hostname; from=<linkuechlamet@kuechla.de> to=<chris.detrick@xxxxxxxxxx.com> proto=ESMTP helo=<Wireless_Broadband_Router>
Feb  3 17:58:46 server1 postfix/smtpd[15268]: lost connection after DATA from pool-72-89-82-167.nycmny.fios.verizon.net[72.89.82.167]
Feb  3 17:58:46 server1 postfix/smtpd[15268]: disconnect from pool-72-89-82-167.nycmny.fios.verizon.net[72.89.82.167]
Feb  3 17:58:46 server1 postfix/smtpd[15267]: connect from a166180.upc-a.chello.nl[62.163.166.180]
Feb  3 17:58:48 server1 postfix/smtpd[15267]: NOQUEUE: reject: RCPT from a166180.upc-a.chello.nl[62.163.166.180]: 554 5.7.1 Service unavailable; Client host [62.163.166.180] blocked using cbl.abuseat.org; Blocked - see [http://cbl.abuseat.org/lookup.cgi?ip=62.163.166.180;](http://cbl.abuseat.org/lookup.cgi?ip=62.163.166.180;) from=<tensingzgs4@harrp.com> to=<brandon@xxxxxxxxxx.com> proto=ESMTP helo=<pc-2d92f25f2e3b.arnhem.chello.nl>
Feb  3 17:58:49 server1 postfix/smtpd[15267]: lost connection after DATA from a166180.upc-a.chello.nl[62.163.166.180]
Feb  3 17:58:49 server1 postfix/smtpd[15267]: disconnect from a166180.upc-a.chello.nl[62.163.166.180]
Feb  3 17:58:59 server1 postfix/smtpd[15260]: connect from pool-72-89-82-167.nycmny.fios.verizon.net[72.89.82.167]

BTW I am getting some errors as follows in the syslog.
Anyone know why ?
Feb  3 17:57:10 server1 authdaemond: PAM unable to dlopen(/lib/security/pam_foreground.so)
Feb  3 17:57:10 server1 authdaemond: PAM [dlerror: /lib/security/pam_foreground.so: undefined symbol: pam_set_data]
Feb  3 17:57:10 server1 authdaemond: PAM adding faulty module: /lib/security/pam_foreground.so

---

### Post by MJN on 2008-02-04
That's much better - you were basically acting as an open relay before and accepting/delivering mail for destinations other that your own domain.

You will get hundreds, if not thousands, of spam attempts a day - this is normal and just par for the course of having a mail server on the Internet. Your use of RBLs at the SMTP stage is a good defence against a lot of it, although there is some risk of losing legitiamate e-mail (e.g. if an ISP's mail server ends up being tagged given a compromised machine on its network - all mail (even genuine) through that server now gets bounced). You might want to look at using RBLs as part of SpamAssassin's weight-scoring system instead (it can then be configured so that only multiple RBL hits trigger the spam threshold).

I don't know about your PAM issues. Is you SMTP client authentication working okay?

Mathew

---

### Post by showe1966 on 2008-02-05
Dear MJN,

Thanks for your help and input.
I had some problems with SMTP authorization for my clients using outlook to send mail .

Mail was sent okay from thunderbird and other non-windows clients.
It appears that this was caused by a problem with the outlook TLS settings for smtp.

The problem was that outlook users could get mail okay with SSL, but they could not send mail with TLS.
If you sent mail in outlook, you get the following error:-

504 5.5.2 <mario>: Helo command rejected: need fully-qualified hostname 

This is related to the presence of the following lines in the /etc/postfix/main.cf file:-

smtpd_helo_restrictions = permit_mynetworks,
     reject_non_fqdn_hostname,
     reject_invalid_hostname,

the file was therefore modified to:-

smtpd_helo_restrictions = permit_mynetworks,

I think this has negative security implications, but then, I guess this is what you have to live with if you will insist on letting people use windows...

BTW I read someting on the net about how iit might be possible for someone to use a packet sniffer to read the passwords in my ssl certificates because of the following setting in the  /etc/postfix/main.cf file:-

smtpd_tls_auth_only = no

This is because there is the possibility that the certificate is sent unencrypted or something like that.

Does anyone know if this is true or not,if this is a problem  ?

Can I tell if this is a problem or not by telneting port 25 of localhost and what should i see ?

---

### Post by MJN on 2008-02-05
> **showe1966 said:**
> I think this has negative security implications, but then, I guess this is what you have to live with if you will insist on letting people use windows...
 
This is not a Windows limitation, but merely how you've configured the Windows machine. Setting Postfix to only allow fully-qualified HELO/EHLO hostnames helps reduce some spam because a lot of spam software, by virtue of them often not following RFCs to the letter, often gives 'localhost' or some other meaningless name (sometimes even *your* hostname) and hence forcing RFC-compliance can help weed some of this out.
 
> BTW I read someting on the net about how iit might be possible for someone to use a packet sniffer to read the passwords in my ssl certificates because of the following setting in the /etc/postfix/main.cf file:-
 
smtpd_tls_auth_only = no
 
This is because there is the possibility that the certificate is sent unencrypted or something like that.
 
Does anyone know if this is true or not,if this is a problem ?
 
It is true, although it is not the certificate being sent unencrypted (indeed there is no certificate - that's the point) but rather your username/password are potentially being send unencrypted if using a plaintext authentication mechanism. Setting smtpd_tls_auth_only to yes means that the authentication options are not given (allowed) until an encrypted TLS tunnel has been established.
 
> Can I tell if this is a problem or not by telneting port 25 of localhost and what should i see ?
 
If you are offered PLAIN/LOGIN authentication methods then you do have this 'problem'. You really ought to use TLS as practically all modern mail clients support it.
 
Mathew

---

### Post by FakeOutdoorsman on 2008-02-05
I also had problems with Outlook and SMTP TLS with Sendmail.  Users received an error "a certificate chain processed but terminated in a root certificate which is not trusted by the trust provider" on each Outlook session until I ran:

```
cd /usr/share/ssl/certs
openssl x509 -in ipop3d.pem -out ipop3d.crt

```

The resulting certificate was then installed on each of the Outlook machines (by opening the certificate in Innernet Explowuh) and that stopped the message.

---

### Post by MJN on 2008-02-05
You can get trusted SSL certs pretty cheap nowadays - the last one I bought was $15/yr and was signed by an Equifax root hence natively trusted by practically all clients. I can dig the link out if you're interested (it saves having to customise clients, and of course allows others to connect with trust).

Mathew

---

### Post by showe1966 on 2008-02-10
Oh dear.

I completely re-installed everything , but still am seeing huge volumes of mail traffic.
Can anyone tell me how to secure my postfix smtp settings ?


Here is an example of some  bad-looking messages:-

Feb 10 16:21:24 server1 postfix/qmgr[4474]: 1284D122E1E3: from=<tarystqeiqwiq@joongang.co.kr>, size=1566, nrcpt=13 (queue active)
Feb 10 16:21:24 server1 postfix/qmgr[4474]: 1B2C5122D6CE: from=<>, size=3773, nrcpt=1 (queue active)
Feb 10 16:21:24 server1 postfix/qmgr[4474]: 1F9BE122D05C: from=<>, size=3898, nrcpt=1 (queue active)

Feb 10 17:37:07 server1 postfix/smtp[11458]: 2E901122F931: to=<est934011@yahoo.com.tw>, relay=mx2.mail.tw.yahoo.com[203.188.197.9]:25, delay=209, delays=1/205/3.5/0, dsn=4.7.0, status=deferred (host mx2.mail.tw.yahoo.com[203.188.197.9] refused to talk to me: 421 4.7.0 [TS01] Messages from xxxxxx temporarily deferred due to user complaints - 4.16.55.1; see [http://postmaster.yahoo.com/421-ts01.html](http://postmaster.yahoo.com/421-ts01.html))



Feb 10 17:39:22 server1 postfix/smtp[11755]: certificate verification failed for ccsun41.cc.ntu.edu.tw: num=19:self signed certificate in certificate chain
Feb 10 17:39:23 server1 postfix/smtp[11755]: 511E7122CBC3: to=<chiishen@ntu.edu.tw>, relay=ccsun41.cc.ntu.edu.tw[140.112.8.41]:25, delay=78150, delays=77975/170/4.9/0.32, dsn=4.0.0, status=deferred (host ccsun41.cc.ntu.edu.tw[140.112.8.41] said: 450 <zjuzsidmnjnztb@med-rz.uni-sb.de>: Sender address rejected: Domain not found (in reply to RCPT TO command))

Feb 10 17:39:55 server1 postfix/smtp[11755]: connect to tve.hshs.tyc.edu.tw[203.68.249.211]: Connection timed out (port 25)
Feb 10 17:39:55 server1 postfix/smtp[11755]: 55282122F0A4: to=<admin@tve.hshs.tyc.edu.tw>, relay=none, delay=10877, delays=10671/175/32/0, dsn=4.4.1, status=deferred (connect to tve.hshs.tyc.edu.tw[203.68.249.211]: Connection timed out)
Feb 10 17:39:56 server1 postfix/smtp[11755]: connect to mail.epaper.com.tw[219.87.131.230]: No route to host (port 25)
Feb 10 17:39:56 server1 postfix/smtp[11755]: 64842122E70F: to=<service-gq@epaper.com.tw>, relay=none, delay=49699, delays=49494/205/0.37/0, dsn=4.4.1, status=deferred (connect to mail.epaper.com.tw[219.87.131.230]: No route to host)
Feb 10 17:40:05 server1 postfix/smtp[11755]: 6CCEE122D134: host mailgw.hfu.edu.tw[210.59.127.2] said: 450 <b84072000029@cat.hfu.edu.tw>: User unknown in local recipient table (in reply to RCPT TO command)



Here is my/etc/postfix/main.cf 

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

myhostname = server1.xxxxxxxxxx.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = server1.xxxxxx.com, localhost.xxxs.com, , localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_invalid_hostname,reject_non_fqdn_hostname,reject_non_fqdn_sender,reject_invalid_hostname,reject_non_fqdn_hostname,reject_non_fqdn_sender,reject_non_fqdn_recipient,reject_unknown_sender_domain,reject_unknown_recipient_domain,reject_unauth_destination,reject_rbl_client list.dsbl.org,reject_rbl_client sbl.spamhaus.org,reject_rbl_client cbl.abuseat.org,reject_rbl_client dul.dnsbl.sorbs.net,

smtpd_error_sleep_time = 1s
smtpd_soft_error_limit = 10
smtpd_hard_error_limit = 20

smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

virtual_maps = hash:/etc/postfix/virtusertable

mydestination = /etc/postfix/local-host-names
disable_vrfy_command = yes
smtpd_delay_reject = yes
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks,

---

### Post by showe1966 on 2008-02-11
ok the mystery is solved.

I really tightened the postfix rules concerning incoming smtp helos in the postfix configuration file and also installed greyfiltering.

I then discovered that a collegue of mine has set up a windows mail server, which has been hacked and which is requesting me to spam people about 5 times a second !
The joke is that i re-installed and every time i got everything working, i gave him my password, log and sent him the server certificate in plain text !!

anyway here's what all my settings are now.
It is probably all a bit OTT and might bounch quite a lot of mail:-


INSTALL GREYLISTING
SEE: [http://www.howtoforge.com/greylisting_postfix_postgrey](http://www.howtoforge.com/greylisting_postfix_postgrey)
AND (Better article including a section on postgrey) [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
apt-get install postgrey

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libberkeleydb-perl libio-multiplex-perl libnet-cidr-perl libnet-server-perl
Suggested packages:
  libio-socket-ssl-perl
Recommended packages:
  libnet-rblclient-perl
The following NEW packages will be installed:
  libberkeleydb-perl libio-multiplex-perl libnet-cidr-perl libnet-server-perl postgrey
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 346kB of archives.
After unpacking 1331kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [ftp://mirror.hetzner.de](ftp://mirror.hetzner.de) gutsy/universe libberkeleydb-perl 0.31-1 [133kB]
Get:2 [ftp://mirror.hetzner.de](ftp://mirror.hetzner.de) gutsy/universe libio-multiplex-perl 1.09-1 [22.6kB]
Get:3 [ftp://mirror.hetzner.de](ftp://mirror.hetzner.de) gutsy/universe libnet-cidr-perl 0.11-1 [14.7kB]
Get:4 [ftp://mirror.hetzner.de](ftp://mirror.hetzner.de) gutsy/universe libnet-server-perl 0.94-1 [131kB]
Get:5 [ftp://mirror.hetzner.de](ftp://mirror.hetzner.de) gutsy/universe postgrey 1.27-4 [44.7kB]
Fetched 346kB in 0s (1590kB/s)
Selecting previously deselected package libberkeleydb-perl.
(Reading database ... 28253 files and directories currently installed.)
Unpacking libberkeleydb-perl (from .../libberkeleydb-perl_0.31-1_i386.deb) ...
Selecting previously deselected package libio-multiplex-perl.
Unpacking libio-multiplex-perl (from .../libio-multiplex-perl_1.09-1_all.deb) ...
Selecting previously deselected package libnet-cidr-perl.
Unpacking libnet-cidr-perl (from .../libnet-cidr-perl_0.11-1_all.deb) ...
Selecting previously deselected package libnet-server-perl.
Unpacking libnet-server-perl (from .../libnet-server-perl_0.94-1_all.deb) ...
Selecting previously deselected package postgrey.
Unpacking postgrey (from .../postgrey_1.27-4_all.deb) ...
Setting up libberkeleydb-perl (0.31-1) ...
Setting up libio-multiplex-perl (1.09-1) ...
Setting up libnet-cidr-perl (0.11-1) ...
Setting up libnet-server-perl (0.94-1) ...
Setting up postgrey (1.27-4) ...
Warning: The home dir you specified does not exist.
Adding system user `postgrey' (UID 113) ...
Adding new group `postgrey' (GID 116) ...
Adding new user `postgrey' (UID 113) with group `postgrey' ...
Not creating home directory `/var/lib/postgrey'.

Creating config file /etc/postgrey/whitelist_clients with new version

Creating config file /etc/postgrey/whitelist_recipients with new version

Creating config file /etc/default/postgrey with new version
Starting postfix greylisting daemon: postgrey.

sudo vi /etc/default/postgrey

chnage delay time to 1.5 minute:-

POSTGREY_OPTS="--inet=127.0.0.1:60000 --delay=90 --max-age=1"


/etc/init.d/postgrey restart

postgrey should be up and running on port 60000

netstat -anp | grep 60000

Configure Postfix

The Postfix configuration files are located in /etc/postfix. Edit /etc/postfix/main.cf and add check_policy_service inet:127.0.0.1:60000 to the smtpd_recipient_restrictions. It should look something like this : 

smtpd_recipient_restrictions = permit_sasl_authenticated,
           permit_mynetworks,
           reject_unauth_destination,
           check_policy_service inet:127.0.0.1:60000

Also i improved my postfix settings as follows:-

The first file we want to create is /etc/postfix/helo.regexp and this will contain:

restart/^subdomain\.host\.com$/           550 Don't use my own hostname
/^xxx\.yyy\.zzz\.xxx$/             550 Don't use my own IP address
/^\[xxx\.yyy\.zzz\.xxx\]$/         550 Don't use my own IP address
/^[0-9.]+$/                        550 Your software is not RFC 2821 compliant
/^[0-9]+(\.[0-9]+){3}$/            550 Your software is not RFC 2821 compliant

/etc/init.d/postfix restart

Next up, we need to create /etc/postfix/helo_client_exceptions:

This file is needed incase a badly behaved mail server can't send the correct helo and you need to allow mail to be accepted from that source.  In my experience, things like standalone devices, CCTV camera are poor at complying to standards so you might need to make an exception for this.

 Before any changes in this file become usable you need to run

postmap /etc/postfix/helo_client_exceptions


Moving down, we have /etc/postfix/sender_checks which allows you to bypass the various FQDN checks and allow a particular sender through.  This is particular useful if a company runs an internal mail network such as domain.com but email runs on int.domain.com and there is no DNS setup int.domain.com, this is great for security but not great becuase external DNS doesn't know about the internal structure and therefore postfix will reject the int.domain.com.

[email]user@domain.com[/email]      REJECT 
[email]user@int.domian.com[/email]   OK 

Once again this file once modified must have a Berkely DB file created and thus we create it using:

postmap /etc/postfix/sender_checks

---

### Post by showe1966 on 2008-02-11
heres the content of my postfix config file now.
As I said it's probably completely OTT at this stage.

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
delay_warning_time = 4h
# will it be a permanent error or temporary
unknown_local_recipient_reject_code = 450
# how long to keep message on queue before return as failed.
# some have 3 days, I have 16 days as I am backup server for some people
# whom go on holiday with their server switched off.
maximal_queue_lifetime = 7d
# max and min time in seconds between retries if connection failed
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
# how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s
# how many address can be used in one message.
# effective stopper to mass spammers, accidental copy in whole address list
# but may restrict intentional mail shots.
smtpd_recipient_limit = 8
# how many error before back off.
smtpd_soft_error_limit = 3
# how many max errors before blocking it.
smtpd_hard_error_limit = 12

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = server1.xxxxxx.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = server1.xxxs.com, localhost.xxxxxxx.com, , localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client relays.ordb.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org,,reject_rbl_client dul.dnsbl.sorbs.net,reject_rbl_client cbl.abuseat.org,reject_rbl_client list.dsbl.org
smtpd_recipient_restrictions = check_policy_service inet:127.0.0.1:60000,permit_mynetworks,permit_sasl_authenticated,reject_invalid_hostname,reject_non_fqdn_hostname,reject_non_fqdn_sender,reject_invalid_hostname,reject_non_fqdn_hostname,reject_non_fqdn_sender,reject_non_fqdn_recipient,reject_unknown_sender_domain,reject_unknown_recipient_domain,reject_unauth_destination,reject_rbl_client list.dsbl.org,reject_rbl_client sbl.spamhaus.org,reject_rbl_client cbl.abuseat.org,reject_unauth_pipelining,permit
#require proper helo at connections
smtpd_helo_required = yes
#waste spammers time before rejecting
smtpd_delay_reject = yes
disable_vrfy_command = yes

smtpd_error_sleep_time = 1s
#smtpd_soft_error_limit = 10
smtpd_hard_error_limit = 20

smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

virtual_maps = hash:/etc/postfix/virtusertable

mydestination = /etc/postfix/local-host-names

---

### Post by MJN on 2008-02-11
Good to hear you're back up-and-running. Just a few comments worth making though:

- Destination domains - You've commented out the mydestination directive and replaced it with a pointer to a 'local-host-names' file - howcome? Whilst you are using virtual domains you should have a 'native' real domain in here if only to ensure local delivery is predictable.

- Queue time - You've mentioned raising the queue time to 16 days to accommodate an extended backup delivery time however you've only set it to 7 days. Notwithstanding this the rest of the config does not suggest you are acting as a backup MX for other domains at all?

- RBLs - There is no need to set the same RBLs in both smtpd_client_restrictions and smtpd_recipient_restrictions as the lookups will be duplicated. Indeed, scrap the smtpd_client_restrictions directive directly as these restrictions can all be accomodated with smtpd_recipient_restrictions.

- SASL authentication - You still haven't set smtpd_tls_auth_only to yes to ensure plaintext credentials are only sent inside an encrypted tunnel - you should do this to prevent the potential for such info to be sniffed on the wire.

Mathew

---

