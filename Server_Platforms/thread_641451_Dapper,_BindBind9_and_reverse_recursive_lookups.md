---
title: "Dapper, Bind/Bind9 and reverse recursive lookups"
date: 2007-12-15
forum: Server Platforms
---

### Post by jbalders on 2007-12-15
I have this annoying but minor problem with two Dapper servers running bind9 (latest updates, no backports).  I've been through the config and logs backwards and forwards and can't seem to find a good reason for it.   Both systems are otherwise stable, have static IP addresses on 100MB ethernet connections (in other words, no DHCP, no ppp, no WLAN).  

I run other DNS servers, and haven't experienced this problem anywhere except for these two.  The other servers include dapper, gutsy, Centos4  There are no errors in the logs to indicate problems.  Both of the problem servers are SPARCs, but I can't see why that should matter for something like Bind.

After a reboot, neither one will do a reverse recursive lookup.  If I issue a "/etc/init.d/bind9 restart", reverse recursive lookups will then work correctly.  Since it'll work correctly after restarting bind, it suggests that my Bind configuration is good.  It's also possible that it stops performing recursive lookups after a while, but I don't have anything to back it up right now.

So, I have two questions:

1) Has anyone experienced or heard of this problem?
2) Did you fix it?  How?

I'm running dapper because I wanted to use an LTS release, so I'd rather not upgrade if at all possible.

Thanks.

---

### Post by koenn on 2007-12-15
to answer your questions : 
1) no
2) no

Did you look at /etc/init.d/bind9 ? Does the case "restart" do anything else than "stop", then "start" ? 
if so, that's a clue
if not, maybe something in the "stop" case makes the thing work on "restart", but not on "start".
see if you can find anything there

---

### Post by HermanAB on 2007-12-16
Well, the init scripts frequently do things that they should not.  To me, BIND generally works when run directly and fails when run from the <insert your favourite distro> init scripts.

So, I have gotten into the habit of always making my own super simple init script for BIND, which generally amounts to inserting the single word "named" at the end of /etc/rc.d/rc.local or something equally schtoopidttt.

Oh, well, what the hell...

Cheers,

Herman

---

