---
title: "Squid Transparent Proxy with ISA Server 2006"
date: 2007-08-22
forum: Server Platforms
---

### Post by MCGrunge on 2007-08-22
Hello,

Our company uses ISA server 2006 in a Windows domain environment to filter internet traffic on our network.  We have wireless routers in our buildings to allow employees to use their personal laptops in house.  We do not want to make changes to their personal laptops, so we are unable to apply our group policy rules to them.  (Their laptops are not on our domain.)

Our problem is that we would like to apply the same filtering rules implemented on our domain over our wireless network.  It was suggested that we use a transparent squid proxy.  We installed Ubuntu Server 7.04 on a machine with 2 ethernet cards.

Our setup now looks like this:
Our Network > Squid Box ETH1 bridged to Squid Box ETH0 > Switch > individual wireless routers. (configured as access points)

ISA server is configured to allow the squid box to authenticate via hostname, so our ISA rules successfully apply to the Squid box.  If we connect a laptop to one of the routers downstream, that laptop will successfully pull an IP address from the DHCP server on our domain controller, so we know the ethernet bridge functions properly.

However, any machines downstream from the squid box appear to have all http traffic unblocked.  We've attempted to configure squid to intercept all http requests originating from ip address downstream and have the squid box make the request in its place, so the our ISA server will filter the request.

So far, we've been unable to locate a resource that will successfully allow us to configure squid in this manner.  Seems as if it would be a simple configuration.  If anyone could assist us, or point us in the direction of a resource that would help us with this configuration, we would be most grateful.

---

### Post by bmathis on 2007-08-22
Can't you point the wireless router's default gateway to your ISA box? Thats the way we have our DHCP scope setup at work. All domain clients authenticate and are allowed access via gpo, all non authenticated clients still hit ISA but have limited access to a set group of sites.

---

