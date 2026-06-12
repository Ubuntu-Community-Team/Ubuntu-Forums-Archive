---
title: "AV Gateway?"
date: 2008-04-07
forum: Security Discussions
---

### Post by Mastermind007 on 2008-04-07
Fairly new to Ubuntu but I am willing to read, research and test. Just need a point in the right direction.

I currently have a 7.10 box running nTop with dual nic's that all other PC's on the network go through. I like the transparent nature of nTop. I have a hardware firewall and I do not need another firewall that I would need to open ports on so it works great.

Other than nTop this is a plain out of the box install that is fully updated.

I would like to have this box serve as an AV gateway since all the traffic is going through it anyway and the nature of Linux makes it resistant to 99.9% of the bad stuff out there it would be perfect.

How is the best way to proceed?

What I would like to end up with is a gateway that is transparent that gives me the ability to scan for virus and provides the network monitoring.

Thanks

---

### Post by HermanAB on 2008-04-07
There are a number of scripts that work with Squid-Cache, to run ClamAV on downloaded files.

Cheers,

Herman

---

### Post by Mastermind007 on 2008-04-08
Thanks for the info HermanAB. I will start reading up on Squid and ClamAV

---

### Post by HermanAB on 2008-04-08
There are some guides on my web site for Squid with a script I wrote which may be all you need, but there are likely better ones out there by now:
[http://aeronetworks.ca/clamav-squid-howto.html](http://aeronetworks.ca/clamav-squid-howto.html)
[http://aeronetworks.ca/willowbark-howto.html](http://aeronetworks.ca/willowbark-howto.html)

---

