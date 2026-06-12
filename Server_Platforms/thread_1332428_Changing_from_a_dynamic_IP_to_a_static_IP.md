---
title: "Changing from a dynamic IP to a static IP"
date: 2009-11-20
forum: Server Platforms
---

### Post by Vunutus on 2009-11-20
At work we currently have a DSL connection with a dynamic external IP assigned to us. We need a static IP for several reasons and are going to be purchasing one soon.

My question is: Do I need to do anything special to make this transition? My network currently consists of one dd-wrt router, one ubuntu server, and some big HP switch that all workstations connect to.

The router provides DHCP services for the whole network. Everything (server, switches, workstations, etc) grabs its internal IP from the router. When I sign up for the static IP services, what actually happens? Will our ISP just set their DHCP servers to always assign us the same IP (requiring no action on my part), or will I have to update configuration files?

---

### Post by jfmanamtr on 2009-11-20
Well, it depends on your ISP. I work for tech suport for a few ISPs on the east coast & they all seem to be different. We have a few that will do a sticky static (setting the DHCP server to always give you the same address) & others who will ask that you input the IP into your router\computer. Your best bet for help would be to contact the ISP & ask them how they would do it.
 
~John

---

### Post by Vunutus on 2009-11-20
> **jfmanamtr said:**
> Well, it depends on your ISP. I work for tech suport for a few ISPs on the east coast & they all seem to be different. We have a few that will do a sticky static (setting the DHCP server to always give you the same address) & others who will ask that you input the IP into your router\computer. Your best bet for help would be to contact the ISP & ask them how they would do it.
 
~John

The ISP in question is AT&T. Given how large they are I'm sure someone here has dealt with them on this issue?

But yeah, I'll definitely ask them when I'm ordering.

---

