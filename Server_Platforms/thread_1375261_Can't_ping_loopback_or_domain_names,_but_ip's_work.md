---
title: "Can't ping loopback or domain names, but ip's work"
date: 2010-01-07
forum: Server Platforms
---

### Post by felixtheratruns on 2010-01-07
Hey I have been logging into a server remotely and trying to set up a mailing list on it. The server is the newest version of ubuntu server:
uname -a:
Linux Themis 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:48:10 UTC 2009 i686 GNU/Linux

I noticed I could not download packages with apt-get or ping domain names, and I can't even ping 127.0.0.1

apt-get:
```

joel@Themis:~$ sudo apt-get install lyx
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package lyx
joel@Themis:~$ lynx
The program 'lynx' can be found in the following packages:
* lynx-cur
* lynx-cur-wrapper
Try: sudo apt-get install <selected package>
-bash: lynx: command not found
joel@Themis:~$ sudo apt-get install lynx-cur
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package lynx-cur
joel@Themis:~$
```domain names:
```
joel@Themis:~$ ping selfseo.com
ping: unknown host selfseo.com
``````
joel@Themis:~$ ping google.com
ping: unknown host google.com
```However when I try to ping the ip's of the aforementioned domain names it works:
```
joel@Themis:~$ ping 87.230.105.175
PING 87.230.105.175 (87.230.105.175) 56(84) bytes of data.
64 bytes from 87.230.105.175: icmp_seq=1 ttl=42 time=174 ms
64 bytes from 87.230.105.175: icmp_seq=2 ttl=42 time=170 ms
64 bytes from 87.230.105.175: icmp_seq=3 ttl=42 time=169 ms
64 bytes from 87.230.105.175: icmp_seq=4 ttl=42 time=168 ms
^C
--- 87.230.105.175 ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4005ms
rtt min/avg/max/mdev = 168.840/170.650/174.020/2.041 ms
``````

joel@Themis:~$ ping 64.233.169.104
PING 64.233.169.104 (64.233.169.104) 56(84) bytes of data.
64 bytes from 64.233.169.104: icmp_seq=1 ttl=234 time=511 ms
64 bytes from 64.233.169.104: icmp_seq=2 ttl=234 time=408 ms
64 bytes from 64.233.169.104: icmp_seq=3 ttl=234 time=506 ms
64 bytes from 64.233.169.104: icmp_seq=4 ttl=234 time=480 ms
64 bytes from 64.233.169.104: icmp_seq=5 ttl=234 time=477 ms
64 bytes from 64.233.169.104: icmp_seq=6 ttl=234 time=475 ms
64 bytes from 64.233.169.104: icmp_seq=7 ttl=234 time=501 ms
64 bytes from 64.233.169.104: icmp_seq=8 ttl=234 time=482 ms
64 bytes from 64.233.169.104: icmp_seq=9 ttl=234 time=463 ms
64 bytes from 64.233.169.104: icmp_seq=10 ttl=234 time=443 ms
64 bytes from 64.233.169.104: icmp_seq=11 ttl=234 time=263 ms
64 bytes from 64.233.169.104: icmp_seq=12 ttl=234 time=342 ms
^C
--- 64.233.169.104 ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 11010ms
rtt min/avg/max/mdev = 263.315/446.272/511.909/71.406 ms
joel@Themis:~$ 
```loopback:
```

joel@Themis:~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
^C
--- 127.0.0.1 ping statistics ---
463 packets transmitted, 0 received, 100% packet loss, time 462002ms
```Any ideas on how to fix this?And do you think there is something wrong with the network card?
Thanks.

---

### Post by Iowan on 2010-01-07
Part of the symptoms point to DNS problems. What is in */etc/resolv.conf* and */etc/hosts*?

---

