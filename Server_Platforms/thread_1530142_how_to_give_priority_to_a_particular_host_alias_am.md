---
title: "how to give priority to a particular host alias among different servernames"
date: 2010-07-13
forum: Server Platforms
---

### Post by tapas_mishra on 2010-07-13
I have a server A and on A in /etc/hosts I have 

192.168.1.5 setup2.com setup3.com setup4.com 

192.168.1.5 is Server B 

and setup2.com setup3.com setup4.com exists on Server B.

My problem is if I ping from A as 

ping setup4.com 
I get a reply as 
```

PING setup2.com (192.168.1.5) 56(84) bytes of data.
64 bytes from setup2.com (192.168.1.5): icmp_seq=1 ttl=64 time=1.06 ms
64 bytes from setup2.com (192.168.1.5): icmp_seq=2 ttl=64 time=0.634 ms
64 bytes from setup2.com (192.168.1.5): icmp_seq=3 ttl=64 time=0.866 ms
^C
--- setup2.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.634/0.855/1.067/0.180 ms
    
```

Is it no way possible that in above output where I am getting 
```

PING setup2.com (192.168.1.5) 56(84) bytes of data.

```

if I ping setup4.com 
I get some thing like 

```

 PING setup4.com (192.168.1.5) 56(84) bytes of data.
 
```
and not 

```

 PING setup2.com (192.168.1.5) 56(84) bytes of data.
 
```

I do not have a DNS so all changes I am doing are in /etc/hosts only.

---

### Post by CannibalZerg on 2010-07-13
As far as we talking about TCP/IP communication, IP address is always prior to domain name, so I don't really understand what the problem is. Of course you can put each hostname in a single line in  /etc/hosts and it will solve your "ping problem".
```

192.168.1.5 setup2.com 
192.168.1.5 setup3.com
192.168.1.5 setup4.com 

```But many people warns against doing this.

---

