---
title: "Some doubts"
date: 2011-11-28
forum: Server Platforms
---

### Post by barezi6 on 2011-11-28
Hello everyone.
i am setting a server to use online, but i have some doubts.

1º
when i open the port 80 to can access anywhere, the ip is of the machine that is the server or my external ip?

2º i create a no-ip host but when i setting the network i can make it static, because if i use a static ip, i lost my internet connect, when i setting my static ip what i need to config?
ip adress
broadcast
...
...
...

Thanks

---

### Post by volkswagner on 2011-11-28
To set a static ip for your server check with your router settings.  It works well using reserved ip based on mac address.

You can find your mac address of you server by running:

```
ifconfig
```

Then in your router look for a setting such as "static lease".  You can then enter the mac address, possibly hostname, and the ip address you want assigned.  Be sure to assign an address outside the DHCP range of your router to avoid conflicts.

Once you do this restart networking or reboot your server.
```
sudo /etc/init.d/networking restart
```

This will allow you to keep dhcp enabled on the server.

When opening port 80, you forward port 80 to your internal ip address of your server.

---

### Post by barezi6 on 2011-11-29
> **volkswagner said:**
> To set a static ip for your server check with your router settings.  It works well using reserved ip based on mac address.

You can find your mac address of you server by running:

```
ifconfig
```

Then in your router look for a setting such as "static lease".  You can then enter the mac address, possibly hostname, and the ip address you want assigned.  Be sure to assign an address outside the DHCP range of your router to avoid conflicts.

Once you do this restart networking or reboot your server.
```
sudo /etc/init.d/networking restart
```

This will allow you to keep dhcp enabled on the server.

When opening port 80, you forward port 80 to your internal ip address of your server.

yes i already done it but i need to know what i need to config when i change to static ip.
Exemple i am using a dhcp and when i use static i need to do this:
ip adress xxx.xxx.xxx
broadcast xxx.xxx.xxx 

i need to know what i need to declare on this config, not the values of ip and this, need to know it: is the ip adress, gateway, broadcast what more?

---

### Post by jonobr on 2011-11-30
in your /etc/network.interfaces file

you should have 

```
auto lo
iface lo inet loopback

#prinary interface settings

iface ethx inet static
address <ip address>
netmask <subnetmask>
broadcast < broadcast address for the network>
gateway <gw ip address>
network <network number>
```

so eg using standard class c 19.168.1.x and eth0 as example

```
auto lo
iface lo inet loopback

#prinary interface settings

iface eth0 inet static
address 192.168.1.20
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
network 192.168.1.0
```

---

