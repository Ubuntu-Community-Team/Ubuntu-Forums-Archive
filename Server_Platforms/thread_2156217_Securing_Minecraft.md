---
title: "Securing Minecraft"
date: 2013-06-20
forum: Server Platforms
---

### Post by PierreRobiquet on 2013-06-20
Hello,

I currently have an Ubuntu 12.04 server that I used to host a Minecraft server, one thing I am worried about is security. At the current time I have the java executable set to run as the user "minecraft" with the sudo -u command that I have in a shell script and I type in my sudo password each time. I'm wondering if there is anything else I can do to further secure the Minecraft server should an exploit be found?

I've attempted to use AppArmor to create a profile for Java, but it seems to cause various issues as Java seems to want to read and write to MANY directories and makes profiling an absolute pain.

Any help would be appreciated.

---

### Post by PierreRobiquet on 2013-06-21
By the way I'm not looking for ways to secure the server against griefing or other minor attacks as I have backups in place, what I'm really concerned about is there being a vulnerability in Minecraft which allows remote code execution so I would like to take all the steps possible to minimise any damage should this happen.

---

### Post by egpetrich on 2013-06-22
I'm running two servers that I expose to the outside world. They run on a virtual machine using a virtual network interface. This is primarily to shield my home's network from access by a compromised account.

The virtual network is "beneath" the home network (i.e. all traffic between the virtual network and the Internet passes through the home network on its way), but I've done my best to limit traffic with iptables rules. For example, iptables won't accept traffic destined for the home network from the virtual network. The virtual machine can't even log in to its gateway (the host machine). Here's the script I use to configure iptables:

```
#!/bin/bash

# Starting commands (assuming the rules existing at boot):
# Forward tcp ports from 25565-25567
iptables -I FORWARD 3 ! -i virbr0 -o virbr0 -p tcp --dport 25565:25567 -j ACCEPT
iptables -t nat -A PREROUTING ! -i virbr0 -p tcp --dport 25565:25567 -j DNAT --to 192.168.2.2
# Forward only tcp port 25565
#iptables -I FORWARD 3 ! -i virbr0 -o virbr0 -p tcp --dport 25565 -j ACCEPT
#iptables -t nat -A PREROUTING ! -i virbr0 -p tcp --dport 25565 -j DNAT --to 192.168.2.2

# Masquerade on packets sent from local network to virtual network.
iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -d 192.168.2.0/24 -j MASQUERADE

# Log and drop invalid packets from the virtual network.
# Accept input packets for established and related connections.
# Derived from "Linux Firewalls" by Michael Rash
iptables -A INPUT -i virbr0 -m state --state INVALID -j LOG --log-prefix "DROP INVALID " --log-ip-options --log-tcp-options
iptables -A INPUT -i virbr0 -m state --state INVALID -j DROP
iptables -A INPUT -i virbr0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Accept special packets associated with virtual machine VNC connection.
iptables -A INPUT -i virbr0 -p igmp -j ACCEPT

# Log and drop spoofed packets from the virtual network.
iptables -A INPUT -i virbr0 ! -s 192.168.2.0/24 -j LOG --log-prefix "DROP SPOOFED PKT "
iptables -A INPUT -i virbr0 ! -s 192.168.2.0/24 -j DROP
iptables -I INPUT 11 -i virbr0 ! -s 192.168.2.0/24 -j LOG --log-prefix "DROP SPOOFED PKT "
iptables -I INPUT 12 -i virbr0 ! -s 192.168.2.0/24 -j DROP

# Log and drop any other packets from the virtual network.
iptables -A INPUT -i virbr0 -j LOG --log-prefix "DROP UNEXPECTED PKT "
iptables -A INPUT -i virbr0 -j DROP

```

Each server runs under a separate account. The accounts have minimal privileges, but I don't put them into jails or anything. I did just change the system default umask (for file permissions) to 027 (edit /etc/login.defs). I log into each account using ssh from the host machine; I use a keypair, so I don't even quite remember the account passwords.

If someone were to exercise an exploit and break out of Minecraft, he would find himself on a pretty boring server with access to the Internet, but nothing else.

---

