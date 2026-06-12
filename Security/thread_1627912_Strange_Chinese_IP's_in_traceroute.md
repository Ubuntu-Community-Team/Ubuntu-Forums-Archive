---
title: "Strange Chinese IP's in traceroute?"
date: 2010-11-22
forum: Security
---

### Post by delta23 on 2010-11-22
Hey :)

first of all, sorry if this is the wrong forum category.
Recently i did a traceroute to my providers homepage and saw some strange ip addresses, here is the output:

```
delta9@netbook ~ $ traceroute aon.at
traceroute to aon.at (195.3.96.72), 30 hops max, 60 byte packets
 1  DD-WRT (192.168.1.1)  1.143 ms  1.895 ms  2.038 ms
 2  dsldevice.lan (10.0.0.138)  55.488 ms  55.193 ms  54.058 ms
 3  113.67.91.160 (113.67.91.160)  30.485 ms 113.70.44.160 (113.70.44.160)  31.837 ms 113.71.176.192 (113.71.176.192)  32.552 ms
 4  195.3.66.133 (195.3.66.133)  19.999 ms  21.821 ms  24.391 ms
 5  AUX10-LKREBC10.highway.telekom.at (195.3.68.61)  48.377 ms  50.161 ms  50.391 ms
 6  195.3.118.182 (195.3.118.182)  36.015 ms  28.154 ms  29.900 ms
 7  172.18.96.235 (172.18.96.235)  81.617 ms  73.965 ms  72.844 ms
```

[LIST]
[*]DD-WRT (192.168.1.1) - my linksys wrt54gs running dd-wrt micro
[*]dsldevice.lan (10.0.0.138 ) - the modem i got from my provider - speedtouch 546v6
[/LIST]

All those 113.xxx addresses looked kinda suspicious to me, so i did some whois query's:
[http://whois.domaintools.com/113.67.91.160](http://whois.domaintools.com/113.67.91.160)
```

inetnum:      113.64.0.0 - 113.95.255.255
netname:      CHINANET-GD
descr:        CHINANET Guangdong province network
descr:        Data Communication Division
descr:        China Telecom
country:      CN
admin-c:      CH93-AP
tech-c:       IC83-AP
remarks:      service provider
status:       ALLOCATED PORTABLE
mnt-by:       APNIC-HM
mnt-lower:    MAINT-CHINANET-GD
mnt-routes:   MAINT-CHINANET-GD

```

What do you guys think? Have i been hacked or am i just paranoid?
The strange thing is btw, that those ip's change all the time. I even get some from Taiwan sometimes (xxxx.veetime.com or sth??)
And the problem isnt OS specific, on Windows the traceroute looks the same (also on different devices). :(

Want to hear your opinions. :)

---

### Post by raw157 on 2010-11-22
I'm sad to say I've not no direct answer for you. However, I'm glad to see that I'm not the only person who enjoys doing trace routs just to see where you signal goes to get to a web page. That's very interesting, I'll be sure to check back to see if you get an answer.

---

### Post by klingerman1 on 2010-12-12
China owns a lot of things..... I wont get more specific.

---

### Post by lensman3 on 2010-12-12
You mean this?  I think wikileaks reported this too.

[http://www.bbc.co.uk/news/technology-11773146]("http://www.bbc.co.uk/news/technology-11773146")

Do a google search on "china dns servers reroute"

---

### Post by WinstonChurchill on 2010-12-14
Routes often make no geographical sense at all. For instance, a friend  of mine in Dallas has an ISP that routes all his traffic through Houston  (Several hundred miles away), even when he talks to other servers in Dallas.

Furthermore, nobody could "hack" your computers or even your ISP and convince it to use different routes. The only control any given router has over a packet is where to send it to next - you can't pre-ordain a packet to follow some specific route. (There is a way to do this in IPv6, but I imagine it would be difficult to do in media res). 

The possibility of redirection through China is intriguing though - 'aon.at' is presumably in Austria (my traceroutes would tend to affirm that). Do you live in Austria? Is this route through China consistent, or on-and-off? 

If you're alarmed by there being multiple IP addresses for that routing point, know that there's nothing unusual about load-balancing routing like that - for instance, when I traceroute google I get:
```

user@host:~$ traceroute google.com -q 10 -n
traceroute to google.com (74.125.227.48), 30 hops max, 60 byte packets
 1  10.0.1.1  0.501 ms  0.647 ms  0.890 ms  1.298 ms  1.276 ms  1.939 ms * * * *
 2  173.*.*.*  8.117 ms  8.091 ms  8.065 ms  7.958 ms  7.935 ms  7.909 ms  8.414 ms  8.820 ms  8.760 ms  8.289 ms
 3  130.81.131.36  8.685 ms  9.620 ms  7.006 ms  6.969 ms  6.885 ms  6.853 ms  6.827 ms  6.714 ms  6.660 ms  6.191 ms
 4  130.81.28.210  7.276 ms  10.100 ms  9.786 ms  8.242 ms  9.738 ms  9.661 ms  9.588 ms  9.563 ms  9.540 ms  9.515 ms
 5  152.63.96.49  9.443 ms  9.424 ms  8.762 ms  6.266 ms  6.832 ms  6.753 ms  8.025 ms  12.966 ms  12.942 ms  12.916 ms
 6  152.63.97.197  12.943 ms 
    152.63.101.62  12.852 ms 
    152.63.101.9   12.826 ms 
    152.63.101.49  12.813 ms 
    152.63.101.25  12.760 ms 
    152.63.101.29  12.735 ms 
    152.63.101.66  12.440 ms 
    152.63.101.29  12.379 ms  7.151 ms  10.927 ms
 7  152.179.51.26  10.807 ms  10.692 ms  10.694 ms  10.573 ms  10.547 ms  10.481 ms  10.455 ms  10.454 ms  10.336 ms  10.311 ms
 8  72.14.233.77  87.879 ms  78.328 ms  9.233 ms  9.166 ms  9.103 ms  9.034 ms  9.053 ms  9.835 ms  9.755 ms  9.741 ms
 9  209.85.250.77  10.289 ms  10.236 ms  12.453 ms  12.393 ms  12.357 ms  12.353 ms  12.277 ms  11.683 ms  11.667 ms  11.640 ms
10  74.125.227.48  11.127 ms  10.968 ms  8.902 ms  8.778 ms  8.691 ms  8.663 ms  10.729 ms  10.705 ms  8.555 ms  10.535 ms

```

---

### Post by The Cog on 2010-12-14
> The only control any given router has over a packet is where to send it to next - you can't pre-ordain a packet to follow some specific route. (There is a way to do this in IPv6, but I imagine it would be difficult to do in media res). 

Nit picking, but...
There is a way to pre-ordain the path taken by a packet. It's an IP option called source routing. You can give a list of IP addresses that the packet must pass through, like way points. You can even specify strict source routing, or loose source routing (where obeying the list need not be so exact). I have no idea how many ISPs obey or ignore this IP option though. I would expect that most ignore it.

---

### Post by WinstonChurchill on 2010-12-15
> **The Cog said:**
> Nit picking, but...
There is a way to pre-ordain the path taken by a packet. It's an IP option called source routing. You can give a list of IP addresses that the packet must pass through, like way points. You can even specify strict source routing, or loose source routing (where obeying the list need not be so exact). I have no idea how many ISPs obey or ignore this IP option though. I would expect that most ignore it.
My mistake - I thought that was only possible in IPv6.

---

