---
title: "Static IP and DNS"
date: 2009-12-29
forum: Server Platforms
---

### Post by humphreybc on 2009-12-29
I've got a local web server running AjaXplorer connected to our router via ethernet. Currently the address to get to it is:

[http://192.168.1.2/AjaXplorer-2.5.4/](http://192.168.1.2/AjaXplorer-2.5.4/)

The router has the DHCP lease time set to one day.

I've got two questions:

1) How do I set a static IP, so that the IP address will stay the same always?

and

2) How can I set it up so that typing in [http://server](http://server) will take you to the server, instead of having to tell people the complicated URL above?

Thanks!
Benjamin

---

### Post by jonest1 on 2009-12-29
I'm not sure on a couple points, and please reply for clarification, if required.

To set you Ubuntu computer to have a static address, follow the instructions at this link.
[https://help.ubuntu.com/9.10/internet/C/connecting-wired.html](https://help.ubuntu.com/9.10/internet/C/connecting-wired.html)

If the people connecting to you are on your lan, you can do one of two things.

1.  Setup a DNS server on your LAN and have the client point to it for DNS queries.
2.  Edit the hosts file of the clients on your LAN to have server point to 192.168.1.2.

As far as the AjaXplorer-2.5.4/ part of the URL goes, I'm not familiar with the app, but it looks like a LAMP application.  You may want to research creating an Apache virtual host which points the virtual host to the AjaXplorer directory.  

I wish I could be of more help on this one.

---

### Post by humphreybc on 2009-12-29
The instructions are only for GUI interfaces - I'm running Server Edition, no GUI.

---

### Post by CharlesA on 2009-12-29
You would need to edit the /etc/network/interfaces file to add the IP address:

```
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

You might also need to edit the /etc/resolv.conf and add the nameserver.

```
nameserger 192.168.1.1
```

---

### Post by Project PWNED on 2009-12-29
CharlesA's solution is far better; more simplistic and running a DNS server is overboard if you ask me. 

```

nameserver 192.168.1.1

```

He had a slight typo ;-)

Also, are you wanting something shorter for the URL for your one desktop (I assume Linux/Ubuntu) or everyone on the local network? If for everyone, running a DNS server is probably what you need.

If just for you

Add into /etc/hosts

```

192.168.1.2 (tab key) ajax

```

So you can type in [http://ajax](http://ajax)

---

### Post by humphreybc on 2009-12-30
Cheers, I'll set the static IP now. I suppose I'll have to change the DHCP IP assignment on the router settings to start from 192.168.1.3 so that it doesn't conflict?

Or is the router smart enough to see that there is already a static IP address with 1.2?

It's for everyone on the network, just not me. Oh well I guess they can just type it in and bookmark it.

---

### Post by Lori700698 on 2009-12-30
At home when I'm behind my router all I have to do is type in the name of the computer/server and /filename.  I would personally rename the file ajax then use  [http://myserver/ajax](http://myserver/ajax).  As for internal static IP's, I set all of ours in the router, we had huge issues with the PS3's and computers fighting over IP's, strangest thing I ever saw.  Anyway if you only assign your server a static IP in the router most are built to know not to re-issue it.
Good luck, it looks interesting program!
Lori

---

