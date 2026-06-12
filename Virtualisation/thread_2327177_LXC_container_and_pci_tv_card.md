---
title: "LXC container and pci tv card"
date: 2016-06-08
forum: Virtualisation
---

### Post by Lin_Loen on 2016-06-08
I´m experimenting with the setup for my new home server. The plan is to use Ubuntu 16.04 server as basis with several applications in their own LXC/LXD container.
One of the containers will run TVHeadend.
In my (old) test server I have a Twinhan pci tv card and I did setup a container called tv, with the ubuntu 16.04 container image.
The tv card does show up on ¨lspci¨ in both host and container.
On the host I have a /dev/dvb/adapter0 dircetory. Not in the container.

I tried to add the tv card to the running tv container with the following command:

 lxc-device -n tv add /dev/dvb/adapter0

Then I got the following error:

lxc-device: lxc_device.c: main: 129 Container tv is not running.

However the tv container is running according: lxc list

Is there anyone who can help me with connecting the tv card to the container or can anyone explain the error.


Rgds.

---

### Post by MAFoElffen on 2016-06-10
Please p[ost the config file for your container. What I'm thinking is that you will have to add a section to do a PCI pass through for the container to see that PCI bus, to that card.

---

### Post by Lin_Loen on 2016-06-11
I guess you mean the config file in /var/lib/lxd/containers/tv ?
There is no config file.

---

