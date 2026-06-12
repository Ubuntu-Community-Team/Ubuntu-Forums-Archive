---
title: "headless server &quot;froze&quot; seems like it's simply ignoreing dhcp offers?"
date: 2012-04-20
forum: Server Platforms
---

### Post by jerome1232 on 2012-04-20
Okay so I have a very, very, very humble home server that I use for mumble, I got the bright idea to try using it as a minecraft server, just to see if it could handle the load, there would only be a max of like 3 clients at one time ever. I started it up and started playing, I kept htop open to see how it handled the load, after a few minutes everything just froze up and I couldn't contact the server via ping or ssh. With just me playing the cpu was around 80% and ram around 90% used.

Checking syslog (that's the right log to check yes?) I notice the same day that this happened syslog is spammed with what seems like very rapid dhcp traffic that is just, getting ignored. Here is what I am talking about. Could that be a symptom of the system being overloaded? Or something else entirely?

```
Apr 18 14:31:53  dhclient: last message repeated 5 times
Apr 18 14:32:42  dhclient: last message repeated 3 times
Apr 18 14:32:42 voiceserv kernel: [1126699.590590] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:64:0f:28:8d:28:41:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=30
842 PROTO=2 
Apr 18 14:32:48 voiceserv dhclient: DHCPREQUEST of 108.215.132.8 on eth0 to 192.168.1.254 port 67
Apr 18 14:33:04 voiceserv dhclient: DHCPREQUEST of 108.215.132.8 on eth0 to 192.168.1.254 port 67
Apr 18 14:33:23 voiceserv dhclient: DHCPREQUEST of 108.215.132.8 on eth0 to 255.255.255.255 port 67
Apr 18 14:34:27  dhclient: last message repeated 5 times
Apr 18 14:34:33 voiceserv avahi-daemon[714]: Withdrawing address record for 108.215.132.8 on eth0.
Apr 18 14:34:33 voiceserv avahi-daemon[714]: Leaving mDNS multicast group on interface eth0.IPv4 with address 108.215.132.8.
Apr 18 14:34:33 voiceserv avahi-daemon[714]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 18 14:34:33 voiceserv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 18 14:34:33 voiceserv dhclient: DHCPOFFER of 108.215.132.8 from 192.168.1.254
Apr 18 14:34:33 voiceserv dhclient: DHCPREQUEST of 108.215.132.8 on eth0 to 255.255.255.255 port 67
Apr 18 14:34:56  dhclient: last message repeated 2 times
Apr 18 14:34:56 voiceserv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 18 14:34:56 voiceserv dhclient: DHCPOFFER of 108.215.132.8 from 192.168.1.254
Apr 18 14:34:56 voiceserv dhclient: DHCPREQUEST of 108.215.132.8 on eth0 to 255.255.255.255 port 67
Apr 18 14:34:59 voiceserv dhclient: DHCPREQUEST of 108.215.132.8 on eth0 to 255.255.255.255 port 67
Apr 18 14:35:07 voiceserv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 18 14:35:07 voiceserv dhclient: DHCPOFFER of 108.215.132.8 from 192.168.1.254
Apr 18 14:35:07 voiceserv dhclient: DHCPREQUEST of 108.215.132.8 on eth0 to 255.255.255.255 port 67
Apr 18 14:35:10 voiceserv dhclient: DHCPREQUEST of 108.215.132.8 on eth0 to 255.255.255.255 port 67
Apr 18 14:35:18 voiceserv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 18 14:35:18 voiceserv dhclient: DHCPOFFER of 108.215.132.8 from 192.168.1.254
Apr 18 14:35:18 voiceserv dhclient: DHCPREQUEST of 108.215.132.8 on eth0 to 255.255.255.255 port 67
Apr 18 14:35:35  dhclient: last message repeated 2 times
Apr 18 14:35:35 voiceserv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 18 14:35:35 voiceserv dhclient: DHCPOFFER of 108.215.132.8 from 192.168.1.254
Apr 18 14:35:35 voiceserv dhclient: DHCPREQUEST of 108.215.132.8 on eth0 to 255.255.255.255 port 67
Apr 18 14:35:46  dhclient: last message repeated 2 times
Apr 18 14:35:46 voiceserv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 18 14:35:46 voiceserv dhclient: DHCPOFFER of 108.215.132.8 from 192.168.1.254
Apr 18 14:35:46 voiceserv dhclient: DHCPREQUEST of 108.215.132.8 on eth0 to 255.255.255.255 port 67
Apr 18 14:36:02  dhclient: last message repeated 2 times
Apr 18 14:36:02 voiceserv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 18 14:36:02 voiceserv dhclient: DHCPOFFER of 108.215.132.8 from 192.168.1.254
Apr 18 14:36:02 voiceserv dhclient: DHCPREQUEST of 108.215.132.8 on eth0 to 255.255.255.255 port 67
Apr 18 14:36:05 voiceserv dhclient: DHCPREQUEST of 108.215.132.8 on eth0 to 255.255.255.255 port 67
Apr 18 14:36:13 voiceserv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 18 14:36:13 voiceserv dhclient: DHCPOFFER of 108.215.132.8 from 192.168.1.254
Apr 18 14:36:13 voiceserv dhclient: DHCPREQUEST of 108.215.132.8 on eth0 to 255.255.255.255 port 67
Apr 18 14:36:34  dhclient: last message repeated 2 times
Apr 18 14:36:34 voiceserv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 18 14:36:34 voiceserv dhclient: DHCPOFFER of 108.215.132.8 from 192.168.1.254
Apr 18 14:36:34 voiceserv dhclient: DHCPREQUEST of 108.215.132.8 on eth0 to 255.255.255.255 port 67
Apr 18 14:36:58  dhclient: last message repeated 2 times
Apr 18 14:36:58 voiceserv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 18 14:36:58 voiceserv dhclient: DHCPOFFER of 108.215.132.8 from 192.168.1.254
Apr 18 14:36:58 voiceserv dhclient: DHCPREQUEST of 108.215.132.8 on eth0 to 255.255.255.255 port 67
Apr 18 14:37:10  dhclient: last message repeated 2 times
Apr 18 14:37:10 voiceserv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3

```

---

### Post by CharlesA on 2012-04-20
Huh, it shouldn't randomly lose it's IP.

What happens if you set it to a static ip and reboot?

---

### Post by jerome1232 on 2012-04-20
> **CharlesA said:**
> Huh, it shouldn't randomly lose it's IP.

What happens if you set it to a static ip and reboot?

Unfortunately I can't. This is a dynamically allocated ip address. It's actually behind a router, when that router puts a device in DMZ+ mode it assigns the device it's [the routers] dynamic public ip. Since that is due to change I can't simply assign it statically.

---

### Post by CharlesA on 2012-04-20
If you have console access when this happens, have you tried killing and restarting the dhclient?

---

### Post by jerome1232 on 2012-04-20
Okay so, I hooked up a monitor and keyboard, as soon as I start the minecraft server my connection just *poofs*, If I manually run dhclient it just quits and logs no broadcast interfaces found to syslog. Upon a reboot the boot process hangs for about a minute on "waiting for network configuration" and has the exact same symptoms. It doesn't work until I shut it down and wait for a very good while to boot it back up.

the log specifically looks like

```
*timestamp* voiceserv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
*timestamp* voiceserv dhclient: No broadcast interfaces found - exiting.
```

If I staticly set the ip to something that should be on my lan (192.168.1.3, which is reserved for static) it won't respond to ping or ssh attempts.

--------------

I got the bright idea to reboot the switch it's connected to, and everything is working for now. It's just strange that twice the switch essentially died just as I started the minecraft server, and my network printer was working which is also connected to the same switch.

For now I'm attributing this as a switch failure, thanks for the help and feel free to offer any insight (even it if's a Yup, you need a new switch)

](*,)

