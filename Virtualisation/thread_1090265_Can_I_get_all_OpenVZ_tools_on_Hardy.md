---
title: "Can I get all OpenVZ tools on Hardy?"
date: 2009-03-08
forum: Virtualisation
---

### Post by starfry on 2009-03-08
Hello,

Playing with OpenVZ, I notice that several commands documented in the OpenVZ Users' Guide are missing. For example:
[LIST]
[*]vzmemcheck
[*]vzdump
[*]vzpkgls
[/LIST]
to name a few.

I presume there are other packages that I need to install ?

Thanks.

---

### Post by bodhi.zazen on 2009-03-09
Yes you can as I have them installed and running.

How did you install openvz ?

At any rate :

```
sudo apt-get install vzquota vzdump vzctl
```

---

### Post by starfry on 2009-03-09
Thanks for that :)

I installed OpenVZ like this :-

$ sudo apt-get update
$ sudo apt-get install linux-openvz vzctl 

Make a symlink (not sure if this is actually necessary)

$ sudo ln -s /var/lib/vz /vz

Make changes to /etc/sysctl.conf

# Added for openvz as per manual

# On Hardware Node we generally need

# packet forwarding enabled and proxy arp disabled

net.ipv4.ip_forward = 1

net.ipv4.conf.default.proxy_arp = 0

# Enables source route verification

net.ipv4.conf.all.rp_filter = 1

# Enables the magic-sysrq key

kernel.sysrq = 1

# TCP Explict Congestion Notification

#net.ipv4.tcp_ecn = 0

# we do not want all our interfaces to send redirects

net.ipv4.conf.default.send_redirects = 1

net.ipv4.conf.all.send_redirects = 0

Then do

$ sudo sysctl -p

$ sudo reboot

---

### Post by starfry on 2009-03-10
Can't find vzdump


root@jl:/# apt-get install vzdump

Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Couldn't find package vzdump

---

### Post by bodhi.zazen on 2009-03-10
I may have installed those tools from the openvz repository, I can look later.

It might be faster for you if you go to the openvz home page and add in their Debian repository.

---

### Post by starfry on 2009-03-12
Success!

```
wget http://www.proxmox.com/cms_proxmox/cms/upload/vzdump/vzdump_1.1-1_all.deb 

apt-get install cstream ssmtp

dpkg -i vzdump_1.1-1_all.deb
```

Seems a shame it is dependent on a mail-transport-agent, but there you are :)

---

### Post by bodhi.zazen on 2009-03-12
proxmox, sweet ...

I have been considering installing proxmox.

Here is a review one of the Montana LUG members wrote up on proxmox :

[http://www.montanalinux.org/proxmox-ve-review.html](http://www.montanalinux.org/proxmox-ve-review.html)

---

### Post by narcisgarcia on 2009-03-20
Very beautiful this Proxmox, but it requires a 64-bit CPU and CPU virtualization extensions.

---

