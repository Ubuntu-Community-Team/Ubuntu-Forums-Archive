---
title: "Email Server"
date: 2012-08-01
forum: Server Platforms
---

### Post by cesar98026 on 2012-08-01
Hello! I am starting a webmail company and got my email server set up (pretty basic at the moment). However, I ran into a problem :( My ISP blocks port 25! I can send mail but not receive it... My setup is Courier, Postfix, and Roundcube on Ubuntu Server 12.04 LTS. I followed this how-to: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) I'm have a Dell PowerEdge 2850. Is there anyway to get past this block? My site at [http://www.emailyourafriend.com/](http://www.emailyourafriend.com/) Make sure you like it :popcorn:

---

### Post by HermanAB on 2012-08-01
You ordered the wrong account type from your ISP.

Ask them for a 'small business server' account.  It will cost a few dollars more and all the ports will be available.

---

### Post by lisati on 2012-08-01
I had a similar problem because my ISP blocks port 25 by default for normal home connections. What I ended up doing was ordering a static IP address, after which port 25 could be unblocked. One thing to be aware of is that depending on your ISP, this can cost extra each month.

---

### Post by a2j on 2012-08-01
Some ISPs offer a relay servers. Works great with a residential Internet account.

---

### Post by SeijiSensei on 2012-08-01
If yuu're starting an Internet-based business, then you need a business-level account from your ISP.  It's as simple as that.  Depending on the cost of upgrading your connection, you might be better off renting a virtual server from some place like [Linode]("http://www.linode.com/") at $20/month and hosting your services there.

While I have your attention, I don't see anything in your list of software that includes spam and virus scanning for email.  You *are* planning on filtering all the mail for spam and viruses, right?  I use [MailScanner]("http://www.mailscanner.info/") in combination with ClamAV and SpamAssassin, with a lot of custom rules for the latter.

If I were your customer, and you delivered an email to me with an attached executable, I would not be your customer any longer.

---

### Post by nbetham on 2012-08-01
I know Bright House Networks offers relays servers and it is pretty easy to setup outgoing mail to access them, you just have to do some google-fu to find out where they are. If I remember correctly, unless you have a properly setup domain some mail servers won't accept mail from providers that aren't properly listed or aren't proven not to be spamming servers. Another option you could use is an external relay service like [http://dyn.com/email/](http://dyn.com/email/) They will provide a certain number of relays a day for decently low cost. It really all depends on what you want to pay and how you want the system setup.

---

