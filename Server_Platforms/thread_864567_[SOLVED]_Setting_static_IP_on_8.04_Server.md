---
title: "[SOLVED] Setting static IP on 8.04 Server"
date: 2008-07-19
forum: Server Platforms
---

### Post by sp0nge on 2008-07-19
Again I find myself missing some small piece of the puzzle that I'm sure is staring me in the face! I have been configuring my server, and I thought I had set a static IP by editing etc/network/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
        address 192.168.1.199
        netmask 255.255.255.0
        network 192.168.1.1
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

But when I attempted to ssh into it, I realize the IP is 192.168.1.102 :( 

Is there some other changes I need to make or did I not make this one correct?

---

### Post by bab1 on 2008-07-19
remove the reference to network in the /etc/network/interfaces file

192.168.1.1 is not a network.  it's just the first addr in the network

mine looks like this:
```
/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static
address 192.168.1.12
netmask 255.255.255.0
gateway 192.168.1.1

```

The server should be static not auto (DHCP)

---

### Post by sp0nge on 2008-07-19
Thanks for the feedback, this has been a great learning experience! 

Taking your suggestion, I removed the reference to the network. After restarting the network, the IP was still not changed or correct. I notice a difference in our files on what would be line 9. Since you mentioned it should *not* be auto, I commented out this line and tried again: 

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto eth0
iface eth0 inet dhcp
        address 192.168.1.199
        netmask 255.255.255.0
        network 192.168.1.1
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

after resetting the network I get: 

```
Listening on LPF/eth0/00:e0:18:cf:6d:8d
Sending on   LPF/eth0/00:e0:18:cf:6d:8d
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Read from remote host 192.168.1.102: Connection reset by peer
Connection to 192.168.1.102 closed.
```

I thought this was a good sign at first, thinking since the IP changed, it would need to reconnect- this was not the case.

Feeling adventurous, I added:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
# auto lo
static lo
iface lo inet loopback

# The primary network interface
# auto eth0
iface eth0 inet dhcp
        address 192.168.1.199
        netmask 255.255.255.0
        network 192.168.1.1
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

still no dice..

---

### Post by tinny on 2008-07-20
Here is the contents of my "interfaces"

```

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

```

Make sure you dont have DHCP in the eth0 config. You will notice mine is set as "static".

"iface eth0 inet static" not "iface eth0 inet dhcp"

Also make sure that you are setting your IP address to be on the same sub net as you router.

Is your router IP: 192.168.1.1 MASK: 255.255.255.0???

---

### Post by windependence on 2008-07-20
Here is your problem, you have your interface set to DHCP and it should be static. Look at the line I have in bold:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto eth0
**iface eth0 inet dhcp**
        address 192.168.1.199
        netmask 255.255.255.0
        network 192.168.1.1
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

That should be:

```
iface eth0 inet static
```

You can also get rid of the network line as has been mentioned and then it should work.

-Tim

---

### Post by skunkbad on 2008-07-20
This is mine in case it might help to look at:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
     address 192.168.1.222
     netmask 255.255.255.0
     network 192.168.0.0
     broadcast 192.168.1.255
     gateway 192.168.1.1

---

### Post by sp0nge on 2008-07-21
Thanks, I have made the changes- I had a feeling I was overlooking something simple, I've been spreading myself so thin that happens quite frequently.

> Is your router IP: 192.168.1.1 MASK: 255.255.255.0???

Yes it is. Everything seems to be working with exception of the static IP, which I hope is fixed with this change.

***The static IP is set, thanks for the input!~***

---

