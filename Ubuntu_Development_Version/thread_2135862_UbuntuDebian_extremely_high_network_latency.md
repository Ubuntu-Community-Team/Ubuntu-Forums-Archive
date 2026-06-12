---
title: "Ubuntu/Debian extremely high network latency"
date: 2013-04-15
forum: Ubuntu Development Version
---

### Post by bird1500 on 2013-04-15
Hi,
For the last several releases (and 13.04 is no exception) I get random and often high network latency on all Ubuntu/Debian based OSes (like Mint) - be it Firefox slow to resolve an address, or "apt-get update" slow to resolve archive.ubuntu.com, sometimes it even fails to resolve a domain.
With non-Debian/Ubuntu based distros (e.g. Fedora) on same computer I don't have this problem.

The interesting thing is -  Chrome doesn't seem to suffer from this annoying issue, I heard Chrome ships with its own tcp or http stack, so could it be that Ubuntu/Debian mangles the http/tcp stack with custom patches that causes me these issues?

I'm on DHCP, screenshot and hw specs attached.

---

### Post by rrnbtter on 2013-04-15
Greetings,
This is not new. I have been using Chrome for my HTTP remote control since some time last year due to firefox latency being such a drag. I still use Firefox even with the problem due to the plug-ins that I prefer.

---

### Post by bird1500 on 2013-04-15
Thanks, though I think it's not (only) a Firefox bug cause apt-get (hence in my case the OS in general) has the same problem.

---

### Post by tgalati4 on 2013-04-15
Post your ping results:

tgalati4@Mint14-Extensa ~/Desktop $ ping -c 10 [www.google.com](www.google.com)
PING [www.google.com](www.google.com) (74.125.224.209) 56(84) bytes of data.
64 bytes from lax02s02-in-f17.1e100.net (74.125.224.209): icmp_req=1 ttl=52 time=50.7 ms
64 bytes from lax02s02-in-f17.1e100.net (74.125.224.209): icmp_req=2 ttl=52 time=49.6 ms
64 bytes from lax02s02-in-f17.1e100.net (74.125.224.209): icmp_req=3 ttl=50 time=50.8 ms
64 bytes from lax02s02-in-f17.1e100.net (74.125.224.209): icmp_req=4 ttl=52 time=51.2 ms
64 bytes from lax02s02-in-f17.1e100.net (74.125.224.209): icmp_req=5 ttl=52 time=51.4 ms
64 bytes from lax02s02-in-f17.1e100.net (74.125.224.209): icmp_req=6 ttl=50 time=51.0 ms
64 bytes from lax02s02-in-f17.1e100.net (74.125.224.209): icmp_req=7 ttl=52 time=51.4 ms
64 bytes from lax02s02-in-f17.1e100.net (74.125.224.209): icmp_req=8 ttl=52 time=50.6 ms
64 bytes from lax02s02-in-f17.1e100.net (74.125.224.209): icmp_req=9 ttl=52 time=50.8 ms
64 bytes from lax02s02-in-f17.1e100.net (74.125.224.209): icmp_req=10 ttl=52 time=51.2 ms

--- [www.google.com](www.google.com) ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 49.695/50.932/51.474/0.541 ms

tgalati4@Mint14-Extensa ~/Desktop $ cat /etc/resolvconf/resolv.conf.d/tail

# OpenDNS Fallback (configured by Linux Mint in /etc/resolvconf/resolv.conf.d/tail).
nameserver 208.67.222.222
nameserver 208.67.220.220

Change the above to 8.8.8.8 and 8.8.4.4 and reboot.

---

