---
title: "Postfix not delivering locally: forwards everything thru relayhost"
date: 2006-06-22
forum: Server Platforms
---

### Post by jabster on 2006-06-22
Hi.
 
 I seem to have encountered a bit of a problem with my mail server (k/ubuntu dapper, fresh install).
 
 I was having trouble getting mail to relay thru sbcglobal.net, tho local intranet mail was being delivered just fine. I found some info, and thought all was fixed, as I was able to send mail outside with the changes I made. Now tho, I can not deliver anyting locally. EVERYTHING is being relayed out thru the SBC server. Anything send locally, and everything that fetchmail grabs as well. Nothing is being delivered to my local mailboxes.  If I'm reading the log correctly.

Can anyone offer some help here?
 
 Relevant files are below. If more is needed, just ask.
 
 Thanks,
 john
 
 /etc/postfix/main.cf
```
smtpd_banner = $myhostname ESMTP $mail_name (Kubuntu Dapper Linux)
biff = no
append_dot_mydomain = no
myhostname = icculus.jabster.net
mydomain = jabster.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
#relayhost = 
#mynetworks = 127.0.0.0/8
#mailbox_command = /usr/bin/procmail -a "$EXTENSION"
#mailbox_command = /usr/bin/procmail -Y -a $DOMAIN
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
mynetworks_style = class
relayhost = [smtp.sbcglobal.yahoo.com]
smtp_sasl_auth_enable = yes
smtp_sasl_security_options = 
smtp_sasl_password_maps = hash:/etc/postfix/saslpass
transport_maps = hash:/etc/postfix/transport
```

/var/log/mail.log
```
Jun 22 07:19:11 icculus postfix/smtp[7868]: B56144467A: to=<myaddress@sbcglobal.net>, relay=smtp.sbc.mail.yahoo4.akadns.net[68.142.198.11], delay=2, status=sent (250 ok 1150978749 qp 87418)
Jun 22 07:19:11 icculus postfix/qmgr[7861]: B56144467A: removed
Jun 22 07:19:39 icculus fetchmail[7828]: 1 message for myaddress@sbcglobal.net at pop.sbcglobal.yahoo.com (2031 octets). 
Jun 22 07:19:40 icculus fetchmail[7828]: reading message myaddress@sbcglobal.net@pop-sbc.mail.yahoo4.akadns.net:1 of 1 (1614 octets) 
Jun 22 07:19:40 icculus postfix/smtpd[7864]: connect from localhost.localdomain[127.0.0.1]
Jun 22 07:19:40 icculus postfix/smtpd[7864]: 1CBD34467A: client=localhost.localdomain[127.0.0.1]
Jun 22 07:19:40 icculus postfix/cleanup[7867]: 1CBD34467A: message-id=<200606220719.08922.jabster@jabster.net>
Jun 22 07:19:40 icculus postfix/qmgr[7861]: 1CBD34467A: from=<jabster@jabster.net>, size=2003, nrcpt=1 (queue active)
Jun 22 07:19:40 icculus fetchmail[7828]:  flushed 
Jun 22 07:19:40 icculus postfix/smtpd[7864]: disconnect from localhost.localdomain[127.0.0.1]
Jun 22 07:19:41 icculus postfix/smtp[7868]: 1CBD34467A: to=<johnj@localhost>, relay=smtp.sbc.mail.yahoo4.akadns.net[68.142.198.11], delay=1, status=sent (250 ok 1150978780 qp 75758)
Jun 22 07:19:41 icculus postfix/qmgr[7861]: 1CBD34467A: removed
Jun 22 07:20:00 icculus fetchmail[7828]: terminated with signal 15 
```

---

### Post by lamego on 2006-06-22
What about trying some automated configuration ? Type:
```
  sudo dpkg-reconfigure postfix
```
Select the Internet with Smart relay option, it will asks you for the domains that should be delivered locally.

---

### Post by jabster on 2006-06-23
well that didn't work. Wont send anything at  all.

kmail now tells me that the recipient (johnj@jabster.net) is being rejected by the server. johnj is the account on the server. Log tells me "relay access denied."

If I comment out "mynetworks = 127.0.0.1/8" it sends, but ends up relaying it thru the sbc server.