Yikes I don't know if this little guy can keep up, we'll see.

---

### Post by CharlesA on 2012-04-20
Wow. I wonder if the switch was the problem. How old is it?

I'd do more testing before replacing it unless it's a fairly old one.

---

### Post by jerome1232 on 2012-04-21
> **CharlesA said:**
> Wow. I wonder if the switch was the problem. How old is it?

I'd do more testing before replacing it unless it's a fairly old one.

I got it [the switch] second hand at a goodwill at least 5 years ago. The computer itself is older than that [read, it originally had win95 on it], I'll do more fiddling with it in a few days, try running it under that load directly connected to the router I guess. I don't know what else I can do to test it.

---

### Post by Jonathan L on 2012-04-21
Hi Jerome

> attributing this as a switch failure

Switch problems are more common than you might imagine, especially if you have a cheap one.

I've had experience of many aging rather badly and jamming up networks, which I presume to be degradation of the eletrical properties.  Also many switches behave poorly when given bursts of heavy load, especially broadcasts, or having to learn many ether addresses; which I've surmised is they behave badly when they run out of RAM for incoming frames or outgoing queues.

Debug by replacing with a known-good direct cable or another switch or hub.  Remember that older computers don't have "auto-swap" so you'll probably need an ethernet swap cable if you do it directly.

Hope that helps.

Kind regards,
Jonathan.

---

### Post by SeijiSensei on 2012-04-21
How about just dropping requests to the broadcast address with iptables?

```
sudo iptables -I INPUT -i eth0 -d 255.255.255.255 -j DROP
```

---

