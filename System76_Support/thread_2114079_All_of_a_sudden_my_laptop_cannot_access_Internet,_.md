---
title: "All of a sudden my laptop cannot access Internet, connects to router just fine."
date: 2013-02-09
forum: System76 Support
---

### Post by cs35 on 2013-02-09
Machine could access the Internet for all these days. Even up to the point this happened I was able to access the Internet. I did not boot into this, happened in the middle of work. The day it happened, running rmmod/modprobe on the wireless driver did not fix the problem. Subsiquent reboots too have not helped. Connects to the wireless network, I can ping the router and even access the admin page. Other devices (another laptop and smart phone) can access the Internet.

**Couple of interesting things:**
[LIST=1]
[*]At the time this happened, I had firefox (Work Gmail) and Chrome (Personal Gmail) running. When I opened new tabs and had no pages returned is when I knew something is up. In both browsers, gmail continued to work (fetch new mail, search mail etc), but not pages in new tabs!? After restarting the browsers, even Gmail would not work.
[*]I rebooted from a Live USB and internet access works!? 
[/LIST]

**Machine Details:**
Lemur UltraThin (lemu2) bought in June 2011
Processor Core i3-330UM Processor  ( 32nm, 3MB L3 Cache, 1.20GHz, 18 Watt )
Hard Drive 80 GB Intel X25-M Solid State Drive
RealTek Wireless
System76 Driver Version: 3.2.3
Ubuntu Version: 12.10

Attached are some log files that may come in handy.

**Some more history:**
I had this problem once before. Last time was about 3 weeks back. I was running 12.04 then. This is when I figured out the problem does not exist if I boot from a Live USB.

Any suggestions/help will be much appreciated.


** EDIT - SOLVED **
The ssl vpn client I was using was the culprit. 99/100 times it was restoring resolv.conf. But the one time it did not, I lost access, due to wrong nameserver. Reboot of machine or restarting network did not restore resolv.conf.

The solution (Thanks to sanderj and jdthood) is to restore resolv.conf. Perhaps the best way to do that is run 'sudo dpkg-reconfigure resolvconf'

---

### Post by sanderj on 2013-02-09
When your router is reachable, but Internet is not (for this machine), what's the output of:

```
ip route show

mtr -rc2 8.8.8.8

time host www.google.com
```

Post the output here

---

### Post by cs35 on 2013-02-09
Sanderj, here are the outputs:

```

$> ip route show
default via 10.2.0.1 dev wlan0  proto static 
10.2.0.0/24 dev wlan0  proto kernel  scope link  src 10.2.0.102  metric 9 
169.254.0.0/16 dev wlan0  scope link  metric 1000 

$> mtr -rc2 8.8.8.8
HOST: gestalt                     Loss%   Snt   Last   Avg  Best  Wrst StDev

$> time host www.google.com
;; connection timed out; no servers could be reached

real	0m12.015s
user	0m0.008s
sys	0m0.004s

```

---

### Post by sanderj on 2013-02-09
Your router/modem/NAT is on 10.2.0.1 ?

Can you ping it?

Reason: your default route is set (good), but your mtr does not show a first hop (strange).

Assuming your gateway 10.2.0.1 is also a DNS, can you do this:

```
host www.google.com 10.2.0.1

```
and post the output here?

Have you installed a firewall on your PC? Check with

```
sudo iptables --list
```

---

### Post by cs35 on 2013-02-09
sanderj, I really appreciate your effort.

> Your router/modem/NAT is on 10.2.0.1 ? Can you ping it?

Yes, Router is 10.2.0.1

```
$> ping 10.2.0.1
PING 10.2.0.1 (10.2.0.1) 56(84) bytes of data.
64 bytes from 10.2.0.1: icmp_req=1 ttl=64 time=1.42 ms
64 bytes from 10.2.0.1: icmp_req=2 ttl=64 time=1.42 ms
64 bytes from 10.2.0.1: icmp_req=3 ttl=64 time=1.29 ms
64 bytes from 10.2.0.1: icmp_req=4 ttl=64 time=1.19 ms
^C
--- 10.2.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 1.192/1.332/1.421/0.099 ms

```

