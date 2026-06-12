---
title: "Mail server can't receive mails"
date: 2007-01-18
forum: Server Platforms
---

### Post by satimis on 2007-01-18
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64
Postfix
Domain: satimis.com


My mail server can send mail but failed to received mail.

Tried sending mail from yahoo.com to "satimis@satimis.com" with following result;```

<satimis@satimis.com>:
64.202.166.11 does not like recipient.
Remote host said: 553 sorry, relaying denied from your location 
[66.163.179.83] (#5.7.1)
Giving up on 64.202.166.11.

```

$ whois 64.202.166.11```

OrgName:    Go Daddy Software
OrgID:      GDS-31
Address:    14455 N Hayden Road
Address:    Suite 226
City:       Scottsdale
StateProv:  AZ
PostalCode: 85260
Country:    US

NetRange:   64.202.160.0 - 64.202.191.255
CIDR:       64.202.160.0/19
NetName:    GO-DADDY-SOFTWARE-INC
NetHandle:  NET-64-202-160-0-1
Parent:     NET-64-0-0-0-0
NetType:    Direct Allocation
NameServer: CNS1.SECURESERVER.NET
NameServer: CNS2.SECURESERVER.NET
Comment:
RegDate:    2002-10-22
Updated:    2004-05-24
.....

```

"64.202.166.11" refers to Godaddy, the Registrant


Total DNS Control on godaddy.com site
```

CNAMES (Aliases)  	 	
Host		Points To			           TTL			Actions
email 		email.satimis.com 		3600
mail 		 pop.satimis.com 		   3600	
webmail      webmail.satimis.com 	  3600	
smtp 		smtp.satimis.com 		3600	
pop 		  pop.satimis.com 		   3600	
e 		    email.satimis.com 		     3600	
www 		@ 				                3600	
mobilemail 	mobilemail-v01.prod.mesa1.secureserver.net 	 3600
pda 		       mobilemail-v01.prod.mesa1.secureserver.net 	3600	
ftp 		         @ 					                                                    3600
	
MX (Mail Exchange)  	 	
Priority	Host	Goes To			                              TTL		Actions
0 		    @ 	      smtp.satimis.com 		                  3600
10 		   @        mailstore1.secureserver.net 	3600
	
TXT (Text)

```

Please help.  Where I shall look up.  TIA


B.R.
satimis

---

### Post by renaissance on 2007-01-18
First you have to take a look your postfix.cf file.
Use pico /etc/postfix/main.cf
if you use Maildir or mbox you have go got lines like:
If you use Maildir
default_mail_env = maildir:~/Maildir (for maildir)
or
If you use Mbox
default_mail_env = mbox:~/mail:INBOX=/var/mail/%u (for mbox)
If you havent got then write them.

and also you have to take a look what is your hostname in Postfix conf.
It have to be same what you write in Postfix install!
myhostname = server1.example.com

---

### Post by satimis on 2007-01-18
Hi renaissance,

Tks for your advice.

> 
First you have to take a look your postfix.cf file.
Use pico /etc/postfix/main.cf
if you use Maildir or mbox you have go got lines like:
If you use Maildir
default_mail_env = maildir:~/Maildir (for maildir)
or
If you use Mbox
default_mail_env = mbox:~/mail:INBOX=/var/mail/%u (for mbox)
If you havent got then write them.

$ cat /etc/postfix/main.cf | grep Maildir```

home_mailbox = Maildir/

```
Changed the line as;```

default_mail_env = maildir:~/Maildir
[code]

> 
and also you have to take a look what is your hostname in Postfix conf.
It have to be same what you write in Postfix install!
myhostname = server1.example.com
I can't recall what has been typed on installing Postfix.  Besides it has been changed several times because first running "dynamic IP + subdomain" and now "static IP + domain"

$ cat /etc/postfix/main.cf[code]
.....
#myhostname = server1.example.com
#myhostname = mail.satimis.freeddns.com
#myhostname = satimis.homelinux.com
myhostname = mail.satimis.com
.......

```


$ sudo /etc/init.d/postfix restart```

 * Stopping Postfix Mail Transport Agent postfix                         [ ok ]
 * Starting Postfix Mail Transport Agent postfix                         [ ok ]

```


Sent another mail from yahoo.com to [email]satimis@satimis.com[/email]

Still the same```

<satimis@satimis.com>:
64.202.166.11 does not like recipient.
Remote host said: 553 sorry, relaying denied from your location 
[66.163.179.91] (#5.7.1)
Giving up on 64.202.166.11.

```
It referred to the IP address of godaddy.com.  Any advice?  TIA


B.R.
satimis

---

### Post by MJN on 2007-01-18
Ensure you have **mydomain** set to your domain (satimis.com by the looks of things?) and also that **mydestination** includes the **$mydomain** variable (e.g. **mydestination = $localhost, $myhostname, $mydomain**).
 
If that doesn't work post your **postconf -n** output and we can take a look.
 
