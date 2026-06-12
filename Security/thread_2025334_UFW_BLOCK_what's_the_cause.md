---
title: "UFW BLOCK what's the cause?"
date: 2012-07-14
forum: Security
---

### Post by mcc28x on 2012-07-14
Hi,

In my UFW.log I have:

[UFW BLOCK] IN=eth0 OUT= MAC=xx.xx.xx.xx.xx.xx SRC=192.168.0.6 DST=239.255.255.250 LEN=652 TOS=0x00 PREC=0x00 TTL=1 ID=31353 PROTO=UDP SPT=58705 DPT=3702 LEN=632

The machine on 192.168.0.6 is my laptop, I have used CurrPorts to obtain the following about the laptop ports,

Process Name = System, System ID = 1332, Protocol = UDP, Local Port = 58705, 
Local Address = 0.0.0.0, Process Created on = N/A, Process Services = EventSystem, fdPHost, netprofm, nsi, SstpSvc, WdiServiceHost, WinHttpAutoProxySvc

I have no idea what this process is and what program is running it and why it should be trying to connect to the server.	

The only port connections I have opened are for Samba, a web server and SSH. Anyone got any ideas how I can track this down please?

thanks

Mark

---

### Post by CharlesA on 2012-07-14
See here:
[http://help.lockergnome.com/general/239-255-255-250-Port-1900--ftopict18953.html](http://help.lockergnome.com/general/239-255-255-250-Port-1900--ftopict18953.html)
[http://www.vistax64.com/network-sharing/273590-what-ip-239-255-255-250-a.html](http://www.vistax64.com/network-sharing/273590-what-ip-239-255-255-250-a.html)

Sounds like you are running Windows.

---

### Post by mcc28x on 2012-07-15
> **CharlesA said:**
> See here:
[http://help.lockergnome.com/general/239-255-255-250-Port-1900--ftopict18953.html](http://help.lockergnome.com/general/239-255-255-250-Port-1900--ftopict18953.html)
[http://www.vistax64.com/network-sharing/273590-what-ip-239-255-255-250-a.html](http://www.vistax64.com/network-sharing/273590-what-ip-239-255-255-250-a.html)

Sounds like you are running Windows.

Hi thanks,

Yes it is running Windows 7. I take it from the links that it's some kind of windows multicasting service. I think I'll just leave it blocked for now.

cheers

Mark

---

