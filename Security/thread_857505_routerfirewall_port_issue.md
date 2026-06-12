---
title: "router/firewall port issue"
date: 2008-07-12
forum: Security
---

### Post by Open-SuSe-A-Me on 2008-07-12
hello all

i use azureus on ports 44444/44445 and i have to open them in my router for it to work.  i also use "ipblock" in combination with azureus and normally when i am done downloading i close the ports in my router and traffic stops on those ports. for some reason today after i closed the ports ipblock is still showing blocks on those ports, even as i write this.  this has never happened before, does anyone have any ideas? i thought the router would be blocking these ports. i also have upnp turned off in azureus.

thanks!

---

### Post by HermanAB on 2008-07-12
You worry too much.

If nothing is listening on a port, then it doesn't matter how the router is set.  Stop futzing with the ports, relax and enjoy your Linux system!

Cheers,

Herman

---

### Post by Open-SuSe-A-Me on 2008-07-12
alrighty thanks Herman. i thought that azureus might still be running in the background somehow because i started it from the terminal today which i normally dont do.   should i use guarddog/firestarter also or am i good with just the router?

---

### Post by The Cog on 2008-07-12
you can see waht ports are open  and by what process with the command:
> sudo netstat -plntu
which will tell you if azereus is still running.

A firewall is not really any use until you install a service that you want to limit who can connect to it. My reason for saying this is:
By default, Ubuntu has no listening ports so there is nothing for a firewall to protect. And if you **do** install a service (like Azureus perhaps), you generally want that open to all callers, so a firewall still isn't going to do anything useful. You would just jave to open one or more of the ports that the firewall was blocking.

---

### Post by Open-SuSe-A-Me on 2008-07-13
this is what i get:

 Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:8118          0.0.0.0:*             LISTEN      5172/privoxy
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5033/cupsd
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN      5186/tor
udp        0      0 0.0.0.0:38444           0.0.0.0:*                           4991/avahi-daemon:
udp        0      0 0.0.0.0:68              0.0.0.0:*                           6631/dhclient
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           4991/avahi-daemon:

what is "avahi daemon" and "dhclient" because now i am getting constant blocks in ipblock for "BOGON" and its showing my own IP (192.168.1.1) on ports 68 and 5353. any clues?

thanks

---

### Post by The Cog on 2008-07-13
The first three are only listening on the loopback port so they are not reachable by other machines - no worries there. 

Avahi daemon is (as far as I can tell) un-documented. I think it's some kind of service advertising thing. It's part of the default Ubuntu install (getting very Microsoft in their ways, they are), and I've not seen any problems caused by disabling it.

dhclient is the DHCP client used for requesting an IP address when the machine boots.

I don't know what ipblock is, so I can't help you there.

---

