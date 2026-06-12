---
title: "Ubuntu Updates"
date: 2017-01-03
forum: Security
---

### Post by poisonfor3 on 2017-01-03
Ubuntu is asking to update TOR Browser and some other programs that I know are up to date because I use the program its self to update them. 

TOR browser is 100% stock. When I click on the check for updates from  within Tor-browser it says it is up to date. When I click the about I  have "6.0.8 (based on Mozilla Firefox 45.6.0)". Yet I run the apt-cache policy tor-browser

```
tor-browser:
  Installed: 6.0.5-1~webupd8~0
  Candidate: 6.0.6-1~webupd8~0
  Version table:
     6.0.6-1~webupd8~0 500
        500 http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu xenial/main amd64 Packages
 *** 6.0.5-1~webupd8~0 100
        100 /var/lib/dpkg/status


```

So if I have 6.0.8 installed why does it think I have 6.0.6 installed?
Seems kinda funny. 
How do I know the repositories have not been compromised like what happened with Mint a wile back?

I could not find that any one else had this problem. Any help to address this concern would be nice.
Thanks

---

