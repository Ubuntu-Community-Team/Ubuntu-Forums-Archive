---
title: "isc-dhcp-server won't start on boot"
date: 2012-10-08
forum: Server Platforms
---

### Post by PhonicLynx on 2012-10-08
Hi,

I have isc-dhcp-server installed on my server and it works beautifully during normal runtime. However if the server gets rebooted or there is a power failure the DHCP server service doesn't load on start up.. hence no computers automatically connect to the network making it hard to reset the server. 

If I "sudo service isc-dhcp-server restart" it tells me that the is no such process meaning that the server didn't even start on boot. I have checked all the rc*d.rc folders and I can't see anything referencing to do with the DHCP server. What is supposed to be happening? What can I check / change to make it work on boot?

---

### Post by albandy on 2012-10-08
Did you configure network throught /etc/network/interfaces  or throught network manager?

---

### Post by newbie-user on 2012-10-08
Check your /etc/default/dhcp3-server to see that you have specified a default interface for DHCP to run on.

---

### Post by clutzer on 2012-10-17
I'm having the same problem.  From kern.log it looks like the isc-dhcp-server process is starting before my network interfaces get configured.  This should be a simple dependency problem...

---

### Post by clutzer on 2012-10-17
I've confirmed my suspicion and provided a fix to my problem.  I checked the isc-dhcp-server upstart configuration file:

/etc/init/isc-dhcp-server.conf

and it did not depend on any interface before starting.  I changed the "on start" line in /etc/init/isc-dhcp-server.conf to look like this:

```
start on runlevel [2345] and net-device-up IFACE=eth1
```

I added the stuff after and including "and...".  Now, after a reboot I get:

```
service isc-dhcp-server status
isc-dhcp-server start/running, process 2853
```

Now, please note that I'm running my DHCP server on eth1.  Please adjust accordingly.  Also note: it would be cleaner if the "on start" dependency automatically depended on any interfaces defined in /etc/default/isc-dhcp-server, but I'll leave that to ISC developers.

---

### Post by badbod on 2012-11-23
> **clutzer said:**
> I've confirmed my suspicion and provided a fix to my problem.  I checked the isc-dhcp-server upstart configuration file:

/etc/init/isc-dhcp-server.conf

and it did not depend on any interface before starting.  I changed the "on start" line in /etc/init/isc-dhcp-server.conf to look like this:

```
start on runlevel [2345] and net-device-up IFACE=eth1
```

I added the stuff after and including "and...".  Now, after a reboot I get:

```
service isc-dhcp-server status
isc-dhcp-server start/running, process 2853
```

Now, please note that I'm running my DHCP server on eth1.  Please adjust accordingly.  Also note: it would be cleaner if the "on start" dependency automatically depended on any interfaces defined in /etc/default/isc-dhcp-server, but I'll leave that to ISC developers.
Nice one Clutzer, same issue and solved with your fix. Many thanks.


[edit] 
Notice the system with problem was a standard Ubuntu desktop system, upgraded several times (think this system started at 10.04 ? around there.) Now 12.04 LTS. Configured static using Network-Manager

Server version 12.04 LTS fresh installs, 2 systems, isc-dhcp-server starts fine without this fix. Configured static, no GUI or Network-Manager. Wonder if this is the difference? Configured in network config file instead of Network-Manager?
 [/edit]

---

### Post by badbod on 2012-11-23
> **albandy said:**
> Did you configure network throught /etc/network/interfaces  or throught network manager?

Albandy you might have something there but all my systems live so can't test.

Also, my problem system is desktop version and it has been upgraded quite a few times, the working fine ones are server version, never upgraded. Ho Humm,  bug report nightmare time  :)

Regards

---

### Post by badbod on 2012-11-23
> **PhonicLynx said:**
> Hi,

I have isc-dhcp-server installed on my server and it works beautifully during normal runtime.

Sorry for spamming this thread but I did have to comment on this.

I have used many DHCP servers, and I have to agree with Ubuntu for moving to this one, and with PhonicLynx on his comment. Lean, Mean and easy. A real breath of fresh air compared with all the others I have used.

Regards

---

