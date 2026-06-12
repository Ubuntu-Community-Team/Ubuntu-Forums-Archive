---
title: "Shields Up!"
date: 2007-04-20
forum: Server Platforms
---

### Post by jmemm37 on 2007-04-20
I just went to the web site Shields Up! and ran their 3 tests that they have for port scans and it is TRUE. Ubuntu is literally stealthed out of the box. The one thing I failed was my computer responded to the ICPM Ping that the sight sent to my computer which means my computer is visible on the internet. I installed Firestarter just a few minutes ago and enabled the filter for echo response and it still responds to the ping request. Any ideas on how to block the ping? Is that something to do with my firmware firewall in my router or is there something I can do to my computer for the solution?

---

### Post by MJN on 2007-04-20
As you've got a NAT router it's likely it that is responding to the PING requests as unless you've explicitly specified where you want pings to be forwarded to it wouldn't know which computer on your LAN to send it to.
 
Hence, to stop ping responses will require you poking around in the config pages of your router - it should be there somewhere (anything to do with WAN ICMP responses etc).
 
Mathew

---

### Post by jmemm37 on 2007-04-20
Thanks you for the advice! I went to my wife's desktop where my wireless router is hooked up and went to its utility page and blocked the ICPM Ping. After doing this, I went back to the Shields Up website, ran the test and got a perfect stealth score for my laptop. Again, thanks!!!

---

### Post by BitHosts on 2007-04-21
I hope you realise that the router is also likely to be blocking everything else - not ubuntu - as that is sitting in front of the linux box...

Im not syaing either way whether Ubuntu is stealthed out of the box but with routers in the way unless its on a DMZ then the tests youve run arent conclusive.

---

