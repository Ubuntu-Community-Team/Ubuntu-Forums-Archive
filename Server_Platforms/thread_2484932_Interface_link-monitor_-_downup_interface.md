---
title: "Interface link-monitor - down/up interface"
date: 2023-03-14
forum: Server Platforms
---

### Post by mos6502mos on 2023-03-14
I have a need to bring down/up interfaces based on upstream behavior. Is there a method to generate a source-interface link-monitor (example: ICMP/PING sourced from a specific interface) that monitors a upstream IP that I control. If the link-monitor fails out said interface - the system will bring that interface down, and turn up another interface.

I do not have the capability to do a bonded or link-aggregated since each interface will connect to two different switches that has two different layer1 and layer2 paths. I also do not have the capability to have upstream switches in VPC or MLAG configuration.

thank you

---

### Post by MAFoElffen on 2023-03-14
I do a lot of testing and building of Virtual tests. I know, a bit geeky... But it helps me replicate things and learn how to approach solutions to problems. In some of my VNet test scenarios, I sometimes use a VM of OpenWRT as a virtual switch within my test suite...

OpenWRT has a package called mwan3, that does "Multi WAN load balancing/failover":
> 
**About mwan3**

    The mwan3 package provides the following functionality and capabilities: 
 
[LIST]
[*] Outbound WAN traffic load balancing or fail-over with multiple WAN interfaces based on a numeric weight assignment 
[*] Monitors each WAN connection using repeated tests and can automatically route outbound traffic to another WAN interface if the first WAN interface loses connectivity 
[*] Creating outbound traffic rules to customize which outbound connections should use which WAN interface (policy based routing). This can be customised based on source IP, destination IP, source port(s), destination port(s), type of IP protocol etc 
[*] Physical and/or logical WAN interfaces are supported 
[*] The firewall mask (default 0x3F00) which is used to mark outgoing traffic can be configured in the /etc/config/mwan3  globals section. This is useful if you also use other packages  (nodogsplash) which use the firewall masking feature. This value is also  used to set how many interfaces are supported. 
[/LIST]
  


Is that what you are describing, that you are trying to do?

---

