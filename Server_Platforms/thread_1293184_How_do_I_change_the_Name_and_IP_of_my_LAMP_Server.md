---
title: "How do I change the Name and IP of my LAMP Server"
date: 2009-10-16
forum: Server Platforms
---

### Post by jigglypuff on 2009-10-16
I know that the Server Name defaults to: ServerName and the IP Defaults to: 127.0.01

I am currently running Ubuntu 9.10 Beta (GNOME)

---

### Post by linuxluver on 2009-10-16
I would also like to know this.

---

### Post by R.Bucky on 2009-10-16
I am not sure that I understand what you mean? Your localhost will be 127.0.0.1. Why would you need to change it? If you have a domain name, change the ServerName in your /etc/sites-available/ directory. Otherwise, BIND9. Otherwise, what is your intent or goal?

---

### Post by cariboo on 2009-10-17
the Ubuntu server gives you the oppertunity to set up a host name during the installation, the default is ubuntu, if you neglected to set a proper hostname, You can edit /etc/hosts to set the host name, this is what my /etc/hosts file looks like

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	chilanko.aplus	chilanko
```

In my case, my servers name is chilanko and the workgroup is aplus

to set a static ip address, I just disable dhcpc3-client:

```
update-rc.d -f dhcp3-client remove
```

then set a static ip address in /etc/network/interfaces. I use nano to edit configuration files:

```
sudo nano /etc/network/interfaces
```

When you are finished the interfaces file should look something like this:

```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
 address	192.168.1.210
 netmask	255.255.255.0
 braodcast	192.168.1.244
 gateway	192.168.1.1
```

---

### Post by jigglypuff on 2009-10-17
I want to make it a Public Server

---

### Post by Bachstelze on 2009-10-17
> **jigglypuff said:**
> I want to make it a Public Server

Just forward port 80 in your router.

---

