---
title: "apt-proxy for unrouted subnet"
date: 2008-04-26
forum: Server Platforms
---

### Post by hessml on 2008-04-26
I'm trying to get apt-proxy setup. This is where I'm at: 

- 8.04 Server AMD 64 
- Server on 2 networks: 1 public, 1 private; the private one is not routed
- I modified /etc/apt-proxy/apt-proxy-v2.conf as follows: 
* uncommented the address line and set to private subnet address = 10.0.2.254 
* Change [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) to [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) 
- I edited /etc/apt/sources.list and replaced all the server addresses with "10.0.2.254:9999" 
- I start the server with sudo /etc/init.d/apt-proxy restart 
- It starts to do some stuff and then stops: 

Get:2 [http://10.0.2.254](http://10.0.2.254) hardy-updates Release.gpg [191B] 
Ign [http://10.0.2.254](http://10.0.2.254) hardy-updates/main Translation-en_US 
Ign [http://10.0.2.254](http://10.0.2.254) hardy-updates/restricted Translation-en_US 
Get:3 [http://10.0.2.254](http://10.0.2.254) hardy-security Release.gpg [191B] 
Ign [http://10.0.2.254](http://10.0.2.254) hardy-security/main Translation-en_US 
Ign [http://10.0.2.254](http://10.0.2.254) hardy-security/restricted Translation-en_US 
Ign [http://10.0.2.254](http://10.0.2.254) hardy-security/universe Translation-en_US 
Ign [http://10.0.2.254](http://10.0.2.254) hardy-security/multiverse Translation-en_US 
Ign [http://10.0.2.254](http://10.0.2.254) hardy Release 
Ign [http://10.0.2.254](http://10.0.2.254) hardy-updates Release 
Ign [http://10.0.2.254](http://10.0.2.254) hardy-security Release 
Ign [http://10.0.2.254](http://10.0.2.254) hardy/main Packages 
Ign [http://10.0.2.254](http://10.0.2.254) hardy/restricted Packages 
97% [Waiting for headers] 

Doing a netstat -nta 
Active Internet connections (servers and established) 
Proto Recv-Q Send-Q Local Address Foreign Address State 
tcp 0 0 10.0.2.254:9999 0.0.0.0:* LISTEN 
tcp 0 0 10.0.2.254:46769 10.0.2.254:9999 ESTABLISHED 
tcp 0 0 10.0.2.254:9999 10.0.2.254:46769 ESTABLISHED 
tcp6 0 0 :::22 :::* LISTEN 
tcp6 0 0 xx.xx.xx.67:22 xx.xx.xx.69:39835 ESTABLISHED 
tcp6 0 0 xx.xx.xx.67:22 xx.xx.xx.69:40624 ESTABLISHED 
tcp6 0 0 xx.xx.xx.67:22 xx.xx.xx.69:40672 ESTABLISHED 

There doesn't appear to be any outbound connections trying to download anything. 

Tailing the log gives this: 

2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [debug] Header: Host: 10.0.2.254:9999 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [debug] Header: Connection: keep-alive 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [debug] Header: User-Agent: Ubuntu APT-HTTP/1.3 (0.7.9ubuntu16) 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [debug] Headers: Host: 10.0.2.254:9999, Connection: keep-alive, User-Agent: Ubuntu APT-HTTP/1.3 (0.7.9ubuntu16)
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [HttpRequestClient] Processing request for: /ubuntu/dists/hardy/main/source/Sources.bz2 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [HttpRequestClient] Request: GET /ubuntu/dists/hardy/main/source/Sources.bz2 backend=ubuntu uri=/ubuntu/dists/hardy/main/source/Sources.bz2 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [HttpRequestClient] backend: ubuntu [<apt_proxy.apt_proxy.BackendServer instance at 0xfb9ef0>] 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [debug] New Cache entry: dists/hardy/main/source/Sources.bz2 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [CacheEntry] Add request: <GET /ubuntu/dists/hardy/main/source/Sources.bz2 HTTP/1.1> total clients: 1 state:New 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/hardy/main/source/Sources.bz2 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [CacheEntry] start download:dists/hardy/main/source/Sources.bz2 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [DownloadQueue] queue file ubuntu/dists/hardy/main/source/Sources.bz2 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] [Channel] Client connection closed 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] [HttpRequestClient] connectionLost 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] Top 10: 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 253 WeakKeyDictionary 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 35 Ephemeral 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 28 Logger 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 24 Protocol 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 21 HttpRequestClient 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 19 FileType 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 17 CacheEntry 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 16 _SocketCloser 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 14 Resource 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 13 HttpFetcher 
2008/04/25 16:05 -0700 [-] [CacheEntry] Last request removed for /var/cache/apt-proxy/ubuntu/dists/hardy/main/source/Sources.bz2 
2008/04/25 16:05 -0700 [-] [Backend] entry_done: dists/hardy/main/source/Sources.bz2 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [HttpRequestClient] New Request, queued=0 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [debug] Header: Host: 10.0.2.254:9999 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [debug] Header: Connection: keep-alive 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [debug] Header: User-Agent: Ubuntu APT-HTTP/1.3 (0.7.9ubuntu16) 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [debug] Headers: Host: 10.0.2.254:9999, Connection: keep-alive, User-Agent: Ubuntu APT-HTTP/1.3 (0.7.9ubuntu16)
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [HttpRequestClient] Processing request for: /ubuntu/dists/hardy/restricted/source/Sources.bz2 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [HttpRequestClient] Request: GET /ubuntu/dists/hardy/restricted/source/Sources.bz2 backend=ubuntu uri=/ubuntu/dists/hardy/restricted/source/Sources.bz2 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [HttpRequestClient] backend: ubuntu [<apt_proxy.apt_proxy.BackendServer instance at 0xfb9ef0>] 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [debug] New Cache entry: dists/hardy/restricted/source/Sources.bz2 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [CacheEntry] Add request: <GET /ubuntu/dists/hardy/restricted/source/Sources.bz2 HTTP/1.1> total clients: 1 state:New 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/hardy/restricted/source/Sources.bz2 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [CacheEntry] start download:dists/hardy/restricted/source/Sources.bz2 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [DownloadQueue] queue file ubuntu/dists/hardy/restricted/source/Sources.bz2 

From the log it appears that it is trying to using the listening address to connect to the outside world which isn't going to work because it is unrouted subnet. Any idea on how I can get around this? Or am I completely off base and is it something else?

---

### Post by bluefrog on 2008-04-26
haven't used apt-proxy since I started using apt-cacher. give it a go, might be easier.

files to edit
/etc/default/apt-cacher    (autostart=1)
/etc/apt-cacher/apt-cacher.conf

James Dupin

---

### Post by koenn on 2008-04-26
> **hessml said:**
> 
From the log it appears that it is trying to using the listening address to connect to the outside world which isn't going to work because it is unrouted subnet. Any idea on how I can get around this? Or am I completely off base and is it something else?

Can't really tell from your logs what the problem is, but assuming your diagnosis is correct : 
- can the server connect to the internet ? It needs internet access to get to the apt-proxy back-ends. 
- if not, you can probably fix this by setting the default route of this server to its WAN interface / IP address.

---

### Post by hessml on 2008-04-26
Default sounds promising. I know nothing about this; how does it work?

Looking at the apt-proxy code it is creating a socket which binds to the default address which turns out to be be the private address.

Will a socket that is bound to a private address on the private interface be able to route to the public interface?

So the source address will be 10.0.2.254 and it will be trying to get out on the public interface which is xx.xx.xx.67 and connect to some server....

I'm not sure this is going to work because the packet is going to have a return address which is a private address which of course is not going to route on return path.

Or is there some magic happening behind the scenes? Or am I over thinking this and I should just try it out and see what happens?

Maybe I should just switch to Squid. It has options on which address to listen for request on as well as well as which address to bind to for outbound connections.

---

### Post by koenn on 2008-04-27
You haven't answered my question so I can't tell you much new.
can the server that runs apt-proxy connect to the internet ? 
do the following to check :```
ping google.com
ping 208.67.222.222
```

also do the following to see your routing table
```
route
```


It's supposed to work as follows : 
- apt-proxy listens on lan.inteface.ip.address for requests from you LAN. 
- if apr-proxy needs to get packages from a back-end server, the TCP/IP stack will be given the ip address of the back-end server. Since that address is not on your LAN, the kernel will invoke its routing procedure and decide what route to take. I assume that letting this default to "internet" will do the trick. This is an other socket than the listening socket towards your LAN.

The strange thing is that this doesn't happen automatically, but that can have something to do with the way your internet connection is configured, eg that it's configured with dhcp from your isp and without default route because your isp doesn't expect multihomed hosts. 
Still, it's weird, so explain a bit about how you connect to the internet and post the output I asked for so we can have a look at what's happening.

---

### Post by hessml on 2008-04-27
Yes it can access the internet. The first netstat dump shows xx.xx.xx.67 which are connections on its public IP (I normally don't publish my IP addresses on public forums hence the obfuscation), the connections are ssh connections. 

Everything is configured statically - no DHCP. 

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.248 U     0      0        0 eth1
10.0.2.0        *               255.255.255.0   U     0      0        0 eth0
default         adsl-xx-xx-xx- 0.0.0.0         UG    100    0        0 eth1

$ cat /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
        address xx.xx.xx.67
        netmask 255.255.255.248
        network xx.xx.xx.64
        broadcast xx.xx.xx.71
        gateway xx.xx.xx.70

# The private network interface
auto eth0
iface eth0 inet static
    address 10.0.2.254
    netmask 255.255.255.0

---

### Post by hessml on 2008-04-27
So I did a test where I forced ping to use each of the different interfaces. When ping is bound to the private address it can't ping google which of course makes sense. Apt-proxy is taking a default source address to bind to which I'm guessing turns out to be the private address which of course doesn't route.

I'm guessing this is why Squid lets you specify a listening address and an outbound address.

$ ping -I xx.xx.xx.67 google.com
PING google.com (72.14.207.99) from xx.xx.xx.67 : 56(84) bytes of data.
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=1 ttl=235 time=78.6 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=2 ttl=235 time=75.9 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=3 ttl=235 time=76.0 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=4 ttl=235 time=75.8 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 75.854/76.637/78.682/1.229 ms


$ ping -I 10.0.2.254 google.com
PING google.com (64.233.167.99) from 10.0.2.254 : 56(84) bytes of data.

--- google.com ping statistics ---
21 packets transmitted, 0 received, 100% packet loss, time 20012ms

---

### Post by koenn on 2008-04-27
>  * uncommented the address line and set to private subnet address = 10.0.2.254
If you comment this line again, probabmy apt-proxy will listen on all available interfaces. You could try to see if that works. If it does, at least you've pin-pointed the problem.

It may not be an acceptable solution for you to have apt-proxy also listen on your WAN connection.
The computer I used to run apt-proxy on has died so I can't check if there are any options that would be of use to specicy separate interfaces.
A workaround could be to use iptables to block http incoming on the poublic interface.

---

### Post by hessml on 2008-04-27
This sounds promising. I'll try this out.

---

