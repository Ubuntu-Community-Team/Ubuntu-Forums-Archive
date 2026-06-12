---
title: "can ufw block icmp from specific ip?"
date: 2011-03-03
forum: Security
---

### Post by clapika on 2011-03-03
Hello everyone,
i just install ufw on my ubuntu,
i'm using usb lan so that it will be 2 different network.
the diagram something like this:

192.168.1.2/24                               192.168.1.1/24 (UFW)    192.168.2.1/24                               192.168.2.2/24
client1 <----------------------------------------->  eth1       Firewall      eth0<-------------------------------------------->client2

when i DROP icmp at  /etc/ufw/before.rules the client2 can't ping firewall buat still can ping client1.
is there a possibility that ufw can make client2 cannot ping client 1?

---