Mathew

---

### Post by satimis on 2007-01-18
Hi Mathew,

> 
Ensure you have **mydomain** set to your domain (satimis.com by the looks of things?) and also that **mydestination** includes the **$mydomain** variable (e.g. **mydestination = $localhost, $myhostname, $mydomain**).

$ cat /etc/postfix/main.cf | grep mydestination```

#mydestination = /etc/postfix/local-host-names
mydestination = $myhostname, localhost.$mydomain, localhost

```
changed the line as;```

mydestination = $localhost, $myhostname, $mydomain

```

Sent a test mail from another network to [email]satimis@satimis.com[/email].  Still failed with following warning;```

<satimis@satimis.com>:
64.202.166.11 does not like recipient.
Remote host said: 553 sorry, relaying denied from your location 
[66.163.179.80] (#5.7.1)
Giving up on 64.202.166.11

```

$ sudo postconf -n
Password:```

alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
mailbox_command =
mailbox_size_limit = 0
mydestination = $localhost, $myhostname, $mydomain
mydomain = satimis.com
myhostname = mail.satimis.com
mynetworks = 127.0.0.0/8, 192.168.0.0/24
myorigin = $myhostname
recipient_delimiter = +
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

```

On following line;```

mynetworks = 127.0.0.0/8, 192.168.0.0/24

```
Shall I make any change?  The Virtual IP on the router for the server is "192.168.0.10" and the fixed/static IP is "220.232.213.178"

TIA


B.R.
satimis






 
If that doesn't work post your **postconf -n** output and we can take a look.
 
[/QUOTE]

---

### Post by MJN on 2007-01-18
Did you reload/restart Postfix after making the change?
 
