---
title: "Security concern, need some help"
date: 2012-08-28
forum: Security
---

### Post by brandon88tube on 2012-08-28
I have a concern with some odd network behavior that I've been having and wanted to know if I should be concerned or not. 

The problem:
Upon having connection issues I decided to check my router logs and I found all of these entries indicating a lot of blocked outgoing packets. Example: Blocked outgoing ICMP packet (ICMP type 3) from 192.168.0.184 to 208.67.220.220 <- that being openDNS. The odd thing is, I cannot figure out what would be sending outgoing packets constantly. Out of curiousity, I booted into Windows and browsed around like normal online and then checked the log again. Not one single blocked outgoing packet. Then I booted back into Linux and right away my log was filling up with entries. My concern is that something malicious is trying to call home or something of the sort. I wanted to know if anyone could help me out with this.

---

### Post by Ms. Daisy on 2012-08-28
Open DNS is domain name service.  Your router is trying to resolve (for  example) "ubuntuforums.org" to an IP address because routers only  understand IP addresses.  Hence every time you go to a  new website, your router tries to resolve the name to an IP.  If you're browsing for a while you can imagine that you'd generate a lot of traffic to DNS.

If you don't understand ICMP type 3, have a look at this:
[http://www.networksorcery.com/enp/protocol/icmp/msg3.htm](http://www.networksorcery.com/enp/protocol/icmp/msg3.htm)

Basically the ICMP type 3 packets indicate that the destination is unreachable for these particular packets.  You can see what's going on yourself with 
```
traceroute 208.67.220.220
```
which will show you what routers your packet hits out on the interwebz as it travels to San Francisco (apparently where that IP for Open DNS lives).  

This link has more details about ICMP type 3 packets if you want to define precisely what's causing the error:
[http://support.microsoft.com/kb/325122](http://support.microsoft.com/kb/325122)

Have you configured your router to use Open DNS?  That should resolve the problem.
[http://use.opendns.com/](http://use.opendns.com/)

---

### Post by brandon88tube on 2012-08-28
Yeah, I already had my router set to openDNS and I knew what it was, I was just wondering why it was blocking them. It seemed suspicious to me, but it seems that is how the router labels unreachable destinations. I honestly didn't know what ICMP type 3 was. I should have Googled that, but my concern is what could be causing these. Even when I'm not doing anything it seems to still populate my logs. So, obviously something that I'm unaware of is trying to go to an unreachable destination.

---

