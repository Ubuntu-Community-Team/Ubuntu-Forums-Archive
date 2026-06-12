---
title: "Ubuntu on Dell SC1425 Server"
date: 2005-03-19
forum: Server Platforms
---

### Post by Ubuntu Warrior on 2005-03-19
Anybody had any success installing Ubuntu on a Dell SC1425 server? Have just purchased two of these for our business and looking to set up one for managing our Internet connectivity (Apache, Squid, etc.) - maybe also act as our main web server in future if Ubuntu proves to be stable. The other one is planned to host a MySQL/PostgreSQL database for gathering management statistics from RRDTool, MRTG, Cacti, etc.

Spec on servers:

3GHz Xeon Proc
2 GB Memory
140GB Storage

Any advice on how to get started and what to watch out for would be appreciated.

---

### Post by defkewl on 2005-04-04
Can you please state your problems?

---

### Post by Ubuntu Warrior on 2005-04-26
No problems yet! Just wanted to get an idea of the risk level in implementing on the Dell SC1425 server. We have gone ahead with the install anyway and now have a half-working Ubuntu-based proxy server in production. Why half-working? Well, we have tried all angles and cannot get the Squid proxy to authenticate from our Windoze domain. Wanted to be able to control Internet access by account name (eg. freds, bobj, simong, etc.) but had to settle for IP-level controls. Not ideal but will work until we have an answer. The SAMBA stuff works perfectly and we can 'see' the Windoze domain from the Ubuntu proxy with no problems - can even authenticate a user successfully (using wbinfo -a mydomain\\myuser%mypasswd).

Will appreciate any help on getting Squid to authenticate seemlessly with a Windoze domain i.e. no challenge when user tries to use the proxy to exit the local network.

---

### Post by neuromystical on 2005-05-28
I personally would not use Ubuntu for your internet connectivity, have you looked at [www.smoothwall.org](www.smoothwall.org), it has squid and modifications to work with domains and is pretty darn easy. I have a few PII's working as my firewall/router/squid/STATS/ETC... I would use these two Dell's power for more important things.  Ubuntu can do the job very good, but why when there is a open community already established for Internet connectivity and security. I would personally set these two boxes up the same and use one for the production enviroment and the other for a DEV system to test your updates and such on. Especially since you say you are using this for business.

Make sense?

---

### Post by Ubuntu Warrior on 2005-06-22
See where you are coming from but we have about 5 Ubuntu Linux servers already deployed in the business doing various things. Naturally we would like to stick with something we know and trust (our entire business is in full support of Ubuntu - both on the server and desktop). We have successfully installed and deployed a working Squid caching/proxying system on the Dell server - only problem is that we have not yet configured RAID on the two internal drives (we want to mirror the disks for increased redundancy). Also still cannot auth from the NT network but this is not a crisis point as we are planning to replace the NT network with an Ubuntu Linux one by the end of the third quarter.

So I guess - thanks but no thanks! Ubuntu is a great flexible and practical solution delivering sound business value in our organisation.

Free your software ... Ubuntu Linux!

---

### Post by Ubuntu Warrior on 2006-01-30
Just a general update ...

We have switched most of our servers onto Breezy (this is more like it - well done Ubuntu coding junkies :) ) and have got some reasonable software RAID working with the ones that don't have hardware RAID controllers.

Have also finally managed to get Open-Xchange working on Breezy - looks very promising but hope those ox folks haven't stopped work on making the install process easier. The Fantoma HOWTO helped somewhat but we came across some basic errors - both on his side and on ours! Looks like we might have a replacement for M$ Exchange afterall. If ox doesn't cut it Zimbra also seems quite capable.

---

