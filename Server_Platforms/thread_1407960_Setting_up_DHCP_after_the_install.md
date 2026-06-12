---
title: "Setting up DHCP after the install"
date: 2010-02-15
forum: Server Platforms
---

### Post by themarker0 on 2010-02-15
Due to me not remembering how my father set up the DHCP in my FreeBSD server (Files etc) i could not input the corrent info while i was installed Ubuntu 8.04 (LTS) server edition (32 bit). Could anyone be nice enough to tell me what i need to do, or what files to edit so i can access the internet from it?

Thank you very much.

---

### Post by ikehack on 2010-02-15
You want your server to be setup to work on a network utilizing DHCP? Is that what you're asking, how to set your server to obtain an IP automatically?

---

### Post by themarker0 on 2010-02-15
When installing ubuntu, i didn't set up the network. Because i didn't have the info.

---

### Post by ikehack on 2010-02-15
Well as I said, if your network is operating on DHCP, you may be able to just run dhclient and see what happens. If not, you may need to get your network information from your father. :\

Try this:
```
ifconfig
```

To determine which interface you wish to connect to the network with. EG: eth0

```
sudo dhclient eth0
```

Hopefully after that you should be connected to the network, if not like I said, you may need to get information from your father.

Oh, and in your /etc/network/interfaces file, make sure the correct interface is set to the correct network type: static or dhcp. An example would be (for DHCP):

**/etc/network/interfaces**
```
...

# The primary network interface
auto eth0
iface eth0 inet dhcp

...

```

---

### Post by themarker0 on 2010-02-15
Thank you very much, my pings went through. It worked like a charm :)

---

### Post by ikehack on 2010-02-15
No problem, glad it worked!:D

---

### Post by Iowan on 2010-02-16
My servers and printers are set up via DHCP, but their addresses don't change. You can ask your father about setting up a static lease (AKA reserved address) in the DHCP server.

---

### Post by themarker0 on 2010-02-16
> **Iowan said:**
> My servers and printers are set up via DHCP, but their addresses don't change. You can ask your father about setting up a static lease (AKA reserved address) in the DHCP server.


I don't need it to be accessed from outside just yet. I am playing around learning first. But i will be sure to do so when the time comes, and i buy my two ips :)

---

### Post by Vishal Agarwal on 2010-02-20
> **Iowan said:**
> My servers and printers are set up via DHCP, but their addresses don't change. You can ask your father about setting up a static lease (AKA reserved address) in the DHCP server.

Can you pls post your dhcp configuration file ?

---

### Post by Iowan on 2010-02-20
```
# Configuration file for dnsmasq.
#
domain-needed
bogus-priv
interface=eth0
expand-hosts
domain=mine

dhcp-range=192.168.1.10,192.168.1.19,12h

dhcp-host=00:a1:ca:a4:30:98,192.168.1.8,infinite
dhcp-host=00:6a:a0:2a:e6:a2,192.168.1.4,infinite

# Override the default route supplied by dnsmasq.
dhcp-option=3,192.168.1.1
```Some of the extra comments removed.

---

### Post by Vishal Agarwal on 2010-02-26
I had a network of 50 machines. And I wanted to give the static IP to every machine based on its NIC address assigned thru DHCP. So that I can create user groups and I can setup squid restrictions based on IP groups. Can you pls give me a few example, how to do it.

---

