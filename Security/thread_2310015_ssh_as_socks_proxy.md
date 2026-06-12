---
title: "ssh as socks proxy"
date: 2016-01-15
forum: Security
---

### Post by marchello_lippi2 on 2016-01-15
Hi all, 

I experience difficulty using ssh as socks proxy. 

Some details... 
I connect to remote host using yakuake 

> ssh [EMAIL="user@remote.host.domain"]user@remote.host.domain[/EMAIL] -D5902

also I use 127.0.0.1:5902 as my socks v5 proxy in browser. 

Everything works fine, but after some time I begin to receive errors in yakuake: 
> channel 57: open failed: connect failed: Connection refusedchannel 12: open failed: connect failed: Connection refused
channel 13: open failed: connect failed: Connection refused
channel 5: open failed: connect failed: Connection refused
channel 13: open failed: connect failed: Connection refused
channel 5: open failed: connect failed: Connection refused
channel 10: open failed: connect failed: Connection refused
channel 6: open failed: connect failed: Connection refused
channel 5: open failed: connect failed: Connection refused
channel 5: open failed: connect failed: Connection refused
channel 9: open failed: connect failed: Connection refused
channel 22: open failed: connect failed: Connection refused
channel 5: open failed: connect failed: Connection refused
channel 9: open failed: connect failed: Connection refused
channel 15: open failed: connect failed: Connection refused
channel 16: open failed: connect failed: Connection refused
channel 9: open failed: connect failed: Connection refused
channel 29: open failed: connect failed: Connection refused
channel 16: open failed: connect failed: Connection refused
In the same time, I experience slow work in browser. 

Then I break session in yakuake and start new one, it helps for some time, then the situation repeats again. 

Remote host: Ubuntu 14.04.3 LTS (GNU/Linux 2.6.32-042stab111.12 x86_64)

Local host: 
$ lsb_release -aNo LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty

Any help on how to solve it without breaking session?

---

### Post by marchello_lippi2 on 2016-02-12
Solved partially by adding '-C' for compressing data. 
Solved fully by moving to other VPS provider with better service quality.

---

