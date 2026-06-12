---
title: "Possible to block aim with SSH server?"
date: 2009-04-17
forum: Server Platforms
---

### Post by jigglywiggly on 2009-04-17
So say I have a SSH server running on ubuntu (openSSH)
Would it be possible to like block these
login.oscar.aol.com:443
login.oscar.aol.com
toc.oscar.aol.com 
login.icq.com


I am just asking out of curiosity really, because this could be potentionally useful in the future. Or would you need a transparent proxy server using something like squid?

BTW(This is assuming they will use a dynamic socks proxy to connect and it will be set in their internet options)

---

### Post by iponeverything on 2009-04-17
Not sure what you asking.


You want to block access to those sites? Block access from those sites? And I am not sure where the ssh server comes into the picture.

---

### Post by Bachstelze on 2009-04-17
A way do do this would be to att lines for those hostnames in [font="monospace]/etc/hosts[/font] with IP address 0.0.0.0. Thus, when the system will match those hosts to that IP address instead of their "real" one, and the users won't be able to connect to the service they expect by using them.

For more flexibility, you could also use iptables, but that would be a little bit more complicated.

---

