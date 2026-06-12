---
title: "Configure static IP/hosts file questions"
date: 2009-03-05
forum: Server Platforms
---

### Post by mobcdi on 2009-03-05
I'm using 8.04 and it seems that my hosts file isn't correctly configured, Would the community be willing to have a look?

**hosts file contents**
127.0.0.1 localhost myserver
[staticIPValue] myserver.company.tld myserver.company.tld

#The following lines are desirable for IPv6 capable hosts
::l ip6- localhost ip6- loopback
fe00::0 ip6- localnet
ff00::0 ip6- allnodes
ff02::2 ip6- allrouters
ff02::3 ip6- allhosts

[LIST=1]
[*]*Is it normal for the server.company.tld to be listed twice beside the static IP address?*
[/LIST]

---

### Post by matey3 on 2009-03-05
mine is almost the same except the staticIPvalue is 127.0.1.1 and the name of the server at the end not the whole address because I am getting address from dhcp no static IP assigned.

like yours should be;

127.0.0.1 localhost myserver
127.0.1.1 (or your real address) myserver.company.tld myserver

you can also add addresses here if you have setup a vpn or other NICs in your server

---

### Post by Iowan on 2009-03-05
My server's hosts file is also similar... but different.```

127.0.0.1   localhost.mynet   localhost
127.0.1.1   server.mynet      server

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by bab1 on 2009-03-05
> **Iowan said:**
> My server's hosts file is also similar... but different.```

127.0.0.1   localhost.mynet   localhost
127.0.1.1   server.mynet      server

...


```

All we are doing here is mapping names to IP addresses.

If you are named Robert and you're called bob you still are the same person.

In the above If you ping "server' it will return "server.mynet".

Try adding a 3rd name on that line and then ping that name.  it will still return "server.mynet"

Scripts can add names and that's what has happened to the OP.  I'll bet the DHCP address is not 127 anything as this is for the lo (virtual internal interface).  DHCP is used to configure the NIC physical address (eth) with an IP address.

---

### Post by mobcdi on 2009-03-06
Thanks to all for the help with the hosts file, Could I be very rude and ask about the resolv.conf too as I'm still getting errors that my host isn't set up properly still

resolv.conf
search myserver.company.tld
nameserver IPaddress1
nameserver IPaddress2

[LIST=1]
[*]Should it be company.tld instead if I want to use the domain level DNS servers?
[*]What should a proper working resolv.conf file contain?
[/LIST]

---

### Post by matey3 on 2009-03-06
your resolv.conf file looks correct.

Linux finds these values at the install if you choose to use DHCP 
typical resolv.conf looks like this;


search  your.server.doman
nameserver  123.123.123.3 (whatever your provider's DNS is)
nameserver  192.168.0.2 (or whatever your local DNS is)


You can add more nameserver in resolv.conf file
I think?

---

### Post by mobcdi on 2009-03-06
Mine looks ok so even if I'm going with a Static IP address

---

### Post by matey3 on 2009-03-06
If you are going to set this machine up as your local DNS then you put its IP address in there also Some times your ISP gives you 2 or more DNS IPs, you can use all of them in resolv.conf but I do not know if you can add more search in there?
I dont see why not? (if this is similar to the system as the 'path' statement?)
But the way I have seen it setup is that 1 machine that acts as the DNS for your network has the ISP's IP addresses in resolv.conf. But the rest of the machines dont. they only use your IP address in their resolv file.

So let's say you choose to set this server up with IP 192.168.1.2
your ISP has the DNS of 123.123.123.3 and 123.123.123.5
your resolv.conf for your server is like this;

search myserver.company.tld
nameserver 192.168.1.2
nameserver 123.123.123.3
nameserver 123.123.123.5

another machine on your network would have this resolv.conf;

search myserver.company.tld
nameserver 192.168.1.2



this way you can act as a gateway between your LAN and the Internet.
I think?
sorry I only been at this for a year and am trying to learn myself. so hopefully we learn by discussing.

Any way I checked the machines on our network that this is how we are set up here, 
One thing you can do is check the file interfaces under /etc/network to make sure your static IP address is OK

---

