---
title: "DHCPv6 Prefix Delegation with Routing"
date: 2017-11-07
forum: Server Platforms
---

### Post by hammons2012 on 2017-11-07
Good Day,

Before I go into details on this, the perspective is coming from the angle that an ISP is trying to setup prefix delegation with dynamic routing. The question is this, is there a way to get the Ubuntu DHCPv6 server to propagate those routes via dynamic routing protocols? There should be a better way to get the routing side of this done, without having to do static routes for everything. Any input would be greatly appreciated, and I'll be lab-ing this up over the next few days. Also, my colleague posted this in a Cisco support forum if anyone is confused about what we are trying to achieve.

[https://supportforums.cisco.com/t5/ipv6-integration-and-transition/isp-ipv6-customer-provisioning/m-p/3211767#M2988](https://supportforums.cisco.com/t5/ipv6-integration-and-transition/isp-ipv6-customer-provisioning/m-p/3211767#M2988)

I know you can install an application that can do dynamic routing for Ubuntu, but I'm just a bit confused on how the prefix delegation works with dynamic routing. I've been scouring the web for an answer, but I can't seem to find one. I get the configuration side, I just want to know how we can work out the routing without having to set statics everywhere.

---

