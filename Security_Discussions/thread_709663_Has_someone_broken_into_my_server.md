---
title: "Has someone broken into my server?"
date: 2008-02-27
forum: Security Discussions
---

### Post by kentl on 2008-02-27
Hi,

I became suspicious when I first started to see a lot of network traffic to my server. Sure it's a web server, but it just contains a page created my touch index.html and primarily serves as my FTP server.

Attached you will find my port forward settings on my router (dog) and the statistics from my server (cow).

What makes me even more suspicious:
[LIST]
[*]Port 1900 and 3000 of my server has been contacted the last minute, according to ntop. But it should be safe from the outside as my router doesn't forward those ports.
[*]15.1MB NFS traffic? I only sometimes use SSH internally and even then only to do command line stuff. No file transfers.
[*]Lots of NetBios IP traffic. I can't see why.
[/LIST]

What should I do to really see if I have some kind of intruder using my system?

Update: The files are here instead as they were too big to attach: 
[port range forward](http://w15.easy-share.com/1699715289.html)
[ntop statistics](http://w15.easy-share.com/1699715293.html)

---

### Post by HermanAB on 2008-02-27
Look for new user accounts in /etc/passwd.
Look at the system logs for login activity.
Run 'tcpdump -A -s 256 -i eth0' and look at the traffic.

If someone broke in, then you need to re-install the machine.

---

### Post by kentl on 2008-02-27
I couldn't find any new suspicius user accounts. But then again, I really do not know which ones should be there. As lots of packages creates new user accounts during installation (like ntop).

I checked my firewall incoming log. And I get lots of traffic to 42001 (my first open port for passive FTP). It's all rejected though. My server also seems to be in contact with Google a lot (from the outgoing log).

My SSH is using a key only login with a long and difficult passphrase. I should be secure. At least I think so. :lolflag:

---

### Post by nardis_Miles1 on 2008-02-28
I found myself on the CBL recently with no suspicious activity. I have checked my auth.log files and found no successes I couldn't account for. However, the offense to spamhaus happened when I was using wifi on a laptop  and logged in to the server. The laptop seemed infected because when I ran rkhunter it found several files, including chattr, that had the wrong size (this doesn't happen on a clean machine.) I found similar discrepancies on several machines behind the firewall. Thus, it seems I brought something home with me. Cleaning the machines has been problematic. 

The lesson I think I learned from this is that an ubuntu laptop on wifi should have security like a server (the same level of firewalling)

---

### Post by kentl on 2008-03-01
I'm on a LAN in a student corridor. My router firewall only protects me from WAN attacks and there are lots of computers on the LAN.

I don't think I've been attacked any more. But I will try rkhunter (never heard of it, hope it's in the repositories) and see what it reports. I guess I should also install a firewall on my server, as it's on 24h and has contact with my untrusted LAN buddies. I've been holding it off as iptables seems like a handfull to learn. :)

---

