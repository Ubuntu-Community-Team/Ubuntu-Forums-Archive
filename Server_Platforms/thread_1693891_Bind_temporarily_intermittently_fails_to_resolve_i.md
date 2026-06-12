---
title: "Bind temporarily intermittently fails to resolve internet hosts"
date: 2011-02-23
forum: Server Platforms
---

### Post by curiousornge on 2011-02-23
Hi all,

Long time reader, first time poster - please be kind :)  This post contains a lot of info; if this is too much, message me and I'll cut it down - I just want to make sure I don't miss anything relevant.

My housemates and I are getting intermittent DNS lookup failures (maybe ~50 per day under reasonably heavy web-usage) from my bind cacher and it has me stumped.  Perhaps some background may help.

The box in question is an old PIII machine running Maverick server, upgraded from Lucid a month or two back.  It is a primarily a router/NAT/firewall box but also runs DHCP and BIND to serve computers in the house and acts as one half of an OpenVPN tunnel to my workplace network.

BIND is tasked with caching upstream DNS requests as well as authoritatively serving one internal domain and acting as a slave for another internal one, plus my work domain.  See the attached config files for more info.

Despite all this, the load average on the box is generally no higher than 0.02 and our internet connection is rarely max-ed out (~13Mb/~1.1Mb ADSL2+).

I have never seen bind fail for any of the internal DNS whether it is authoritative or not.  External hosts, however, are a different matter and sometimes fail (maybe 1% of the time, as a wild stab in the dark).  This also occurred before the upgrade to Maverick.

Hosts such as i.imgur.com, reddit.com, youtube.com and bbc.co.uk appear particularly susceptible, but that may be because they are commonly visited.

Some (probably relevant) symptoms: Web pages almost never fail to load once they start; on link boards such as b3ta.com, embedded content from one host (such as youtube) may be missing; sometimes the browser takes a while (~5 - 10 seconds) to commence loading a page, but is as fast as normal once it does; sometimes the browser throws a 105 error and refuses to load at all.  No domains permanently fail - refreshing the page after a few seconds to a few minutes results in normal operation.

My first thoughts were that maybe upstream DNS requests (to google's DNS - I use 8.8.8.8 and 8.8.4.4 as primary and secondary and have swapped them a number of times to no effect) were being lost either outbound or inbound on the ADSL, but bombarding google.com with pings once a second for over a day resulted in 0 dropped packets, and we've not had any connection problems with our ISP of the last 5 years or this particular line, which we have had for 6 months.  We are also in the remarkably lucky position that our ISP does not shape our traffic.

I have now turned on bind logging (all categories, debug 3) and am scouring them for patterns in these failures, but am not quite sure what I am looking for and there sure are a lot of them.  According to my housemate, there was a failure resolving i.imgur.com at around 15:43 today and in the attached log (named.log) I see activity starting at 15:43:33.346, but frankly have no idea whether this represents a normal operation or not.  The only thing which jumps out as odd was that at 15:40:46.636, the database category threw this: 'database: debug 1: decrement_reference: delete from rbt: 0xb5cdc008 3799-imgur-voxcdn-com.voxcdn.com'.  The removal time does not appear to tie in with the TTL I got from digging that host and any previous requests, however, any subsequent requests should surely just result in a cache miss and an upstream request rather than a complete failure.

Any ideas?

---

### Post by headvampyre@hotmail.co.uk on 2011-02-23
Have you tried settings DNS server addresses to any external ones on your clients to find out if its internal DNS? Ive had several issues like this with Ubuntu before

---

### Post by curiousornge on 2011-02-23
That's a fair point - no, I haven't.  I'll try that on my computer when I get home.

Did you ever resolve what was causing your issues?

---

### Post by headvampyre@hotmail.co.uk on 2011-02-23
Yeah, i dont actually know how though :^/ ive noticed issues in ubuntu tend to come and go for no apparent reason. If theres still a problem id recommend backing up your configuration files for Bind9 and reinstalling it, i run a fairly similar environment to yours, but with Samba4, and it works flawlessly.

---

### Post by curiousornge on 2011-02-24
Hmm, bypassing the nameserver seemed to work, so I backed up /etc and reinstalled Maverick from scratch, then copied the config files back.

Touch wood, bind now works fine.  Very strange.  :confused:

---

### Post by reneemariejones on 2012-07-08
I have exactly the same problem, with almost an identical setup.  Bind9, one internal domain, cache for external lookups.  Secondlife.com sometimes fails to resolve.  Restarting bind9 or waiting for the negative reply timeout will fix it until the next time.  I wondered if bind was just not waiting long enough for replies, but I could not find the timeout parameter to increase.  It is scary if a reinstall fixes things.

---

