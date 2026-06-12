---
title: "Strange local domain BIND problems"
date: 2010-05-19
forum: Server Platforms
---

### Post by siersmak on 2010-05-19
Today my DNS servers, which I have sole control over and are not on the public internet, suddenly started denying DNS resolution for names that are within my local domain.  I had no problem getting DNS for hosts outside my domain.  I took down all the Windows machines on my network, thinking maybe one of them had a virus, but I still had the same problem.  I disconnected the wireless, but still had the same problem.  The named logs on my two DNS servers appeared to be getting the requests for all DNS requests, and I didn't see a discernible difference between requests that passed and requests that failed.  The only thing I saw was "Name or service not known" error messages when trying to slogin to different machines on the network.  

Anyone have any idea at all why all of a sudden the DNS servers would stop returning IPs for my local domain?

I "solved" the problem by putting /etc/hosts files containing all the local machines on each machine, but I've been running for years without having to do that and can't understand why all of a sudden I have to do it now.

---

