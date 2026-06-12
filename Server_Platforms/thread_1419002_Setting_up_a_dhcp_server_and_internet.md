---
title: "Setting up a dhcp server and internet"
date: 2010-03-01
forum: Server Platforms
---

### Post by aquavitae on 2010-03-01
I'm trying to set up a home server using ubuntu server 9.10, and its all working fine except that I'm having problems starting the dhcp server and connecting to the internet.

The syslog shows that dhcp starts, but brings up the error "No subnet declaration for br0 (0.0.0.0). br0 is the bridge interface I'm using, but I set it to have an ip address of 10.10.10.1 in /etc/network/interfaces.  If I manually start the dhcp server its fine, so I assume that its trying to start before the interface is fully up. Unfortunately I have no idea how to fix this.

The second problem is that I'm not sure how to get the internet to connect at startup. Its a slightly unusual device, so I need to use a simple pon command to start it up, which I can do manually, but I'd like to put it in a startup script somewhere. Where would be the appropriate place to put it?

Thanks for the help.

---

### Post by ICEB3AR on 2010-03-01
You could create a startup script like the following and place it in /etc/init.d/myownstartupscript
```
#!/bin/sh -e 

#do the script work....
``` 
after this you could create a link in the right runlevel dir:
```
ln -s /etc/init.d/myownstartupscript /etc/rc2.d/S99mystartup
```

Maybe a solution for your first Problem is to later (higher Number in startup-file (above number 99 is highest)) restart dhcp-server. Although it is not a very nice solution.

EDIT: Maybe you could try to set the startup-number of the dhcp-startup script to a higher (watch at ```
update-rc.d
```). But to my mind dhcp should start after the Network-Configuration

---

### Post by aquavitae on 2010-03-02
Thanks for the suggestions.  I tried moving the dhcp server to 80, but it didn't make any difference. I don't see an startup script for the network though, so I'm not sure when it is initialised. The other confusing thing is that br0 is a bridge connection which I define in /etc/network/interfaces, and it looks like dhcp is seeing the device, but not the ip address, which is defined in the same place.

I had thought of creating a new startup script to start the internet, but I wasn't sure if that was the best way of doing it. I also thought of doing it in /etc/profile, but that only runs when I log in, which I'm not going to do on a server. Another idea was to create a udev rule so that it will connect when the modem is detected, but I couldn't get that to work.

---