### Post by bird1500 on 2013-04-15
Thanks, took like 2-3 minutes:
> $ ping -c 10 [www.google.com]("http://www.google.com")
PING [www.google.com]("http://www.google.com") (212.0.195.44) 56(84) bytes of data.
64 bytes from 212.0.195.44: icmp_req=1 ttl=59 time=36.3 ms
64 bytes from 212.0.195.44: icmp_req=2 ttl=59 time=36.5 ms
64 bytes from 212.0.195.44: icmp_req=3 ttl=59 time=36.7 ms
64 bytes from 212.0.195.44: icmp_req=4 ttl=59 time=35.5 ms
64 bytes from 212.0.195.44: icmp_req=5 ttl=59 time=35.4 ms
64 bytes from 212.0.195.44: icmp_req=6 ttl=59 time=36.9 ms
64 bytes from 212.0.195.44: icmp_req=7 ttl=59 time=35.9 ms
64 bytes from 212.0.195.44: icmp_req=8 ttl=59 time=37.7 ms
64 bytes from 212.0.195.44: icmp_req=9 ttl=59 time=35.5 ms
64 bytes from 212.0.195.44: icmp_req=10 ttl=59 time=35.3 ms

--- [www.google.com]("http://www.google.com") ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 135440ms
rtt min/avg/max/mdev = 35.344/36.231/37.717/0.748 ms



I don't have a "tail" file as in /etc/resolvconf/resolv.conf.d/tail
only a head and base file(s), both empty.

Now I'll change to 8.8.8.8 and 8.8.4.4, reboot, and report if anything's different.

---

### Post by bird1500 on 2013-04-15
Created the tail file, rebooted, and
> ping -c 10 [www.google.com](www.google.com)
PING [www.google.com](www.google.com) (212.0.195.44) 56(84) bytes of data.
64 bytes from host-static-212-0-195-44.moldtelecom.md (212.0.195.44): icmp_req=1 ttl=59 time=35.4 ms
64 bytes from host-static-212-0-195-44.moldtelecom.md (212.0.195.44): icmp_req=2 ttl=59 time=36.1 ms
64 bytes from host-static-212-0-195-44.moldtelecom.md (212.0.195.44): icmp_req=3 ttl=59 time=36.2 ms
64 bytes from host-static-212-0-195-44.moldtelecom.md (212.0.195.44): icmp_req=4 ttl=59 time=37.7 ms
64 bytes from host-static-212-0-195-44.moldtelecom.md (212.0.195.44): icmp_req=5 ttl=59 time=36.1 ms
64 bytes from host-static-212-0-195-44.moldtelecom.md (212.0.195.44): icmp_req=6 ttl=59 time=36.7 ms
64 bytes from host-static-212-0-195-44.moldtelecom.md (212.0.195.44): icmp_req=7 ttl=59 time=36.1 ms
64 bytes from host-static-212-0-195-44.moldtelecom.md (212.0.195.44): icmp_req=8 ttl=59 time=36.3 ms
64 bytes from host-static-212-0-195-44.moldtelecom.md (212.0.195.44): icmp_req=9 ttl=59 time=36.0 ms
64 bytes from host-static-212-0-195-44.moldtelecom.md (212.0.195.44): icmp_req=10 ttl=59 time=35.8 ms

--- [www.google.com](www.google.com) ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 46226ms
rtt min/avg/max/mdev = 35.422/36.286/37.761/0.598 ms


Though google.com in Firefox still took like 6-10 seconds to load.

---

### Post by sanderj on 2013-04-15
That sounds like a DNS problem.

Is

```
ping -n 8.8.8.8
```

fast?

---

### Post by bird1500 on 2013-04-15
Each row (ping) below took like a second, I'm not sure if it's fast or slow:

> 
ping -c 10 -n 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=46 time=115 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=46 time=155 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=46 time=109 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=46 time=124 ms
64 bytes from 8.8.8.8: icmp_req=5 ttl=46 time=99.7 ms
64 bytes from 8.8.8.8: icmp_req=6 ttl=46 time=110 ms
64 bytes from 8.8.8.8: icmp_req=7 ttl=46 time=128 ms
64 bytes from 8.8.8.8: icmp_req=8 ttl=46 time=108 ms
64 bytes from 8.8.8.8: icmp_req=9 ttl=46 time=123 ms
64 bytes from 8.8.8.8: icmp_req=10 ttl=46 time=123 ms

--- 8.8.8.8 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9014ms
rtt min/avg/max/mdev = 99.783/119.871/155.199/14.548 ms




---

### Post by sanderj on 2013-04-15
ping will ping each second. So that's normal.

---

