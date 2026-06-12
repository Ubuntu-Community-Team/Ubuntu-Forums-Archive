---
title: "Unable to browse squirrelmail on domain"
date: 2012-01-27
forum: Server Platforms
---

### Post by satimis on 2012-01-27
Hi folks,

Ubuntu 1010 server 64bit

Oracle VirtualBox

Squirrelmail is running on a VM (guest).  It can be contacted on the host by running;

[http://ip/webmail](http://ip/webmail)

But unable to contact it running:

[http://server1.domain.com/webmail](http://server1.domain.com/webmail)

Please help.  TIA

B.R.
satimis

---

### Post by stefangr1 on 2012-01-27
Does server1.domain.com resolve correctly?

---

### Post by satimis on 2012-01-27
> **stefangr1 said:**
> Does server1.domain.com resolve correctly?

Hi,

On host terminal:

# nslookup server1.domain.com```

;; connection timed out; no servers could be reached

```

# ping server1.domain.com```

ping: unknown host server1.domain.com

```

# ping 192.168.0.xxx (server IP)```

PING 192.168.0.xxx (192.168.0.xxx) 56(84) bytes of data.
64 bytes from 192.168.0.xxx: icmp_req=1 ttl=64 time=3.65 ms
64 bytes from 192.168.0.xxx: icmp_req=2 ttl=64 time=0.161 ms
....

```

On server (VM) terminal:
# cat /etc/resolv.conf ```

nameserver xxx.xxx.xxx.xxx (ISP nameserver IP)
nameserver 192.168.0.1

```


B.R.
satimis

---

### Post by stefangr1 on 2012-01-27
This seems like a DNS problem. Your primary DNS server is your ISP's, and apparently that one doesn't even know your website. This implies your website can't be reached from the outside world either. Normally, this should be arranged upon registration of your website.

Even when this would have worked however, your ISP's DNS server should return the IP address you received from your ISP, e.g. the one that can be used to connect from the outside world. To be able to use the same domain name from within your home network, you would ideally need to run a reverse DNS server.

For systems on the home network you can also add an entry in the  /etc/hosts files of the client machines
```
192.168.0.xxx	server.domain.com
```

---

### Post by satimis on 2012-01-27
Hi,

Thanks for your advice.

I have installed bind9 on this VM but I don't have a DNS server installed on a separate VM.  I'm now using ISP DNS server instead.

> **stefangr1 said:**
>  - snip -

To be able to use the same domain name from within your home network, you would ideally need to run a reverse DNS server.

Pls explain in more detail about reverse DNS server.  Thanks

> 
For systems on the home network you can also add an entry in the  /etc/hosts files of the client machines
```
192.168.0.xxx	server.domain.com
```

Noted and thanks

B.R.
satimis

---

### Post by stefangr1 on 2012-01-28
I'm a bit puzzled about the way you have set things up.

Normally when you register a website, you provide the ip-address of the system that hosts your website and they then manage the DNS stuff for you. So if you provided the ip-address you've got from your ISP, your domain name will resolve to the external ip-address of your internet modem.

On the home network, however, all systems have their own 192.168.x.x ip address. If you forward the appropriate ports in your internet modem to the internal address of your server, you should be able to reach your server* from the outside world*. If, on the other hand, you attempt to reach it from within your home network, your domain name will still resolve to your external ip-address and this simply doesn't work.

So what you can do to solve this, is run your own dns server, that knows only your own website. I'm sure there are a lot of tutorials etc. on how to configure bind9. In your router, you then set the primary dns server to your virtual machine, and the secondary to your ISP's dns server. This way, all computers on the home network will use your VM as their primary dns server. If the resolved address is server.domain.com, it will return the internal 192.168.x.x address, if it is any other address it will refer to the dns server of your ISP (you have to configure this as well in bind).

---

