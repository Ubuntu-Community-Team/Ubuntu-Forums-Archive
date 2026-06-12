---
title: "Setting Up A New Server"
date: 2008-06-01
forum: Server Platforms
---

### Post by JC1337 on 2008-06-01
How do I get the router to patch through when IP or url is entered into url bar?

---

### Post by Joeb454 on 2008-06-01
For an Apache web server?

You'll need to configure your router to forward port 80 to your server.

To do this you'll need to learn your router's interface a little better ;) And also you'll have to give your server a static IP address within your network

---

### Post by spiderbatdad on 2008-06-01
run ```
netstat -r
``` look for the ip address in the row 'default,' of the the column 'gateway'...That address in your browser window should get you to your router. 

Default passwords...[http://www.phenoelit-us.org/dpl/dpl.html](http://www.phenoelit-us.org/dpl/dpl.html)

---

### Post by JC1337 on 2008-06-01
this is what it said when I ran "" in the terminal

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

```

and I have a Netgear router and I'm using a LAMP server
(Does it matter that my friend already has a site running off the same router?)

---

### Post by windependence on 2008-06-02
> **JC1337 said:**
> this is what it said when I ran "" in the terminal

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

```

and I have a Netgear router and I'm using a LAMP server
(Does it matter that my friend already has a site running off the same router?)

Yes. Unless you have multiple static IPs and a router capable of doing several VLANs you can only forward port 80 to one internal machine. You can overcome this by using named based virtual hosting in Apache. It's not too hard to set up.

Here are some tutorials:

[http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/](http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/)

[http://www.ubuntugeek.com/howto-create-name-based-and-ip-based-virtual-hosts-in-apache.html](http://www.ubuntugeek.com/howto-create-name-based-and-ip-based-virtual-hosts-in-apache.html)

Good luck!

-Tim

---

