---
title: "dogtag pki"
date: 2021-01-31
forum: Server Platforms
---

### Post by uglyoldbob on 2021-01-31
Has anybody managed to setup a working dogtag pki service? I am trying to setup some test services to see if it has what I am looking for, but havn't made it particularly far.

I setup 389ds on my test system. (dscreate from-file blablab)
I setup a dogtag pki ca. (pkispawn -s CA -f filename.cfg)

When i try to go to a page served by the new instance, I get some interesting errors. I get error 404 on the unsecure port (description The origin server did not find a current representation for the target resource or is not willing to disclose that one exists.) and the https ports just timeout.

I was thinking maybe it has to do with the the hostname I type into my browser, but I setup the hosts file so that I can use the exact literal url reported by "pki-server status".

Any ideas on what I can do to get this working?

---

