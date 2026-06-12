---
title: "ssh connect to host, Operation timed out"
date: 2009-07-15
forum: Server Platforms
---

### Post by Risoh on 2009-07-15
I have a server 9.04 conected to router/adsl modem. I am using fixed IP to MAC feature on my router to have fixed IP for my server.

I didn't set up any network configuration on server itself.

Sometimes after start I'd get ssh connect to host xxx.xxx.x.xx port 22: Operation timed out. After restarting the server most of the time I can connect no problem to my server. 

Any idea what can be the problem? Do I need to set the IP adress on my server network interfaces, or is it problem in my router set up?

thanks

---

### Post by giggins on 2009-07-16
Ok, so it sounds like you're using a static DHCP assignment by MAC address. Not a bad thing, but it might be simpler to just assign the server a static IP. But, to try and help with your problem as is, you could probably start by checking the logs on the server before you reboot it. Try checking on it from the console:

```
dmesg
```

You could also try disabling + renabling the interface instead of rebooting it:

```
sudo ifdown eth0
sudo ifup eth0
```

There may be something up with the dhcp server / client if this fixes it...

---

### Post by Risoh on 2009-07-17
Thanks for reply.

I will try to run dmesg next time it happens.


I have maybe couple of basic questions to your first suggestion, but I am not so good with networking:-)

Should I try to assign the static IP on router or can I set it in server configuration?

If I do it on server, will my router accept this? I guess the IP have to be outside of DHCP range.

Thanks again.

---

### Post by giggins on 2009-07-17
> **Risoh said:**
> Should I try to assign the static IP on router or can I set it in server configuration?

Well, both should have a static IP address, but likely your router already does. Here's a good example:

```
192.168.0.0/24 (IPs 192.168.0.1 - 192.168.0.254 are usable by devices)
192.168.0.0  ->  network address (don't use)
192.168.0.1  ->  router
192.168.0.2  ->  **assign to server**
192.168.0.50 - 192.168.0.200 -> DHCP range
192.168.0.255 -> broadcast address (don't use)
```Obviously, your scenario may be setup a little differently, but it should be pretty close. You can figure out your real situation by running the following on your Linux server:

```
route -n
```Look for the route with a Destination of 0.0.0.0, and the Gateway will tell you your router's IP, and then you look for the route with a Gateway of 0.0.0.0, and the Destination will tell you your network address. You should be able to assign the IP after your router's IP to your server, but to be on the safe side, you should try pinging it:

```
ping -c 5 192.168.0.2
```If you get "Destination Host Unreachable", then the IP is likely not in use.

Assiging the IP to the server is done through editing /etc/network/interfaces (assuming your not using Network Manager on a desktop version of Ubuntu). If you are using a desktop version of Ubuntu, you should use the GUI to change the IP on the server. Let me know which you're using, and I can tell you how to change the IP.

---

### Post by Risoh on 2009-07-17
Ok. 

Does it mean that if I set up on server the static IP. (Something like here [http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)) my router will automatic accept the static IP from server and will exlude it from assigning the DHCP IP to it?

Thanks and sorry for stupid question ;-)

---

### Post by giggins on 2009-07-17
Looks like those instructions are accurate. As long as the IP address is within the network your router is routing for, then it should work. You may need to look into the configuration of your router to determine the DHCP range (the IPs the router gives out), and make sure the address you assign your server is not within that range.

---

### Post by Risoh on 2009-07-18
Great. Got it. Thanks a lot.

---