### Post by cesar98026 on 2012-08-01
I think I might go with a business account, but it seems expensive (I don't have a big budget :( ). But virtual servers seems more promising to me. Does anybody have experience with Amazon EC2? Also I do have some spam scanning ninjas too :rolleyes:

---

### Post by sandyd on 2012-08-01
> **cesar98026 said:**
> I think I might go with a business account, but it seems expensive (I don't have a big budget :( ). But virtual servers seems more promising to me. Does anybody have experience with Amazon EC2? Also I do have some spam scanning ninjas too :rolleyes:
Their micro instance CPU allocation is jittery. Don't use it if you can avoid it :|. The small instances, and everything else is fine tho

Either use rackspace cloud, or look up reputable providers at somewhere like WHT

Hivelocity is doing 1GB RAM instances for 35/mo. [https://www.sparknode.com/order/cart/&step=3](https://www.sparknode.com/order/cart/&step=3)
Gigenet does $20/mo instances [http://www.gigenet.com/cloud-servers/pricing/](http://www.gigenet.com/cloud-servers/pricing/)
Future Hosting does $30/mo instances [http://www.webhostingtalk.com/showthread.php?t=1171442](http://www.webhostingtalk.com/showthread.php?t=1171442)

There is a lot more here: [http://www.webhostingtalk.com/forumdisplay.php?f=104&sort=threadstarted&order=desc](http://www.webhostingtalk.com/forumdisplay.php?f=104&sort=threadstarted&order=desc)

btw, you could simply just use Google Apps (community edition) or Windows Live Domains for mail.

---

### Post by SeijiSensei on 2012-08-02
I really, really, really like [Linode]("http://www.linode.com/").  Their prices are competitive, their staff is competent and helpful, and they have a variety of online tools you can use to access your machine.  Even if you make an iptables error, for instance, you won't be locked out of the machine because you can use their web-based shell client. You have your pick of hosting locations as well.  I have one server in New Jersey and one in California.  Both do DNS so I'm protected against outages in one location or the other.  (Not that I've experienced even a moment of downtime in two years.)  There are other locations available outside the US as well.

---

### Post by d4m1r on 2012-08-02
If you are on a real budget, [123systems.net]("https://123systems.net/billing/aff.php?aff=709") has linux VPS available for $3/month that should be more than powerful enough to run an email server....I personally use them for my own website and couldn't be more satisfied :D

---

### Post by cesar98026 on 2012-08-14
I went with Linode and I'm happy! However I got this in log: Aug 14 22:26:31 li519-49 postfix/master[4258]: fatal: bind 27.0.0.1 port 10025: Cannot assign requested address

---

### Post by SeijiSensei on 2012-08-14
You're missing an initial "1" in 127.0.0.1.

Glad you're happy with Linode!  Enjoy!

---

### Post by cesar98026 on 2012-08-14
> **SeijiSensei said:**
> You're missing an initial "1" in 127.0.0.1.

Glad you're happy with Linode!  Enjoy!

Yeah I figured that out right after posting. But I got it working!!! I need to figure how people are going to sign up for this :( I know how to add a user in the database but how can I have the users make their own accounts? :confused:

---

### Post by SeijiSensei on 2012-08-15
I just create standard Unix accounts for my half-dozen users.  Your configuration seems to use a database backend for accounts.  If so, you could write a set of PHP applications to enable people to create accounts online.  You'll have to be vigilant about monitoring them, though, since you'll find spammers signing up to exploit your service.

Again, I strongly recommend that you apply virus and spam scanning to every message you process, both inbound and outbound.  Remember that you cannot trust your users.

---

### Post by cesar98026 on 2012-08-15
> **SeijiSensei said:**
> I just create standard Unix accounts for my half-dozen users.  Your configuration seems to use a database backend for accounts.  If so, you could write a set of PHP applications to enable people to create accounts online.  You'll have to be vigilant about monitoring them, though, since you'll find spammers signing up to exploit your service.

Again, I strongly recommend that you apply virus and spam scanning to every message you process, both inbound and outbound.  Remember that you cannot trust your users.
I'm a newbie and followed flurdy's guide, I don't know if I have scanning on inbound and outbound? But I changed roundcube's port setting to 465 and now when I try to send emails it says this: SMTP Error (554): Failed to add recipient "example@gmail.com" (5.7.1 <localhost[127.0.0.1]>: Client host rejected: Access denied).
I have smtps enabled in Postfix too.
And what should I use as a relayhost? I was thinking of Google's smtp server.

---

### Post by SeijiSensei on 2012-08-15
> **cesar98026 said:**
> I'm a newbie and followed flurdy's guide, I don't know if I have scanning on inbound and outbound? But I changed roundcube's port setting to 465 and now when I try to send emails it says this: SMTP Error (554): Failed to add recipient "example@gmail.com" (5.7.1 <localhost[127.0.0.1]>: Client host rejected: Access denied).

It sounds like it's still trying to send mail via port 25.  I've never used roundcube, only SquirrelMail, so I can't help with that.  I also use MailScanner rather than amavis-new though it seems likely that it will scan messages in both directions.  Try forwarding a spam you have lying around to the machine and see what happens.  Then try sending the spam outbound by copying and pasting the spam message into roundcube.

Next get a copy of the eicar.com test virus from [here](http://eicar.org/85-0-Download.html) and send it both to and from the server.  It should be flagged both ways and the message deleted or (better) quarantined depending on how you have things set up.

> And what should I use as a relayhost? I was thinking of Google's smtp server.

You don't need a relay host if the server is sitting on a Linode VM. Mail will be sent directly to the recipients' SMTP servers. Make sure you set the reverse DNS entry for your IP address to match the hostname of the server.  If your server is mail.example.com on 10.10.10.10, then the reverse entry for 10.10.10.10 should point to mail.example.com.  In the Linode Manager, choose "Remote Access" then follow the link for Reverse DNS.

---

### Post by cesar98026 on 2012-08-15
Oh yeah my anti-spam ninjas worked with the eicar.com file.

 15 19:44:23 li519-49 amavis[2869]: (02869-03) p.path BANNED:1 [email]something@gmail.com[/email]: "P=p003,L=1,M=multipart/mixed | P=p002,L=1/2,M=text/plain,T=asc,N=eicar.com", matching_key="(?^i:.\\.(exe|vbs|pif|scr|bat|cmd|com|cpl)$)"
Aug 15 19:44:23 li519-49 amavis[2869]: (02869-03) run_av (ClamAV-clamd): /var/lib/amavis/tmp/amavis-20120815T191147-02869/parts INFECTED: Eicar-Test-Signature
Aug 15 19:44:23 li519-49 amavis[2869]: (02869-03) virus_scan: (Eicar-Test-Signature), detected by 1 scanners: ClamAV-clamd
Aug 15 19:44:23 li519-49 amavis[2869]: (02869-03) checking/creating quarantine subdirs under /var/lib/amavis/virusmails/
Aug 15 19:44:23 li519-49 amavis[2869]: (02869-03) local delivery: <cesar@emailyourafriend.com> -> virus-quarantine, mbx=/var/lib/amavis/virusmails/K/virus-KJ4-dVrsFRMe
Aug 15 19:44:23 li519-49 amavis[2869]: (02869-03) Blocked INFECTED (Eicar-Test-Signature), LOCAL [127.0.0.1] [127.0.0.1] <cesar@emailyourafriend.com> -> <something@gmail.com>, quarantine: K/virus-KJ4-dVrsFRMe, Message-ID: <f8e8e52b7222829293f149b73a4eacc9@emailyourafriend.com>, mail_id: KJ4-dVrsFRMe, Hits: -, size: 1013, 365 ms

I think thats good. But when I try to telnet localhost 465 I connect then when I ehlo server1.emailyourafriend.com it disconnects? I think SMTPs isn't working. I sent a spam email I had lying around and it got passed inbound and outbound :( Also how do you post code here so it's not so big, like a config file? :popcorn:

---

### Post by cesar98026 on 2012-08-17
:confused::( Brute force SSH attacks on my server... ```
 11:35:51 li519-49 sshd[16882]: input_userauth_request: invalid user mp3 [preauth]
Aug 17 11:35:51 li519-49 sshd[16882]: pam_unix(sshd:auth): check pass; user unknown
Aug 17 11:35:51 li519-49 sshd[16882]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.51.85.115 
Aug 17 11:35:53 li519-49 sshd[16882]: Failed password for invalid user mp3 from 200.51.85.115 port 51019 ssh2
Aug 17 11:35:53 li519-49 sshd[16882]: Received disconnect from 200.51.85.115: 11: Bye Bye [preauth]
Aug 17 11:35:55 li519-49 sshd[16884]: Invalid user mp3 from 200.51.85.115
Aug 17 11:35:55 li519-49 sshd[16884]: input_userauth_request: invalid user mp3 [preauth]
Aug 17 11:35:55 li519-49 sshd[16884]: pam_unix(sshd:auth): check pass; user unknown
Aug 17 11:35:55 li519-49 sshd[16884]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.51.85.115 
Aug 17 11:35:56 li519-49 sshd[16884]: Failed password for invalid user mp3 from 200.51.85.115 port 51306 ssh2
Aug 17 11:35:57 li519-49 sshd[16884]: Received disconnect from 200.51.85.115: 11: Bye Bye [preauth]
Aug 17 11:35:58 li519-49 sshd[16886]: Invalid user mp3 from 200.51.85.115
Aug 17 11:35:58 li519-49 sshd[16886]: input_userauth_request: invalid user mp3 [preauth]
Aug 17 11:35:58 li519-49 sshd[16886]: pam_unix(sshd:auth): check pass; user unknown
Aug 17 11:35:58 li519-49 sshd[16886]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.51.85.115 
Aug 17 11:36:00 li519-49 sshd[16886]: Failed password for invalid user mp3 from 200.51.85.115 port 51588 ssh2
Aug 17 11:36:00 li519-49 sshd[16886]: Received disconnect from 200.51.85.115: 11: Bye Bye [preauth]
Aug 17 11:36:02 li519-49 sshd[16888]: Invalid user emilie from 200.51.85.115
Aug 17 11:36:02 li519-49 sshd[16888]: input_userauth_request: invalid user emilie [preauth]
Aug 17 11:36:02 li519-49 sshd[16888]: pam_unix(sshd:auth): check pass; user unknown
Aug 17 11:36:02 li519-49 sshd[16888]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.51.85.115 
Aug 17 11:36:04 li519-49 sshd[16888]: Failed password for invalid user emilie from 200.51.85.115 port 51880 ssh2
Aug 17 11:36:04 li519-49 sshd[16888]: Received disconnect from 200.51.85.115: 11: Bye Bye [preauth]
Aug 17 11:36:06 li519-49 sshd[16890]: Invalid user emilie from 200.51.85.115
Aug 17 11:36:06 li519-49 sshd[16890]: input_userauth_request: invalid user emilie [preauth]
Aug 17 11:36:06 li519-49 sshd[16890]: pam_unix(sshd:auth): check pass; user unknown
Aug 17 11:36:06 li519-49 sshd[16890]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.51.85.115 
Aug 17 11:36:08 li519-49 sshd[16890]: Failed password for invalid user emilie from 200.51.85.115 port 52179 ssh2
Aug 17 11:36:08 li519-49 sshd[16890]: Received disconnect from 200.51.85.115: 11: Bye Bye [preauth]
Aug 17 11:36:10 li519-49 sshd[16892]: Invalid user emilie from 200.51.85.115
Aug 17 11:36:10 li519-49 sshd[16892]: input_userauth_request: invalid user emilie [preauth]
Aug 17 11:36:10 li519-49 sshd[16892]: pam_unix(sshd:auth): check pass; user unknown
Aug 17 11:36:10 li519-49 sshd[16892]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.51.85.115 
Aug 17 11:36:11 li519-49 sshd[16892]: Failed password for invalid user emilie from 200.51.85.115 port 52427 ssh2
Aug 17 11:36:12 li519-49 sshd[16892]: Received disconnect from 200.51.85.115: 11: Bye Bye [preauth]
Aug 17 11:36:13 li519-49 sshd[16894]: Invalid user emilie from 200.51.85.115
Aug 17 11:36:13 li519-49 sshd[16894]: input_userauth_request: invalid user emilie [preauth]
Aug 17 11:36:13 li519-49 sshd[16894]: pam_unix(sshd:auth): check pass; user unknown
Aug 17 11:36:13 li519-49 sshd[16894]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.51.85.115 
Aug 17 11:36:15 li519-49 sshd[16894]: Failed password for invalid user emilie from 200.51.85.115 port 52720 ssh2
Aug 17 11:36:15 li519-49 sshd[16894]: Received disconnect from 200.51.85.115: 11: Bye Bye [preauth]
Aug 17 11:36:17 li519-49 sshd[16896]: Invalid user emilie from 200.51.85.115
Aug 17 11:36:17 li519-49 sshd[16896]: input_userauth_request: invalid user emilie [preauth]
Aug 17 11:36:17 li519-49 sshd[16896]: pam_unix(sshd:auth): check pass; user unknown
Aug 17 11:36:17 li519-49 sshd[16896]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.51.85.115 
Aug 17 11:36:19 li519-49 sshd[16896]: Failed password for invalid user emilie from 200.51.85.115 port 53017 ssh2
Aug 17 11:36:20 li519-49 sshd[16896]: Received disconnect from 200.51.85.115: 11: Bye Bye [preauth]
Aug 17 11:36:21 li519-49 sshd[16898]: Invalid user emilie from 200.51.85.115
Aug 17 11:36:21 li519-49 sshd[16898]: input_userauth_request: invalid user emilie [preauth]
Aug 17 11:36:21 li519-49 sshd[16898]: pam_unix(sshd:auth): check pass; user unknown
Aug 17 11:36:21 li519-49 sshd[16898]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.51.85.115 
Aug 17 11:36:23 li519-49 sshd[16898]: Failed password for invalid user emilie from 200.51.85.115 port 53312 ssh2
Aug 17 11:36:23 li519-49 sshd[16898]: Received disconnect from 200.51.85.115: 11: Bye Bye [preauth]
Aug 17 11:36:25 li519-49 sshd[16900]: Invalid user emilie from 200.51.85.115
Aug 17 11:36:25 li519-49 sshd[16900]: input_userauth_request: invalid user emilie [preauth]
Aug 17 11:36:25 li519-49 sshd[16900]: pam_unix(sshd:auth): check pass; user unknown
Aug 17 11:36:25 li519-49 sshd[16900]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.51.85.115 
Aug 17 11:36:27 li519-49 sshd[16900]: Failed password for invalid user emilie from 200.51.85.115 port 53605 ssh2
Aug 17 11:36:27 li519-49 sshd[16900]: Received disconnect from 200.51.85.115: 11: Bye Bye [preauth]
Aug 17 11:36:29 li519-49 sshd[16902]: Invalid user emilie from 200.51.85.115
Aug 17 11:36:29 li519-49 sshd[16902]: input_userauth_request: invalid user emilie [preauth]
Aug 17 11:36:29 li519-49 sshd[16902]: pam_unix(sshd:auth): check pass; user unknown
Aug 17 11:36:29 li519-49 sshd[16902]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.51.85.115 
Aug 17 11:36:31 li519-49 sshd[16902]: Failed password for invalid user emilie from 200.51.85.115 port 53899 ssh2
Aug 17 11:36:31 li519-49 sshd[16902]: Received disconnect from 200.51.85.115: 11: Bye Bye [preauth]
Aug 17 11:36:33 li519-49 sshd[16904]: Invalid user emilie from 200.51.85.115
Aug 17 11:36:33 li519-49 sshd[16904]: input_userauth_request: invalid user emilie [preauth]
Aug 17 11:36:33 li519-49 sshd[16904]: pam_unix(sshd:auth): check pass; user unknown
Aug 17 11:36:33 li519-49 sshd[16904]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.51.85.115 
Aug 17 11:36:35 li519-49 sshd[16904]: Failed password for invalid user emilie from 200.51.85.115 port 54203 ssh2
Aug 17 11:36:35 li519-49 sshd[16904]: Received disconnect from 200.51.85.115: 11: Bye Bye [preauth]
Aug 17 11:36:37 li519-49 sshd[16906]: Invalid user emilie from 200.51.85.115
Aug 17 11:36:37 li519-49 sshd[16906]: input_userauth_request: invalid user emilie [preauth]
Aug 17 11:36:37 li519-49 sshd[16906]: pam_unix(sshd:auth): check pass; user unknown
Aug 17 11:36:37 li519-49 sshd[16906]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.51.85.115 
Aug 17 11:36:39 li519-49 sshd[16906]: Failed password for invalid user emilie from 200.51.85.115 port 54498 ssh2
Aug 17 11:36:39 li519-49 sshd[16906]: Received disconnect from 200.51.85.115: 11: Bye Bye [preauth]
Aug 17 11:36:41 li519-49 sshd[16908]: Invalid user emilie from 200.51.85.115
Aug 17 11:36:41 li519-49 sshd[16908]: input_userauth_request: invalid user emilie [preauth]
Aug 17 11:36:41 li519-49 sshd[16908]: pam_unix(sshd:auth): check pass; user unknown
Aug 17 11:36:41 li519-49 sshd[16908]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.51.85.115 
Aug 17 11:36:43 li519-49 sshd[16908]: Failed password for invalid user emilie from 200.51.85.115 port 54791 ssh2
Aug 17 11:36:43 li519-49 sshd[16908]: Received disconnect from 200.51.85.115: 11: Bye Bye [preauth]
Aug 17 11:39:01 li519-49 CRON[16910]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 17 11:39:01 li519-49 CRON[16910]: pam_unix(cron:session): session closed for user root
Aug 17 11:45:01 li519-49 CRON[16917]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 17 11:45:01 li519-49 CRON[16917]: pam_unix(cron:session): session closed for user root
```
:confused: How do I know if they got in? What should I do about this? Also I got it working correctly!

---

### Post by d4m1r on 2012-08-17
Install fail2ban.

---

### Post by SeijiSensei on 2012-08-18
If you know the IP addresses from which you will be connecting to your server with SSH, just add an iptables rules that allows those addresses and blocks everyone else.  

If you want the ability to connect from anywhere, I suggest using a non-standard port for SSH, or setting up an OpenVPN tunnel using a [shared key]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html").

---

### Post by cesar98026 on 2012-08-21
Ok, will do. But when someone signs up for my webmail, they can't log in right away because I have to send them a welcome email to create their mailbox. Is there a way to automatically send a welcome email to new users?

---

### Post by SeijiSensei on 2012-08-22
> **cesar98026 said:**
> Ok, will do. But when someone signs up for my webmail, they can't log in right away because I have to send them a welcome email to create their mailbox. Is there a way to automatically send a welcome email to new users?

As I said, before:

> **SeijiSensei said:**
> Your configuration seems to use a database backend for accounts.  If so, you could write a set of PHP applications to enable people to create accounts online.

I don't know how you intend to have them sign up online without writing some type of forms-processing application.  It sounds like you also expect them to have an email address somewhere else already; otherwise where would you send the welcome notice?

---

### Post by cesar98026 on 2012-08-23
> **SeijiSensei said:**
> As I said, before:



I don't know how you intend to have them sign up online without writing some type of forms-processing application.  It sounds like you also expect them to have an email address somewhere else already; otherwise where would you send the welcome notice?
I already have a online form for signing up, but before any mailbox is created they have to have a email sent to their @emailyourafriend.com address to create the mailbox. Even if you manually put the entries in the mail database, their mailboxes arn't created. Is there a way around this? Does postfix or courier handle mailbox creation? :guitar:

---

### Post by cesar98026 on 2012-08-28
> **cesar98026 said:**
> I already have a online form for signing up, but before any mailbox is created they have to have a email sent to their @emailyourafriend.com address to create the mailbox. Even if you manually put the entries in the mail database, their mailboxes arn't created. Is there a way around this? Does postfix or courier handle mailbox creation? :guitar:
 I really, really feel like a dummy. I underestimated PHP... The simple mail() function! So when somebody signs up a welcome email is automatically sent to their @emailyourafriend.com address to create the mailbox!
:p

---

### Post by cesar98026 on 2012-11-21
A few months after I got it figured out, something went wrong! 
This is the code I got: 
mail.php
[PHP]<?php
 $to = "$fname@emailyourafriend.com";
 $subject = "Welcome!";
 $message = "Hello! blah....";
 $from = "ask@emailyourafriend.com";
 $headers = "From: The EmailFriend Team" . $from;
 mail($to,$subject,$message,$headers);
 echo "Mail Sent.";
 ?>[/PHP]
This is not working, or maybe it is... It's not sending emails. In the mail.log, I got this:
postfix/sendmail[22306]: fatal: Recipient addresses must be specified on the command line or via the -t option

However, if I make a simple mail() php script using an existing email address, it works!
This is what is including it:
[PHP]<?php

session_start();

include('connection.php');
include('mail.php');

$fname=$_POST['fname'];

$lname=$_POST['lname'];

$address=$_POST['address'];

mysql_query("INSERT INTO users(id, name, maildir, crypt)VALUES('$fname@emailyourafriend.com', '$lname', '$fname/', ENCRYPT('$address') );");
mysql_query("INSERT INTO aliases (mail,destination) VALUES
	('$fname@emailyourafriend.com','$fname@emailyourafriend.com') );");

header("location: index.php?remarks=success");

mysql_close($con);
:confused:
 
?>[/PHP]
It does enter stuff into the database but not sending the emails!

---

### Post by SeijiSensei on 2012-11-21
> **cesar98026 said:**
> ```

$from = "ask@emailyourafriend.com";
$headers = "From: The EmailFriend Team" . $from;

```

I don't know if this is the problem, but the From header this generates does not comply with the standard.  The email address must be enclosed in angle brackets:

```

$headers = "From: The EmailFriend Team <".$from.">";

```

---

### Post by cesar98026 on 2012-11-21
I fixed it by adding a line in php.ini.... I was locking down my server more and came across S/MIME. I was wondering if I should implement S/MIME in my email service? I already have things like TLS and SASL, etc. Also, do you have any suggestions for more security? How do I get clear passwords out of mail.log?

---

