---
title: "Setting up Port Address Translation?"
date: 2009-09-14
forum: Server Platforms
---

### Post by uylug on 2009-09-14
Any ideas on how to setup an Ubuntu Server 9.04 to do Port Address translation?

That is, I want to connect to my http server on port 80 using a different port.

Please do not suggest changing the default port because that is not what i want to do :D

Any ideas?

---

### Post by doru001 on 2009-09-14
I am using this to open a port in a router for a torrent application: 

iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 33697 -j DNAT --to-destination 192.168.xxx.xxx:33697

Maybe you can try: 

iptables -t nat -A PREROUTING -i eth0 --dport 8080 -j DNAT --to-destination your-server-ip:80

---

### Post by uylug on 2009-09-14
Great! Seems like that would work! I'm gonna give it a try!

---

### Post by doru001 on 2009-09-16
Please let me know if it works.

---

