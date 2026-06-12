---
title: "Denying any access to server except a few IPs"
date: 2022-01-30
forum: Server Platforms
---

### Post by johndid on 2022-01-30
Hi,
I am almost totally new to UFW firewall, and I'm still trying to get a gist.
I have been reading articles and guides about it on Internet, then experimenting with my linux Ubuntu server 20.04 LTS.
No security risk for my server since it runs in my Home Lab and it is even behind my home router/firewall at the moment.

Anyway, I'm trying to figure out now how to deny any access to my linux server, and to the services'webguis which run on it, from any IPs except a few, even in my own LAN.

So, I enabled it. its status now:

```

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
137,138/udp (Samba)        ALLOW IN    Anywhere
139,445/tcp (Samba)        ALLOW IN    Anywhere
22/tcp                     ALLOW IN    Anywhere
137,138/udp (Samba (v6))   ALLOW IN    Anywhere (v6)
139,445/tcp (Samba (v6))   ALLOW IN    Anywhere (v6)
22/tcp (v6)                ALLOW IN    Anywhere (v6)



```

But it seems that any devices in my LAN still can get access to it and its services' webGUI.
Well, not exactly. They can't acces cockpit webGUI, just those of services running as docker containers.  Do I need to set up deny forward rules?
I didn't understand how to do that with UFW.

Could you help figure it out, please?

Thanks

---

### Post by volkswagner on 2022-01-30
When you create your rule add a single IP in the "from" field. You can also include
a range or subnet. If you have just a few IP addresses, you'll want to add a rule
for each IP (I don't think you can use a comma-separated list of unique IPs).

[https://www.configserverfirewall.com/ufw-ubuntu-firewall/ufw-allow-ip-address-ubuntu-firewall/](https://www.configserverfirewall.com/ufw-ubuntu-firewall/ufw-allow-ip-address-ubuntu-firewall/)

Notice your "from" field says from "Anywhere".

Once you add the rules for specific IPs, you can delete the "from anywhere rules".
[https://linuxize.com/post/how-to-list-and-delete-ufw-firewall-rules/](https://linuxize.com/post/how-to-list-and-delete-ufw-firewall-rules/)

---

### Post by johndid on 2022-01-30
> **volkswagner said:**
> When you create your rule add a single IP in the "from" field. You can also include
a range or subnet. If you have just a few IP addresses, you'll want to add a rule
for each IP (I don't think you can use a comma-separated list of unique IPs).

[https://www.configserverfirewall.com/ufw-ubuntu-firewall/ufw-allow-ip-address-ubuntu-firewall/](https://www.configserverfirewall.com/ufw-ubuntu-firewall/ufw-allow-ip-address-ubuntu-firewall/)

Notice your "from" field says from "Anywhere".

Once you add the rules for specific IPs, you can delete the "from anywhere rules".
[https://linuxize.com/post/how-to-list-and-delete-ufw-firewall-rules/](https://linuxize.com/post/how-to-list-and-delete-ufw-firewall-rules/)


It wasn't that difficult.
I allowed two IPs:


```

....
Anywhere                   ALLOW       192.168.2.100
Anywhere                   ALLOW       192.168.2.18

....

```

Now, Any IPs except those above can't get access the server itself and any services running DIRECTLY on it like CUPS or the Cockpit's dashboard, but they can still access services running as docker containers like Plex

I'd like now to allow access ONLY the IP of my smartTV (192.168.2.99... + those IPs above of course) which is running a Plex app.
It must have something to do with forwarding rules since docker containers run on internal (bridge or host) network in linux.

Could you help me with that?
Thanks again

---

### Post by volkswagner on 2022-01-30
I'm not familiar with Docker and its network stack.
My guess is you'd have to set up rules
in the docker config, or use a firewall inside Docker, or...?

---

### Post by johndid on 2022-01-31
> **volkswagner said:**
> I'm not familiar with Docker and its network stack.
My guess is you'd have to set up rules
in the docker config, or use a firewall inside Docker, or...?


I think that I'm going to apply a few firewall rules on the host's ports which forward to the internal containers.
No particular needs or security issues here, so I think that it could be a quick way to solve the issue. 

Thanks

---

