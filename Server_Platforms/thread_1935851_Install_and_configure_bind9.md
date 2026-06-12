---
title: "Install and configure bind9"
date: 2012-03-05
forum: Server Platforms
---

### Post by bsaidus on 2012-03-05
Hello to all the Ubuntu community !!
I'm wondering if there is a step by step tutorial on how to configure bind9 to work in normal or in a chroot mode .
I have tried to configure bind9 in my Ubuntu 10.04.3 but (( [https://help.ubuntu.com/8.04/serverguide/C/dns-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/dns-configuration.html) )) but i did'nt understand  :oops:  the meaning of ns. ( is **ns** in **ns.example.com ** refer to the name of the server (PC) ?? or something else ...?? )

```

; BIND data file for local loopback interface ; 
$TTL    604800 
@       IN      SOA     ns.example.com. root.example.com. (                               [INDENT][INDENT]1         ; Serial     
[/INDENT][/INDENT][INDENT][INDENT]604800        ; Refresh  
[/INDENT][/INDENT][INDENT][INDENT]86400           ; Retry     
[/INDENT][/INDENT][INDENT][INDENT]2419200        ;Expire    
[/INDENT][/INDENT][INDENT][INDENT]604800 )       ; Negative Cache TTL ; @       
[/INDENT][/INDENT]IN      NS      ns.example.com. 
@       IN      A       192.168.1.10 
ns      IN      A       192.168.1.10

```So, please tel me what to configure for first (PC, hostnames ..) before creating zone files and configuring DNS
thanks in advence.

---

### Post by sanderj on 2012-03-05
Why do you want bind9 on your system? bind9 and nameservers are very difficult to setup.

If you want to access other systems on your LAN by their name, you don't need bind: you can already access them by their name only. See snippet below.

If you want a FQDN (name) and a public IP address on Internet consider something like dyndns, or a hosted dns services (like enom).

If you still want bind9, consider setting it up via webmin; webmin will create the basic files and you can add entries via webmin's webgui. 

HTH


```

sander@netbook:~$ ping r540.local.
PING r540.local. (192.168.1.53) 56(84) bytes of data.
64 bytes from R540.home (192.168.1.53): icmp_req=1 ttl=64 time=1043 ms
64 bytes from R540.home (192.168.1.53): icmp_req=2 ttl=64 time=36.1 ms
64 bytes from R540.home (192.168.1.53): icmp_req=3 ttl=64 time=1.78 ms
^C
--- r540.local. ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2009ms
rtt min/avg/max/mdev = 1.788/360.565/1043.751/483.289 ms, pipe 2


sander@netbook:~$ ping r540
PING r540.home (192.168.1.53) 56(84) bytes of data.
64 bytes from R540.home (192.168.1.53): icmp_req=1 ttl=64 time=27.1 ms
64 bytes from R540.home (192.168.1.53): icmp_req=2 ttl=64 time=48.8 ms
^C
--- r540.home ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 27.175/38.019/48.864/10.846 ms
sander@netbook:~$ 

```

---

### Post by bsaidus on 2012-03-05
> 
Why do you want bind9 on your system? bind9 and nameservers are very difficult to setup.
If you want to access other systems on your LAN by their name, you don't  need bind: you can already access them by their name only. See snippet  below.
If you want a FQDN (name) and a public IP address on Internet consider  something like dyndns, or a hosted dns services (like enom).

So what is the solution to do if I want to publish Web an Mail servers on the web !! "certennely " I need DNS ((BIND)).
for this moment I want to configure manually bind on my machine and I don't want to use webmin.

thank you .

---

### Post by sanderj on 2012-03-05
If you want web and mail, you probably want a domain too? If so, you can get that (including a webgui to edit your nameserve entries) at enom ([http://www.enom.com/](http://www.enom.com/)). I have a domain at enom, and it works great.

If you don't want a real domain, but just something like somesystem.generaldomain.com, then dyndns is an easy solution. See for example [http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html](http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html)

You don't need a local bind server. I don't understand why you do not want webmin. If your goal is to learn bind, then I advice you this book [http://shop.oreilly.com/product/9780596100575.do](http://shop.oreilly.com/product/9780596100575.do) . I have read that book a lot of years ago, and bind is a beast.

---

