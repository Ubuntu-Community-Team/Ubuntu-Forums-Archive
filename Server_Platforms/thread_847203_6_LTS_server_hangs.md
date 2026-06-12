---
title: "6 LTS server hangs"
date: 2008-07-02
forum: Server Platforms
---

### Post by Stephen_at on 2008-07-02
Got a very odd problem.

Machine has been pretty much rock solid since I built it apart from an odd recurring incident when the machine just seems to hang. There seems to be nothing in the logs which all just seem to stop getting anything in them at the same time. I thought it was the SiS900 network card as I used to be able to get the box to lockup if I did a lot of pushing and pulling off the box.

I did have no problems with 30+ day uptimes but its recently dropped to 3-5 days and actually I got 10 minutes out of it this morning before it just stopped responding.

Any ideas on what I can do to investigate this further?

Its just a server that I run at home with some file shares on it and bounce some email through so its not like its overloaded.

Digging round the last thing I can see is some message from the evm-engine. I'm not even using evm so what is going on? if I try to uninstall evm it takes ubuntu-standard out which I need for other things so can I just take evm out of the startup?

Thanks

---

### Post by jonabyte on 2008-07-02
try:

```
top
```

and 

```
tail -f /var/log/messages
```


might give you a clue.

---

### Post by jonabyte on 2008-07-02
> **jonabyte said:**
> try:

```
top
```

and 

```
tail -f /var/log/messages
```


might give you a clue.


sorry but that should include sudo in front of the commands, as always....](*,)

---

### Post by Stephen_at on 2008-07-02
The problem is that when its "sulking" its not possible to get anything out of it.

messages has this in it for the hang last night

```

Jul  1 20:30:00 bantock -- MARK --
Jul  1 20:50:03 bantock -- MARK --
Jul  1 21:10:07 bantock -- MARK --
Jul  1 21:30:09 bantock -- MARK --
Jul  1 21:50:11 bantock -- MARK --
Jul  1 22:10:13 bantock -- MARK --
Jul  1 22:30:15 bantock -- MARK --
Jul  1 22:50:17 bantock -- MARK --
Jul  1 23:10:20 bantock -- MARK --
Jul  2 07:09:52 bantock syslogd 1.4.1#17ubuntu7.1: restart.
Jul  2 07:09:52 bantock kernel: Inspecting /boot/System.map-2.6.15-52-server
Jul  2 07:09:52 bantock kernel: Loaded 23278 symbols from /boot/System.map-2.6.15-52-server.

```

daemon.log has

```

Jul  1 23:03:12 bantock ntpd[4238]: synchronized to 194.238.48.2, stratum 2
Jul  2 07:09:52 bantock dnsmasq[3868]: started, version 2.41 cachesize 450
Jul  2 07:09:52 bantock dnsmasq[3868]: compile time options: IPv6 GNU-getopt no-ISC-leasefile no-DBus no-I18N TFTP

```

syslog contains :

```

Jul  1 23:10:09 bantock /USR/SBIN/CRON[13581]: (root) CMD (/usr/lib/cgi-bin/awstats.pl -config=tty  -update >/tmp/tty.txt)
Jul  2 07:09:52 bantock syslogd 1.4.1#17ubuntu7.1: restart.
Jul  2 07:09:52 bantock kernel: Inspecting /boot/System.map-2.6.15-52-server
Jul  2 07:09:52 bantock kernel: Loaded 23278 symbols from /boot/System.map-2.6.15-52-server.

```

kern.log:

```

Jul  1 20:01:45 bantock kernel: [43599247.620000] eth0: Media Link On 100mbps full-duplex
Jul  2 07:09:52 bantock kernel: Inspecting /boot/System.map-2.6.15-52-server
Jul  2 07:09:52 bantock kernel: Loaded 23278 symbols from /boot/System.map-2.6.15-52-server.
Jul  2 07:09:52 bantock kernel: Symbols match kernel version 2.6.15.

```

---

### Post by Stephen_at on 2008-07-04
OK I shutdown and disabled the evm stuff and I also swapped the built in SiS900 network card for a trusty old DEC tulip card

Machine now seems much more responsive and hasn't crashed for 2 days.

---

