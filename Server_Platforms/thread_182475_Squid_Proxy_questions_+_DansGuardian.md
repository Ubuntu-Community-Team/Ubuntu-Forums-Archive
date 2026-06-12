---
title: "Squid Proxy questions + DansGuardian"
date: 2006-05-26
forum: Server Platforms
---

### Post by Lugia on 2006-05-26
Hi there doods, since this is my first post here I'll try to do a nice post:

Actually I'm using my Ubuntu box as a multimedia viewer (32" TFT) in my cibercafe, for that I just use tomem-xine + win32codecs to display videos, appart from WMV10 videos, everything works fine, same goes for radio broadcastings.

In the other side, I've setup an squid proxy cache to do caching of the html requests, it works fine and transparent.

Appart from that I've some doubts, I've seen in the repository a packet called "Squid-Prefetch" and I'm not relly sure if it will help me save B/W or if it will kill more :\ I'd really apreciate some words into that packet and if anyone knows I'd really apreciate an how-to or something like (I've search yet in google with no luck -.-)

And what I more really need help with is DansGuardian, I don't have no fck** idea of where to start :S

Thanks in advance.

---

### Post by Lugia on 2006-05-27
*bump*

---

### Post by Abhi Kalyan on 2007-01-29
Hi could you please give the method you used to mnake a transparent proxy?

---

### Post by schizoman on 2007-09-13
Hope I understand your question right. I'm being lazy, and am using Feisty desktop rather than server.  I'm just setting it up now to be a proxy server.  So far, so good.  Here's what I did:

1) Installed Squid 2.6 via Synaptic Package Manager.

2) Edited the extremely large (but informative) configuration file (sudo gedit /etc/squid/squid.conf) and did the following:

Uncomment the line that begins with "acl our_networks src" 
and make sure that the network IP matches yours.  (in my case, this would be 192.168.1.0/24)

uncomment the line that reads "#http_access allow our_networks"

Examine the line that contains "http_port 3128".  If it's commented, uncomment it.  If you want to change the port, that's fine.  I left it at 3128.

3) Save the configuration file then restart Squid (sudo /etc/init.d/squid restart).

4) Configure your browser to use your proxy server.  In Firefox, go to Edit->Preferences->Advanced.  Click on the "Network" tab, then the "Settings" button.  Select the Manual Proxy Configuration radio button, enter the proxy server's IP address next to HTTP Proxy, and 3128 (assuming that you didn't change this in squid.conf) for the port. Restart your browser.

If you want to be sure that you're accessing the internet via the proxy, type the following in a terminal window:

sudo tail -f /var/log/squid/access.log

===========

I did this and tried a test site.  First load was over 6 seconds.  I cleared the browser cache and forced a refresh.  This time, it only took 2.1 seconds to load, since it was in the proxy server's cache.

Hope this helps.  --schizoman

---

