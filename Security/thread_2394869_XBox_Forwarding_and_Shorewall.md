---
title: "XBox Forwarding and Shorewall"
date: 2018-06-22
forum: Security
---

### Post by jmarsz on 2018-06-22
I need a bit of help here.  I'm trying to be able to Stream from my XBox to my computer over the internet.  From the instructions I have read, I need the following ports open:

4838
5050
49000-65000

These are both UDP and TCP.  So in my Shorewall rules, I have written the following:

#Allowing XBox Streaming from the Net to the Xbox
DNAT            net             lan:192.168.0.151 tcp   5050
DNAT            net             lan:192.168.0.151 udp   5050
DNAT            net             lan:192.168.0.151 tcp   4838
DNAT            net             lan:192.168.0.151 udp   4838
DNAT            net             lan:192.168.0.151 tcp   49000:65000
DNAT            net             lan:192.168.0.151 udp   49000:65000

It sees the XBox One from the program, and says it's connected, but the streaming then reports that there's a network quality issue.  From what I can tell, it's the port range where that streaming connection comes through, and I'm not 100% sure I have shorewall set up correctly.

Does this configuration look correct?  The 192.168.0.151 is the IP of the XBox One on the Internal network.

Thanks!

---

