---
title: "Server can't access internet directly, but I can ssh tunnel just fine."
date: 2010-09-09
forum: Server Platforms
---

### Post by mathgirl on 2010-09-09
Hello all! ):P

I have a server that I ssh into all the time (it's on a wired connection to my router) and tunnel web traffic through from work sometimes.  So I know it can fetch stuff from the internet and send it out.  It even hosts a webpage, so I know it can receive and send web data.

BUT, if I log into it and try to access a website via wget or lynx, it just times out.  I only discovered this because I can't sudo apt-get anything anymore (none of the servers resolve).

Any ideas what to change?  Any help appreciated!  :p

example:
```

$ ping www.google.com
ping: unknown host www.google.com
$ wget -O - www.google.com > /dev/null
--2010-09-09 10:45:45--  http://www.google.com/
Resolving www.google.com... failed: Name or service not known.
wget: unable to resolve host address `www.google.com'
$ 

```

---

### Post by jbrown96 on 2010-09-09
What are your routes?

---

### Post by cj.surrusco on 2010-09-09
It sounds like it may be a DNS server problem. Have you tried pinging some IP addresses instead of host names?

Also, you might want to check out the /ect/resolv.conf file to check that the name servers match the ones that your ISP provides.

---

### Post by CharlesA on 2010-09-09
My bet is that DNS isn't resolving names.

Try this:

```
dig www.google.com
```

---

### Post by mathgirl on 2010-09-09
Thanks for the help guys! Problem solved! :o

I don't know what my routes are because I don't know what routes are.

digging didn't work:
```

$ ping yahoo.com
ping: unknown host yahoo.com
$ dig www.google.com

; <<>> DiG 9.7.0-P1 <<>> www.google.com
;; global options: +cmd
;; connection timed out; no servers could be reached

```

But you were right, I could ping google's IP even though I can't ping google.
```

$ ping 74.125.43.147
PING 74.125.43.147 (74.125.43.147) 56(84) bytes of data.
64 bytes from 74.125.43.147: icmp_seq=1 ttl=50 time=117 ms
64 bytes from 74.125.43.147: icmp_seq=2 ttl=50 time=121 ms
64 bytes from 74.125.43.147: icmp_seq=3 ttl=50 time=118 ms
^C
--- 74.125.43.147 ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3004ms
rtt min/avg/max/mdev = 117.876/119.207/121.226/1.451 ms
$ ping www.google.com
ping: unknown host www.google.com
$

```

My network is:

modem <-> router_A <-> router_B <-> server

For some reason, resolv.conf contained router_A's IP address.  I changed it to router_B's address (ye olde 192.168.1.1) and now everything works!

I remember I had to do complicated things to update a long time ago, so maybe I changed it back then?

Anyway thank you guys!

---

### Post by Hobgoblin on 2010-09-09
Assuming router A is providing DHCP and your server is using DHCP you may want to look at Router A's settings and change the DNS server to either Router B or use your ISP/Google/OpenDNS DNS servers.

---

### Post by mathgirl on 2010-09-09
What's the default?  I don't remember having to figure out a DNS server to feed to ubuntu when I first installed -- it just automagically connected to the internet.

---

### Post by CharlesA on 2010-09-09
> **mathgirl said:**
> What's the default?  I don't remember having to figure out a DNS server to feed to ubuntu when I first installed -- it just automagically connected to the internet.
It probably just grabbed network info from DHCP when you installed. Not sure why or how that info would have changed unless there are 2 DHCP servers on the network.

---

### Post by cj.surrusco on 2010-09-09
> **mathgirl said:**
> What's the default?  I don't remember having to figure out a DNS server to feed to ubuntu when I first installed -- it just automagically connected to the internet.

DHCP will automatically set up the DNS servers, but if you set up a static IP, then you will have to manually configure them. Have you recently set up a static IP for that server?

---

