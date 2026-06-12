---
title: "[SOLVED] browser access from another node for raid utility"
date: 2008-07-12
forum: Server Platforms
---

### Post by glok_twen on 2008-07-12
hi. i have installed 8.04 server. the only optional packages i selected at install were for it to be an ssh server.

so i installed a 3ware raid card. it has a utility daemon to manage the overall raid configuration. so the daemon is up and running. but when i try to access it via firefox from another desktop, i get an error in the browser saying the connection was reset.

are there other packages i need to the server can respond to the browser? or is it something like a security issue where i need to look at something lie hosts.allow?

---

### Post by windependence on 2008-07-12
Most likely a firewall issue. you may have to open a port. It could also be an apparmor problem.

-Tim

---

### Post by glok_twen on 2008-07-12
thanks i attempted to open the port and make sure it's listening, still getting the same message from the browser:

it appears to have the utility successfully listening on port 888. and the firewall accepting input on the same port. but still get an error about connection refused when accessing from the browser. even though i can in fact ssh from that same node. any ideas?

> An error occurred while loading [http://192.168.1.4:888:](http://192.168.1.4:888:)
Connection to host 192.168.1.4 is broken.

here is what i did:
> iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 888 -j ACCEPT

root@storage10:/home/jeff# iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:888

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@storage10:/home/jeff# netstat -an | grep "LISTEN "
tcp        0      0 0.0.0.0:888             0.0.0.0:*               LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
root@storage10:/home/jeff#                         

---

### Post by glok_twen on 2008-07-12
the issue was this service needed https. thanks for helping.

---

