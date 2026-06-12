---
title: "firestarter problem"
date: 2008-02-29
forum: Security Discussions
---

### Post by scaa on 2008-02-29
I started firestarter and then checked my system with shields up. While all service ports were 'stealthed' the test failed as 'ping' was successful.
How can I correct this issue ?

---

### Post by Sam Lars on 2008-03-01
Look for a tutorial on iptables that will do that.  That's the firewall that Firestarter actually configures, but you have to do this manually.

---

### Post by Irihapeti on 2008-03-01
It's been a while since I used Firestarter, so my memory of the exact details is hazy. There is an option in one of the menus to allow or disable ICMP services. It's set to allow by default. You can safely disable ICMP services (unless perhaps you are running a server - I'm out of my depth there). Then Shields Up will show your machine as totally stealthed.

---

### Post by scaa on 2008-03-01
Thanks for yours posts. I am novice to understand the iptable tutorial. And as suggested  ICMP is not enabled

---

### Post by mamboze on 2008-03-02
Hi,
I've got the same problem - I want to stealth port 80. Following the suggestions I enable ICMP filtering in firestarter, then turned it off and restarted. But on running ShieldUP port 80 still showed up as open (not stealthed). 

any help would be wolcome. thanks

---

### Post by Oldsoldier2003 on 2008-03-02
> **mamboze said:**
> Hi,
I've got the same problem - I want to stealth port 80. Following the suggestions I enable ICMP filtering in firestarter, then turned it off and restarted. But on running ShieldUP port 80 still showed up as open (not stealthed). 

any help would be wolcome. thanks

the thing to remember about iptables is the rules are processed in order. If a packet meets a rulle that allows it to pass- it is through the firewall, it doesnt matter if there is a rul that would deny it even if it was the very next rule, because it has already passed through the filter.

---

### Post by OrangeCrate on 2008-03-02
> **ICMP filtering options**

ICMP packets make up a special class of traffic used by many common network utilities, for example ping and traceroute.

By default Firestarter allows ICMP traffic, although it throttles it somewhat to prevent excessive flooding or Denial of Service attacks. By enabling ICMP filtering you can block these services altogether. Note that blocking a certain ICMP type also prevents you from using it yourself.

Firestarter allows control of the following ICMP types:

    * Echo request and Echo reply
      Used by the ping network tool, but also widely by network enabled games and programs in general. Ping can also be used as a component in various network attacks and information gathering roles.
    * Timestamping
      Timestamping is used by Internet gateways to assess how long a packet destined for a host should remain active before being discarded. Users of the @Home Cable network should not filter timestamping requests, as these are commonly used to maintain statistics tracking and keepalives throughout the networks.
    * Traceroute and MS Traceroute
      These ICMP types are used for pathfinding between networks. Useful for configuring networks for Quality of Service as well as detecting network dropouts. Microsoft Traceroute can safely be filtered if you (or your uplink) do not operate Microsoft DNS servers.
    * Unreachable
      Sometimes used in Fingerprinting attacks, unreachable messages are sent when a destination host is not responding to a request from your machine. Unreachable requests should not be filtered unless you are running DMZ services on your machine.
    * Address Masking
      No longer used since Linux 2.2, you can filter these requests unless you have really old machines on your internal network.
    * Redirection
      Used in inter-network traffic, redirection is useful if you have networks connected in different locations (possibly different countries) connected via a VPN or other networking service. In these cases, the gateways can provide redirection for incoming packets, informing them that the destination host is actually on the same logical network, and should therefore be forwarded. If you are not in this situation, you may filter these packets.
    * Source Quenches
      No longer used since Linux 2.2, you can filter these requests unless you have proprietary UNIX boxes on your internal network that are able to respond to these.

[http://www.fs-security.com/docs/preferences.php](http://www.fs-security.com/docs/preferences.php)

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

