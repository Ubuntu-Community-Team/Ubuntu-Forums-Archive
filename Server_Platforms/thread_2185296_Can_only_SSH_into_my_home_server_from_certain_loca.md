---
title: "Can only SSH into my home server from certain locations"
date: 2013-11-01
forum: Server Platforms
---

### Post by achampsaur on 2013-11-01
Hello,
I recently set up Ubuntu on a Dell, and I'm hoping to use the computer as a file and web server. However, I'm not able to access it from just any location. I can ssh into it from two different ".edu" locations (using accounts on servers associated with two American universities), and also from an ssh terminal app on my cell phone (through Verizon), but not from any other location that I've tried, either wireless or wired. Here are some possible problems I've already addressed:
- I can successfully ping the server from any location
- if I try to ssh into it, it just times out without providing any additional information (even when using verbose flags)
- I've forwarded the correct ports on my router
- I've tried using different ports with no success
- my firewall should allow the correct port but is disabled anyways

Is it known that by default, Ubuntu only allows certain domains to ssh into it, or is this something that has more to do with my provider (Comcast)?
Has anyone else had similar problems?

Thanks

---

### Post by papibe on 2013-11-01
Hi achampsaur. Welcome to the forum ):P
> **achampsaur said:**
> Is it known that by default, Ubuntu only allows certain domains to ssh into it?
There's no such (default) restriction on both an Ubuntu installation or the ssh package.
> **achampsaur said:**
> is this something that has more to do with my provider (Comcast)?
It could be. I would use a port on the dynamic range (49152&#8211;65535) instead of ssh's default (22).

Having said that, if you were able to log from other places, it may not be a Comcast restriction.

My first guess would be to consider the restriction for outgoing traffic on the place you are trying to connect (place of business rules for instance).

Another thought: how are you connecting? Are you using a dynamic DNS service? Do you have an static public IP? If you are just using the last know IP, the ssh connection may be failing because of ISP DHCP renewal.

Just some thoughts. Let us know how it goes.
Regards.

---

### Post by achampsaur on 2013-11-06
> **papibe said:**
> 

Another thought: how are you connecting? Are you using a dynamic DNS service? Do you have an static public IP? If you are just using the last know IP, the ssh connection may be failing because of ISP DHCP renewal.



Thanks for the reply. I'm using my home network's public IP address, which always seems to be the same when I check online.

---

### Post by Iowan on 2013-12-31
Thread continues here:
[http://ubuntuforums.org/showthread.php?t=2196804](http://ubuntuforums.org/showthread.php?t=2196804)

---

