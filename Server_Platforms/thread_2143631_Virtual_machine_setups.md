---
title: "Virtual machine setups"
date: 2013-05-09
forum: Server Platforms
---

### Post by tad1073 on 2013-05-09
Here is what I want to accomplish: [My box with internet connection as the gateway and dns]--->[virtual router,squid]--->[vrtual vpn server ]--->[virtual lamp,mail server], is it feasable and what sizes should I make the virtal machines?

---

### Post by TheFu on 2013-05-09
Sure, all of this is possible, but we can't possibly help you size the VMs without lots more information for every aspect of each machine.  I'm not certain that I understand what your setup will look like since an email server behind a VPN is pretty worthless for communicating with the rest of the world.

I'd probably put all the VMs that will be behind the VPN on a different subnet that only the VPN can access.  I'd also keep the physical hardware as far from the Internet as possble - only allow VMs - the fewer the better - with network access to the internet.  Something link this [http://www.ratemynetworkdiagram.com/?i=15442](http://www.ratemynetworkdiagram.com/?i=15442) might give you some ideas?

---

### Post by Toxic64 on 2013-05-10
Well as far as I know it is possible but although I like Ubuntu very much, I wouldn't go with it for those functions as ClearOS (based on centOS ) has all of them bundled and running one VM only. I use it for one of my customers and it works like a charm.(my customer's VM is 20 Go / 1Gb Ram / 1 64bit cpu)

---

### Post by tad1073 on 2013-05-10
I'm just doing this for something to do really, I already have lamp, xbmc media server with mysql, bind9 and squid on my maching now.

---

### Post by TheFu on 2013-05-10
bind and sendmail have been hacked more times than all other UNIX services combined. Be very careful running bind.  In 2000, my bind install was hacked - I avoid running DNS myself since that time.

BTW, I'm just up I-75 from you in East Cobb.  Did you attend the ALE-NW meeting last night?  Check out ale.org to get involved locally, if you have any interest.  The ALE-central meetings are heavily into server administration. Much to be learned from that crew. Mark Next Thursday on your calendar.

---

### Post by tad1073 on 2013-05-10
Cool, that sounds like a plan, where it the meeting and what time?

---

### Post by TheFu on 2013-05-10
> **tad1073 said:**
> Cool, that sounds like a plan, where it the meeting and what time?

[http://ale.org](http://ale.org) has the meeting information. Signup for the email list (link on the left side) if you want to be notified of anything. We **don't** tweet, facebook, meetup. email is really the only communications channel for that group.  There are 2 meeting locations; Emory Law and SPSU.

---

### Post by SeijiSensei on 2013-05-11
> **TheFu said:**
> bind and sendmail have been hacked more times than all other UNIX services combined. Be very careful running bind.  In 2000, my bind install was hacked - I avoid running DNS myself since that time.

I avoided putting sendmail directly on the Internet for a long time, too.  My own mail system still uses an old store-and-forward SMTP server to accept inbound mail.  (It has a very flexible anti-spam filter that lets me ignore the 40% of mail that I know should never be accepted.)  However the sendmail of 2013 is substantially more secure than whatever version you may have used in the past.  I have a couple of clients' mail servers running sendmail in conjunction with MailScanner.  They have never been hacked.

The same can largely be said of BIND, though the occasional compromise is still found. [CERT]("http://www.kb.cert.org/vuls/") reports about forty vulnerabilities in BIND 9 dating back to 1999.  There were two in 2012.

Remember these are programs originally designed for a time when the Internet was a relatively well-managed network with a small club of participants.  Because these were the archetypal programs for SMTP and DNS, their use grew quickly with the expansion of the Internet after 1993.  It's not surprising that they became an obvious target for early hackers, but those attacks have vastly improved the security of both programs.

---

