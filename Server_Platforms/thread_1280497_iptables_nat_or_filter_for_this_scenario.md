---
title: "iptables nat or filter for this scenario ?"
date: 2009-10-02
forum: Server Platforms
---

### Post by dragos2 on 2009-10-02
I have an Ubuntu 8.04 openvz with nat networking like this:

```

     VEID      NPROC STATUS  IP_ADDR         HOSTNAME
       777         27 running 192.168.1.1     vps1.subdom.domain.com
       778         22 running 192.168.2.1     vps2.subdom.domain.com
       779          - stopped 192.168.3.1     vps3.subdom.domain.com
       780         28 running 192.168.4.1     mysql.subdom.domain.com

```

And I used NAT to allow internet accees into each vps by my desire also
with NAT I allowed each vps access to internet as needed.

Hardware node runs on public ip.

I want to be able to access from vps1 for example the mysql 3306 port
in mysql vps but I don't want to expose 3306 to internet, it should
be visible only from 192.168.x.y range.

How can I do it: filter or nat table ? I am a bit confused ..

---

### Post by bodhi.zazen on 2009-10-02
With openvz you do not need to do any of that.

Let us assume your host node has a public IP of 1.2.3.4

Bring up your guest and assign an IP

```
vzctrl start 777
vzctrl set 777 --ipadd 192.168.1.1 --nameserver ip_of_you_host_nameserver --save
```Put your guests on the same subnet (not sure if it matters)

192.168.1.1
192.168.1.2
192.168.1.3
192.168.1.4

use the same nameserver in that second command as on your host node.

That's it, your guests can ping the internet and eachother.

```
vzctrl enter 777

ping -c 4 google.com
ping -c 4 192.168.1.4 #your mysql server
```If you wish you can write firewalls for your guests, but unless you assign a public IP to your guests and then forward the port from the host, you can not reach the guest from your LAN or the internet.

---

