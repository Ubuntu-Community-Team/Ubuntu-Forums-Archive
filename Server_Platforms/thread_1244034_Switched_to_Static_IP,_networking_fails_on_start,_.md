---
title: "Switched to Static IP, networking fails on start, mySQL slow remote login."
date: 2009-08-19
forum: Server Platforms
---

### Post by JillSwift on 2009-08-19
Ok, so...
I got a new NAT router today because my old one started dropping connections like 3rd period French.

The new NAT didn't have the ability to assign IPs to MACs, so to keep addresses the ssame as I'm used to, I chose to assign all my machines static IP addresses. This worked dandy on everything but my server.

Server: Ubuntu server 8.04. Compaq Presario with Pentium 4HT.

[s]Problem 1: On boot, the server will be invisible to other computers (no route to host). If I re-start networking on the server, it shows up fine, and functions ok. This was no problem at all when it was getting an address from DHCP.[/s]  *This appears fixed.*

Problem 2: Logging into mySQL has become painfully slow. mysql -h192.168.0.111 -u???? -p???? takes  5 seconds to connect.

**edit: **Once connected, queries are nice and fast.
**edit: **my laptop, on wifi, connects near-instantly. All the Ethernet machines take the 5 seconds.

**/etc/network/interfaces**
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
 address 192.168.0.111
 netmask 255.255.255.0
 gateway 192.168.0.1
```**/etc/resolv.conf** ```
nameserver 192.168.0.1
```Where 192.168.0.1 is the address of the NAT box, which does look-up forwarding, etc.

I Googled till my eyes bled, I can't find anything to help me past this.

Any ideas?

---

### Post by JillSwift on 2009-08-19
Ok, new info:

On the mySQL server, I added skip-name-resolve to the config file. Connections from all machines are essentially instant now.

This means something, yes? (hope hope)

---

### Post by Bachstelze on 2009-08-19
> **JillSwift said:**
> Ok, new info:

On the mySQL server, I added skip-name-resolve to the config file. Connections from all machines are essentially instant now.

This means something, yes? (hope hope)

This probably means that your server is having trouble resolving the hostname of your client. Can you paste your server's /etc/hosts?

---

### Post by JillSwift on 2009-08-19
> **HymnToLife said:**
> This probably means that your server is having trouble resolving the hostname of your client. Can you paste your server's /etc/hosts?

Yus:
```
127.0.0.1    localhost
127.0.1.1    ubuntu-server-presario

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by Bachstelze on 2009-08-19
> **JillSwift said:**
> Yus:
```
127.0.0.1    localhost
127.0.1.1    ubuntu-server-presario

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I guess that's your problem: MySQL is unable to resolve the address of the machine that tries to connect since it's not in your /etc/hosts (and of course not on the DNS either), so it just keeps on trying until the request times out. Try adding an entry for the machine you connect from, for example:

```
192.168.0.50 alice
```

disable skip-name-resolve, and see what happens.

---

### Post by JillSwift on 2009-08-19
> **HymnToLife said:**
> I guess that's your problem: MySQL is unable to resolve the address of the machine that tries to connect since it's not in your /etc/hosts (and of course not on the DNS either), so it just keeps on trying until the request times out. Try adding an entry for the machine you connect from, for example:

```
192.168.0.50 alice
```disable skip-name-resolve, and see what happens.
Yeah, adding an entry for the client machines worked.

Now I wonder why this problem didn't rear its ugly head when I was using DHCP.

Thanks for the assistance, HymnToLife. :)

---

### Post by Bachstelze on 2009-08-19
> **JillSwift said:**
> Now I wonder why this problem didn't rear its ugly head when I was using DHCP.

Probably because when you used DHCP, the router knew which machine got which IP, and could add that information to its DNS cache.

---

