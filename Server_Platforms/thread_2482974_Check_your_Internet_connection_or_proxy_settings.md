---
title: "Check your Internet connection or proxy settings"
date: 2023-01-16
forum: Server Platforms
---

### Post by bigmonmulgrew on 2023-01-16
I have a game server on ubuntu 22.04.1

I've been having some networking issues with it, on logging I get 

```
Check your Internet connection or proxy settings
```

Pinging google gives

```
ping: google.co.uk: Temporary failure in name resolution
```

I've found that adding "nameserver 8.8.8.8" to /etc/resolv.conf solves the problem until I restart.

How do I make this change permanent.

---

### Post by MAFoElffen on 2023-01-16
Add it under nameservers in your NetPlan yaml file (in /etc/netplan/)... Example:
```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp1s0:
      addresses:
        - 10.10.10.2/24
      nameservers:
        search: [mydomain, otherdomain]
        addresses: [10.10.10.1, 1.1.1.1, 8.8.8.8]
      routes:
        - to: default
          via: 10.10.10.1

```

---

### Post by bigmonmulgrew on 2023-01-18
Ok I guess thats a clue to where the issue is. I don't have anything in /etc/netplan its an empty directory.

This server was originally 16.04 if I recall correctly back then the network config was in /etc/network/interfaces which leads me to this.#


```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp2s0
iface enp2s0 inet static
address 192.168.0.199
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 8.8.8.8 192.168.0.1

```

Unfortunately adding 8.8.8.8 to the nameservers here doesnt seem to be doing anything. I would guess the issue is that something is expecting the config from netplan but its not there. How do I move from one to the other.

I can plug a keyboard into the server if necessary to kill the network while working on it.

---

### Post by SeijiSensei on 2023-01-18
Recent versions of Ubuntu like 22.04 use systemd-resolved by default. The standard /etc/resolv.conf is managed by that process.

```

nameserver 127.0.0.53
options edns0 trust-ad

```

You can edit (as root with sudo) /etc/systemd/resolved.conf to add your nameservers. Put the primary in the DNS= entry, and any backups in the FallBackDNS= entry. See "[man resolved.conf]("https://man.archlinux.org/man/resolved.conf.5.en")" for details.

Then restart the process with "sudo systemctl restart systemd-resolved". Your resolv.conf won't change, but you'll now be using the servers you entered.

---

### Post by bigmonmulgrew on 2023-01-20
> **SeijiSensei said:**
> Recent versions of Ubuntu like 22.04 use systemd-resolved by default. The standard /etc/resolv.conf is managed by that process.

```

nameserver 127.0.0.53
options edns0 trust-ad

```

You can edit (as root with sudo) /etc/systemd/resolved.conf to add your nameservers. Put the primary in the DNS= entry, and any backups in the FallBackDNS= entry. See "[man resolved.conf]("https://man.archlinux.org/man/resolved.conf.5.en")" for details.

Then restart the process with "sudo systemctl restart systemd-resolved". Your resolv.conf won't change, but you'll now be using the servers you entered.

This has worked, thank you very much

---

