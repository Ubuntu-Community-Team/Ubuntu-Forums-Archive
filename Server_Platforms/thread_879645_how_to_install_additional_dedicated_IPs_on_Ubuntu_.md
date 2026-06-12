---
title: "how to install additional dedicated IPs on Ubuntu 8.04 Server"
date: 2008-08-04
forum: Server Platforms
---

### Post by maxidrom11 on 2008-08-04
how to install additional dedicated IPs on Ubuntu 8.04 Server??? :confused:

---

### Post by TreeFinger on 2008-08-04
> **maxidrom11 said:**
> how to install additional dedicated IPs on Ubuntu 8.04 Server??? :confused:

Please elaborate a little bit more on the question you are asking.

I believe a NIC can only have 1 IP address assigned to it.

If you would like your server to have more than one IP you are going to need more than 1 NIC.

If you do, tell us.

--edit

ignore my post :) read below

---

### Post by hyper_ch on 2008-08-04
you could setup something like this in your /etc/network/interfaces
```

# Loopback
auto lo
iface lo inet loopback

# Main IP
auto eth0
iface eth0 inet static
  address 192.168.0.250
  netmask 255.255.255.224
  gateway 192.168.0.225

# additional IPs
auto eth0:1
iface eth0:1 inet static
  address 192.168.1.249
  netmask 255.255.255.248

auto eth0:2
iface eth0:2 inet static
  address 192.168.1.250
  netmask 255.255.255.248

auto eth0:3
iface eth0:3 inet static
  address 192.168.1.251
  netmask 255.255.255.248

auto eth0:4
iface eth0:4 inet static
  address 192.168.1.252
  netmask 255.255.255.248

auto eth0:5
iface eth0:5 inet static
  address 192.168.1.253
  netmask 255.255.255.248

auto eth0:6
iface eth0:6 inet static
  address 192.168.1.254
  netmask 255.255.255.248

```

and then restart networing
```

sudo /etc/init.d/networking restart

```

---

### Post by hyper_ch on 2008-08-04
Or you could use iproute

(1) install iproute

(2) adjust your network to something like this:

```

# Loopback
auto lo
iface lo inet loopback 

# Main IP
auto eth0
iface eth0 inet static
  address 192.168.0.250
  netmask 255.255.255.255
  gateway 192.168.0.225
  pointopoint 192.168.0.225

  # Additional IPs
  up ip addr add 192.168.1.249/29 dev eth0
  up ip addr add 192.168.1.250/29 dev eth0
  up ip addr add 192.168.1.251/29 dev eth0
  up ip addr add 192.168.1.252/29 dev eth0
  up ip addr add 192.168.1.253/29 dev eth0
  up ip addr add 192.168.1.254/29 dev eth0

```

(3) restart networking
```

sudo /etc/init.d/networking restart

```

(4) list ip addresses
```

ip addr show

```

---

