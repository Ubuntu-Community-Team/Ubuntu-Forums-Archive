---
title: "Security Checklist"
date: 2011-09-08
forum: Security
---

### Post by Depravitus on 2011-09-08
Hey all.

Just wondering if some of the security gurus could do a casual audit of my security and let me know of any big holes I need to plug.

I'm aiming for a 7-8 out of 10 on security, 1 being "durrr" and 10 being "Google is reading my brainwaves!"

I have UFW configured to auto-DENY all incoming/outgoing traffic save for safe ports I've designated. (Verified with Umit) 

I have ClamTK installed to scan occasionally so I don't pass on any intarwebz STDs. 

Firefox is running AdBlock, strict NoScript profile, and of course common sense browsing.

My /home directory is encrypted via standard Ubuntu encryption. Haven't gotten to anything else yet. All sensitive documents are kept in pass protected encrypted directories.

Next big hurdle is getting a secondary system set up with user > (squid?) > privoxy > tor > internet setup... designed as a 'transparent proxy' to handle ALL outgoing traffic. Production system will be routed through this mini proxy server. Haven't had much luck here yet.

I'm mildly concerned about the more obscure weak points that I may not be aware of, especially with all the 'lulzsec' and sundry hacking that took place recently.

Anything I'm missing? Thanks for reading.

---

### Post by haqking on 2011-09-08
> **Depravitus said:**
> Hey all.

Just wondering if some of the security gurus could do a casual audit of my security and let me know of any big holes I need to plug.

I'm aiming for a 7-8 out of 10 on security, 1 being "durrr" and 10 being "Google is reading my brainwaves!"

I have UFW configured to auto-DENY all incoming/outgoing traffic save for safe ports I've designated. (Verified with Umit) 

I have ClamTK installed to scan occasionally so I don't pass on any intarwebz STDs. 

Firefox is running AdBlock, strict NoScript profile, and of course common sense browsing.

My /home directory is encrypted via standard Ubuntu encryption. Haven't gotten to anything else yet. All sensitive documents are kept in pass protected encrypted directories.

Next big hurdle is getting a secondary system set up with user > (squid?) > privoxy > tor > internet setup... designed as a 'transparent proxy' to handle ALL outgoing traffic. Production system will be routed through this mini proxy server. Haven't had much luck here yet.

Anything I'm missing? Thanks for reading.


Sounds reasonable.

for tor see here [https://www.torproject.org/docs/debian](https://www.torproject.org/docs/debian)

pretty straight forward

---

### Post by Depravitus on 2011-09-08
Thanks for the reply.

Agreed, standard Tor configuration is extremely easy. It gets a bit more complex when setting up a transparent proxy though... routing ALL outgoing traffic from a system through it. Normally only designated SOCKS capable programs work.

---

### Post by haqking on 2011-09-08
> **Depravitus said:**
> Thanks for the reply.

Agreed, standard Tor configuration is extremely easy. It gets a bit more complex when setting up a transparent proxy though... routing ALL outgoing traffic from a system through it. Normally only designated SOCKS capable programs work.


hh ha yes agreed.  See here [https://trac.torproject.org/projects/tor/wiki/doc/TransparentProxy](https://trac.torproject.org/projects/tor/wiki/doc/TransparentProxy)

or here for a VM [http://www.janusvm.com/tor_vm/](http://www.janusvm.com/tor_vm/)

then make the VM your proxy

---