### Post by tgalati4 on 2013-04-15
Sometimes the telephone company or cable company has a switch problem that causes delays.  Your ping results are faster than mine:  37 ms vs 50 ms, but you have several seconds of wait time.  Using google's dns servers improved your speed somewhat, but you are still waiting several seconds for each packet burst.

My ping results for 8.8.8.8 are slightly faster than yours:

tgalati4@Mint14-Extensa ~/Desktop $ ping -n 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=41 time=77.9 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=41 time=89.3 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=41 time=89.5 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=41 time=77.2 ms
64 bytes from 8.8.8.8: icmp_req=5 ttl=41 time=77.9 ms
64 bytes from 8.8.8.8: icmp_req=6 ttl=41 time=77.6 ms
64 bytes from 8.8.8.8: icmp_req=7 ttl=41 time=79.4 ms
64 bytes from 8.8.8.8: icmp_req=8 ttl=41 time=77.3 ms
64 bytes from 8.8.8.8: icmp_req=9 ttl=41 time=78.4 ms
64 bytes from 8.8.8.8: icmp_req=10 ttl=41 time=78.8 ms
^C
--- 8.8.8.8 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9012ms
rtt min/avg/max/mdev = 77.298/80.390/89.543/4.579 ms

I would normally attribute the slowness to video streaming of March Madness (college basketball) games, but it could also be Tax Day traffic.

Complain to your ISP provider and let them run modem diagnostics.  One time I had my DSL line replaced because of squirrel chews which caused similar behavior.

---

### Post by chrisle on 2013-04-15
Hi

here is a link to chrome networking [http://www.igvita.com/2012/06/04/chrome-networking-dns-prefetch-and-tcp-preconnect](http://www.igvita.com/2012/06/04/chrome-networking-dns-prefetch-and-tcp-preconnect)

I do not have any issues with Firefox.  What you can do to test is type in a webpage you have NOT visited before and hit enter and count how long it takes to load the page completly. 
Than copmare the time you got for both browsers. eg [www.spiegel.de](www.spiegel.de)

You should also check what DNS servers you use on your router 192.168.1.1 and test how fast they respond. Do pingtests like before. If they are good you can change your network settings and test maybe all works faster than. ;-)

Hope this helps.

---

