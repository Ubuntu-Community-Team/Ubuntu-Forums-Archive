---
title: "Backup MX server - necessary?"
date: 2007-03-14
forum: Server Platforms
---

### Post by jmacdonagh on 2007-03-14
I have a Postfix server running on a dedicated VPS host. I've been with them for a few months, and have not noticed any downtime.

The question is, is a backup MX server necessary? Right now my domain zone has an MX record pointing to my server with priority 1, and then another record pointing to a Gmail for your domain account I have. If there is something wrong with my server, it will end up at Gmail.

However, I want to start using Postgrey to greylist my e-mail. I was able to set it up correctly, but to my dismay, after Postgrey rejected a test e-mail from a test account, the test account resent the e-mail to the next MX server instead of retrying my original server. In this sense, the first e-mail from every address will end up in my Gmail account.

I'm assuming that most MX backup services will hold the e-mail and attempt to resend it, which would work with the Postgrey system. Gmail, however, does not (although I could set up that Gmail account to foward all e-mail it recieves).

The question is, how useful are backup MX records? Shouldn't most SMTP servers be set to retry the message? How long is the average retry period? With this information, should I remove those backup MX records and allow Postgrey to filter?

Thanks,

Johann

---

### Post by MJN on 2007-03-14
IMHO a backup MX is unnecessary and having researched the very same topic a while back it seems this opinion is shared by many, at least in the context of the modern day Internet...

When SMTP was first introduced the Internet was obviously a very different place than it is today. Systems and network connectivity at all ends did not enjoy the almost-permanent uptime we have today and so backup MX's were advantageous. Furthermore, the open peering relationships and limited mail traffic were such that backup mail provision could be reciprocated between different systems to provide an almost seamless service despite the underlying connectivty issues.

These days however those relationships are few and far between and indeed there is little need for them. As you've mentioned most mail servers nowadays are quite happy if your MX is not answering - they'll happily hold the mail for later. 'Later' is obviously a variable amount however we're generally talking a matter of days. Hence, unless you're expecting downtimes of that magnitude then there's little to be gained from providing your own (or GMail's) backup service.

The disadvantages of backup MX's really start to show themselves when it comes to spam and given the vast majority of mail traffic is spam this is obviously of great relevence here. Greylisting, unless you've got synchronised greylisting deployed on all mail servers, starts to weaken. If you've got unsynchronised greylisting then you can end up delaying incoming more than necessary if the sending server hits both servers. Worse still, if you haven't got greylisting on a server (e.g. GMail) then that blows a huge whole in the greylisting given you've got to accept mail from that server without question.

You'd hope that your backup server would only come into play when your primary is unavailable. However... when I did some tests a while back in this very issue I was noticing, like many others do, that spammers regularly target your backup (lower priority) mail server regardless of its stated priority and the availability of your primary server. Hence no greylisting on that server and you've got no protection.

All in all I'd say drop the backup - even a mail server running at home shouldn't really require it and given yours is professionally hosted I'd say you've got practically nothing to gain yet plenty to lose.

I think that's a fair opinion however I'd welcome other thoughts from the same/different angles as there could be something I'm missing...

Mathew

