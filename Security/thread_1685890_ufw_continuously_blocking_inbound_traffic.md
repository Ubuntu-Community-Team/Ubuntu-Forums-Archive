---
title: "ufw continuously blocking inbound traffic"
date: 2011-02-11
forum: Security
---

### Post by Stephen Morgan on 2011-02-11
My ufw is configured to deny inbound connections, just the default with no extra rules, and since yesterday I'm getting reams of log messages like this:  ```
Feb 11 16:44:06 newlands kernel: [99337.502951] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:72:ec:92:c4:30:46:9a:d0:28:59:08:00 SRC=[deleted] DST=192.168.0.4 LEN=64 TOS=0x00 PREC=0x00 TTL=46 ID=26923 DF PROTO=TCP SPT=21090 DPT=63279 WINDOW=65535 RES=0x00 SYN URGP=0 
```  I think it's the done thing to delete the incoming IP, but it never seems to be the same twice anyway. In this case it was a .th ISP, sometimes the whois shows Telstra in Australia or Verizon in America or something in the Korean alphabet and so forth. These messages are coming every few seconds, although not at a set interval but between 0 and 40 seconds apart.   Very annoying and seems to be slowing my connection down, and only happening since yesterday.  Another example:  ```
Feb 11 16:47:06 newlands kernel: [99517.419116] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:72:ec:92:c4:30:46:9a:d0:28:59:08:00 SRC= DST=192.168.0.4 LEN=95 TOS=0x00 PREC=0x00 TTL=114 ID=24229 PROTO=UDP SPT=22589 DPT=63279 LEN=75 
```  That's from a &quot;Opal DSL&quot; apparently based in Manchester, according to whois.  Now, I'm not running a server or anything, this is just a standard home computer and I don't have a lot of experience with security matters, so while the slightly slower connection is annoying I'm mostly curious as to why these characters appear to be trying to connect to my box.   Any ideas?

---

### Post by cariboo on 2011-02-11
It's probably the usual script kiddies trying to log into ssh.

---

### Post by Stephen Morgan on 2011-02-11
How would such a large variety of IPs come to be used by script kiddies? Would that be likely to be many people or something like a botnet? Also, as this has been non-stop for over twenty four hours, how much patience should I expect them to show?

---

### Post by cariboo on 2011-02-11
You could use something like denyhosts to block ip addresses after 5 attempts, or you could create an iptables rule to do the same thing, there are many examples in this sub-forum.

---

### Post by Kinstonian on 2011-02-11
Looks like you might be using bittorrent on port 63279.

---

### Post by Stephen Morgan on 2011-02-11
As ufw is blocking them anyway I'm not sure it would be worth blocking them again. As for torrents, I wasn't running any when it started and starting and stopping torrents hasn't made any difference, besides which my only torrent client isn't configured for that port.

---

