---
title: "directory access and traversal attempts in log files"
date: 2009-07-20
forum: Security
---

### Post by arsnova on 2009-07-20
I have two questions:

1) BASE reports a fair number of "WEB-PHP directory.php access" alerts, and my log files return these with 200 status. Since this file doesn't exist, are these unsuccessful probes, or are these even of a malicious nature? I'm not sure otherwise why these would be collected by BASE.

2) More concerning is the following reported by OSSEC: "A web attack returned code 200 (success)." My log file read as:

----------
XXX.XXX.XXX.XXX - - [--DATE/TIME REMOVED--] "GET /name-of-file.php?var=Resources/file-name.php?variable=../../../../../../../../../../../../../../../etc/passwd%00 HTTP/1.1" 200 5438 "-" "libwww-perl/5.80
----------

This directory traversal does not correlate with my filesystem, so I'd like feedback about the 200 status. Does this mean only that the page was returned to the browser successfully, or does it imply that /etc/passwd was compromised? I'm running the input from GET through a sanitizing function.

Thanks, everyone.

---

### Post by bodhi.zazen on 2009-07-20
Those logs are of the more grey / black hat type. They are trying to get your http server to display the contents of /etc/passwd, :lolflag:

This is where selinux and apparmor shine, why is apache trying to access /etc/passwd ? => block with apparmor or selinux.

Did you scan yourself with a scanning tool ?

Otherwise , usually, OSSEC will simply echo what snort (base) detects and will usually ban the offending IP. So long as ossec is working (you should test that) you probably do not need to do anything else (unless they do not go away fast, in which case black list the ip if you wish).

Snort rules are very generic and may or may not apply to you. Look up the rule in your data base or on the internet (links provided in base) for more info.

Pick your poison. Most scanners will scan for multiple vulnerabilities , for windows and Linux hosts. Assuming you are not running windows, you can delete the windows alerts, however you lessen the sensitivity of your system. You can delete the windows rules and increase the specificity at the expense of sensativity.

Most people use snort as an early warning system and accept false positives. See NIDS vs HIDS ;)

Some people simply collect baseline data on "normal activity" (you will get some noise so long as you are connected to the internet) and then statistically analyze the data and only concern themselves with deviations from the norm.

Personally I assume I will get many false positives and block persistent cracking attempts (multiple attacks from an IP over multiple methods and multiple days) and watch my host OSSEC for successful attacks.

The point is, now that you are aware, start watching. So much better then a flash on your desktop every time your firewall blocks a packet, no ? This is giving you information on what is happening on your network and is usually enough to stir a little paranoia.

At the end of the day it is an art and you will get a feel for it if you just keep watching ;)

/me likes to watch.

---

### Post by arsnova on 2009-07-20
Thanks, Bodhi. I've had to step out of my more customary role in recent months, so I'm picking up quite a bit on security. Your thread postings and explanations have been indispensable. Not to sound like a fanboy. :)

I've become a log addict, and I know OSSEC is doing its job well in responding to unwanted activity. I've locked myself out several times when testing through a non-whitelisted VPN connection. I haven't adjusted any of the Snort rules, so I'm accustomed to getting a fair number of alerts via email. 

The question (#2 from my post) was the first of this particular activity I've seen, and I wanted to be clear that I understand what BASE is telling me--or at least suggesting I investigate. I'll read more carefully the AppArmor sticky. This seems to make it more relevant. I'm seeing a lot of activity from #1, though, even from my own IP--does this suggest a configuration problem?

I've used Sara for scanning, and I'm waiting for results from a comprehensive third-party pen test. I do sense that it's more than science, as you say it's an art--it just happens to be that my colors are a little muddy right now (but I like earthtones!)

Thanks!

---

### Post by bodhi.zazen on 2009-07-20
To be honest, I do not know off the top of my head :)

A code of 200 == success so apache may well have displayed /etc/passwd .

The logs will tell you if you keep reading them they start to make sense.

Most likely these alerts are coming from either your test or the 3rd party. Probably best to turn ossec off for testing & back on when testing is done, or even better one set of tests with ossec off and one with ossec on ;)

---

