---
title: "Power DNS Troubleshooting"
date: 2013-02-14
forum: Server Platforms
---

### Post by villie on 2013-02-14
I'm installing a name server for educational purposes but I've already hit a snag. I've installed Power DNS on a localbox running 12.04 (desktop) with mysql & poweradmin. I've setup a zone and the wildcard sub-domain resolves but the root domain does not. 

For example, if I "dig [www.devconnect.net](www.devconnect.net) any" I get an A-record answer section that is points to the correct IP. If I "dig devconnect.net any" I don't get any answer section. Same result doing "nslookup" although it says 'Non-authoritative' answer:' doing the sub-domain.

I do notice that I get a message in my syslog of "Should not get here (devconnect.net|1): please run pdnssec rectify-zone devconnect.net". I'm not entirely sure what that message means (would be great if someone could explain it) but I do as it says and run the command. It gives me an error of "Unable to connect to database" (pdns). Straight forward enough, but I can't find the config file to correct this error (I've tried "pdns.d/pdns.local" & "pdns.d/pdns.local.gmysql").

So I have two questions I guess: 1) Can someone provide some direction on resolving my issue of the root domain not resolving? 2) How do I setup pdns so the 'pdnssec' command works?

Cheers.

UPDATE & SOLUTION (19/2/2013)

I stumbled upon [this bug.]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=656292") It seems as though the 'include' directive at the bottom of the main config file is not executed. After moving my gmysql config from /etc/powerdns/pdns.d/pdns.local to the bottom of the main config file (/etc/powerdns/pdns.conf) and commenting out the 'include' directive, I was able to use pdnssec command without errors.

Now running 'pdnssec rectify-zone devconnect.net' I get the result of 'Adding NSEC ordering information' and now a 'dig devconnect.net any' returns the correct results.

---