### Post by felixtheratruns on 2010-01-07
There is no [I]/etc/resolv.conf 
[/I]There is however a */etc/resolvconf  *and it only has one folder:
 */etc/resolvconf/update-libc.d/* which has two files:

[I]
/etc/resolvconf/update-libc.d/avahi-daemon[/I]
```
#!/bin/sh
#
# If we have an unicast .local domain, we immediately disable avahi to avoid
# conflicts with the multicast IP4LL .local domain

if [ -x /usr/lib/avahi/avahi-daemon-check-dns.sh ]; then
  exec /usr/lib/avahi/avahi-daemon-check-dns.sh
fi
```[I]

/etc/resolvconf/update-libc.d/postifx[/I]
```
#!/bin/sh -e

# make sure we're still here...
[ -x /usr/sbin/postconf ] || exit 0

cp /etc/resolv.conf $(/usr/sbin/postconf -h queue_directory)/etc/resolv.conf
/etc/init.d/postfix reload >/dev/null 2>&1 || exit 0

exit 0
```However hosts does exist:
/etc/hosts
```
127.0.0.1    localhost
127.0.1.1    Themis

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```I tried pinging 127.0.1.1, localhost, and Themis as well, but the results were the same as when I pinged127.0.0.1

---

### Post by felixtheratruns on 2010-01-08
Ok, good news!  We can now 

ping [google.com]("http://google.com/")

and we get a response.  The issue is that it is EXTREMELY slow. My friend (the owner of the server) "fixed" it just by creating resolv.conf and adding the single line:

nameserver 192.168.1.1

So he says it is using his router as the DNS nameserver.  His router can't really handle this.  He says he needs to find a better DNS (or several) to point it at. His ISP is Bellsouth so he's guessing that we need to point it to one of theirs? He says he doesn't know the IPs for their servers though.  In the meantime he's going to remove the line in resolv.conf because it makes the connection to the server extremely slow and says it probably is slowing down the Internet for his whole family right now :) 
Any idea's on how we can get this working normally? Thanks.

---

### Post by SlugSlug on 2010-01-08
you could use opendns's IP 
nameserver 208.67.222.222
nameserver 208.67.220.220

---

### Post by felixtheratruns on 2010-01-08
Ok so he looked at the resolv.conf on his other server and put it into the server I am working on:

domain [launchmodem.com]("http://launchmodem.com/")
search [launchmodem.com]("http://launchmodem.com/")
nameserver 205.152.150.23
nameserver 205.152.132.23

He said when he did this it starting working much faster. Ping responses sped up and even boot up time went from 5 minutes to under 1.

Now we can ping domain names. However we can NOT ping loopback and we still can't download packages.

I also tried pinging the server's own ip that is internal to the network and noticed that that didn't work either:
joel@Themis:~$ ping 192.168.1.110
PING 192.168.1.110 (192.168.1.110) 56(84) bytes of data.
^C
--- 192.168.1.110 ping statistics ---
37 packets transmitted, 0 received, 100% packet loss, time 36005ms

---

### Post by Iowan on 2010-01-09
I've seen a couple of different versions of what should be there, but what is in */etc/nsswitch.conf*?

---

### Post by felixtheratruns on 2010-01-09
Ok it looks like we've fixed it. What I think the problem was is that the cache of apt-get was outdated or corrupt, when I did "apt-get update" it solved this, and now I can download packages normally. 

I'm not going to mark this thread as resolved yet because I'm still curious as why I can't ping loopback. It may be a setting in iptables but im not sure, because my friend said he was able to ping the server from within its own network, I guess this isn't too big a deal, BUT I STILL WANT TO KNOW! lol:

```
root@Themis:/home/joel# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             192.168.122.0/24    state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.122.0/24     anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
```@Iowan here is the /etc/nsswitch.conf:

