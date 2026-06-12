---
title: "Wifi Web Server"
date: 2007-09-04
forum: Server Platforms
---

### Post by TheSpecs on 2007-09-04
Hey. I have a problem im hoping you guys can solve.

I have moved my server into my shed and have installed a wifi card and everything is great as i can connect to it through ssh and view the web server... but only within my network.

I cannot access my webserver at all outside my network, and i know it might sound like a firewall problem but i have opened the right ports and setup the virtual server.

I'm at a loss what to do, can anyone help? 

Thanks! :confused:

---

### Post by romandog on 2007-09-04
If you forwarded your ports correctly on the router, it should work just fine.  I would suggest not serving on port 21 as you'll get loads of breakin attempts.  (still can get them on any port, but changing that number reduced mine 99+%)

are you sure you have the correct WAN address?

---

### Post by TheSpecs on 2007-09-04
> **romandog said:**
> If you forwarded your ports correctly on the router, it should work just fine.  I would suggest not serving on port 21 as you'll get loads of breakin attempts.  (still can get them on any port, but changing that number reduced mine 99+%)

are you sure you have the correct WAN address?

Yeah, i havnt setup ftp fully yet but i do plan to use a different port for that. I'm also pretty sure that i have setup the virtual server right. I didn't have any problems when i  was using a Ethernet connection, just now im on wifi :(

---

### Post by KCPokes on 2007-09-04
You are assigning a static IP to your wifi card, which is the same IP that you are forwarding the open ports?  If it serves internally then there is nothing to stop it from serving externally, theoretically.  I'd start with the firewall/router, as that is your entry point.  

As a side note, whether you change your port or not, realistically you should not be running FTP in general.  A port scan is going to find that port within a matter of minutes, regardless, and given that FTP is less then secure, you might consider using SSH (SFTP would be an easily viable option).

---

### Post by Brazen on 2007-09-04
changing ports is generally considered a "smoke and mirrors" security measure.  It is trivial to run a port scan and detect what services are running on the responding ports.

To the OP: are you able to connect to ANYTHING on the server from outside your network?  Most ISPs block the ports needed for things like http, ftp, smtp because they don't want you using a residential connection for "business" purposes (they charge more for that ability).  You should be able to connect to ssh though, assuming your router is forwading tcp port 22 to your server.

It is possible to get around this restriction though, albeit not very "professionally".  My ISP blocks tcp port 80, so I run my webserver on tcp port 856 and then I can connect to it from anywhere.

---

### Post by KCPokes on 2007-09-04
> **TheSpecs said:**
> Yeah, i havnt setup ftp fully yet but i do plan to use a different port for that. I'm also pretty sure that i have setup the virtual server right. I didn't have any problems when i  was using a Ethernet connection, just now im on wifi :(

I just noticed this post.  Can you connect to your webserver on your local network when it is connected via wifi?  Were you able to verify that you could connect, externally, when it was hardwired?

---

### Post by TheSpecs on 2007-09-05
Hello, cheers for all the responces!

Ok, The wifi card is static and its configured to 192.168.2.5, which is what i can access form my PC and view the webserver on. The router has a virtual server configured to allow port 80 through, and since i could use it with a hardwired connection with both my domian names then i guess that isnt the issue. 

I tried changing ports so no luck there either.

Give me a few minnutes and ill post a few config files i think are relevant. TBH, i do feel its a misconfig of the network interface :S

Thanks again!

---

### Post by KCPokes on 2007-09-05
Stupid question, I'm sure, but I assume you have your router sitting on 192.168.2.1?  Just noticed that you are not using the standard .0.1 or 1.1 addresses.

---

### Post by TheSpecs on 2007-09-05
Yep, my router is accessed from 192.168.2.1

/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
        address 192.168.2.5
        netmask 255.255.255.0
        broadcast 192.168.2.255
        gateway 192.168.2.1


```

iwconfig wlan0(my wireless card)
```

wlan0     IEEE 802.11g  ESSID:"#####"
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:11:50:93:F2:AC
          Bit Rate=2 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr=2432 B   Fragment thr=2432 B
          Encryption key:####-####-##   Security mode:restricted
          Power Management:off
          Link Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Would anything else be helpful?

EDIT: I scanned my IP with 'http://www.t1shopper.com/tools/port-scanner/' and no ports are open :S

---

