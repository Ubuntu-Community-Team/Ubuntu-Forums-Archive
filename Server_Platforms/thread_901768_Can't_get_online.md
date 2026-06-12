---
title: "Can't get online"
date: 2008-08-26
forum: Server Platforms
---

### Post by magicplayr2000 on 2008-08-26
I recently moved my server, and ever since then I haven't been able to connect to the internet from it.  My other computers are fine, and I can ping my server from the others.  I can ping my router from the server, but I cannot ping other computers connected to the router from my server, even though I'm connecting to the server from the other computers.

---

### Post by mbeach on 2008-08-26
is this all on the same network?

can the other machines ping each other?

can you ping an ip outside of your network, say 91.189.94.12 ?

if all you've done is physically move the machine, I'd first suspect a cable - try another one, but if you see your router from your server, and no other changes have been made thats an interesting problem.

What does the contents of /etc/network/intferfaces look like on the server?

---

### Post by magicplayr2000 on 2008-08-27
It's all on the same network.  I'm using a different router from the one I use at home.  Here's my /etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        gateway 192.168.0.1

```

The router's a linksys, and I changed the local IP of the router to 192.168.0.1.  The subnet mask is 255.255.255.0.

I still can't ping other computers on the network, and can't ping websites.  I can ping 192.168.0.1 though.

---

### Post by windependence on 2008-08-27
What is the contents of your /etc/resolv.conf?

-Tim

---

### Post by magicplayr2000 on 2008-08-27
I can ping 91.189.94.12 mbeach.  My resolv.conf is:
```

search hsd1.va.comcast.net.
nameserver 68.87.73.242
nameserver 68.87.71.226

```
is there a way to reset this?

---

### Post by magicplayr2000 on 2008-08-27
Fixed it.  I had to change the nameservers to the dns server ip.

---

### Post by windependence on 2008-08-27
Well, glad we pointed you in the right direction. ;)

-Tim

---

