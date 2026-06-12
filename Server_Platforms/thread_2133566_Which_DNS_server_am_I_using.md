---
title: "Which DNS server am I using?"
date: 2013-04-08
forum: Server Platforms
---

### Post by wlraider70 on 2013-04-08
I have dhcp and dhcp3 server installed. One of them is running, but the log doesn't seem to specify if its 3 or not.
I tried service dhcp-server status and got nothing. I also tried a bunch of permutations.
I did get a result from service isc-dhcp-server status. Now I'm more confused, is this a third server or one of the first 2?


Ultimately, I just want to remove the unused one.

---

### Post by papibe on 2013-04-08
Hi  wlraider70.

My first guess is that one is a meta package that install the latest package. So it is probably no problem, and you shouldn't uninstall it.

For instance, in 12.04 the package dhcp3-server is a meta, or a virtual package. See it [here]("http://packages.ubuntu.com/quantal/dhcp3-server"). Which just install the latest proper server package: isc-dhcp-server.

To see, what packages are installed on your system do this:
```
dpkg -l | grep dhcp
```
Or to check specific version packages:
```
apt-cache policy dhcp3-server

apt-cache policy isc-dhcp-server
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by wlraider70 on 2013-04-08
Ok, I think I follow most of that

```

server@philo:/etc/dhcp$ dpkg -l | grep dhcp
ii  dhcp3-server                       4.1.ESV-R4-0ubuntu5.6               ISC DHCP server (transitional package)
ii  isc-dhcp-client                    4.1.ESV-R4-0ubuntu5.6               ISC DHCP client
ii  isc-dhcp-common                    4.1.ESV-R4-0ubuntu5.6               common files used by all the isc-dhcp* packages
ii  isc-dhcp-server                    4.1.ESV-R4-0ubuntu5.6               ISC DHCP server for automatic IP address assignment

```

So then where do I do my configuration? 
I have a /etc/dhcp/dchpd.conf 
and       /etc/dhcp3.dhcpd.conf

They are different files.

---

### Post by papibe on 2013-04-08
This one should be the good one:
```
/etc/dhcp/dhcpd.conf
```
Regards.

---

### Post by chrisguk on 2013-04-08
Hi if you are unsure why not take a look at my video here:

[http://www.youtube.com/watch?v=Cq_5ksf5iQY](http://www.youtube.com/watch?v=Cq_5ksf5iQY)

---

