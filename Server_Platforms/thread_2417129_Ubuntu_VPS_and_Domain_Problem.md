---
title: "Ubuntu VPS and Domain Problem"
date: 2019-04-21
forum: Server Platforms
---

### Post by numanburakfidan on 2019-04-21
Hi, I hired Ubuntu 14.04 VPS and I have a domain. I just want to access my server via my domain instead of the IP address on browser. I tried a few ways I could find but non of them worked. I also entered my IP address to type A on DNS management page on the web site of my host provider. Here is the files I changed :

hostname = soilprime
/etc/hosts                                                 --> [https://paste.ubuntu.com/p/pnRKhYzVTD/](https://paste.ubuntu.com/p/pnRKhYzVTD/)
/etc/apache2/sites-available/soilprime.com.conf --> [https://paste.ubuntu.com/p/SVmDFVq9K9/](https://paste.ubuntu.com/p/SVmDFVq9K9/)

---

### Post by SeijiSensei on 2019-04-21
In the Apache configuration, you can have only one canonical ServerName.  Make the second entry a ServerAlias.

---

### Post by numanburakfidan on 2019-04-21
I deleted it but it didn't solve the problem.

---

### Post by SeijiSensei on 2019-04-21
> 127.0.1.1 soilprime
0.0.0.0 soilprime.com
0.0.0.0 [www.soilprime.com](www.soilprime.com)

I presume [www.soilprime.com](www.soilprime.com) is supposed to point to your VPS's external address, right?  Then these entries are entirely wrong.

First, I'd delete all of them and see if your DNS changes are sufficient to resolve the problem.  If you want to keep the /etc/hosts entries, then you should have just this one:

```
your.external.ip.addr     www.soilprime.com soilprime.com soilprime
```

Any names after the first are aliases.

The 0.0.0.0 address points to no host.  It is the "default" address used to route traffic to any address not locally defined.  Take a look at the results of "route -n". On this machine it reads,

```

0.0.0.0         192.168.100.1   0.0.0.0         UG    100    0        0 enp7s0
192.168.100.0   0.0.0.0         255.255.255.0   U     100    0        0 enp7s0

```

Traffic for the 192.168.100.0/24 network is broadcasted by the Ethernet interface to the local network.  All other traffic is forwarded to my "default gateway" at 192.168.100.1.

---

### Post by numanburakfidan on 2019-04-22
I changed the hosts file, after I reboot the system when I open the file it becomes 176.53.62.231 soilprime.com soilprime soilprime soilprime.com. What should I do ?

---

### Post by SeijiSensei on 2019-04-23
I've never seen /etc/hosts be modified.  If that persists, you can make the file "immutable" with

```
sudo chattr +i /etc/hosts
```

Now no user, even root, can change that file. Use "-i" to make turn off immutability.

---

