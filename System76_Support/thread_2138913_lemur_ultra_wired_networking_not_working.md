---
title: "lemur ultra: wired networking not working"
date: 2013-04-25
forum: System76 Support
---

### Post by shochatd on 2013-04-25
Today, in preparation for upgrading to 13.04, I plugged in an ethernet cable to my router, since I prefer to use a wired connection for distribution upgrades. Visually, everything looked fine (it said Wired Connection 1 had been established). But my web browser acted as though I was not connected. So I tried pinging my router (192.168.1.1). This gives the result:
ping: sendmsg: Operation not permitted
pinging the loopback interface is successful.
When I use WiFi, everything is fine. 
My 32 bit desktop machine, running 13.04, is using a wired connection to the same router (although it uses a static IP address instead of DHCP). No problem there.
I went ahead and upgraded the Lemur to 13.04 (using WiFi), downloaded the latest System 76 Driver, enabled it, and restarted. Still have the same problem with wired networking. WiFi is still fine.
I would appreciate any suggestion on where to go from here.
-- David

---

### Post by isantop on 2013-04-25
Hi David.

Is the router's DCHP server enabled? Also, make sure that you are using DCHP on the Lemur, or that if you are using a static IP, that it isn't conflicting with any other deivces on the network (wired or wireless).

---

### Post by shochatd on 2013-04-25
> **isantop said:**
> Hi David.

Is the router's DCHP server enabled? Also, make sure that you are using DCHP on the Lemur, or that if you are using a static IP, that it isn't conflicting with any other deivces on the network (wired or wireless).

I know that DHCP works on the router because I can connect without error using WiFi (using DHCP). Also, there are numerous devices on my internal network that are using DHCP. Most of these are using WiFi, but my Roku box is connected using ethernet and is using DHCP (with no problem). I have not tried using static IP on the Lemur. Google has taken me to various solutions which seem to imply that this is firewall-related. My Lemur does have firestarter installed. Since WiFi is ok, it seems to me that it has to be something specific to the eth0 interface. Also, I can see from ifconfig that I'm getting 192.168.1.10 from DHCP for eth0. And I can ping myself using that address, successfully.

---

### Post by shochatd on 2013-04-25
I tried doing sudo firestarter --stop and that solved the problem. When I run firestarter, I don't see anything about rules specific to eth0 vs. wlan0, so I'm still mystified by the fact that it was preventing traffic on eth0 but not on wlan0. At home, I don't really need to be running a firewall on this laptop since I'm inside my local network. But what about when I take the lemur to a hotel? What is the System76 recommended method for firewall configuration?

---

### Post by shochatd on 2013-04-25
I looked in "Getting Started with Ubuntu 12.04" (I know, a bit out of date) and it suggested gufw. So I uninstalled firestarter and installed gufw. Configured it to deny all incoming connections (not running any servers on the lemur at the moment). With this setup, everything still seems to be working fine both with WiFi and with wired (eth0). So I guess I need to mark this solved.
-- David

---

