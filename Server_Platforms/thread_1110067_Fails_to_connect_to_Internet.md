---
title: "Fails to connect to Internet"
date: 2009-03-29
forum: Server Platforms
---

### Post by ricolinux on 2009-03-29
Hello every one
here's my problem, I have 7 boxes one w/Ubuntu server 8.10, a NAS. 3 win (Vista, XP, Win2000) and 2 Ubuntu desktops (8.04 Edubuntu, 8.10) All boxes connect internally I can access any file from the NAS and The Ubuntu Server box which also does duties as a printer server. The problem is the server fails to connect to the WORLD to get updates, all started when I tried to install the last update for the TIME savings, now I can PING any IP address outside my LAN, even using [www.name.com](www.name.com) but when I run apt-get or using Synaptic it hangs and return a Failed to connect to whatever site  or repo, mind I can ping the repos IP and get 0% errors. as you can imagine I going nut over this. What could br wrong and what can I do to resolve this???????
Thanks in advace for your imput :( :confused:
RICOLINUX

---

### Post by kamaji792 on 2009-03-29
Sounds like you don't have any domain name servers specified.

If you are using static IP addresses then

/etc/resolv.conf

should have something like this in it:

```
nameserver 192.168.0.1
nameserver 4.2.2.2
```

Replace the IP addresses whith the ones your ISP tells you to use.

atb

---

### Post by ricolinux on 2009-03-29
Thanks Kamaji792 
my etc/resolv.conf
has the right nameservers as given by my ISP
where else can I look for a solution.
My internet connection works just fine, internally I can ssh to my server box and do anything except to update or connect to the WORLD, by the way I installed a GUI desktop and I can not use firefox to browse around the WEB but I can still ping any address or IP with no problems.
 Thanks again
:lolflag:

---

### Post by m3bik on 2009-03-29
I had a similar problem the other day... I checked my DNS records, and they appeared to be correct. Come to find out, I had the Trojan Flush.M which actually hijacked my DNS records and pointed them towards malicious DNS servers. I had many problems until I fixed this.

So if your DNS servers are any of these (look out!):

* 85.255.112.36
* 85.255.112.41
OR
* 64.86.133.51
* 63.243.173.162

---

### Post by ricolinux on 2009-04-01
I found that my router was blocking port 80 always for the server Static IP.
Thanks to all who tried to help. I'll stick with UBUNTU and away from  Bill Gates):P

---

