---
title: "Configuring the apache2.conf"
date: 2007-01-06
forum: Server Platforms
---

### Post by ishift on 2007-01-06
hey guys

having been extremely impressed with edgy desktop, i decided to use it to create a lamp server to host my site.

now, i've got apache, php, and mysql up and running. i've even got webalizer and phpmyadmin as well. the only obstacle i keep running into is the apache2.conf configuration.

i've registered a domain with yahoo ( for example, ***shift.com*** ). i also have the wan ip in front of me. i can only access my server's files from the port i assigned ( port 78 ). how can i instruct apache to let me (and the rest of the world) access my site?

i've spent many hours googling and researching, but i only get more confused.

any help would be greatly appreciated.

***EDIT:  Nevermind, the newb that i am, i didn't realize that port forwarding wasn't set up correctly for my router. thanks though for the help!***

---

### Post by rth on 2007-01-06
Is your WAN IP static or dynamic? As in, it's the same number every time you connect and you have a business service or something, or every time you connect, it can change?

What's missing is DNS for the outside world to point to you. Whoever you bought the name from generally has a web-based administration area for your site. There will be a NS or Name Server part somewhere. Where this points depends on the answer above. If you have a business connection with a static IP, your provider may let you point to them and they would then configure their servers to say that your domain is at your IP. If it's dynamic (which is your standard home Internet connection), then you will need to use a service from DynDNS or No-IP or something and point the NS to them.

---

### Post by ishift on 2007-01-06
i've made the server wan ip static, and yahoo is providing the domain to my wan ip.

---

### Post by Nikron on 2007-01-07
I'm trying to do something simliar, except I don't know how to foward the port.  How do I find out the computer's internal IP?

---

### Post by MJN on 2007-01-07
**ifconfig**

e.g.
```

mathew@rugrat:~$ ifconfig
eth0    Link encap:Ethernet  HWaddr 00:40:F4:54:73:10
          inet addr:**192.168.0.50 ** Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe54:7310/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39349043 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39131776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1393020348 (1.2 GiB)  TX bytes:3045658567 (2.8 GiB)
          Interrupt:11 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:735571 errors:0 dropped:0 overruns:0 frame:0
          TX packets:735571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:165609181 (157.9 MiB)  TX bytes:165609181 (157.9 MiB)


```Mathew

---