```
$> host www.google.com 10.2.0.1
Using domain server:
Name: 10.2.0.1
Address: 10.2.0.1#53
Aliases: 

www.google.com has address 74.125.236.52
www.google.com has address 74.125.236.50
www.google.com has address 74.125.236.49
www.google.com has address 74.125.236.48
www.google.com has address 74.125.236.51
www.google.com has IPv6 address 2404:6800:4007:800::1014

```
:confused:



> Have you installed a firewall on your PC?

No, I do not have a firewall.

```
$> sudo iptables --list
[sudo] password for chaitresh: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

---

### Post by sanderj on 2013-02-09
I'm still confused about your MTR output. Can you try this one:

```
mtr -nrc4 8.8.8.8
```

and post the output here?

---

### Post by cs35 on 2013-02-09
Here you go:

```
$> mtr -nrc4 8.8.8.8
HOST: gestalt                     Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 10.2.0.1                   0.0%     4    1.1   2.6   1.1   5.1   1.8
  2.|-- 123.201.253.193            0.0%     4   19.9  16.9  15.6  19.9   2.0
  3.|-- 203.109.116.93             0.0%     4   18.1  21.6  18.1  29.8   5.5
  4.|-- 203.187.252.65             0.0%     4   21.7  18.2  10.8  23.6   5.7
  5.|-- 125.16.141.41              0.0%     4   18.3  30.0  18.3  47.8  13.7
  6.|-- 182.79.247.30              0.0%     4   28.3  28.0  20.7  36.1   6.4
  7.|-- 72.14.216.229              0.0%     4   36.7  27.6  22.3  36.7   6.3
  8.|-- 66.249.94.170              0.0%     4   40.3  34.0  25.7  41.8   8.2
  9.|-- 209.85.241.21              0.0%     4   36.6  34.0  24.4  38.8   6.5
 10.|-- 8.8.8.8                    0.0%     4   25.1  26.1  20.3  37.0   7.6
$> 
```

---

### Post by sanderj on 2013-02-09
OK, looks very good. And what's the ouput of:

```
mtr -rc4 8.8.8.8
```

(note the missing 'n' option)

And then 

```
mtr -rc4 www.google.com
```

---

### Post by cs35 on 2013-02-10
Those take a long time to complete. On my other laptop (where there is no problem) it completes in about 45 seconds.

```
$> date; mtr -rc4 8.8.8.8; date
Sun Feb 10 11:23:12 IST 2013
HOST: gestalt                     Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 10.2.0.1                   0.0%     4    1.1  16.0   1.1  58.7  28.5
  2.|-- 123.201.253.193            0.0%     4   15.3  13.9   9.6  17.7   3.5
  3.|-- 203.109.116.93             0.0%     4   12.2  17.3  10.5  33.9  11.1
  4.|-- 203.187.252.65             0.0%     4   11.0  13.0  10.9  16.1   2.6
  5.|-- 125.16.141.41              0.0%     4    9.1  11.0   9.0  14.7   2.7
  6.|-- 182.79.247.30              0.0%     4   53.0  30.8  14.8  53.0  18.1
  7.|-- 72.14.216.229              0.0%     4   45.6  35.3  19.0  47.5  13.7
  8.|-- 66.249.94.170              0.0%     4   28.7  24.2  17.0  28.7   5.1
  9.|-- 209.85.241.21              0.0%     4   15.2  25.4  15.2  37.0  10.8
 10.|-- 8.8.8.8                    0.0%     4   14.5  22.2  14.5  32.9   8.6
Sun Feb 10 11:27:26 IST 2013
```
```
$> date; mtr -rc4 www.google.com; date
Sun Feb 10 11:27:41 IST 2013
Failed to resolve host: Name or service not known
Sun Feb 10 11:29:01 IST 2013
```

---

### Post by sanderj on 2013-02-10
OK, probable root cause: your name resolution (DNS) is not working.

What is the output of:

```

