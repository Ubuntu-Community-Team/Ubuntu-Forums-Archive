---
title: "Postfix/Dovecot ++ mail server. Can send mail but not receive mail"
date: 2017-12-23
forum: Server Platforms
---

### Post by rajohan on 2017-12-23
[COLOR=#242729][FONT=Arial][B]Some back story
[/B][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have the 3 last days struggled hard to try to get a mail server up and run. After first trying to get it up on a server with blocked ports I decided yesterday after several reinstalls to transfer my server over to linode.com so I dont have the struggels with blocked ports.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I finally have a mail server up and running with Postfix, Dovecot, SpamAssassin, ClamAV, Sieve and Roundcube. And even tho my server dont have blocked ports I'm running all mail through dynu.com with a SMTP Outbound Relay and Email Store/Forward for the extra security layer and storing/backup if my server for some reason should be unavailable.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][B]The Problem
[/B][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Now to the problem, I can't recive any mail for some reason. But I can send mail just fine from the terminal, roundcube and from my iphone and it gets to the reciver without any problems.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]When I check the logs dynu acctualy try's to deliver but something are failing along the way as this is what the log contains after a delivery request
[FONT=Consolas]
[/FONT][/FONT][/COLOR]
Dec 23 12:44:17 rajohan postfix/smtpd[22192]: connect from mx1.dynu.com[ip address]
Dec 23 12:44:18 rajohan postfix/smtpd[22192]: lost connection after UNKNOWN from mx1.dynu.com[ip address]
Dec 23 12:44:18 rajohan postfix/smtpd[22192]: disconnect from mx1.dynu.com[ip address] unknown=0/1 commands=0/1
[COLOR=#242729][FONT=Arial][FONT=Consolas]
[/FONT]I would be really grateful if someone could take a look at my master, main and dovecot config's and see if they can see why. I'm by no means a linux expert, in fact I just started toying with linux about 1 month ago and are now feeling quite lost on what to do.

[/FONT][/COLOR]
My master.cfg: [https://pastebin.com/pH12rCq7](https://pastebin.com/pH12rCq7) 
My main.cfg: [https://pastebin.com/uZCFHNzS](https://pastebin.com/uZCFHNzS) 
My dovecot.cfg  [https://pastebin.com/9SCKz1dj](https://pastebin.com/9SCKz1dj)

[COLOR=#242729][FONT=Arial]**And here are some of my DNS settings**[/FONT][/COLOR]

[LIST=1]
[*]MX record 1 and 2 is applied to mail.rajohan.no
[*]mail.rajohan.no has a A record to the server ip
[*]rajohan.no has a A record to the server ip
[*]Reverse DNS is applied to rajohan.no (not sure if this should be applied to mail.rajohan.no and not rajohan.no)
[*]DKIM is applied to mail._domainkey.relay.rajohan.no
[*]SPF is applied to rajohan.no
[/LIST]
[COLOR=#242729][FONT=Arial]And another question when i set hostname in terminal to rajohan would what overwrite localhost? Or is thoose 2 separate things?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]




[/FONT][/COLOR]

---

### Post by TheFu on 2017-12-23
hostnames don't really matter to email.  As long as the name resolution works as expected (name --> IP), having a different hostname+domainname isn't really an issue for email servers.  It is the IP address that matters.  Don't get the IP or subnet wrong inside the config.

Rather than describing stuff, just post the command output. Often we have blinders when the commands show clearly what the issues are.  Happens to everyone.

Never under estimate the power of using raw telnet to check things for SMTP stuff. SMTP is a very simple protocol and easy to manually make requests directly to most SMTP servers. It is a common troubleshooting technique for SMTP.

In short, simplify and test.  Keep doing that until you get something working. Over and over.  Start with just postfix running on your server. Can you telnet into port 25 from a client? Can you send SMTP commands? Does it respond?  If no, simplify more.  Forget about anti-spam stuff until you get that working.  Then add 1 complexity at a time.

A few other ideas from my 20+ yrs running email servers:

For sending and receiving emails, only the SMTP process, usually postfix, matters.  Forget about all the other things for now. Disable them.  Similarly, forget about DKIM and SPF for now.  Get things working first.  That involves only port 25/tcp. Nothing else. If something else is in the way and you didn't get pure SMTP working first, simplify some more.

The MX records point to mx1.dynu.com. and mx2.dynu.com.  That seems fine, provided that service provider is actually forwarding the email to your server.

IME email gateways provide 2 different services - in and out.  Those are often sold separately, as different offerings.  It is easy to pay for 1, but not the other.  Are you positive you purchased what you expect to work?

And be certain you don't ever leave your SMTP server as an open-relay. That will get the IP(s) on a blacklist and it is non-trivial to be removed from those lists.  Took me 3 years to get my server off 1 (one) blacklist at a single, regional, ISP. It wasn't on any other RBLs but 50% of my clients used that ISP so it was a hassle.

Check that none of the IPs are on email RBLs.  If they are, you'll forever have issues sending emails.  

Many daemons have a config file checker. For postfix, that is **postconf -n**.  How does that look? Like you expected?

I'm still on 14.04 for email servers. Don't think that looking at your configs will be very helpful as postfix has changed over the years.

Good luck.  Simplify.

---

### Post by SeijiSensei on 2017-12-23
By default Postfix on Ubuntu only accepts mail sent to localhost.  Have you changed the [mynetworks]("http://www.postfix.org/postconf.5.html#mynetworks") setting in main.cf?

---

