---
title: "Trying to Set Domain to IP"
date: 2015-08-22
forum: Server Platforms
---

### Post by patrickmcknewportf on 2015-08-22
I have Ubuntu Server 15.04 and Windows 10 on my ASUS G75VW laptop. I was able to get my wireless connection setup by using DCHP, and I can use sudo and download packages. I decided to use iptables to help secure my server.  However, I can't get my site to connect my domain name.
ifconfig -a:
```
lo        Link encap:Local Loopback            inet addr:xxx.xxx.xxx.xxx  Mask:xxx.x.xxx.xxx
          inet6 addr: ::x/xxxx Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10345 (10.3 KB)  TX bytes:10345 (10.3 KB)


p3p1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:xxx.xxx.x.x  Bcast:xxx.xxx.xx.xxx  Mask:xxx.xxx.xxx.xx
          inet6 addr: xxxx::xxxx:xxxx:xxxx:xxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:725483 (725.4 KB)  TX bytes:4389 (4.3 KB)


wlan0:1   Link encap:Ethernet  HWaddr dc:xx:xx:xx:xx:xx  
          inet addr:xxxx.xxxx.xxxx.xxxx  Bcast:xxx.xxx.x.xxx  Mask:xxx.xxx.xxx.x
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```
I had to configure wlan0 with DCHP. I thought that trying to create a static connection would help solve things. The wlan0:1 comes from reading [this]("http://www.linuxdevcenter.com/cmd/cmd.csp?path=i/ifconfig") while searching on how to configure a static wireless connection.

nmap for what I believe is my public IP
```
Host is up (0.0025s latency).Not shown: 993 closed ports
PORT     STATE SERVICE
xx/xxx   open  telnet
xx/xxx   open  http
xx/xxx  open  https
xxx/xxx  open  telnets
xxxx/xxx open  tram
xxxx/xxx open  http-proxy
xxxx/xxx open  https-alt
```

 Any help will be greatly appreciated.

---

### Post by TheFu on 2015-08-23
What do you mean by "set domain to IP?"  
If you just want a domainname set, use that command and put the domainname into the /etc/domainname file.
If you want someone in the world to be able to find the machine that takes more. [http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site](http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site) explains the parts. Need lots more data about the network before we can help with details.

BTW - running telnet and telnets are red flags. Probably a really bad idea. I don't know what "tram" is. Seeing the port/protocol would help.

You've removed all the important information to the point that I can't help.

---