cat /etc/resolv.conf
lsb_release -a

```

---

### Post by cs35 on 2013-02-10
You are right! 10.4.4.20 and 10.4.4.10 are the nameserver at the company I work for - where I VPN into. Those were not cleaned up by the VPN software I guess.

How do I resolve it? resolv.conf is not normally edited manually correct?

```
$> cat /etc/resolv.conf
search CompanyIWork.com
nameserver 10.4.4.20
nameserver 10.4.4.10

```
```
$> lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal
```

---

### Post by sanderj on 2013-02-10
Reboot?

Or reload networking?

Or just copy the info below over your /etc/resolv.conf

```
sander@R540:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search home
sander@R540:~$
```

---

### Post by cs35 on 2013-02-10
Reboot never fixed this issue, which was the problem. Restarting networking with:

sudo service networking stop
sudo service networking start

did not fix it either.

Editing resolv.conf and replace everything with 'nameserver 127.0.1.1' did the trick.

Thank you Sanderj for helping me through this!

I don't know how to mark this as solved. Perhaps I do not have enough privileges in the forum.

---

### Post by sanderj on 2013-02-10
Mark it SOLVED under Thread Tools ... :)

Oh, and please report a bug to the VPN supplier ...

---

### Post by jdthood on 2013-02-10
> **cs35 said:**
> Editing resolv.conf and replace everything with 'nameserver 127.0.1.1' did the trick.

The more correct solution is to restore the symbolic link /etc/resolv.conf -> ../run/resolvconf/resolv.conf which was deleted by your VPN client. One way to accomplish this is to run "sudo dpkg-reconfigure resolvconf".

You will probably have to do this every time after you run the VPN client. What VPN client are you using, exactly?

If the VPN client uses shell script to futz with /etc/resolv.conf then perhaps you can edit the script so that it integrates with the resolvconf framework instead of manipulating /etc/resolv.conf.

---

### Post by cs35 on 2013-02-10
> **jdthood said:**
> The more correct solution is to restore the symbolic link /etc/resolv.conf -> ../run/resolvconf/resolv.conf which was deleted by your VPN client. One way to accomplish this is to run "sudo dpkg-reconfigure resolvconf".

You will probably have to do this every time after you run the VPN client. What VPN client are you using, exactly?

If the VPN client uses shell script to futz with /etc/resolv.conf then perhaps you can edit the script so that it integrates with the resolvconf framework instead of manipulating /etc/resolv.conf.

I use 'SSL VPN' by F5 Networks. This software restores resolv.conf 99/100 times. Hence I did not suspect it.

I like your work around of running "sudo dpkg-reconfigure resolvconf" whenever the vpn software does fail for whatever reason. Thanks!

---

### Post by lolwtfhax on 2013-02-15
You can also add your nameservers to /etc/resolvconf/resolv.conf.d/head which will overwrite /etc/resolv.conf whenever the resolvconf daemon is reloaded.

---

### Post by jdthood on 2013-02-16
> **lolwtfhax said:**
> You can also add your nameservers to /etc/resolvconf/resolv.conf.d/head which will overwrite /etc/resolv.conf whenever the resolvconf daemon is reloaded.

Resolvconf simply prepends the contents of /etc/resolvconf/resolv.conf.d/head to /run/resolvconf/resolv.conf so if the problem is that the symbolic link /etc/resolv.conf has been deleted, futzing with /etc/resolvconf/resolv.conf.d/head won't help.

Under no normal circumstances is it best to put "nameserver" lines into any file in /etc/resolvconf/resolv.conf.d/. Nameserver addresses belong either on "dns-nameservers" lines in /etc/network/interfaces or in the "Additional DNS servers" field in the NetworkManager configuration window for a particular connection, depending on whether you are using ifup or NetworkManager to configure interfaces. Additional nameserver addresses are provided to resolvconf by locally running nameservers and by DHCP clients.

---

