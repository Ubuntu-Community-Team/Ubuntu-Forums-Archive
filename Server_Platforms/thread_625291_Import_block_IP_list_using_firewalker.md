---
title: "Import block IP list using firewalker"
date: 2007-11-27
forum: Server Platforms
---

### Post by will_i_am on 2007-11-27
I have a block IP list I wish to import into my firewall that uses Firewalker. I am happy with terminal commands. There are some 10,000 IP's so I can not import using the add 1 GUI. Can someone explain how I can do this?

Thank you,
will_i_am

---

### Post by HermanAB on 2007-11-28
10,000? Nope, that is the wrong way to filter large lists.

Rather look at squid-cache and squidguard, or dansguardian.   These tools are designed to filter large block lists without slowing the system down. Squidguard can easily handle hundreds of thousands to millions of entries.

Cheers,

Herman

---

### Post by will_i_am on 2007-11-28
Thank you. I will look at this.

---

### Post by will_i_am on 2007-11-28
I installed squid and squidguarden. When I attempt to run I get this:

william@william:~$ squid
FATAL: Unable to open configuration file: /etc/squid/squid.conf: (13) Permission denied
Squid Cache (Version 2.6.STABLE14): Terminated abnormally.
CPU Usage: 0.004 seconds = 0.004 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted (core dumped)
william@william:~$

---

### Post by HermanAB on 2007-11-29
There are a few tricks to it.  See this older guide of mine:
[http://aeronetworks.ca/squidguard-howto.html](http://aeronetworks.ca/squidguard-howto.html)

Cheers,

Herman

---

### Post by will_i_am on 2007-11-29
Thank you. I will try this. 

William

---

