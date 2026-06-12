---
title: "Suricata &quot;recommended&quot; rule settings"
date: 2014-12-08
forum: Security
---

### Post by unite2 on 2014-12-08
Hi guys!

I'm trying to test Suricata IPS at the moment. In my environment it is the gateway between my two lab subnets and is running in NFQUEUE mode. I'm quite new to it, so for testing the IPS capabilities I've just modified all the rules from "alert" to "drop" using Oinkmaster. So, I can say, that it works. :) However, it blocks far too much, some simple legitimate traffic like rdp or smb takes very long to pass through suricata and i see some drops in the log - i guess if all rules are set to "drop" suricata becomes pretty paranoid. Can anyone advice any "recommended" rule setting? So for it to block traffic when it's 100% certain that it's under attack and be a little more patient on traffic which is very likely legitimate?

Thanks in advance.

---

### Post by unite2 on 2014-12-19
Can't anyone help?

---

### Post by bashiergui on 2014-12-19
I'd never heard of suricata until this thread. The most popular open source IDS/IPS is Snort by a landslide, you're far more likely to find help from a variety of sources with Snort.

I see that Suricata has an irc channel and a mailing list, those are probably your best bet at getting help.
[http://suricata-ids.org/support/](http://suricata-ids.org/support/)

---

