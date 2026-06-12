---
title: "Performance Tuning on Multi-Core Servers"
date: 2012-01-20
forum: Server Platforms
---

### Post by SeijiSensei on 2012-01-20
I've now installed a dual Xeon gateway server (Dell R410) at a client's office with about 250 desktop users.  Linux treats the machine as having 16 CPUs.  I'd like to ensure that the workload is distributed across the processors as evenly as possible.  FWIW, I'm using CentOS 6, but I don't think the distribution matters here.

The machine runs two processor-intensive services.  MailScanner handles SMTP and scans every message for viruses with clamscan and for spam with spamassassin.  Both MailScanner and SpamAssassin are Perl applications so they are pretty demanding.  We also use Squid+SquidClamAV to scan every downloaded object for malware.  The loads are generally quite respectable, remaining well under 2.0 most of the time, but CPUs zero and eight handle the bulk of the work with the rest idle most of the time.

I'm running sixteen children for each service.  In the case of MailScanner each child is a scanning manager that invokes clamscan and spamassassin for each message.  For SquidClamAV I'm using sixteen instances of the c-icap server as the interface between Squid and clamd.  Should I assume that the kernel adequately distributes these children across the processors, or is there something I should be doing to bind the child processes to specific CPUs?  There's only one instance of clamd running, though.  Should I consider setting up multiple copies of that daemon, each bound to a separate port, to spread the load?

Other suggestions?

---

### Post by rubylaser on 2012-01-20
> **SeijiSensei said:**
> I've now installed a dual Xeon gateway server (Dell R410) at a client's office with about 250 desktop users.  Linux treats the machine as having 16 CPUs.  I'd like to ensure that the workload is distributed across the processors as evenly as possible.  FWIW, I'm using CentOS 6, but I don't think the distribution matters here.

The machine runs two processor-intensive services.  MailScanner handles SMTP and scans every message for viruses with clamscan and for spam with spamassassin.  Both MailScanner and SpamAssassin are Perl applications so they are pretty demanding.  We also use Squid+SquidClamAV to scan every downloaded object for malware.  The loads are generally quite respectable, remaining well under 2.0 most of the time, but CPUs zero and eight handle the bulk of the work with the rest idle most of the time.

I'm running sixteen children for each service.  In the case of MailScanner each child is a scanning manager that invokes clamscan and spamassassin for each message.  For SquidClamAV I'm using sixteen instances of the c-icap server as the interface between Squid and clamd.  Should I assume that the kernel adequately distributes these children across the processors, or is there something I should be doing to bind the child processes to specific CPUs?  There's only one instance of clamd running, though.  Should I consider setting up multiple copies of that daemon, each bound to a separate port, to spread the load?

Other suggestions?

As I'm sure you know, the ability to use all of the cores depends on how well the application is threaded.  I would imagine, you're seeing cores 0 through 8 as the ones under load, because they are the physical cores.  The other 8 are logical cores, so don't provide nearly the same benefit as additional physical cores do, and are likely not being used.  

As long as the application is well threaded, the kernel should distribute the load evenly across the cores. But, with loads around 2, I wouldn't worry about it. I would expect a machine that's that well equipped to handle 250 users very well.  That being said, clamd itself is well threaded, and should be able to use all of the cores efficiently. But, I've never used SquidClamAV, so I haven't tested it's threading capabilities or it's load with a userbase of that size.

Have you run into slowdowns or very high loads at any point, or are you just trying to be proactive?

---

### Post by ian dobson on 2012-01-20
Hi,

