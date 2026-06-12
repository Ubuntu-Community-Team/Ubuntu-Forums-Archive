---
title: "OSSEC triggering on KMail IMAP access?"
date: 2008-11-16
forum: Security
---

### Post by needhelpplease on 2008-11-16
Server: Ubuntu Intrepid Ibex.  Desktop: Hardy Heron with KDE4.

I installed the latest version of OSSEC, and the version of Snort that is packaged for 8.10.

It was very easy to get it all set up and running.  I turned on active response, so that it would put in an iptables DROP against port-scanners, ssh-brute-forcers, etc.  I thought this would be a very good security measure, because I know we get ssh brute-force scanned constantly.  Sooner or later, some password could get hit.

I started it running, and a few minutes later, my SSH shell froze up and I couldn't access the web server.  It didn't take me too long to figure out I had been OSSECed out of my own server.

I logged in from another IP address, shut down ossec, removed the DROP from iptables, and then started to investigate what could be happening.

Looking in the logs, I saw a lot of alerts like:

```
** Alert 1226863114.12878: - ids,
2008 Nov 16 11:18:34 example->/var/log/snort/alert
Rule: 20101 (level 6) -> 'IDS event.'
Src IP: 68.164.234.162
User: (none)
[**] [1:100000135:1] COMMUNITY IMAP GNU Mailutils request tag format string vulnerability [**][Classification: Attempted Administrator Privilege Gain] [Priority: 1] 68.164.234.162:60761 -> 211.111.230.202:143
```

It looks like my IMAP client, which is KMail, is sending some string that is causing alerts within OSSEC / Snort, which in turn is triggering it to block the IP address.

I googled for this error and didn't find any info.  Any idea what's causing this?  Is there a way I can change one of OSSEC's rules to ignore this problem, so I can at least use it?

---

### Post by Kinstonian on 2008-11-17
The Snort's false positive seems to be the root cause of your problem.  You could find that snort rule and comment it out, but you might just be hit with some other false positive later that causes another DoS.  I'm sure OSSEC has the ability to use whitelists to prevent legitimate hosts from being firewalled, but I don't have much experience with OSSEC.  There is a book that looks good called [OSSEC Host-Based Intrusion Detection Guide](http://www.amazon.com/OSSEC-Host-Based-Intrusion-Detection-Guide/dp/159749240X/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1226928811&sr=8-1).  It looks like it's a must read for anyone using OSSEC.

Edit:  You can use a whitelist by adding the hosts between the <white_list></white_list> in your ossec.conf file.

---

### Post by needhelpplease on 2008-11-17
Thanks for the info.  I'll look for the Snort rule.

I can't whitelist because we have users from all kinds of IP addresses.

---

### Post by bodhi.zazen on 2008-11-17
Yes, you will have to fine tune snort, snort rules, and ossec rules.

You are best off white listing at least 1 IP address to allow remote access while you go through the process. Just take care you understand what you are doing before you inactivate a rule.

---

### Post by needhelpplease on 2008-11-18
I found the rule that is triggering this.  It's in Snort's community-imap.rules.  Should I just delete that rule in that file, or is there some place where I should store my "local" configurations, that override the community rules?  I'm worried that if I do an upgrade, that rule will be replaced and my IMAP will again lock me out.

I'm sure I don't need the rule.  It's only for an exploit in GNU Mail, which I'm not using, and which was fixed 3 years ago.  I do wonder what on earth KMail is doing that is mimicking the exploit, but it doesn't really matter.

---

### Post by Kinstonian on 2008-11-18
I would try putting that rule in your local.rules file and replace the "alert" in the rule with "pass".  The local.rules file shouldn't be messed with during rule updates, and the telling it to "pass" says it will ignore the matching packet(s) it rather than alert.  Keep in mind, while I have read a book on snort, it was a while ago.  You might want to wait for bodhi.zazen for confirmation.

---

### Post by bodhi.zazen on 2008-11-18
> **needhelpplease said:**
> I'm sure I don't need the rule.  It's only for an exploit in GNU Mail, which I'm not using, and which was fixed 3 years ago.  I do wonder what on earth KMail is doing that is mimicking the exploit, but it doesn't really matter.

Good to see you have done your home work ;)

Personally I would just comment out the rule by adding a # in the front (if you are going to ignore it why not just comment it out). Take that advice with a large grain of salt as I do not consider myself an expert on the subject.

How much time do you want to spend on snort rules ?

But that brings up a good point, how to maintain your rules ?

Take a look at oinkmaster

[http://oinkmaster.sourceforge.net/about.shtml](http://oinkmaster.sourceforge.net/about.shtml)

---

### Post by needhelpplease on 2008-11-19
Thanks for the info Bodhi.  I did that, I just commented it out.  Really, that rule should be removed; no one should be running such an out-of-date IMAP server at this point.

With that one rule gone, I'm getting no false positives, and it's great.  It detects when some zombie is trying to probe it for bogus email addresses, because it reads the mail log, and when it sees such a zombie, it just firewalls it out.  Saves load on the mail server, probably cuts out some spam, and prevents attacks.

I've only been running it for less than a day but I have noticed in the past ssh-brute-force attacks, and it looks like OSSEC would easily stop those cold.

I need to also tell it to start looking at my JBoss server logs for various web attacks.  Not that any of it is vulnerable; I have JBoss very locked down. But still, better to drop those zombie packets.

---

### Post by bodhi.zazen on 2008-11-19
yes, but ...

Don't forget you are trying to detect suspicious traffic, so in general, you want to be aware of suspicious activity, even if you are not vulnerable to it.

The "problem" is that you are detecting it with OSSEC which then responds by banning, in the case of a false positive, legitimate activity, so yes you are needing to modify (remove) that rule.

This is where something like snort comes in handy :) Snort can detect the activity ...

