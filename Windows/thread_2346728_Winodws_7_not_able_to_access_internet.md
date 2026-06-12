---
title: "Winodws 7 not able to access internet"
date: 2016-12-17
forum: Windows
---

### Post by tech291083 on 2016-12-17
Hi Friends,

I am running Windows 7 Home Basic 32 bit on my PC. Its a genuine copy of Windows, which is updated to this date. There is a reputed 3rd party Internet Security Suite, which is also fully updated. Just a couple of days ago, Firefox web browser version 50.0.2 (I also keep updating it as well) crashed for some reason, I then immediately uninstalled Firefox and restarted the PC and since then I have not been able to access the internet even with internet explorer (IE). 

I went into safe mode with networking and was able to access the internet without any problems whatsoever, so how come I am not able to access the internet in regular mode.

I googled a bit and came across the following site,

[http://superuser.com/questions/470585/how-to-force-windows-7-to-ask-for-a-fresh-ip-address-from-dhcp-server](http://superuser.com/questions/470585/how-to-force-windows-7-to-ask-for-a-fresh-ip-address-from-dhcp-server)

After a normal I did the following commands in CMD as Administrator,

```

ipconfig /release
net stop dhcp
net start dhcp
ipconfig /renew

```

Rebooted the PC. But still the issue was not resolved, internet was not accessible via any browser whatsoever.

I went into safe mode with networking (and I as mentioned earlier was able to access the internet via IE as Firefox was already un-installed) and again I did the following commands in CMD as Administrator,

```

ipconfig /release
net stop dhcp
net start dhcp
ipconfig /renew

```

Rebooted the PC. But still the issue was not resolved, internet was not accessible.

So, again I booted normally and tried the following in CMD as Administrator,

```

netsh winsock reset catalog
netsh int ip reset reset.log

```

After a reboot, the issue not resolved.

Now, I booted into safe mode with networking and again I did the following commands in CMD as Administrator,

```

netsh winsock reset catalog
netsh int ip reset reset.log

```

Rebooted the PC into normal mode, but the issue never really got resolved.

I am no expert when it comes to networking, but I observed that even if I tried the above commands in CMD as Administrator, after a reboot the ipconfig command will still show the same ip assigned to my PC ie 192.168.0.100

I am using a router. PC is connected to the router via a LAN cable. Other devices ie laptops, mobiles are connected to the same router wirelessly and they are able to access the internet as of now despite the issue. My router's (TP-LINK TL-WR740N) settings page shows my PC as one of the clients (connected devices).

Can you please help me?

Thanks a lot.

---

### Post by tech291083 on 2016-12-21
Friends,

As all my efforts failed, I just re-installed my 3rd party Internet Security Suite and the issue disappeared automatically, thanks.

---