(I'd like to rule this out before going through your config)
 
Also, do you mail logs provide any more info?
 
Mathew

---

### Post by satimis on 2007-01-18
Hi Mathew,

> 
Did you reload/restart Postfix after making the change?
 
(I'd like to rule this out before going through your config)

Yes, I ran;
$ sudo /etc/init.d/postfix restart```

Password:
 * Stopping Postfix Mail Transport Agent postfix                         [ ok ]
 * Starting Postfix Mail Transport Agent postfix                         [ ok ]

```

>  
Also, do you mail logs provide any more info?

$ tail -f /var/log/mail.log```

Jan 18 14:51:20 mail postfix/cleanup[5651]: 3B029754050: message-id=<20070118065120.3B029754050@mail.satimis.com >
Jan 18 14:51:20 mail postfix/qmgr[5446]: 3B029754050: from=<root@mail.satimis.com>, size=557, nrcpt=1 (queue act ive)
Jan 18 14:51:20 mail postfix/local[5653]: 3B029754050: to=<satimis@mail.satimis.com>, orig_to=<root>, relay=loca l, delay=0, status=sent (delivered to maildir)
Jan 18 14:51:20 mail postfix/qmgr[5446]: 3B029754050: removed
Jan 18 17:28:16 mail postfix/master[4883]: terminating on signal 15
Jan 18 17:28:17 mail postfix/master[6251]: daemon started -- version 2.2.10, configuration /etc/postfix
Jan 18 19:11:21 mail postfix/master[6251]: terminating on signal 15
Jan 18 19:11:22 mail postfix/master[6635]: daemon started -- version 2.2.10, configuration /etc/postfix
Jan 18 21:32:48 mail postfix/master[6635]: terminating on signal 15
Jan 18 21:32:49 mail postfix/master[7034]: daemon started -- version 2.2.10, configuration /etc/postfix

```

What I can't resolve is on the warning of the returned mail;```

<satimis@satimis.com>:
64.202.166.11 does not like recipient.
Remote host said: 553 sorry, relaying denied from your location 
[66.163.179.84] (#5.7.1)
Giving up on 64.202.166.11.

```
It always referred to the IP address of godaddy.com


B.R.
satimis

---

### Post by MJN on 2007-01-18
But what do the logs say when your message fails? (the snippet you posted is a successfull delivery)
 
Mathew

---

### Post by satimis on 2007-01-18
> **MJN said:**
> But what do the logs say when your message fails? (the snippet you posted is a successfull delivery)

Hi Mathew,

Oh, I see.

I sent a webmail direct from Yahoo site to [email]satimis@satimis.com[/email].  the mail was rejected immediately.  I suppose it won't arrive my server.

B.R.
satimis

---

### Post by MJN on 2007-01-18
I just checked out your DNS for satimis.com - it's screwed:
 
satimis.com IN MX 0 smtp.satimis.com (okay, that's fine)
smtp.satimis.com IN CNAME smtp.satimis.com (that's not fine - any lookup on this will loop)
 
Given the loop you'll get failures at best and unpredictable errors at arguably worst.
 
Hence, you need to either delete your CNAME and replace it with an A record pointing to your IP address, or configure the CNAME to point at whatever permanent name your IP may currently have.
 
Mathew
 
P.S. I just sent you a test message directly and your server's now accepting e-mail fine - however until the DNS is fixed this won't work for everyone else.

---

### Post by satimis on 2007-01-18
Hi Mathew,

>  
Hence, you need to either delete your CNAME and replace it with an A record pointing to your IP address, or configure the CNAME to point at whatever permanent name your IP may currently have.

I deleted the whole line.  It did not, sending mail to [email]satimis@satimis.com[/email] still failed.  Now I recreated the line

Host     Pointing To
smtp  	smtp.satimis.com

How to change them?   TIA.

Others noted with tks.


B.R.
satimis

---

### Post by MJN on 2007-01-18
I'm not familiar with the GoDaddy interface so if you could post a screenshot that would help.
 
The bottom line, however, is that you should not be using any CNAMEs at all.
 
Mathew

---

### Post by satimis on 2007-01-18
> **MJN said:**
> 
The bottom line, however, is that you should not be using any CNAMEs at all.

Sorry I don't follow.

ScreenShot attached.  Tks.

satimis

---

### Post by MJN on 2007-01-18
A CNAME is effectively an alias which states that whatever is on the left-hand side is another name for what's on the right (so go look that up instead).

To backstep briefly, the screenshot is effectively your satamis.com zonefile with all the entries in it. The first entry, @, basically means same-as-parent and hence it means 'satimis.com' (if you'd put satismis.com in here it would mean satimis.com.satimis.com as everything is suffixed with the zone origin - satimis.com). This entry is correct.

The www and ftp CNAMEs are also correct - it's simply saying that [www.satimis.com](www.satimis.com) is another name for @ so look that up instead (which it does as per the first line). Likewise, pda and mobilemail are also likely correct as you've said they're other names for mobilemail...etc.

However, the rest of the CNAME entries are wrong - each one is referring to itself whereas you intended them to refer to your IP (as defined by @). These are all loops (and it's a shame the GD interface doesn't pick up on these). Hence, remove them and replace them with either 'smtp points to @' (to use GD's terminology) etc or even simply '* points to @'. This latter config effectively acts as a catchall so if there is no more-specific match (e.g. like there would be if someone looked up pda.samitis.com) then resolve it to whatever @ is pointing at, i.e. your IP.

Mathew

---

### Post by satimis on 2007-01-18
Hi Mathew,

Tks for your datailed advice.  Now problem solved.  Mails received from Yahoo.com went to one/single master file named "satimis" on /var/mail/satimis

New screenshot of Godaddy's DNS Contorl Panel attached.

> 
Hence, remove them and replace them with either 'smtp points to @' (to use GD's terminology) etc or even simply '* points to @'. This latter config effectively acts as a catchall so if there is no more-specific match (e.g. like there would be if someone looked up pda.samitis.com) then resolve it to whatever @ is pointing at, i.e. your IP.

I was not allowed to edit as```

Enter an Alias Name: *
Points To Host Name: @

```
Godaddy complained;```

Please enter a valid host name for the Alias Name field.

```

Please advise how to edit Postfix so that mails received will not go into one master file but retained separately?  How to create mail boxes for other persons so that mails to "aaa@satimis.com", "bbb@satimis.com", etc. will go to their mail boxes.(NOT as a single file)  TIA

B.R.
satimis

---

### Post by MJN on 2007-01-19
> **satimis said:**
> Hi Mathew,
 
Tks for your datailed advice. Now problem solved. Mails received from Yahoo.com went to one/single master file named "satimis" on /var/mail/satimis
 
Glad to hear it.
 
> 
I was not allowed to edit as[code]
Enter an Alias Name: *
Points To Host Name: @

 
A brief web search seems to suggest that GoDaddy don't currently support DNS wildcards (not sure why) but that they are planning on allowing them 'soon' (this was back in December).
 
> Please advise how to edit Postfix so that mails received will not go into one master file but retained separately? How to create mail boxes for other persons so that mails to "aaa@satimis.com", "bbb@satimis.com", etc. will go to their mail boxes.(NOT as a single file) TIA
 
Well I have individual user accounts (on the system) hence all mail is directed to the appropriate system account.
 
I hope this doesn't sound like sloping shoulders but you would do well to read the Postfix documentation - there is plenty of good stuff at [www.postfix.org]("http://www.postfix.org") where not only will you find the answer to your questions but learn a lot more besides too!
 
Of course, a quick fix is always nice, but the old adage 'teach a man to fish....' is particularly apt here.
 
Mathew

---

### Post by satimis on 2007-01-19
Hi Mathew,

Tks for your advice and URL

I have a collection of relevant document but non for Ubuntu.  A very nice document about setup:-
Virtual Mail Server 
Postfix + PostfixAdmin + MySQL + Apache2 + PHP4 + PHP4-Session + Cyrus-sasl + Courier-imap + Maildrop + Squirrelmail
was found from a Taiwan site but for FreeBSD.  I shall follow it to see what will happen.

Tks.


B.R.
satimis

---

