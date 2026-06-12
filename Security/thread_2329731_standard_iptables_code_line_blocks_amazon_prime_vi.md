---
title: "standard iptables code line blocks amazon prime video"
date: 2016-07-04
forum: Security
---

### Post by sidney256 on 2016-07-04
I run an iptables firewall on my debian toshiba laptop, and the main line that sets up the firewalling is

```
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
```

This line was chosen as the best way to go, but it is incompatible with the streaming of amazon prime video.  When I click on the green "watch video" button, absolutely no data flows from them to me.  I turn off the firewall and it works.  Amazon says their video is encrypted and sometimes problematic with firewalls, and that I need to open port 443.  

Yes there are other lines

```
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP
```

I also have the ssh and ftp ports blocked, lots of offending urls blocked, but it is the conntrack ctstate line that is the deal breaker.

I will not open port 443 to anyone anywhere.

I would rather not have to open it for amzn, as they may be constantly changing the urls they use, and also, I trust no one.  This would allow them to connect to my laptop after I shutoff amazon video and go to sleep.  They don't need that access.

I need a line of code that allows my clicking of the watch video button to initiate a connection with their streaming server.

What is that line? or What am I missing?

sidney

---

### Post by Doug S on 2016-07-05
Hi, And welcome to Ubuntu forums.

Without the context of your entire iptables rule set , it will be hard for us to help. I do not believe that the root issue is your "ESTABLISHED,RELATED" line. It may be that some packet sniffing using tcpdump (or wireshark, if you prefer) could help to gain insight into what is going on. Also watching the packet counters in iptables and adding logging statements to the rule set can help with debugging.

---

### Post by The Cog on 2016-07-05
Posting the complete output from the command **sudo iptables-save -c** would be a good start. 
Like Doug S, I don't think the conntrack line is the problem, because all that can do is to allow connections - it can't of itself block them.

Next, the output from **sudo tcpdump -np** while you try to start the video would probably tell us a lot.
You may need to specify the interface like **sudo tcpdump -np -i eth0** .

---

