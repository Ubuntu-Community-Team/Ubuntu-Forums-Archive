---
title: "vmware port forward"
date: 2012-02-27
forum: Virtualisation
---

### Post by vikkyhacks on 2012-02-27
I am using Ubuntu 11.04 and VMware® Workstation 8.0.0 build-471780

I want to port-forward all port 80 http requests connection from 192.168.35.1 (host ubuntu machine) to 192.168.36.133 (windows XP guest http server).

I added the line to /etc/vmware/vmnet8/nat/nat.conf

  80 = 192.168.35.133:80

and type 192.168.35.1 in my Ubuntu host web browser and get message "server not found" ... Help me !!!,:confused::confused:

---

### Post by dcstar on 2012-03-01
> **vikkyhacks said:**
> I am using Ubuntu 11.04 and VMware® Workstation 8.0.0 build-471780

I want to port-forward all port 80 http requests connection from 192.168.35.1 (host ubuntu machine) to 192.168.36.133 (windows XP guest http server).

I added the line to /etc/vmware/vmnet8/nat/nat.conf

  80 = 192.168.35.133:80

and type **192.168.35.1** in my Ubuntu host web browser and get message "server not found" ... Help me !!!,:confused::confused:

That is not the NAT network.

[http://www.vmware.com/support/ws55/doc/ws_net_advanced_ipaddress.html](http://www.vmware.com/support/ws55/doc/ws_net_advanced_ipaddress.html)

---

### Post by vikkyhacks on 2012-03-02
I need to port forward ... So how do i use that link ???:confused::confused:

---

