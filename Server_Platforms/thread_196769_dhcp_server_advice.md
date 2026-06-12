---
title: "dhcp server advice"
date: 2006-06-14
forum: Server Platforms
---

### Post by FredSambo on 2006-06-14
hello all.

i have an ubuntu server computer running as a standalone firewall on a 25 station network.  i need to install a dhcp server on this computer so it will deliver ip addresses to the (intranet) netwoirk from now on, since the old dhcp server is dead.

can anyone recommend a guide or tutorial that will help me through this?

---

### Post by Soleil-Raid on 2006-06-14
Bluntly speaking:

sudo apt-get install dhcp3-server
sudo vim /etc/dhcp3/dhcpd.conf
sudo /etc/init.d/dhcp3-server restart

man dhcpd.conf will give you the manual for the configuration file, but it's pretty well documented internally anyway.

---

### Post by FredSambo on 2006-06-14
cool.

what about this:

```

sudo apt-get install dhcp
sudo apt-get install dhcp-relay
sudo vim /etc/dhcpd.conf
sudo /etc/init.d/dhcp restart

```

is that old school?

---

### Post by FredSambo on 2006-06-15
well after messing with the unix stuff last night, i finally decided to go with [ipcop](http://www.ipcop.org/index.php) since all i really need is a standalone firewall that provides DHCP to my network.  this seems to be exactly what i am looking for and it is its own distro, which is kind of cool.

---

