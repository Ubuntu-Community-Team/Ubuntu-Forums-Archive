---
title: "dhcpd.conf setting to enable Vista clients (broadcast flag)"
date: 2008-06-12
forum: Server Platforms
---

### Post by Takilara on 2008-06-12
Hello, my first post here :)

After hours of googling I've given up, and resorted to asking here.

I have an Ubuntu 8.04 box, that I use as DHCP server. This has worked brilliant untill yesterday, when I got my new laptop with Vista on it. This is the first Vista machine in my house.

And now to the problem: Vista will not accept the IP address it gets from the dhcp server. Something about the broadcast flag not beeing supported. This is explained here: [http://support.microsoft.com/kb/928233](http://support.microsoft.com/kb/928233)
The solution in the microsoft documentation is either to fix the dhcp server, or to do a registry tweak in Vista. 

I have tried (and currently uses) the registry tweak. And even though this does fix the problem, I'd rather fix the dhcp server.

I've seen some places that say that adding the 
```
always-broadcast on; 
```
statement will help. 
This did not help, and prevented all my XP clients from getting ip address.

Does anyone know what it takes to get the dhcp3-server to support that broadcast flag? Is it even possible? Are there alternative dhcp servers that will work?

I am fairly confident that the solution is ridiculously simple, its just me thats unable to figure it out..

Regards

---

### Post by beckols on 2008-06-16
Did you explicitly declare the broadcast address in dhcpd.conf??  I think it is just optional, since most computers can decipher it on their own, but maybe vista needs to see it.

---

### Post by Takilara on 2008-06-16
Yea, i tried both with 192.168.1.255 and with 255.255.255.255
didnt notice any change :(

---

### Post by Bardo77n on 2008-07-01
That's strange. I have a Hardy DHCP server and Vista clients receive an IP fine from it.

Actually, the reason I built the server is because Vista clients weren't getting IPs. We have a open access Wifi vlan and the simple DHCP server that we were using did not support the broadcast flag that Vista requires. It was built in to our gateway, I built a vanilla Ubuntu DHCP server, attached it to the vlan, and everybody (including Vista clients) is working.

Brad

---

### Post by Takilara on 2008-07-01
Hmm, i installed dhcpd before i upgraded to hardy, maybe the default conf file is not the same ?

could you show me your conf? 
(btw, i do suspect that the problems also have to do with the fact that I do **not** use the same server as DNS server. (when i did (before I ever tried Vista clients), I had a problem that all the clients would loose connection after approx 24 hours, and i had to do "repair" on the connections, or ipconfig /renew), as soon as i set the ubuntu dhcp server to say that the linksys box was the route, everything was working perfect until the vista clients... 

(i have been using my linksys router as dhcp server for the last couple of weeks)

---

### Post by antono on 2008-10-08
have the same issue. anybody solved it on hardy?
is there any option to support both XP and Vista clients?

---

### Post by Takilara on 2008-10-08
I ended up giving up. Now i use my Linksys router both as dhcp and dns server. And the ubuntu box only as file/web server :(

There probably is a super simple way to fix it, but when i couldn't find a solution in one week, then I just couldn't bother anymore :(

---

### Post by janhendrik on 2009-02-24
Not sure if this will work for you, but it did for me:

[http://forums.fedoraforum.org/archive/index.php/t-157188.html](http://forums.fedoraforum.org/archive/index.php/t-157188.html)

It Boils down to removing the 127.0.0.2 lookup in you /etc/hosts file. In other world make sure that your hostname is resolved to your network ip address and not a 127-net address

---

