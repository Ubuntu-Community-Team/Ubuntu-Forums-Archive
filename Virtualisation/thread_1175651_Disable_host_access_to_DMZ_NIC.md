---
title: "Disable host access to DMZ NIC"
date: 2009-06-01
forum: Virtualisation
---

### Post by HDave on 2009-06-01
I am trying to set up a VMWare Server host to provide some web server guests that will operating in a DMZ.  The host has two NICs, so this should not be a problem.

I have read however that it is good security practice to have the guests use a bridge to a NIC that is connected to the DMZ, but that the host should not be able to see any traffic over that NIC.   In Windows they say you should disable TCP/IP binding to the NIC, but in Linux they say nothing!

How can I setup eth1 so that there is NO chance of the host talking on it, but the bridge protocol can still get through?

---

