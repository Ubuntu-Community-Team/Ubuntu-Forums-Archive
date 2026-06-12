---
title: "NUT Client"
date: 2018-07-04
forum: Server Platforms
---

### Post by BigYellowDog on 2018-07-04
I have my UPS connected to my Synology Disk Station and it is running a UPS server.  

My Ubuntu server, Synology server and switch are connected to UPS.  

My router is located in another part of my house, so it is not on UPS. 

If I disconnect my UPS Ubuntu receives a message about being in battery mode.  I also receive a message when power has been restored.

The problem I have is when I loose power and the switch can not communicate with the router.  Then this happens, nut-client keeps powering down Ubuntu.  Ubuntu would boot and immediately shut down. 

```

Jul  4 11:30:20 ubuntu upsmon[31359]: UPS ups@192.168.1.10:3493 on battery
Jul  4 11:30:45 ubuntu upsmon[31359]: UPS ups@192.168.1.10:3493 on line power
Jul  4 11:30:55 ubuntu upsmon[31359]: UPS ups@192.168.1.10:3493: forced shutdown in progress
Jul  4 11:30:55 ubuntu upsmon[31359]: Executing automatic power-fail shutdown
Jul  4 11:30:55 ubuntu upsmon[31359]: Auto logout and shutdown proceeding
```

I'm not sure why nut-client thinks it need to power down, after receiving a message about being "on line power"
I mount share from my synology and ping the IP address.

I am using the IP address in /etc/nut/upsmon.conf

```
MONITOR ups@192.168.1.10:3493 1 <USERNAME> <PASSWD> slave
```

Does my router need to be on UPS for nut-client to function correctly?

---

