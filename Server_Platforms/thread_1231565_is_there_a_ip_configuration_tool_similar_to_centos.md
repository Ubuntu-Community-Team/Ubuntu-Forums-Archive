---
title: "is there a ip configuration tool similar to centos's &quot;setup&quot; for ubuntu?"
date: 2009-08-04
forum: Server Platforms
---

### Post by fatfranko on 2009-08-04
i've been setting up more ubuntu server boxes lately.  i am just wondering if there is a ip configuration tool similar to centos's "setup" for ubuntu.  for now, i edit "/etc/network/interfaces" but i'm hoping there is a more convenient way of doing this.

---

### Post by fatfranko on 2009-08-06
*bump*

---

### Post by cariboo on 2009-08-06
THe Ubuntu server has no gui, so there aren't any gui tools for it.

---

### Post by fatfranko on 2009-08-06
> **cariboo907 said:**
> THe Ubuntu server has no gui, so there aren't any gui tools for it.


thank you for the response cariboo907.  yeah, i'm not using a gui in centos as well.  i install centos with only the base packages.  "setup" is actually the command in cli.  i know there isn't a tool in the ubuntu server install.  i'm hoping there is a tool similar to centos's "setup" command that may be available in the repositories.

---

### Post by rslrdx on 2009-08-06
There is not a tool to do that, but i know it would be nice....

here is a link you may find helpfull
[URL="http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html"]
Howto: Ubuntu Linux convert DHCP network configuration to static IP configuration[/URL]

But mostly, you just need to edit /etc/network/interfaces

so, i usually do these steps on the command line:

sudo nano /etc/network/interfaces

change :

iface eth0 inet dhcp

to (adding the lines bellow and matching the network config you use): 

iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254

you might want to edit your dns resolvers too

sudo nano /etc/resol.conf

add lines like this: (one per line)

nameserver 200.176.2.10
nameserver 200.176.2.12



to get out of nano use Ctrl+X, it will ask you to save the file, confirm it, and then restart the network

sudo /etc/init.d/network restart

or just reboot.

hope that helps.

---

### Post by rslrdx on 2009-08-06
in case you already knew how to edit this files, at least the answer should help someone else in a future search

---

