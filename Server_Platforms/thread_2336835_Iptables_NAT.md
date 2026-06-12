---
title: "Iptables NAT"
date: 2016-09-11
forum: Server Platforms
---

### Post by juraj-papic on 2016-09-11
HI all,

I have this nat command , but is not working, I disable the firewall. Should I need to add some other lines?

sudo iptables -t nat -A PREROUTING -p tcp -d 192.168.88.133 --dport 8000 -j DNAT --to-destination 10.0.4.145:443 

thanks.!

---

### Post by darkod on 2016-09-12
That command it is not for NAT, it is for port forwarding. If you want to do NAT in general without any conditions, you can do:
```
sudo iptables -t nat -A POSTROUTING -j MASQUERADE
```

You can add conditions like incoming and outgoing interface, or local subnet, etc, but the above command will do general NAT.

---

### Post by juraj-papic on 2016-09-12
hello,
still having the same issue. this rule Im applying is for my openstack the 10.x.x.x Ip is for my horizon dashboard, and the 192.x.x.x is the host where I have access.

thanks.

---

### Post by darkod on 2016-09-12
The MASQUERADE takes care of NAT. If the traffic doesn't arrive the way you expect check on by one each machine on the route and look that you haven't missed something. Both 192.168. and 10. are private subnets so you might need NAT and port forwarding on the device before 192.168.x.x?

---