### Post by bird1500 on 2013-04-15
Thanks tgalati4, but here's what baffles me: how can you explain that with Google Chrome I don't experience this issue at all - e.g. google.com, phoronix.com and other on-line sites always load up instantly.
An example I ran just now: Chrome loaded up instantly the site archive.ubuntu.com, and when I clicked on file at
[http://archive.ubuntu.com/ubuntu/ls-lR.gz](http://archive.ubuntu.com/ubuntu/ls-lR.gz)
it offered instantly to download it.
But, after it I fired up gnome-terminal and wget took like 10 seconds to resolve "archive.ubuntu.com" to download that file, so it's the OS, not my ISP provider, right?
Also, I don't experience this problem with Fedora (aka non-debian distros) or window$.

---

### Post by chrisle on 2013-04-15
Hi 

as stated above I do not have the problem you describe so no gerneral OS issue. 

But there seems to be some DNS issue maybe you are affected try changing your DNS and test. Have a look here [http://www.dedoimedo.com/computers/ubuntu-dns-resolution.html](http://www.dedoimedo.com/computers/ubuntu-dns-resolution.html)

Btw I use chromium for testing and archive.ubuntu.com takes below one second with both browsers downlaod of the tgz is also nearly the same.

---

### Post by alphacrucis2 on 2013-04-16
Sometimes Firefox goes funny if network.dns.disableIPv6 is set to false when no ipv6 dns server is available. Try setting to this to **true** under about:config in firefox (you type about:config into the firefox URL bar - it will give you a warning as arbitrarily changing some of the stuff in there can bork firefox - then type ipv6 into the search field to save scrolling miles down through the settings). Don't do this if you are actually accessing dns servers via ipv6.

---

### Post by bird1500 on 2013-04-16
> **alphacrucis2 said:**
> Sometimes Firefox goes funny if network.dns.disableIPv6 is set to false when no ipv6 dns server is available. Try setting to this to **true** under about:config in firefox (you type about:config into the firefox URL bar - it will give you a warning as arbitrarily changing some of the stuff in there can bork firefox - then type ipv6 into the search field to save scrolling miles down through the settings). Don't do this if you are actually accessing dns servers via ipv6.

You did the unthinkable, you fixed my oldest gripe about Ubuntu, Firefox now works fine, thank you, I'm shining and it's all rainbows and ponies all around!
The rest of the OS (wget, apt-get) still have the ~10 second delay issue, but they're not nearly as important as Firefox. Their problem is probably also an IPv6 one, though, unlike with Firefox, I/we don't know how to fix them, that is the rest of the OS.

---

### Post by sanderj on 2013-04-16
> **bird1500 said:**
> 
The rest of the OS (wget, apt-get) still have the ~10 second delay issue, but they're not nearly as important as Firefox. Their problem is probably also an IPv6 one, though, unlike with Firefox, I/we don't know how to fix them, that is the rest of the OS.

What's the output of:

```
time host www.google.com
```

---

### Post by jdthood on 2013-04-16
What is the content of /etc/resolv.conf?

---

### Post by alphacrucis2 on 2013-04-16
> **bird1500 said:**
> You did the unthinkable, you fixed my oldest gripe about Ubuntu, Firefox now works fine, thank you, I'm shining and it's all rainbows and ponies all around!
The rest of the OS (wget, apt-get) still have the ~10 second delay issue, but they're not nearly as important as Firefox. Their problem is probably also an IPv6 one, though, unlike with Firefox, I/we don't know how to fix them, that is the rest of the OS.

I've seen this issue with firefox on windows too so it isn't specifically a ubuntu problem. I don't know how to fix the wget, apt-get problem unfortunately.

---

### Post by bird1500 on 2013-04-16
> **sanderj said:**
> What's the output of:

```
time host www.google.com
```

It's pretty quick
> $ time host [www.google.com]("http://www.google.com")
[www.google.com]("http://www.google.com") has address 212.0.195.24
[www.google.com]("http://www.google.com") has address 212.0.195.49
[www.google.com]("http://www.google.com") has address 212.0.195.39
[www.google.com]("http://www.google.com") has address 212.0.195.35
[www.google.com]("http://www.google.com") has address 212.0.195.20
[www.google.com]("http://www.google.com") has address 212.0.195.45
[www.google.com]("http://www.google.com") has address 212.0.195.59
[www.google.com]("http://www.google.com") has address 212.0.195.30
[www.google.com]("http://www.google.com") has address 212.0.195.50
[www.google.com]("http://www.google.com") has address 212.0.195.25
[www.google.com]("http://www.google.com") has address 212.0.195.54
[www.google.com]("http://www.google.com") has address 212.0.195.29
[www.google.com]("http://www.google.com") has address 212.0.195.55
[www.google.com]("http://www.google.com") has address 212.0.195.40
[www.google.com]("http://www.google.com") has address 212.0.195.44
[www.google.com]("http://www.google.com") has address 212.0.195.34
[www.google.com]("http://www.google.com") has IPv6 address 2a00:1450:4017:801::1010

real    0m1.196s
user    0m0.000s
sys    0m0.008s


The interesting thing is, it also pings archive.ubuntu.com quickly, then I type "wget http://archive.ubuntu.com/ubuntu/ls-lR.gz"
and it waits for like 10 seconds with "Resolving archive.ubuntu.com (archive.ubuntu.com)...", then proceeds downloading.
Weird.


As to what's in /etc/resolv.conf - I already changed its contents to "nameserver 8.8.8.8 and nameserver 8.8.4.4" as suggested above and I don't recall what was there originally.

---

### Post by zika on 2013-04-16
Mea culpa. Sorry...

---

### Post by tgalati4 on 2013-04-16
For future reference, if you are running firefox, check your *about:config* page:  (These are my settings, yours may be different.)

Search on "ipv"

network.dns.disableIPv6;true
network.dns.ipv4OnlyDomains;
network.http.fast-fallback-to-IPv4;true

---

### Post by sanderj on 2013-04-16
> **bird1500 said:**
> It's pretty quick

The interesting thing is, it also pings archive.ubuntu.com quickly, then I type "wget http://archive.ubuntu.com/ubuntu/ls-lR.gz"
and it waits for like 10 seconds with "Resolving archive.ubuntu.com (archive.ubuntu.com)...", then proceeds downloading.
Weird.


As to what's in /etc/resolv.conf - I already changed its contents to "nameserver 8.8.8.8 and nameserver 8.8.4.4" as suggested above and I don't recall what was there originally.


A possible explanation is this:
1) The host you want to access (like archive.ubuntu.com), has both IPv4 and IPv6 addresses (=fact, see below)
2) Your system **thinks** it can handle IPv6, and wget / firefox / ... tries on IPv6 first. Alas IPv6 does not work, so that results in a time-out after a few seconds.
3) After the time-out, the program tries on IPv4, and that works immediatly
4) Result: a sloooooow connection setup
This is a well-known problem on "confused" system / setups.
Google has introduced a solution for this, called "happy eyeballs" (see [http://en.wikipedia.org/wiki/Happy_Eyeballs](http://en.wikipedia.org/wiki/Happy_Eyeballs)), and has implemented this in Chrome / Chromium. So: can isntall and test the speed in Chromium?
Another workaround/solution is to disable IPv6 at the OS level, or in the DNS lookups.

But first a question: can you post the output of "ifconfig"? That way we can see if there are any public IPv6 addresses.


```
$ host archive.ubuntu.com
archive.ubuntu.com has address 91.189.92.156
archive.ubuntu.com has address 91.189.92.176
archive.ubuntu.com has address 91.189.92.202
archive.ubuntu.com has address 91.189.92.177
archive.ubuntu.com has address 91.189.92.201
archive.ubuntu.com has address 91.189.92.200
archive.ubuntu.com has IPv6 address 2001:67c:1360:8c01::18
archive.ubuntu.com has IPv6 address 2001:67c:1360:8c01::1a
archive.ubuntu.com has IPv6 address 2001:67c:1360:8c01::19

```

---

### Post by sanderj on 2013-04-16
PS:

Happy Eyebalss testing - made easy: See [http://ipv6-or-no-ipv6.blogspot.nl/2013/02/easy-happy-eyeballs-testing.html](http://ipv6-or-no-ipv6.blogspot.nl/2013/02/easy-happy-eyeballs-testing.html)

```

time curl [http://badipv4.test.ipv6friday.org/](http://badipv4.test.ipv6friday.org/) > /dev/null
time curl [http://badipv6.test.ipv6friday.org/](http://badipv6.test.ipv6friday.org/) > /dev/null

```

Can you run that on your system?

---

### Post by rrnbtter on 2013-04-16
Greetings,
Miredo is available in the Software Center as Teredo.  Its a 640k install and provides an immediate fix. It ports the ipv6 call to ipv4 if needed and therefore removes the delay.   Run the test [http://test-ipv6.com/](http://test-ipv6.com/) before and after the install and compare. Not bad! Thanks for the information!

---

### Post by rrnbtter on 2013-04-16
Greetings, 
I suggest you run a quick software update after installing Teredo.  I got a 5meg system and network update. Not sure if it applies to this thread but I did a complete update around 11am and it is odd that I now get a network update after installing Teredo.

---

### Post by bird1500 on 2013-04-16
ifconfig (with teredo which didn't help):
```

ifconfig
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:c4:24:cf  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e2cb:4eff:fec4:24cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:756 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1189356 (1.1 MB)  TX bytes:73359 (73.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12243 (12.2 KB)  TX bytes:12243 (12.2 KB)

teredo    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet6 addr: 2001:0:53aa:64c:2c9e:908f:d1c8:e26f/32 Scope:Global
          inet6 addr: fe80::ffff:ffff:ffff/64 Scope:Link
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1280  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:144 (144.0 B)

```

time curl:
the 1st one: doesn't get any "received" packets, just waits for something, doesn't exit, I killed it after like a minute.
the 2nd one waits for like 15 seconds and prints this:
> $ time curl [http://badipv6.test.ipv6friday.org/](http://badipv6.test.ipv6friday.org/) > /dev/null
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   226  100   226    0     0     14      0  0:00:16  0:00:15  0:00:01  1124

real    0m15.228s
user    0m0.008s
sys    0m0.004s



Since I don't have IPv6 enabled (or so I get the problem), I wonder if I can just "enable" it, in my first post there's my screenshot which shows IPv6 has no IP/data, maybe there's a magic button to enable it, my computer is fairly modern, or does it depend on my ISP.

---

### Post by rrnbtter on 2013-04-16
Greetings, This is mine.

ifconfig
teredo    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet6 addr: 2001:0:53aa:64c:a3:6638:5949:afde/32 Scope:Global
          inet6 addr: fe80::ffff:ffff:ffff/64 Scope:Link
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1280  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:17632 (17.6 KB)  TX bytes:19104 (19.1 KB)

Satellite-L305:~$  time curl [http://badipv6.test.ipv6friday.org/](http://badipv6.test.ipv6friday.org/) > /dev/null
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   226  100   226    0     0     41      0  0:00:05  0:00:05 --:--:--   668

real    0m5.428s
user    0m0.012s
sys    0m0.000s

---

### Post by chrisle on 2013-04-16
Hi all

Can someone point me to an article or something why the poster of the problem should have an ipv6 dual stack problem when he does not have an IPv6 address enabled?

Does a Linux host asks a DNS server for an IPv6 address  even though he has no way of reaching an IPv6 host without some sort of tunneling?

Thanks a lot

---

### Post by Sworddragon on 2013-04-17
The problem seems to be really simple for you all:

I had the same problem some time ago too. Firefox had a delay of exact 5 seconds to resolve the first time a DNS address but after this the loading appeared instantly. This is because Firefox has an own internal DNS cache (and other browsers/applications maybe too).

I have debugged this problem with Wireshark and figured out that quad-A records (IPv6 DNS request) aren't answered the first time which caused any application to wait exactly 5 seconds for the next request. The second request was successfull every time. Applications that doesn't use an internal DNS cache are affected on every request (like apt and wget). Applications that are using only IPv4 aren't affected from this issue. Changing to 8.8.8.8 or 8.8.4.4 doesn't solve this issue.

Interestingly this behavior happened on other machines even with other operating systems (like Windows). The solution was simple: Over the years my router got partly defect and caused this issue. After getting a new router from my ISP all was working fine.

**I recommend you to debug this problem with Wireshark and get a new router/modem if needed. A workaround is to install a local DNS-server or to disable any IPv6 on your system.**

---

### Post by bird1500 on 2013-04-17
It's not the router, I don't have this problem with Fedora or Win7 on same computer, only with Ubuntu/Debian derivatives.

---

### Post by Sworddragon on 2013-04-17
Maybe your Fedora installation had already a local DNS server. At least Windows 7 does cache DNS addresses. I recommend you to do some research with Wireshark to look what is happening there.

---

### Post by zika on 2013-04-17
Do You use dnsmasq?

---

### Post by bird1500 on 2013-04-17
Anything's by default except what I've been asked to do in this forum, thanks anyone, I'll mark the thread as solved and move on since I don't think the (rest of the) issue's gonna get solved, the thread's big and ppl don't read thru it and we're likely starting to repeat ourselves.

---

### Post by zika on 2013-04-17
> **bird1500 said:**
> Anything's by default except what I've been asked to do in this forum, thanks anyone, I'll mark the thread as solved and move on since I don't think the (rest of the) issue's gonna get solved, the thread's big and ppl don't read thru it and we're likely starting to repeat ourselves.
My message about dnsmasq was a suggestion/advice... That helped several machines/users that I help to use Ubuntu/Linux... You might try it... Choice is Yours...

---

### Post by rrnbtter on 2013-04-17
Greetings, 
Installing Miredo seems to have fixed the problem with Firefox for me. The ipv6/ipv4 problem seems to be well documented elsewhere. I will check out the dnsmasq utility and see what I can make of it.

---

