---
title: "Over-Cautious,"
date: 2007-11-07
forum: Server Platforms
---

### Post by dburnett77 on 2007-11-07
May be over-concerned, but has anyone thought of devising a check-point so to speak.  War era talk, but seriously, if there were a site where users could register, and a small downloadable program ran a checksum (similar to MD5 and such) and upload vital areas according to their signature.  It could run a very quick comparison on affected areas.

I'd say among the boards, ea. user would need approx. 5KB on an average system spec.

The tree data, authorizations, and untampered data sig. could be stored for future reference.


:::Hailing from the State of Paranoia...

---

### Post by HermanAB on 2007-11-07
Every system is different...

Linux provides security in depth - multiple layers of protection:
User privelege separation
Servers run as unprivileged users
Netfilter
TCPwrappers
Syslog
SELinux

Your best defence maintenance is to periodically scan your logs.

Cheers,

Herman

---

### Post by dburnett77 on 2007-11-07
Good advice.  But, when I start seeing things in logs such as manual entered Addresses: ie;

[http://www.isc.org/sw/dhcp](http://www.isc.org/sw/dhcp)

there's a certain amount of hokey pokey going on.

I attempt to check my end via time=stamp, but that's a helter skelter game right now.
There used to be a good DOS program that produced checksums, which could be verified, and I'm aware of the linux install of AppArmor, but I'd like a throw myself; given the example.

---

