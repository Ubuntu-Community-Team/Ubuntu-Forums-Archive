---
title: "accessing a remote virtual server using a public ip"
date: 2013-06-28
forum: Virtualisation
---

### Post by umaDik on 2013-06-28
Hi all,

I have a ubuntu desktop in my remote virtual machine(which has a public ip). I'm running the wayback machine in [http://localhost.arc.org:8080](http://localhost.arc.org:8080). Could someone please tell me how to access this via the public ip???

Regards

---

### Post by SeijiSensei on 2013-06-28
In the Network settings for the VM, try using "bridged" mode rather than the default "NAT".  That will enable the guest to obtain an IP on the same network as the host is connected to.  You should then be able to connect directly to the guest over the bridged IP.

---

### Post by umaDik on 2013-07-06
Hi,

I have Heritrix running on 8086 port and I can access it using public ip as [http://public](http://public) ip:8086.

But I **cannot** access the wayback machine using public ip as follows,

[http://public ip.arcive.org:8080]("http://localhost.arc.org:8080/")[COLOR=#000000].

Is there any way to do this?

Regards
/Umanda[/COLOR]

---

### Post by umaDik on 2013-07-07
I found the solution and what I did was chaged the wayback.xml base dir url to [http://public ip:8080]("http://localhost.arc.org:8080/")[COLOR=#000000][COLOR=#000000]. Then shut down the tomcat and restart it again.[/COLOR][/COLOR]

---