P.S. There's a seemingly little-known tool that comes with Postgrey called **postgreyreport** - if you feed it your logs it'll given you an idea how effective it is being by telling you how many servers were seen once and then never came back... It soon shows just how effective greylisting is (of course this might change if/when spamming tools get 'smarter' but the whole thing's an arms race anyway).

---

### Post by Mr. C. on 2007-03-16
As the previous post indicated, backup MX's become spam pits unless they have the same management policies as the primary MX.   If the backup MX is out of your control, don't use it.

Servers will retry for 5 days by default.  If your systems go down for that long, you have bigger issues.

Since you are running postfix, try my latest postfix logwatch report/filters.  Instructions inside.

[http://www.mikecappella.com/logwatch](http://www.mikecappella.com/logwatch)

MrC

---

### Post by astrogazer on 2007-03-16
In out organization we have a Gigabit backbone connection from two carriers so for
all practical purposes we have a zero downtime on network connectivity.

Email is very important for our coworkers(500+)  therefore as you can imagine we
can't risk going offline. 

We have two mail servers-production & backup. Both are super duper machines
with fast CPUs lots of ECC RAM, RAID, double power supplies, NICs.

Why two when you have so good machines?

No single machine is redundant. The possibility, for example, of a burned south bridge
 chip is VERY small, but still possible. Can you afford a 4hr downtime?
(this is the best case scenario where you happen to be at work at the time the failure happens
and there is a store right outside your building that sells a motherboard exactly the same
as the one you have)

Some other notes:
-The SMTP RFC states that mail servers should retry for 5 days to deliver mail.
-Not all mail servers are RFC compliant and you will be suprised to see some of those
in large institutions. The consequence of this is that they might try to resend mail for only 2
days or so.
-Further more, if you use postgrey keep in mind that some servers will not retry to send mail

---

### Post by MJN on 2007-03-16
> -Not all mail servers are RFC compliant and you will be suprised to see some of those
in large institutions. The consequence of this is that they might try to resend mail for only 2
days or so.
 
I suppose in that time it would be relatively easy to setup up a store-and-forward mail server and reconfigure the DNS to that. However, even my domestic Internet service has never suffered a downtime of anywhere near that magnitude (not saying it couldn't happen mind!).
 
> Further more, if you use postgrey keep in mind that some servers will not retry to send mail
 
True, however there are updated whitelists available to minimise the risk of it happening. It could well be sensible to use postgreyreport to keep an eye on any genuine mail that may be failing at least when you start using it to ensure genuine partners/senders are not being received. Of course, the next step is then not just to whitelist them but instead/also try and convince their admins to make their setup RFC compliant!
 
Matehw

---

### Post by MJN on 2007-03-16
> **Mr. C. said:**
> Since you are running postfix, try my latest postfix logwatch report/filters. Instructions inside.
 
Mr C, I don't want to hijack the thread so little more than a yes or no is required but do your filters parse SPF passes/failures etc?
 
Mathew

---

### Post by Mr. C. on 2007-03-16
Interesting you ask that - I'm in the process now of adding additional support.  I added support for postfix/policy-spf just the other day, parsing SPF pass, etc. to do simple stats.  I'm now adding code to break down SPF messages to allow more detail of domain, IP, etc.

```

... postfix/policy-spf[1193]: : SPF fail: smtp_comment=Please see ...
   http://www.openspf.org/why.html?sender=
   user%40example.com&ip=10.0.0.1&receiver=sample.net, header_comment=sample.net: 
   domain of uesr@example.com does not designate 10.0.0.1 as permitted sender
```

Turns into:


```


 ****** Summary *******************************************************************
 
     2504   Policy SPF            
 

 ****** Detailed ******************************************************************
 
     1221   Policy SPF ------------------------------------------------------------
      973   SPF none
      152   SPF pass
       31   SPF fail
       30   SPF neutral
       27   SPF softfail
        8   SPF unknown
```

I'll likely have the Detailed code completed today.

MrC

---

### Post by MJN on 2007-03-16
That's great - I'll keep an eye out for it.

I only recently implemented SPF and it'd be handy to see as part of my daily Logwatch reports how effective it is proving or, of just as much interest for me, how widely implemented it is (in terms of other domains publishing SPF records).

From what I have seen so far it doesn't appear to be as widely used/supported as I'd hoped although I have noticed a massive (practically complete) drop in backscatter so I might take on my own DNS and see how often my domain's SPF records are queried...

Mathew

---

### Post by Mr. C. on 2007-03-21
MJN,

I've updated the logwatch postfix filter to include postfix policy-spf details.  It is now available at:

[http://www.mikecappella.com/logwatch](http://www.mikecappella.com/logwatch)

Download, unarchive, and read the README.

MrC

---

### Post by MJN on 2007-03-21
Hi Mr C,
 
I gave your new scripts a quick go this morning and whilst they're looking good (I like the summaries - a great improvement over my current script output) I'm not having much/any joy with the SPF analysis. It looks like it could well be down to the SPF I'm using - libmail-spf-query-perl on Dapper (v1.997-3) - which at the very least appears to be using the 'old' URL (spf.pobox.com) as opposed to the new [www.openspf.org]("http://www.openspf.org").
 
Hence (note I am using greylisting hence the initial rejects are likely skewing some of the figures):
 
```

--------------------- postfix Begin ------------------------ 
 
 ****** Summary
*************************************************************************************
 
      130   Rejected                                 100.00%
 --------   ------------------------------------------------
      130   Total                                    100.00%
 ========   ================================================
 
        1   Reject relay denied                        0.77%
       83   Reject recipient address                  63.85%
       46   Reject RBL                                35.38%
 --------   ------------------------------------------------
      130   Total Rejects                            100.00%
 ========   ================================================
 
      245   Connections made      
      178   Connections lost      
      245   Disconnections        
       47   Delivered             
        2   Sent via SMTP         
       96   Policy SPF            
 
        2   Illegal address syntax in SMTP command 
        1   Numeric hostname      
       29   Hostname verification errors 
        9   TLS connections (inbound) 
 
 
 
 ****** Detailed
************************************************************************************
 
        1   Reject relay denied
---------------------------------------------------------------------
        1      61.216.82.13     61-216-82-13.dynamic.hinet.net
 
       83   Reject recipient address
----------------------------------------------------------------
       30      Mailbox does not exist.
       29      Address not used. Contact me via the webform at
[_[COLOR=#606420]http://www.newtonnet.co.uk/contact/[/COLOR]_]("http://www.newtonnet.co.uk/contact/")...
       23      Mailbox not monitored - please resend any mail queries to...
        1      Please see
[_[COLOR=#0000ff]http://spf.pobox.com/why.html?sender=tprrorxjkl%40bmic.net&ip=86.108.94[/COLOR]_]("http://spf.pobox.com/why.html?sender=tprrorxjkl%40bmic.net&ip=86.108.94")....
 
       46   Reject RBL
------------------------------------------------------------------------------
       43      zen.spamhaus.org
        3      bl.spamcop.net
 
      178   Connections lost
------------------------------------------------------------------------
      119      After RCPT
       47      After CONNECT
        9      After DATA
        3      After MAIL
 
       47   Delivered
-------------------------------------------------------------------------------
       47      newtonnet.co.uk
 
        2   Sent via SMTP
---------------------------------------------------------------------------
        1      mail.com
        1      yahoo.co.uk
 
       96   Policy SPF
------------------------------------------------------------------------------
       96      SPF none
 
        2   Illegal address syntax in SMTP command
--------------------------------------------------
        2      MAIL
 
        1   Numeric hostname
------------------------------------------------------------------------
        1      Hostname
 
       29   Hostname verification errors
------------------------------------------------------------
       25      Name or service not known
        4      Address not listed for hostname
 
        9   TLS connections (inbound)
---------------------------------------------------------------
        3      80.243.183.178   unknown
        2      67.19.55.98      mohawk.buybeach.com
        2      156.99.125.105   cob-mgate1.itg.state.mn.us
        1      83.137.134.189   thepassionofthechrist.com
        1      216.113.188.96   outbound1.den.paypal.com

```
 
As you can see the SPF section is short on content, and this is explained the series of unmatched entries - a sample (to protect the innocent some address are munged) of which is:
 
```

 **Unmatched Entries**
        2   Mar 20 09:33:16 localhost postfix/policy-spf[4263]: decided
action=PREPEND Received-SPF: none (rugrat: domain of
[_[COLOR=#0000ff]stxarvccmdb@grungecafe.com[/COLOR]_]("https://secure.newtonnet.co.uk/mail/src/compose.php?send_to=stxarvccmdb%40grungecafe.com") does not designate permitted sender hosts) 
        2   Mar 20 09:33:16 localhost postfix/policy-spf[4263]: handler
sender_permitted_from: PREPEND Received-SPF: none (rugrat: domain of
[_[COLOR=#0000ff]stxarvccmdb@grungecafe.com[/COLOR]_]("https://secure.newtonnet.co.uk/mail/src/compose.php?send_to=stxarvccmdb%40grungecafe.com") does not designate permitted sender hosts) is
decisive. 
        2   Mar 20 09:33:16 localhost postfix/policy-spf[4263]: handler
sender_permitted_from: PREPEND Received-SPF: none (rugrat: domain of
[_[COLOR=#0000ff]stxarvccmdb@grungecafe.com[/COLOR]_]("https://secure.newtonnet.co.uk/mail/src/compose.php?send_to=stxarvccmdb%40grungecafe.com") does not designate permitted sender hosts) 
        2   Mar 20 09:33:16 localhost postfix/policy-spf[4263]: handler testing: DUNNO 
        1   Mar 20 22:08:13 localhost postfix/policy-spf[11747]: decided
action=PREPEND Received-SPF: none (rugrat: domain of [_[COLOR=#0000ff]puestos@our-asylum.net[/COLOR]_]("https://secure.newtonnet.co.uk/mail/src/compose.php?send_to=puestos%40our-asylum.net")
does not designate permitted sender hosts) 
        1   Mar 20 12:28:45 localhost postfix/policy-spf[4594]: handler
sender_permitted_from: PREPEND Received-SPF: none (rugrat: domain of
[_[COLOR=#0000ff]mms38.com@gregsart.com[/COLOR]_]("https://secure.newtonnet.co.uk/mail/src/compose.php?send_to=mms38.com%40gregsart.com") does not designate permitted sender hosts) is
decisive. 
        1   Mar 20 19:22:20 localhost postfix/policy-spf[9775]: decided
action=PREPEND Received-SPF: none (rugrat: domain of REMOVED[EMAIL="REMOVED@fleetpictures.com"]_[COLOR=#0000ff]@fleetpictures.com[/COLOR]_[/EMAIL]
does not designate permitted sender hosts) 
        1   Mar 20 14:12:37 localhost postfix/policy-spf[6134]: handler testing: DUNNO 
        1   Mar 20 16:53:10 localhost postfix/policy-spf[7561]: handler
sender_permitted_from: PREPEND Received-SPF: none (rugrat: domain of
REMOVED[EMAIL="REMOVED@ohiggins.ubuntu.com"]_[COLOR=#0000ff]@ohiggins.ubuntu.com[/COLOR]_[/EMAIL] does not designate permitted sender hosts) 
        1   Mar 20 22:14:42 localhost postfix/policy-spf[11831]: decided
action=PREPEND Received-SPF: none (rugrat: domain of
REMOVED[EMAIL="REMOVED@parisblues.com"]_[COLOR=#0000ff]@parisblues.com[/COLOR]_[/EMAIL] does not designate permitted sender hosts) 
        1   Mar 20 22:22:57 localhost postfix/policy-spf[11868]: handler
sender_permitted_from: PREPEND Received-SPF: none (rugrat: domain of
REMOVED[EMAIL="REMOVED@oxalide.com"]_[COLOR=#0000ff]@oxalide.com[/COLOR]_[/EMAIL] does not designate permitted sender hosts)
        1   Mar 20 04:11:22 localhost postfix/policy-spf[3184]: handler testing: DUNNO 
        1   Mar 20 21:16:41 localhost postfix/policy-spf[11210]: handler
sender_permitted_from: PREPEND Received-SPF: none (rugrat: domain of
[_[COLOR=#0000ff]soft@paulandpaula.com[/COLOR]_]("https://secure.newtonnet.co.uk/mail/src/compose.php?send_to=soft%40paulandpaula.com") does not designate permitted sender hosts) is
decisive. 
        1   Mar 20 23:06:48 localhost postfix/policy-spf[12295]: : SPF pass:
smtp_comment=Please see
[_[COLOR=#0000ff]http://spf.pobox.com/why.html?sender=SDN_Program%40mail.communications.sun.com&ip=209.11.164.54&receiver=rugrat:[/COLOR]_]("http://spf.pobox.com/why.html?sender=SDN_Program%40mail.communications.sun.com&ip=209.11.164.54&receiver=rugrat:")
209.11.164.0/22 contains 209.11.164.54, header_comment=rugrat: domain of
REMOVED[EMAIL="REMOVED@mail.communications.sun.com"]_[COLOR=#0000ff]@mail.communications.sun.com[/COLOR]_[/EMAIL] designates 209.11.164.54 as
permitted sender 
1   Mar 20 18:13:04 localhost postfix/policy-spf[8621]: : SPF fail:
smtp_comment=Please see
[_[COLOR=#0000ff]http://spf.pobox.com/why.html?sender=tprrorxjkl%40bmic.net&ip=86.108.94.112&receiver=rugrat[/COLOR]_]("http://spf.pobox.com/why.html?sender=tprrorxjkl%40bmic.net&ip=86.108.94.112&receiver=rugrat"),
header_comment=rugrat: domain of [_[COLOR=#0000ff]tprrorxjkl@bmic.net[/COLOR]_]("https://secure.newtonnet.co.uk/mail/src/compose.php?send_to=tprrorxjkl%40bmic.net") does not designate
86.108.94.112 as permitted sender 

```
 
Whilst the URL is the obvious tripping point for many, there are some (the first few for example) which do not contain a URL.
 
I don't know if you're interested in this failure case (I'm not expecting you to fix it) as perhaps I ought to be updating the SPF in place anyway. However, I'm not overly keen from straying too far from the repository versions given the manual update obligation. Looking at the openspf software repository it looks like v2-onwards is using packages that aren't in the standard Dapper distribution (e.g. libmail-spf-perl).
 
I'm happy to provide any further info if you're interested.
 
Mathew

---

### Post by Mr. C. on 2007-03-21
Matt, I will take a look at integration of your unmatched lines, and report back.

MrC

---

### Post by MJN on 2007-03-21
That's great - it'll be appreciated.
 
You're more than welcome to an entire, untouched, logfile if it's of any use although I guess you've probably got what you need above albeit with some formatting alterations. (although I see there are no SOFTFAIL entries)
 
This has made me wonder if I'm behind the times with my SPF implementation - although I guess I can't be the only one. I might still look at seeking an upgrade but for now it'll just have to be yet another item on the 'To Do' list!
 
Mathew

---

### Post by Mr. C. on 2007-03-21
I've sent you a PM.

With respect to various entries, you'll have to tell me if a line should be ignored and dropped (eg. debugging, or duplicated by following line), or how it should be classified into the SPF results codes:

```
# Pass      the SPF record designates the host to be allowed to send accept
# Fail      the SPF record has designated the host as NOT being allowed to send  reject
# SoftFail  the SPF record has designated the host as NOT being allowed to send but is in transition  accept but mark
# Neutral   the SPF record specifies explicitly that nothing can be said about validity   accept
# None      the domain does not have an SPF record or the SPF record does not evaluate to a result accept
# PermError a permanent error has occured (eg. badly formatted SPF record) unspecified
# TempError a transient error has occured accept or reject

```

This that have an SPF pass, or SFP fail are clear.  But what about "decided action=PREPEND ..." and "handler sender_permitted_from:..." lines?

MrC

---

### Post by MJN on 2007-03-21
(PM responded to; logfile sent)

Mr C,

I was hoping you wouldn't ask any questions like that as it'll highlight my newbieness of SPF in general, and this particular implementation in particular!

However, having looked at the logs I think I can identify what's useful to capture and what can be ignored. I'll highlight them below to save you trawling through my logs!

To start with, a general SPF log with my implementation appears to take the following form: (a straightforward 'SPF none' in this case)

```

Mar 18 10:23:04 localhost postfix/policy-spf[24685]: : testing: stripped sender=unliquid@silverbengal.com, stripped rcpt=usenet@newtonnet.co.uk
Mar 18 10:23:04 localhost postfix/policy-spf[24685]: handler testing: DUNNO
Mar 18 10:23:04 localhost postfix/policy-spf[24685]: : SPF none: smtp_comment=SPF: domain of sender unliquid@silverbengal.com does not designate mailers, header_comment=rugrat: domain of unliquid@silverbengal.com does not designate permitted sender hosts
Mar 18 10:23:04 localhost postfix/policy-spf[24685]: handler sender_permitted_from: PREPEND Received-SPF: none (rugrat: domain of unliquid@silverbengal.com does not designate permitted sender hosts)
Mar 18 10:23:04 localhost postfix/policy-spf[24685]: handler sender_permitted_from: PREPEND Received-SPF: none (rugrat: domain of unliquid@silverbengal.com does not designate permitted sender hosts) is decisive.
Mar 18 10:23:04 localhost postfix/policy-spf[24685]: decided action=PREPEND Received-SPF: none (rugrat: domain of unliquid@silverbengal.com does not designate permitted sender hosts)

```As you can probably gather a Received-SPF: header line is added to the message and it is let through. With regards to logging however the only line of real interest is number 3 (**: SPF none: ....**) - the other lines are redundant and can be ignored.

For SPF passes, I am getting the following:

```

Mar 19 13:06:52 localhost postfix/policy-spf[21503]: : testing: stripped sender=gginx05@emarketing.servicemail24.de, stripped rcpt=usenet@newtonnet.co.uk
Mar 19 13:06:52 localhost postfix/policy-spf[21503]: handler testing: DUNNO
Mar 19 13:06:52 localhost postfix/policy-spf[21503]: : SPF pass: smtp_comment=Please see http://spf.pobox.com/why.html?sender=gginx05%40emarketing.servicemail24.de&ip=195.71.127.229&receiver=rugrat: 195.71.127.224/29 contains 195.71.127.229, header_comment=rugrat: domain of gginx05@emarketing.servicemail24.de designates 195.71.127.229 as permitted sender
Mar 19 13:06:52 localhost postfix/policy-spf[21503]: handler sender_permitted_from: PREPEND Received-SPF: pass (rugrat: domain of gginx05@emarketing.servicemail24.de designates 195.71.127.229 as permitted sender)
Mar 19 13:06:52 localhost postfix/policy-spf[21503]: handler sender_permitted_from: PREPEND Received-SPF: pass (rugrat: domain of gginx05@emarketing.servicemail24.de designates 195.71.127.229 as permitted sender) is decisive.
Mar 19 13:06:52 localhost postfix/policy-spf[21503]: decided action=PREPEND Received-SPF: pass (rugrat: domain of gginx05@emarketing.servicemail24.de designates 195.71.127.229 as permitted sender)

```Again, same six lines the interesting one of which is number 3.

For SPF fail, we have:

```

Mar 19 11:22:54 localhost postfix/policy-spf[19752]: : testing: stripped sender=rojjbrmahtlkrkfael@mm.pl, stripped rcpt=usenet@newtonnet.co.uk
Mar 19 11:22:54 localhost postfix/policy-spf[19752]: handler testing: DUNNO
Mar 19 11:22:55 localhost postfix/policy-spf[19752]: : SPF fail: smtp_comment=Please see http://spf.pobox.com/why.html?sender=rojjbrmahtlkrkfael%40mm.pl&ip=81.190.186.216&receiver=ru
grat, header_comment=rugrat: domain of rojjbrmahtlkrkfael@mm.pl does not designate 81.190.186.216 as permitted sender
Mar 19 11:22:55 localhost postfix/policy-spf[19752]: handler sender_permitted_from: REJECT Please see http://spf.pobox.com/why.html?sender=rojjbrmahtlkrkfael%40mm.pl&ip=81.190.186.21
6&receiver=rugrat
Mar 19 11:22:55 localhost postfix/policy-spf[19752]: handler sender_permitted_from: REJECT Please see http://spf.pobox.com/why.html?sender=rojjbrmahtlkrkfael%40mm.pl&ip=81.190.186.21
6&receiver=rugrat is decisive.
Mar 19 11:22:55 localhost postfix/policy-spf[19752]: decided action=REJECT Please see http://spf.pobox.com/why.html?sender=rojjbrmahtlkrkfael%40mm.pl&ip=81.190.186.216&receiver=rugrat

```Again, third log entry is of interest.

There's obviously a pattern here - always 6 lines and any line starting with **: testing: **, **handler testing:** , **handler sender_permitted_from:** or **decided action** can be ignored. The one of interest is always **: SPF <pass|fail|etc>:**

For SPF softfail, we have:

```

Mar 19 07:33:20 localhost postfix/policy-spf[15033]: : testing: stripped sender=208edie@ismysexy.name, stripped rcpt=contact@northerncrock.co.uk
Mar 19 07:33:20 localhost postfix/policy-spf[15033]: handler testing: DUNNO
Mar 19 07:33:21 localhost postfix/policy-spf[15033]: : SPF softfail: smtp_comment=Please see http://spf.pobox.com/why.html?sender=208edie%40ismysexy.name&ip=219.140.181.50&receiver=r
ugrat, header_comment=rugrat: transitioning domain of 208edie@ismysexy.name does not designate 219.140.181.50 as permitted sender
Mar 19 07:33:21 localhost postfix/policy-spf[15033]: handler sender_permitted_from: PREPEND Received-SPF: softfail (rugrat: transitioning domain of 208edie@ismysexy.name does not designate 219.140.181.50 as permitted sender)
Mar 19 07:33:21 localhost postfix/policy-spf[15033]: handler sender_permitted_from: PREPEND Received-SPF: softfail (rugrat: transitioning domain of 208edie@ismysexy.name does not designate 219.140.181.50 as permitted sender) is decisive.
Mar 19 07:33:21 localhost postfix/policy-spf[15033]: decided action=PREPEND Received-SPF: softfail (rugrat: transitioning domain of 208edie@ismysexy.name does not designate 219.140.181.50 as permitted sender)

```For SPF where the domain doesn't exist (is that perm or temperror?): (the mail was accepted but I guess that doesn't decide either way)

```

Mar 18 21:29:48 localhost postfix/policy-spf[5347]: : testing: stripped sender=root@ont1.saint-paul.lu, stripped rcpt=usenet@newtonnet.co.uk
Mar 18 21:29:48 localhost postfix/policy-spf[5347]: handler testing: DUNNO
Mar 18 21:29:48 localhost postfix/policy-spf[5347]: : SPF unknown: smtp_comment=Please see http://spf.pobox.com/why.html?sender=root%40ont1.saint-paul.lu&ip=80.92.64.162&receiver=rugrat: domain of sender root@ont1.saint-paul.lu does not exist, header_comment=rugrat: error in processing during lookup of root@ont1.saint-paul.lu
Mar 18 21:29:48 localhost postfix/policy-spf[5347]: handler sender_permitted_from: PREPEND Received-SPF: unknown (rugrat: error in processing during lookup of root@ont1.saint-paul.lu)
Mar 18 21:29:48 localhost postfix/policy-spf[5347]: handler sender_permitted_from: PREPEND Received-SPF: unknown (rugrat: error in processing during lookup of root@ont1.saint-paul.lu) is decisive.
Mar 18 21:29:48 localhost postfix/policy-spf[5347]: decided action=PREPEND Received-SPF: unknown (rugrat: error in processing during lookup of root@ont1.saint-paul.lu)

```I think that's all I've seen. I don't think I've had anything that would fall under 'neutral'. Same with whatever results in permerror/temperror that's not the one above... In time I guess these should show themselves as unmatched entries in any revised Logwatch script output so I could let you know...

Is that any help? Was it the sort of thing you needed?

Mathew

---

### Post by Mr. C. on 2007-03-21
Perfect.  I'll update today.

MrC

---

### Post by Mr. C. on 2007-03-22
The postfix filter has been updated to handle the various SPF log entries.

Pick up the new version at:

   [http://www.mikecappella.com/logwatch](http://www.mikecappella.com/logwatch)

MrC

---

### Post by MJN on 2007-03-22
Great work Mr C - works perfectly.

Johann - sorry for the hijacked thread... have you decided what you're doing about your backup mail server? ;)

Mathew

---

