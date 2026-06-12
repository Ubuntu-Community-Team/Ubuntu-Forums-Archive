---
title: "how to have eth1 start at boot ?"
date: 2006-02-26
forum: Server Platforms
---

### Post by nephish on 2006-02-26
hello there. i am using an ubuntu box to share with two other computers in the house. the first ubuntu gets the internet from adsl with pppoe. This comes in on eth0. i use a terminal to bring up eth1 like this
```
ifconfig eth1 192.168.1.2 up
```
i use firestarter to manage the internet sharing.

my question is.... how can i get this to happen automatically when i boot ?
if i reboot my computer, i have to open the terminal and bring up the eth1 by hand, then i have to start firestarter. 
is there an easy way to get eth1 to come up on boot, and then start firestarter ?

thanks for any tips

---

### Post by bikeboy on 2006-02-26
Open a terminal and do:

```
cat /etc/network/interfaces
```

Post the output of that and I should be able to help you. Getting interfaces up on boot is a pretty common question.

---

### Post by fdoving on 2006-02-26
Add something like this to your /etc/network/interfaces

# Network settings
iface eth1 inet static
   address 192.168.1.2
   netmask 255.255.255.0
   gateway 192.168.1.1

auto eth1
# this line is the one bringing up eth1 when /etc/init.d/networking is started.

You can read more about it in "man interfaces"

- Frode

---

### Post by nephish on 2006-02-26
ok, here is what i have in /etc/network/interfaces
```

# The loopback network interface
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
auto eth0
    iface eth0 inet manual

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

```

do i need to put the stuff about the gateway? this computer does not use a gateway, but acts as the gateway for the other computers in the house ?

thanks much

---

### Post by nephish on 2006-02-26
thats what worked, added my eth1 to /etc/network/interfaces and now it works.
thanks much

---

