---
title: "Deluge and Iptables."
date: 2010-11-10
forum: Security
---

### Post by zozza on 2010-11-10
Hello,

I am going to use iptables and ufw to lock down my system but I have a couple of questions first:

I am using Deluge for torrents and its preferences allow the setting of incoming and outgoing ports.

If I set outgoing ports to 25000 then netstat -anp --tcp shows:

tcp        0      0 MY IP ADDRESS:25000      201.61.129.148:17933    ESTABLISHED      

That looks fine to me.  

However, I am not sure of the point of restricting outgoing ports in conjunction with iptables because Firefox issues (AIUI) psuedorandom ports for web connections like this:

tcp        0      0 MY IP ADDRESS:55645    77.238.187.39:80        ESTABLISHED 4833/firefox-bin
tcp        0      0 MY IP ADDRESS:43598    87.248.122.122:80       ESTABLISHED 4833/firefox-bin
tcp        0      0 MY IP ADDRESS:55639    77.238.187.39:80        ESTABLISHED 4833/firefox-bin
tcp        0      0 MY IP ADDRESS:35135    209.85.229.148:80       ESTABLISHED 4833/firefox-bin
tcp        0      0 MY IP ADDRESS:33786    77.238.187.43:80        ESTABLISHED 4833/firefox-bin

Therefore, I assume there is zero point in restricting outbound ports because of these pseudorandom ports issued by Firefox?

Second, more importantly, incoming ports.

I have a direct connection (no NAT).  Having run Shield's Up from Steve Gibson's website on the "common ports", only 113 could be noted (it was closed).  The others were "stealth".  

The following shows the connection between me and a remote client using the tracker.

tcp        0      0 MY IP ADDRESS:33623    201.62.128.148:17933    ESTABLISHED 1704/python 

I entered 33623 into Shield's Up but it said it was not found ("stealthy"). 

I assumed the netstat result meant that my port 33623 was open although Shield's Up says no.  Have I been wrong to think that the ports connected to my remote torrent users are open?

If I set the incoming port to 6882 (rather than random) then netstat shows:

tcp        0      0 0.0.0.0:6882            0.0.0.0:*               LISTEN      1704/python 

However, does this prove that all incoming Deluge connections are only to port 6882?  Is there a way I can prove or disprove this?

Thanks.

---

### Post by zozza on 2010-11-16
bump...

---

### Post by Cas07 on 2010-11-17
Might be worth asking on the [deluge fourms]("http://forum.deluge-torrent.org")

---

