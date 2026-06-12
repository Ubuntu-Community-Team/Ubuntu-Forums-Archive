---
title: "Ubuntu Server: No internet connection"
date: 2006-04-17
forum: Server Platforms
---

### Post by exir on 2006-04-17
Hi Folks,

Im a little bit an newbee with working on linux but so far so good.

I have installed ubuntu server on my pc. It act's like an webserver with php etc, etc. Everything is working fine!

Now i wanted to change the dynamic ip address to an static ip address.
I changed this with ifconfig eth0 'ipaddres' 'broadcast' 'subnetmask'.

after changing this one, i lost my connection with internet. I still have an network connection and the server is reachable by pinging the ip address. But from outside my home and from the server to the internet there is no connection.

I think this is because there are no DNS configured in the network configuration, but i don't know how i can add them to it.
I allready tried with ifconfig dns / ifconfig domain-name-server. but none of them seams to be working :(

Does anybody know how to do this?

Thnx in advance!

---

### Post by fdoving on 2006-04-17
You put dns servers in /etc/resolv.conf edit the file with your favorite editor and add the dns servers you want.

Example:
```

nameserver 127.0.0.1
nameserver 192.168.0.1

```

Change the IP's to match your setup.


You also want to set a default route/gateway:
```

route add default gw 192.168.0.1

```

Replace 192.168.0.1 with the IP of your router/gateway 


- Frode

---