```
# /etc/nsswitch.conf                                                                                                 
#                                                                                                                    
# Example configuration of GNU Name Service Switch functionality.                                                    
# If you have the `glibc-doc-reference' and `info' packages installed, try:                                          
# `info libc "Name Service Switch"' for information about this file.                                                 

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```So this is really my only remaining question: why can't I ping loopback? Thanks.

---

### Post by Iowan on 2010-01-09
Glad you're getting closer... in spite of my "help" ;)
My */etc/nsswitch.conf* is identical... but pings work.

---

### Post by Cisco9 on 2010-01-18
Is "lo" interface listed when you enter "ifconfig"?

If not, then try to manually start the loopback interface, "lo" by entering the following command:
sudo /sbin/ifconfig lo 127.0.0.1 up

I got this to work for myself, but don't know how to make it start automatically on startup.

---

### Post by SlugSlug on 2010-01-18
> **Cisco9 said:**
> Is "lo" interface listed when you enter "ifconfig"?

If not, then try to manually start the loopback interface, "lo" by entering the following command:
sudo /sbin/ifconfig lo 127.0.0.1 up

I got this to work for myself, but don't know how to make it start automatically on startup.


that is done in /etc/network/interfaces
it should contain

auto lo
iface lo inet loopback

---

### Post by Cisco9 on 2010-02-05
I checked the /etc/interfaces/network file. It contains the entries that you suggest and nothing more. ???

auto lo
iface lo inet loopback

--Cisco

---

### Post by bab1 on 2010-02-05
```
Chain **[COLOR="DarkRed"]FORWARD[/COLOR]** (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             192.168.122.0/24    state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.122.0/24     anywhere            
ACCEPT     all  --  anywhere             anywhere            
[COLOR="Red"]REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable [/COLOR]

```

I would suspect this.

---

### Post by felixtheratruns on 2010-02-07
Thanks so much Cisco; that worked. Sorry about the delay of responding, was moving.
Here's it working! I'm so happy! :)

```
joel@Themis:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d3:c3:50:5d
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fec3:505d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100060 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13977027 (13.9 MB)  TX bytes:914399 (914.3 KB)
          Interrupt:20 Base address:0xe800

virbr0    Link encap:Ethernet  HWaddr 82:ce:c3:95:6e:82
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::80ce:c3ff:fe95:6e82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:614521 (614.5 KB)

joel@Themis:~$ ifconfig | grep lo
joel@Themis:~$ sudo /sbin/ifconfig lo 127.0.0.1 up
[sudo] password for joel:
joel@Themis:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d3:c3:50:5d
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fec3:505d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13990698 (13.9 MB)  TX bytes:925525 (925.5 KB)
          Interrupt:20 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0    Link encap:Ethernet  HWaddr 82:ce:c3:95:6e:82
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::80ce:c3ff:fe95:6e82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:614521 (614.5 KB)

joel@Themis:~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.095 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.066 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.073 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.071 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.075 ms
64 bytes from 127.0.0.1: icmp_seq=6 ttl=64 time=0.051 ms
64 bytes from 127.0.0.1: icmp_seq=7 ttl=64 time=0.075 ms
64 bytes from 127.0.0.1: icmp_seq=8 ttl=64 time=0.056 ms
64 bytes from 127.0.0.1: icmp_seq=9 ttl=64 time=0.084 ms
64 bytes from 127.0.0.1: icmp_seq=10 ttl=64 time=0.071 ms
64 bytes from 127.0.0.1: icmp_seq=11 ttl=64 time=0.074 ms
^C
--- 127.0.0.1 ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 9992ms
rtt min/avg/max/mdev = 0.051/0.071/0.095/0.016 ms
joel@Themis:~$
```Oh and here's the iptables now:

```
joel@Themis:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             192.168.122.0/24    state RELATED,ESTABLISHED
ACCEPT     all  --  192.168.122.0/24     anywhere
ACCEPT     all  --  anywhere             anywhere
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
joel@Themis:~$
```

---

### Post by dazman19 on 2012-05-06
add to /etc/network/interfaces

```
auto lo
iface lo inet loopback
```

Should do the trick for boot up.

---

