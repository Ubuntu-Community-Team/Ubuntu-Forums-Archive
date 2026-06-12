---
title: "dhcp3-server error on startup, not a clue what its asking for"
date: 2009-10-21
forum: Server Platforms
---

### Post by Predatorian on 2009-10-21
hello *buntu'ers,

im trying to set up a dhcp server on a network that isnt conencted to the internet. i downloaded the packages, and then put it on the network. i set the ip of the eth0 to static, and ifconfig reports i set it correctly. then when i configred /etc/default/dhcp3-server, i edited the file to have INTERFACES="eth0" and then i edited the /etc/dhcp3/dhcpd.conf so that it would have the appropriate configurations as an older dhcp server i had. but when i try to start the server, i get this error,

```

No subnet declaration for eth0 (0.0.0.0).
** Ignoring requests on eth0. If this is not what
    you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface eth0 is attached **

Not configured to listen on any interfaces!

```

im not sure what this means, because i set the options bracket to start with 

```

subnet 192.168.1.0 netmask 255.255.255.0
{

```

any ideas folks?

---

### Post by lykwydchykyn on 2009-10-21
Can you post all of /etc/network/interfaces and /etc/dhcp3/dhcpd.conf?

---

### Post by Predatorian on 2009-10-21
im sorry, i messed up, and didnt look at a correct option in my interfaces file. thank you though. if an administrator could, please delete this thread.

---

