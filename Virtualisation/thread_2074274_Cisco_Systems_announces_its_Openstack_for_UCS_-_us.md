---
title: "Cisco Systems announces its Openstack for UCS - uses Ubuntu 12.04 LTS"
date: 2012-10-21
forum: Virtualisation
---

### Post by bmullan on 2012-10-21
As a long time Cisco employee and huge Open Source fan I can't be happier  about this.  

Our UCS, OpenStack .. and Ubuntu .. woot !!

Cisco certified on our UCS ([Unified Computing System]("http://www.cisco.com/web/solutions/data_center/ucs_servers.html?POSITION=SEM&COUNTRY_SITE=us&CAMPAIGN=ucs_servers&CREATIVE=UCS+-+Brand_UCS&REFERRING_SITE=Google&KEYWORD=cisco+ucs_p|mkwid_sPXd3yxz5_13676689213_272267a16717")) cloud platform which is used by some of the largest IaaS Service Providers in the world!

Click on the 'Get Instructions" under Installation to learn how to install it using Ubuntu 12.04 LTS.

[http://www.cisco.com/web/solutions/openstack/index.html]("http://www.cisco.com/web/solutions/openstack/index.html")

---

### Post by Skaperen on 2012-10-23
> **bmullan said:**
> As a long time Cisco employee and huge Open Source fan I can't be happier  about this.  

Our UCS, OpenStack .. and Ubuntu .. woot !!

Cisco certified on our UCS ([Unified Computing System]("http://www.cisco.com/web/solutions/data_center/ucs_servers.html?POSITION=SEM&COUNTRY_SITE=us&CAMPAIGN=ucs_servers&CREATIVE=UCS+-+Brand_UCS&REFERRING_SITE=Google&KEYWORD=cisco+ucs_p%7Cmkwid_sPXd3yxz5_13676689213_272267a16717")) cloud platform which is used by some of the largest IaaS Service Providers in the world!

Click on the 'Get Instructions" under Installation to learn how to install it using Ubuntu 12.04 LTS.

[http://www.cisco.com/web/solutions/openstack/index.html](http://www.cisco.com/web/solutions/openstack/index.html)
I don't see anything on those pages that suggest there is a service there that works like AWS.  AWS is mostly the way I'd like things to operate, but there are some things I think they could improve on ... but which would also involve a major architectural change, so it would not be likely for them to change it.  I'm just wondering if this IaaS added it.  But I really don't see any IaaS features listed.

How is storage organized and deployed?  How is networking organized and deployed (one would hope Cisco would have an awesomely flexible network infrastructure that lets anyone do anything).  How is the pricing structured (is it a pay as you use structure like AWS)?

For example, I would like to have a networking structure that does ALL of these at the same time (AWS can't do it):

1.  Provision a PRIVATE IP subnet of my choice (even if other customers chose the same, or superset, or subset, subnet).  Allow both IPv4 and IPv6.
2.  Provision (at cost) a PUBLIC IP subnet (priced by size).  Allow both IPv4 and IPv6.
3.  Utilize an alternative subnet for instance to infrastructure communication.  IPv6 scope local may be a good choice for this.  Or do as AWS does with link local IPv4.
4.  Allow my instance to use my choice of PRIVATE IP in my subnet (or not).
5.  Allow my instance to use my choice of PUBLIC IP from my provisioned public subnet -OR- use a random IP address provisioned from the random pool -OR- have no public IP address.  Allow both IPv4 and IPv6.
6.  Allow any choice of #4 and any choice of #5 at the same time in any combination of IPv4 and IPv6.
7. I would assume a full security configuration for public access, per subnet and per IP.  Anything less would just not be a networking company.
8.  Provide optional secured VPN gateway service between subnets in different regions on either a routed or bridged or optimized-bridged basis (optimized to manage ARP and NDP to minimize traffic).
9.  Be sure SCTP works and can be configured in all firewall/security configurations.

If this service doesn't even have IPv6 from the start THESE DAYS, that would be a sad indicator.

---