Spamassassin supports compiling the rule tests to native code using sa-compile ([http://spamassassin.apache.org/full/3.2.x/doc/sa-compile.html](http://spamassassin.apache.org/full/3.2.x/doc/sa-compile.html)). 

On my email/spamassassin box running sa-compile reduces the load by a good amount.

Spamassassin also supports creating several children and keeping them alive, have a look at  /etc/default/spamassassin

```
Jan 20 21:27:09 alpha2 spamd[9414]: logger: removing stderr method
Jan 20 21:27:11 alpha2 spamd[9416]: zoom: able to use 1572/1572 'body_0' compiled rules (100%)
Jan 20 21:27:11 alpha2 spamd[9416]: spamd: server started on port 783/tcp (running version 3.3.2)
Jan 20 21:27:11 alpha2 spamd[9416]: spamd: server pid: 9416
Jan 20 21:27:11 alpha2 spamd[9416]: spamd: server successfully spawned child process, pid 9417
Jan 20 21:27:11 alpha2 spamd[9416]: prefork: child states: I
```

Regards
Ian Dobson

---

### Post by SeijiSensei on 2012-01-20
> **rubylaser said:**
> That being said, clamd itself is well threaded, and should be able to use all of the cores efficiently. But, I've never used SquidClamAV, so I haven't tested it's threading capabilities or it's load with a userbase of that size.

I'm glad to hear that clamd is well-threaded.  Rereading the SquidClamAV [manual]("http://squidclamav.darold.net/config.html") shows there's a "clamd failover" specification that can take advantage of multiple clamd servers.  It recurses through the list of server addresses until it finds one that doesn't time out.  Unfortunately they all have to use the same port.  If the situation arises, I might consider creating a small subnet of aliased Ethernet adapters and assign multiple clamd daemons to them.

One thing we discovered recently is the need to turn off the DetectBrokenExecutables switch in clamd to avoid a problem with SquidClamAV.  When it was enabled, authentic updates for Adobe Reader could not be downloaded via Adobe's updater.  It probably had something to do with the structure of the update file, but I just turned off the option instead.  We had a couple of machine hitting the proxy continuously trying to update Reader with this switch enabled.  The file itself passes muster with both clamscan and clamdscan, so I don't know why it throws a "broken executable" error when scanned using the same tools but invoked by SquidClamAV.

> Have you run into slowdowns or very high loads at any point, or are you just trying to be proactive?

Mostly proactive.  Loads are highest around lunch time, of course, when surfing reaches its peak.  Most of the time the server is cruising along at 0.5-1.0.  The parent squid daemon is by far the most CPU-intensive task, but squid has no native support for multiple processors.  I came across [this article]("http://www.thenetcircle.com/2008/08/22/the-squid-is-dead-long-live-to-the-nginx/") on replacing Squid with [nginx]("http://wiki.nginx.org/Main") instead.  I might look into that some day when I have the ambition, but I have a well-organized squid configuration that can be managed by local admins using Webmin.  I'd prefer to keep that arrangement unless performance suffers visibly, which it hasn't so far.

> **ian dobson said:**
> Spamassassin supports compiling the rule tests to native code using sa-compile ([http://spamassassin.apache.org/full/3.2.x/doc/sa-compile.html](http://spamassassin.apache.org/full/3.2.x/doc/sa-compile.html)).

On my email/spamassassin box running sa-compile reduces the load by a good amount.


Thanks!  I'll look into that.  The ruleset is pretty stable at this point so compilation makes a lot of sense. 

> Spamassassin also supports creating several children and keeping them alive

MailScanner is configured to invoke the spamassassin binary for each message, but I believe it can be configured to use spamd instead.  If so, that's another worthwhile approach.

Edit:  No, it works by invoking the binary.  Still it's already pretty fast and compiling the rules should help even more.

Thanks to you both!

---

### Post by rubylaser on 2012-01-20
> **SeijiSensei said:**
> I'm glad to hear that clamd is well-threaded.  Rereading the SquidClamAV [manual]("http://squidclamav.darold.net/config.html") shows there's a "clamd failover" specification that can take advantage of multiple clamd servers.  It recurses through the list of server addresses until it finds one that doesn't time out.  Unfortunately they all have to use the same port.  If the situation arises, I might consider creating a small subnet of aliased Ethernet adapters and assign multiple clamd daemons to them.

One thing we discovered recently is the need to turn off the DetectBrokenExecutables switch in clamd to avoid a problem with SquidClamAV.  When it was enabled, authentic updates for Adobe Reader could not be downloaded via Adobe's updater.  It probably had something to do with the structure of the update file, but I just turned off the option instead.  We had a couple of machine hitting the proxy continuously trying to update Reader with this switch enabled.  The file itself passes muster with both clamscan and clamdscan, so I don't know why it throws a "broken executable" error when scanned using the same tools but invoked by SquidClamAV.



Mostly proactive.  Loads are highest around lunch time, of course, when surfing reaches its peak.  Most of the time the server is cruising along at 0.5-1.0.  The parent squid daemon is by far the most CPU-intensive task, but squid has no native support for multiple processors.  I came across [this article]("http://www.thenetcircle.com/2008/08/22/the-squid-is-dead-long-live-to-the-nginx/") on replacing Squid with [nginx]("http://wiki.nginx.org/Main") instead.  I might look into that some day when I have the ambition, but I have a well-organized squid configuration that can be managed by local admins using Webmin.  I'd prefer to keep that arrangement unless performance suffers visibly, which it hasn't so far.!

I'd love it if Nginx as a traditional Proxy Server (like Squid), but that article seems to be describing a reverse proxy (acting as a cache for a dynamic website).  I've used it many times as a reverse proxy for my Ruby on Rails websites with Passenger Phusion in place of Apache, but I don't think it will act like a internal caching Squid proxy. If I misunderstood that article, I would actually be pleased, because if it was a traditional proxy and it isas lightweight as it's webserver is, it would be fantastic.

---

### Post by ian dobson on 2012-01-21
Hi,

If your worried about the server load, then going over to using spamd/spamc will make a huge difference. As spamd runs as a deamon and on starting it can read all the rules and setup server children that wait for connections from spamc.

Regards
Ian Dobson

---

### Post by SeijiSensei on 2012-01-21
> **ian dobson said:**
> If your worried about the server load, then going over to using spamd/spamc will make a huge difference. As spamd runs as a deamon and on starting it can read all the rules and setup server children that wait for connections from spamc.

As I said, MailScanner doesn't take the spamc/spamd approach.  It operates as a store-and-forward SMTP server.  Incoming messages are extracted from a sendmail queue, then evaluated based on MS's own rules, a pass through the spamassassin binary, then for non-spams, a pass though a virus scanner like clamscan.  The processed message is either forwarded along for delivery or quarantined.  It's more akin to amavisd though with a lot more flexibility.

From what little I recall of spamd, this is designed for scanning at the delivery phase like clamd.  In my case there is no local delivery.  All the mail is passed on to another mail server behind the gateway.  The gateway acts simply as an SMTP relay with spam and virus scanning bolted on.

---

### Post by ian dobson on 2012-01-21
> **SeijiSensei said:**
> As I said, MailScanner doesn't take the spamc/spamd approach.  It operates as a store-and-forward SMTP server.  Incoming messages are extracted from a sendmail queue, then evaluated based on MS's own rules, a pass through the spamassassin binary, then for non-spams, a pass though a virus scanner like clamscan.  The processed message is either forwarded along for delivery or quarantined.  It's more akin to amavisd though with a lot more flexibility.

From what little I recall of spamd, this is designed for scanning at the delivery phase like clamd.  In my case there is no local delivery.  All the mail is passed on to another mail server behind the gateway.  The gateway acts simply as an SMTP relay with spam and virus scanning bolted on.

Using spamassassin or spamc/spamd exactly the same from the callers point of view. With spamassassin.pl the perl script loads/configures/reads the rule set, processes the message and returns the processed message to the caller. With spamc/spamd the caller starts spamc with the email text, spamc passes the email to spamd which processes the message and passes it back to spamc which passes it back to the caller.

Some time ago I converted a script that used spamassassin.pl to use spamc/spamd. It took about 30minutes to change, and only involved finding/changing the call to spamassasin the rest of the code remained unchanged.

Regards
Ian Dobson

---