And it depends on your level of paranoid, why allow someone to probe your server ?

This is why the rule set is merely a starting point, it almost always needs to be fine tuned. I am not trying to be disagreeable, just pointing out the utility of "false positive". If I see a repeat offender in terms of IP, I black list the IP address in my firewall.

At any rate, it looks as if you have gotten off to a great start and certainly are on the right track. I love the way ossec hammers the script kiddies :)

---

### Post by needhelpplease on 2008-11-19
> **bodhi.zazen said:**
> And it depends on your level of paranoid, why allow someone to probe your server ?

Right, if they're probing, that's only the first step, and if they throw out 100 probes that don't work, maybe they will hit on one that does.  Better to block them as soon as they have proven themselves to be problematic.

> **bodhi.zazen said:**
> This is why the rule set is merely a starting point, it almost always needs to be fine tuned.

That's what I'm learning.  Snort started rejecting connections because one of my URLs is /calendar which triggered some rule.  I found it and removed it.  This will be an iterative process, of seeing where I get blocked and fixing the rules.  Better to start too-secure and then loosen up than the other way around.

Running this and looking at how many hosts get blocked makes it really concrete the situation we're in.  There are vast botnets out there, attacking all the time, with constantly updating attack methods.  I used to think a plain old firewall was enough, but these guys are trying everything.  Now that I'm running Snort / OSSEC I realize that I need them.

> **bodhi.zazen said:**
> At any rate, it looks as if you have gotten off to a great start and certainly are on the right track. I love the way ossec hammers the script kiddies :)

It sure does, and the spam-zombies, which is a double-benefit.  Now that I understand about needing to tune the rules I'm liking the whole system.

---

### Post by needhelpplease on 2008-11-19
I think I'm going to need to adjust a lot of the rules.  Somehow JBoss Seam + RichFaces is really triggering it.

---

### Post by bodhi.zazen on 2008-11-19
Just a small clarification ... 

Snort will not trigger any response, it is ossec (which is monitoring for snort alerts).

Once the dust settles, consider reporting these false positives to snort and ossec, as they can hopefully refine the rules ;)

---

### Post by Kinstonian on 2008-11-19
It's great you're actively trying to detect intrusions, but just so you know, intrusion detection is more than an automated IDS/IPS.  You can also detect intrusions manually if you have the appropriate network data.  For example some more tools are:

1.  [httpry](http://dumpsterventures.com/jason/httpry/), which creates proxy like logs of HTTP data.  Having this enables you to grep through it looking for say, suspicious files that your server may of downloaded from Russia at 3:00 AM.  Knowing a workstation downloaded 1.exe, cwkdx.exe or svchost.exe could also be a good lead.

2.  [Argus](http://qosient.com/argus/) creates session data, which although is just a summary of communications between two computers, it can often be more valuable than an alert from an IDS.  You can use BPFs to continually discard sessions that you know are good until you are left with the more suspicious and interesting sessions.  For example you could systematically discard all expected traffic (maybe just HTTP and SSH) relating to your web server, leaving you with only sessions of interest.  If you see your web server made 100's of connections to hosts on the internet for port 445, made a connection to an IRC server, or a FTP server in China, you've probably detected an incident.

3.  [tcpdump](http://www.tcpdump.org/) allows you to log full content data.  I'm sure it sounds like a lot of data, but using BPFs you could really narrow it down.  For example a filter like *not (dst host 192.168.1.101 and tcp dst port 80) or (src host 192.168.1.101 and tcp src port 80)* would log all traffic not relating to HTTP for your web server (192.168.1.1).  If you filter out all the traffic you expect, and only log the unexpected, you have just what you need.  For example you could get the FTP username/password, as well as the files that your computer downloaded or uploaded to another country.

The best thing (if you have the resources) would be to log all types of data.  For example if your web server got hacked, you may not have full content tcpdump data of the exploit because normal HTTP traffic was discarded, but you have the Snort alert.  You also have the Argus session data relating to the alert.  Nearly all attacks will initiate an outbound connection so if it's HTTP, you have the httpry proxy logs to see what files were downloaded.  You have session data to see all of the connections that happened around the incident.  As well as tcpdump logging all unexpected traffic so you could for example view all IRC traffic in Wireshark if your server became part of a botnet.

Just keep in mind that defense in depth is just as important in detection as it is in prevention.  For example if Snort didn't alert you to an incident, you could probably detect it using Argus.  Using different tools like this provides you with greater network visibility.  After all, you can't defend your network if you don't have access to data about the state it's in, or what is happening on it.  You can check out the [NSM Wiki](http://nsmwiki.org/index.php?title=Main_Page) for more information on Network Security Monitoring if you want...

---

### Post by bodhi.zazen on 2008-11-20
Thank you Kinstonian for taking the time to give such sage advice.

IMO people really benefit from taking a more active approach to security.

---

### Post by Kinstonian on 2008-11-20
No problem man...  Just spreading some information around, hopefully it will help make the internet a better place. :)

---

### Post by stmurray on 2008-11-21
You really should update your snort rules in the local.rules.  The reason being if you update your rules (like using oinkmaster), I believe it will overwrite the edits you have made in the default rule-set and you will have to go back an fix them again, (or it may not add new important rules into that file, if it believes you have updated the file and therefore will not update the file.  I can't recall how oiknmaster works)   But generally, for ids, you should fix false positives by updating your local rules to ignore or "override" the false positive.  And it's always a nice idea to notify the IDS owner or maintainer of the false positive as they may want to fix the rule.

---

