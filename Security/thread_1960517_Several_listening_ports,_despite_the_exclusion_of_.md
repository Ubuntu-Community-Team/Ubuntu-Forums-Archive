---
title: "Several listening ports, despite the exclusion of services."
date: 2012-04-17
forum: Security
---

### Post by kleenex on 2012-04-17
Hi, despite the exclusion of services e.g. avahi, cups and so on, Xubuntu 12.04 still listen on multiple tcp/udp ports. To disable services, I used the BootUp-Manager program, I tried to remove the executable bit with **chmod -x** for services in **/etc/init.d/** directory. I also tried standard **update-rc.d** utility, but after system start there is several listening ports:

```
**[COLOR=SeaGreen]$ netstat -tulp[/COLOR]**
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:domain        *:*                     LISTEN      -               
tcp        0      0 localhost:ipp           *:*                     LISTEN      -               
tcp6       0      0 ip6-localhost:ipp       [::]:*                  LISTEN      -               
udp        0      0 localhost:domain        *:*                                 -               
udp        0      0 *:bootpc                *:*                                 -               
udp        0      0 *:bootpc                *:*                                 -               
udp        0      0 *:mdns                  *:*                                 -               
udp        0      0 *:47376                 *:*                                 -               
udp6       0      0 [::]:43162              [::]:*                              -               
udp6       0      0 [::]:mdns               [::]:*                              - 

**[COLOR=SeaGreen]$ lsof -i |grep mdns[/COLOR]**
avahi-dae 1159  avahi   13u  IPv4   8754      0t0  UDP *:mdns 
avahi-dae 1159  avahi   14u  IPv6   8755      0t0  UDP *:mdns
```I am most interested these two services: **localhost:domain** (something related to DHCP?) and **localhost:ipp**. I have never seen anything like it. I use a standard DSL connection with DHCP.

---

### Post by Hungry Man on 2012-04-17
I'm pretty sure those are just connecting to your router *or* maybe your DNS cache(or both) (if on ubuntu 12.04) but I'm not positive.

---

### Post by sanderj on 2012-04-17
:domain is DNS
:ipp is internet printing

---

### Post by Ms. Daisy on 2012-04-17
You need your computer listening on localhost, which is loopback (the computer communicating with itself). It can't function without it.

---

### Post by kleenex on 2012-04-17
Hi, so everything is normal?

---

### Post by Ms. Daisy on 2012-04-17
Definitely.

---

### Post by kleenex on 2012-04-18
Thank You, Ms. Daisy ;-) Best regards!

---

### Post by jreed1 on 2012-04-18
If you run netstat -tulpan with sudo, it will show you which application has those ports open. Just run it as root or sudo.

---

### Post by Hungry Man on 2012-04-18
I just used netstat tulpan with sudo and there are like... 1000 of these unix domain sockets 

Active UNIX domain sockets (w/o servers)

A lot of them: /var/run/dbus/system_bus_socket


 
unix  3      [ ]         STREAM     CONNECTED     1300606  @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     1300605  
unix  3      [ ]         STREAM     CONNECTED     1299867  @/tmp/dbus-gUbtXeOjxc

What's up with this? I don't know what those are lol

I also have very few listening ports:

sudo netstat --tcp --udp --listening --program

Gives me typical stuff. dnsmasq, etc.

---

### Post by Ms. Daisy on 2012-04-18
Yeah, those are system processes. X11 has to do with the X graphical user interface.

I prefer ```
sudo watch netstat -anlpe
``` which gives you the PID/Program name to make it a bit easier to figure out what the heck the process is.  When you use watch, netstat updates itself every few seconds.

---

