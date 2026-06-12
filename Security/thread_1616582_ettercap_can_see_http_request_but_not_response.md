---
title: "ettercap can see http request but not response"
date: 2010-11-08
forum: Security
---

### Post by bashologist on 2010-11-08
ettercap can see http request but not response

I'm trying to see regular http responses from my wireless ipad (victim) from my wired pc (attacker). Everything's working great but I can only see the http requests not the responses.

I've done much reading and googling and tried registering in more relevant forums but some forums were shutdown, so I've come here.

```

# setup ip forwarding
echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward

# use ettercap to do the mitm using only mitm
sudo ettercap --iface eth0 --text --plugin autoadd --only-mitm --mitm arp:remote /192.168.0.1/ /192.168.0.155/

# use wireshark for the examination of traffic
wireshark
```

I've setup the config file how everyone says to with iptables etc.
/etc/etter.conf

Version:
ettercap NG-0.7.3
Wireshark 1.2.11
Ubuntu 10.04 Lucid Lynx 

192.168.0.1     my router
192.168.0.155   my ipad (wireless victim)
74.125.95.102   google
my attacking pc is using a wired connection using eth0 interface

```

No.     Time        Source                Destination           Protocol Info
     50 21.022638   192.168.0.155         192.168.0.1           HTTP     GET / HTTP/1.1 
     51 21.022651   192.168.0.155         192.168.0.1           HTTP     [TCP Out-Of-Order] GET / HTTP/1.1 
     82 21.099417   192.168.0.155         192.168.0.1           HTTP     GET /style.css HTTP/1.1 
     83 21.099437   192.168.0.155         192.168.0.1           HTTP     [TCP Out-Of-Order] GET /style.css HTTP/1.1 
    125 21.126066   192.168.0.155         192.168.0.1           HTTP     GET /substyle_DIR-655.css HTTP/1.1 
    126 21.126079   192.168.0.155         192.168.0.1           HTTP     [TCP Out-Of-Order] GET /substyle_DIR-655.css HTTP/1.1 
    131 21.128810   192.168.0.155         192.168.0.1           HTTP     GET /utils.js HTTP/1.1 
    132 21.128826   192.168.0.155         192.168.0.1           HTTP     [TCP Out-Of-Order] GET /utils.js HTTP/1.1 
    139 21.131472   192.168.0.155         192.168.0.1           HTTP     GET /ajax.js HTTP/1.1 
    140 21.131488   192.168.0.155         192.168.0.1           HTTP     [TCP Out-Of-Order] GET /ajax.js HTTP/1.1 
    143 21.133692   192.168.0.155         192.168.0.1           HTTP     GET /md5.js HTTP/1.1 
    144 21.133704   192.168.0.155         192.168.0.1           HTTP     [TCP Out-Of-Order] GET /md5.js HTTP/1.1 
    215 21.229304   192.168.0.155         192.168.0.1           HTTP     GET /Images/img_bg_masthead_red.gif HTTP/1.1 
    216 21.229321   192.168.0.155         192.168.0.1           HTTP     [TCP Out-Of-Order] GET /Images/img_bg_masthead_red.gif HTTP/1.1 
    217 21.231108   192.168.0.155         192.168.0.1           HTTP     GET /Images/img_masthead_red.gif HTTP/1.1 
    218 21.231124   192.168.0.155         192.168.0.1           HTTP     [TCP Out-Of-Order] GET /Images/img_masthead_red.gif HTTP/1.1 
    223 21.234134   192.168.0.155         192.168.0.1           HTTP     GET /Images/img_wireless_bottom.gif HTTP/1.1 
    224 21.234141   192.168.0.155         192.168.0.1           HTTP     [TCP Out-Of-Order] GET /Images/img_wireless_bottom.gif HTTP/1.1 
    350 36.826795   192.168.0.155         74.125.95.102         HTTP     GET /complete/search?json=t&nolabels=t&client=iphonesafari&q=t HTTP/1.1 
    351 36.826810   192.168.0.155         74.125.95.102         HTTP     [TCP Out-Of-Order] GET /complete/search?json=t&nolabels=t&client=iphonesafari&q=t HTTP/1.1 
    368 37.086760   192.168.0.155         74.125.95.102         HTTP     GET /complete/search?json=t&nolabels=t&client=iphonesafari&q=te HTTP/1.1 
    369 37.086775   192.168.0.155         74.125.95.102         HTTP     [TCP Out-Of-Order] GET /complete/search?json=t&nolabels=t&client=iphonesafari&q=te HTTP/1.1 
    373 37.354390   192.168.0.155         74.125.95.102         HTTP     GET /complete/search?json=t&nolabels=t&client=iphonesafari&q=tes HTTP/1.1 
    374 37.354406   192.168.0.155         74.125.95.102         HTTP     [TCP Out-Of-Order] GET /complete/search?json=t&nolabels=t&client=iphonesafari&q=tes HTTP/1.1 
    386 37.613574   192.168.0.155         74.125.95.102         HTTP     GET /complete/search?json=t&nolabels=t&client=iphonesafari&q=test HTTP/1.1 
    387 37.613589   192.168.0.155         74.125.95.102         HTTP     [TCP Out-Of-Order] GET /complete/search?json=t&nolabels=t&client=iphonesafari&q=test HTTP/1.1 

```

I don't see any responses just the http requests. Am I wrong to be expecting there to be http responses?

Here's the full output of the ettercap command, although there were not problems/errors afaik.
```

sudo ettercap --iface eth0 --text --plugin autoadd --only-mitm --mitm arp:remote /192.168.0.1/ /192.168.0.155/

ettercap NG-0.7.3 copyright 2001-2004 ALoR & NaGA

Listening on eth0... (Ethernet)

  eth0 ->	xx:xx:xx:xx:xx:xx     192.168.0.150     255.255.255.0

Privileges dropped to UID 0 GID 0...

  28 plugins
  39 protocol dissectors
  53 ports monitored
7587 mac vendor fingerprint
1698 tcp OS fingerprint
2183 known services

Scanning for merged targets (2 hosts)...

* |==================================================>| 100.00 %

2 hosts added to the hosts list...

ARP poisoning victims:

 GROUP 1 : 192.168.0.1 xx:xx:xx:xx:xx:xx

 GROUP 2 : 192.168.0.155 xx:xx:xx:xx:xx:xx
Activated the mitm attack only... (press 'q' to exit)
Exiting...

ARP poisoner deactivated.
RE-ARPing the victims...

Terminating ettercap...

```

---

### Post by cariboo on 2010-11-08
Is your ipad running a http server? If it isn't how can it respond?

---

### Post by bashologist on 2010-11-08
Don't have http server on ipad.

What I'm looking to get both the request and the response to and from google. Like it should look something like this:
```
59	10.160642	192.168.0.150	74.125.95.99	HTTP	GET /gen_204 HTTP/1.1 
60	10.233618	74.125.95.99	192.168.0.150	HTTP	HTTP/1.1 204 No Content

```

But when I do the arp poisoning to sniff the traffic I'm only getting the first line, like this.
```
59	10.160642	192.168.0.150	74.125.95.99	HTTP	GET /gen_204 HTTP/1.1

```

---

