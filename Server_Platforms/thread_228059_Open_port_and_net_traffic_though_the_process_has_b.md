---
title: "Open port and net traffic though the process has been killed"
date: 2006-08-02
forum: Server Platforms
---

### Post by timetunnel on 2006-08-02
Hi,
I have been running aMule for only a few minutes and completely quit it. No aMule process is running anymore. However, I can still see net traffic in the GNOME system monitor. Starting Firestarter shows that there's still an open connection on port 4662 (which is the aMule port I configured).

I tried the following, but to my surprise all returned nothing:
```
netstat | grep 4662
lsof -i :4662
```

If I start aMule, these commands return stuff:
```
:~$ lsof -i :4662
amule   11518 username   15u  IPv4 142937       TCP *:4662 (LISTEN)

:~$ netstat | grep 4662
tcp        0      0 192.168.1.2:4662        toronto-HSE-ppp42:61748 TIME_WAIT
tcp        0      0 192.168.1.2:4662        140.115.152.69:1394     TIME_WAIT
tcp        0      0 192.168.1.2:4662        adsl-220-229-149-:28564 TIME_WAIT
tcp        0  15972 192.168.1.2:60225       chello084010173009:4662 VERBUNDEN
tcp        0    138 192.168.1.2:4662        mar44-3-82-235-65-:4995 VERBUNDEN
tcp        0    498 192.168.1.2:55097       p54A32C3A.dip0.t-i:4662 VERBUNDEN

```
Can anybody help me understand what's going on here? How can the port still be open and download/upload stuff when the process that opened the port has been killed? Has my computer been hijacked?

Thanks
Jens

---