even if I comment out "relayhost=[..]" in main.cf, I get the "relay access denied" error message.

WTF is going on here? This worked fine on my gentoo box. Something about this setup is just not working correctly. ](*,) 

any other ideas?

-john

---

### Post by MJN on 2006-06-23
The config looks okay (however it's easy to not see the woods from the trees in this sort of situation). Can you confirm that you haven't touched /etc/postfix/master.cf and /etc/postfix/transport?
 
And, more to the point, what steps did you take to solve your initial problem of local mail working, external mail not? Therein obviously the clue as to what is likely to be the problem! Did it involve adding the transport_maps directive? If so, what's in your transport file?
 
Mathew

---

### Post by jabster on 2006-06-23
ok.
local problem solved again. same as last time: I need "jabster.net" on the "mydestination" line. Don't know why that isn't included by default...but oh well.

Problem this time: it's "jabster.net", not "jabster.nt". 

D'oh.

It's amazing what looking at a printed copy can do for ya. :-/

So local works now due to a typo. Which is pretty much far as I got last time. Now I'm heading back to check on relaying.

will report back asap.

And I have not touched master.cf at all.

transport looks like this:
```
* smtp:[smtp.sbcglobal.yahoo.com]
sbcglobal.net smtp:[smtp.sbcglobal.yahoo.com]
.sbcglobal.net smtp:[smtp.sbcglobal.yahoo.com]
```

thx,
john

---

### Post by jabster on 2006-06-23
ok. back to relaying.

i now have this (bold new or uncommented)
```
smtpd_banner = $myhostname ESMTP $mail_name (Kubuntu Dapper Linux)
biff = no
append_dot_mydomain = no
myhostname = icculus.jabster.net
mydomain = jabster.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
**mynetworks = 127.0.0.0/8**
#mailbox_command = /usr/bin/procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
**relayhost = [smtp.sbcglobal.yahoo.com]**
smtp_sasl_auth_enable = yes
smtp_sasl_security_options = 
smtp_sasl_password_maps = hash:/etc/postfix/saslpass
transport_maps = hash:/etc/postfix/transport
```

salspass:```

smtp.sbcglobal.yahoo.com email:pw
smtp-sbc.mail.yahoo.com email:pw
smtp-sbc-v1.mail.vip.sc5.yahoo.com email:pw
smtp.sbc.mail.yahoo4.akadnas.net email:pw
```

here's my error from mail.log:```
Jun 23 21:22:00 icculus postfix/anvil[16142]: statistics: max connection rate 1/60s for (smtp:192.168.100.67) at Jun 23 21:18:38
Jun 23 21:22:00 icculus postfix/anvil[16142]: statistics: max connection count 1 for (smtp:192.168.100.67) at Jun 23 21:18:38
Jun 23 21:22:00 icculus postfix/anvil[16142]: statistics: max cache size 1 at Jun 23 21:18:38
Jun 23 21:22:07 icculus postfix/local[16170]: CEA64446AC: to=<johnj@icculus.jabster.net>, orig_to=<root>, relay=local, delay=11, status=sent (delivered to command: procmail -a "$EXTENSION")
Jun 23 21:22:07 icculus postfix/qmgr[16059]: CEA64446AC: removed
Jun 23 21:23:20 icculus imaplogin: Connection, ip=[::ffff:192.168.100.67]
Jun 23 21:23:20 icculus imaplogin: LOGIN, user=johnj, ip=[::ffff:192.168.100.67], protocol=IMAP
Jun 23 21:23:21 icculus imaplogin: /etc/courier/shared/index: No such file or directory
Jun 23 21:23:22 icculus postfix/smtpd[16185]: connect from unknown[192.168.100.67]
Jun 23 21:23:24 icculus postfix/smtpd[16185]: NOQUEUE: reject: RCPT from unknown[192.168.100.67]: 554 <jabster42@sbcglobal.net>: Relay access denied; from=<jabster@jabster.net> to=<jabster42@sbcglobal.net> proto=ESMTP helo=<[192.168.100.67]>
Jun 23 21:23:24 icculus postfix/smtpd[16185]: disconnect from unknown[192.168.100.67]
Jun 23 21:23:30 icculus imaplogin: LOGOUT, user=johnj, ip=[::ffff:192.168.100.67], headers=0, body=836, time=10, starttls=1
```

Any ideas why relaying is being refused?

thx,
john

---

### Post by ape on 2006-06-24
You may want to add 192.168.100.0/24 to your mynetworks line.  Currently the only network that it detects as local is 127.0.0.0/8.

---

### Post by MJN on 2006-06-24
[quote=jabster]ok.
local problem solved again. same as last time: I need "jabster.net" on the "mydestination" line. Dn't know why that isn't included by default...but oh well.[/quote] 
It is included by virtue of including $mydomain.

[quote=jabster]Problem this time: it's "jabster.net", not "jabster.nt". [/quote] 
Eh? I don't see any typo in your config...? Or have I misunderstood?

[quote=jabster]transport looks like this:
```
* smtp:[smtp.sbcglobal.yahoo.com]
sbcglobal.net smtp:[smtp.sbcglobal.yahoo.com]
.sbcglobal.net smtp:[smtp.sbcglobal.yahoo.com]
``` 
[/quote] 
You don't need that in transport - you've already declared non-local mail to be relayed via smtp.sbcglobal.yahoo.com and given that sbcglobal.net is not local it'll go that way. Why have you included the * wildcard, and declared it to all go via smtp.sbcglobal.yahoo.com? Again, there's no need as all non-local mail will go that way by virtue of your relayhost directive. Indeed one might suspect that this is why even local mail is being relayed... but as you say it's working I guess not.

Mathew

---

### Post by jabster on 2006-06-24
> It is included by virtue of including $mydomain....
Eh? I don't see any typo in your config...? Or have I misunderstood?

I had to add "jabster.net" myself tho. It's not there by default. Problem came in after running "dpkg -reconfigure postfix" as recommended earlier, which gave me a main.cf without the variables in mydestination. When I added jabster.net, I typed "jabster.nt." (Also, I added jabster.net to the mydestinations line within dpkg, and it didn't show up in the main.cf when it finished. Little bug in that program it looks like.) But oh well. Now it's there and working (locally). The initial main.cf posted above is before running "sudo dpkg-reconfigure postfix", which is where I think you misunderstood the typo problem. No big deal.

As far as transport goes, I had that on the old gentoo box, and everything was working fine. SBC seems to be a troublesome relay host for some reason, what with requiring sasl authentication. Google postfix, relayhost, and sbc, and you'll see what I mean. :-/ So everything I've done previously (transport, multiple lines in saslpass, sasl lines in main.cf) has been done based on multiple "getting postfix to relay mail thru sbc smtp servers" sites.

I don't know if something has changed with the latest postfix release? Bug or feature.

I'll remove the transport file and see what happens. Will report back.

I'm also going to compare my gentoo and current main.cf's **yet again** to make sure I didn't miss anything.

thanks,
john

---

### Post by jabster on 2006-06-29
well, I finally got a chance to get back to this thing last night. been a tad busy the past few days.

Everything is working now. Not sure WHY exactly, but it is.

Here's what I did:
added "192.168.100.0/24" to "mynetworks"
Added:
relayhost = [smtp.sbcglobal.yahoo.com]
smtp_sasl_auth_enable = yes
smtp_sasl_security_options =
smtp_sasl_password_maps = hash:/etc/postfix/saslpassword

Didn't change transport at all.

So, to summarize:
1. Run "sudo dpkg-reconfigure postfix" 
2. Add jabster.net to mydestination
3. Add 192.168.100.0/24 to mynetworks
4. Add relayhost and smtp_sasl lines above.

I don't  know if I was just missing something in my original config or what. Something that the dpkg-reconfigure fixed? Maybe the gentoo main or master had some things that didn't work correctly with the ubuntu setup.

Don't know. At this particular time, I don't really care. 

email is fully functional now, and my wife can stop her grumbling about me always having to mess things up. :)

thanks for the help and support.

-john

---

### Post by MJN on 2006-06-30
I would recommend configuring Postfix step-by-step and just concentrating on getting one aspect working at a time. Given it is so multi-faceted you're asking for trouble trying to implement a big-bang approach - start simple and build up from there.
 
A scatter-gun approach at best can leave you with a messy installation (which may or may not work), at worst it can leave you open for abuse.
 
Mathew

---

