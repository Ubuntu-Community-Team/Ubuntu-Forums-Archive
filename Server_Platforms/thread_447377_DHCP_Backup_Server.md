---
title: "DHCP Backup Server?"
date: 2007-05-17
forum: Server Platforms
---

### Post by puelly on 2007-05-17
I would like to create a DHCP backup server that can assume the duties of the main DHCP server should any failure to the main one occour.  I would prefer the failover to be seamless as possible.  Does anyone have any configuration suggestions for such a setup?

---

### Post by craigp84 on 2007-05-18
Hi Puelly,

ISC DHCPD has supported this for a while. It's as simple as "apt-get install dhcpd" - or otherwise installing the same version on both boxes, then configuring /etc/dhcpd.conf as normal, with an extra stanza for the failover that looks like the following on one box:

```

failover peer "dhcp-failover" {
  primary;
  address 10.0.0.254;
  port 520;
  peer address 10.0.0.253;
  peer port 520;
  max-response-delay 30;
  max-unacked-updates 10;
  load balance max seconds 3;
  mclt 1800;
  split 128;
}
```

and like:

```
failover peer "dhcp-failover" {
  secondary;
  address 10.0.0.253;
  port 520;
  peer address 10.0.0.254;
  peer port 520;
  max-response-delay 30;
  max-unacked-updates 10;
  load balance max seconds 3;
}
```

On the other box.

Hope this helps,

-c

---

### Post by hogman23 on 2008-02-21
Where do you put this statement???  I keep getting this error:

Feb 21 12:53:41 ####### dhcpd: failover peer dhcp-failover: I move from recover to startup
Feb 21 12:53:41 ####### dhcpd: failover peer declaration with no referring pools.
Feb 21 12:53:41 ####### dhcpd: In order to use failover, you MUST refer to your main failover declaration
Feb 21 12:53:41 ####### dhcpd: in each pool declaration.   You MUST NOT use range declarations outside
Feb 21 12:53:41 ####### dhcpd: of pool declarations.

---

### Post by Neunerball on 2008-02-25
see URL: [http://www.madboa.com/geek/dhcp-failover/]("http://www.madboa.com/geek/dhcp-failover/")

---

