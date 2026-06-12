---
title: "Wifi Web Server"
date: 2008-08-22
forum: Server Platforms
---

### Post by mafitzpatrick on 2008-08-22
Hi I'm having the same problem reported in this thread last year:
[http://ubuntuforums.org/showthread.php?t=542939&highlight=Wifi+Web+Server](http://ubuntuforums.org/showthread.php?t=542939&highlight=Wifi+Web+Server)

Basically, it is possible to set up a web server available to the net using a direct ethernet into the back of the router, but when connecting the computer via wifi any connection from outside fails.

I'm not sure if this is a router / ubuntu issue, however I've not found any reports of anyone having problems except on linux systems (that other thread! and I have the same problem on openSUSE).

Unfortunately I don't have a Windows box (yay!) so cannot test that. Is there anyone with knowledge about routers, or with a window web server connecting via wifi to test this out. Similarly if anyone else can attempt to do this on Ubuntu/other distro I'd be interested in the results.

Much appreciated.

---

### Post by mafitzpatrick on 2008-08-22
I should mention that I've tried 2 different routers with no effect :(

---

### Post by windependence on 2008-08-23
OK, what IP is assigned to your server, and what IP is the address of your router? Do you have your server IP set up as a static IP on the LAN?

You should have port 80 forwarded from your router to the IP of the server. Apache should also be listening on 80. Then, go to [www.canyouseeme.org](www.canyouseeme.org) and check your port 80 to make sure it isn't being blocked by your ISP (it probably is).

It would also help if you post the contents of your /etc/resolv.conf, etc/network/interfaces. and etc/hostname files.

On a side note, serving the web from a wireless connection is really not a good idea because of the latency, not to mention the security implications. I assume you already know that though. ;)

-Tim

---

### Post by mafitzpatrick on 2008-08-23
Thanks windependence, port is not blocked ( Success: I can see your service on 92.236.180.133 on port (80) Your ISP is not blocking port 80 ). So that's one ticked off :)

Server (this ubuntu box) is 192.168.1.2 assigned statically by the router. Router is on 192.168.1.1. Port forwarding is to 192.168.1.2

/etc/resolv.conf:
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5039
#
### END INFO

nameserver 192.168.1.1


/etc/network/interfaces:
auto lo
iface lo inet loopback

/etc/hostname:
dell-desktop


Also the dynamic dns to access this is dell-desktop.dyndns.org. When I go to that address I get the router setup login, although I've had it confirmed that from externally this is inaccessible. I think I'm going to do a router hard reset and see where that gets me - I've had this for about 3 years and never reset it once and it's moved around a lot maybe the old bird is confused.

Don't worry I'm not intended to host a real site on this address. It's just for knocking up tests/demos that I don't want to go through the bother of installing/setting up on a remote server. Purely temporary (& only occasionally on!)

Thanks for your help, I'll report back on the reset - assuming it comes back on ;)

---

### Post by mafitzpatrick on 2008-08-23
Unfortunately the reset did nothing. Now I'm stumped :)

---

### Post by windependence on 2008-08-23
OK you are missing some important stuff from your network config file. Your /etc/network/interfaces should read like so:

```
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.2
gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
```

I would add to your /etc/resolv.conf

```
nameserver  208.67.222.222 
nameserver  208.67.220.220
```

probably not necessary but the additional DNS servers will make your name resolution faster and more reliable.

Your router does not assign an IP statically unless you set up a reserved address. Most people don't know how to do this. From your network config file, you weren't even set up for DHCP so I don't know how you were pulling an IP address. That is probably why your port forwarding wasn't working. Make your interfaces file look wxactly the way the one looks I posted.

Then restart your network:

```
sudo /etc/init.d/networking restart
```

-Tim

---

### Post by windependence on 2008-08-23
> **mafitzpatrick said:**
> Unfortunately the reset did nothing. Now I'm stumped :)

Don't forget to forward your port 80 back to your server again.

-Tim

---

### Post by mafitzpatrick on 2008-08-23
Thanks for that. Added the information given although it hasn't had any effect - same as before.

Connection setup was using networkmanager - as mentioned this is over wifi, it automatically connects to that network at startup and the router provides the IP. A static IP is set up on the router for this computer (by mac) and the port forwarding is to that IP. From the config you gave for interfaces it looks as though that is ethernet, not wlan, no?

Strangely following the hard reset of the router it is no longer possible to connect *at all* to the ubuntu desktop. Putting the IP address into another computer (wifi phone) gets a gateway error. Mucho confused.

Access from outside is still a no no though.

And yup, I did re-enter the port forwarding... eventually! :) Thanks again.

UPDATE: Access on the local network is working again, needed to reboot the other devices. So back to where we were at the beginning :) Can access the server on the network (via wifi) but not externally. I've asked in the router's forum so hopefully that will give some tips also.

---

### Post by windependence on 2008-08-23
Well the network manager thing is definitely non-standard and that is probably where the routing problem is. 

One thing though. From inside your LAN, you should put an alias entry into the hosts file of every computer that will access the server like so:

192.168.1.2   dell-desktop

In Ubuntu the file is located in /etc/hosts and on Windows it's at C:\Windows\system32\drivers\etc\hosts.

I totally spaced on the fact that your interface is wlan0. Sorry about that. Let me think about it and get back to you.

One thing would be interesting if from the server you could do a traceroute to an outside IP address so that we could see the route the packets are taking. That may help us troubleshoot this.

-Tim

---

### Post by windependence on 2008-08-23
Here is what looks like a great guide for setting up your wireless.

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

-Tim

---

### Post by mafitzpatrick on 2008-08-23
Traceroute (mtr) to google came out with:

 Host
 1. WGT634U
 2. 10.63.56.1
 3. osr01king-v11.network.virginmedia.net
 4. osr02perr-tenge73.network.virginmedia.net
 5. perr-t3core-1b-ge-010-0.network.virginmedia.net
 6. bir-bb-b-so-120-0.network.virginmedia.net
 7. nth-bb-a-so-100-0.network.virginmedia.net
 8. pop-bb-b-so-120-0.network.virginmedia.net
 9. tele-ic-2-as0-0.network.virginmedia.net
10. 212.250.14.138
11. 209.85.252.76
12. 64.233.175.213
13. 209.85.248.216
14. 66.249.94.134
15. 64.233.175.26
16. py-in-f99.google.com

Which is interesting, as the 10.63.56.1 looks like an internal network IP (or am I getting confused here?) which would explain why the port forwarding isn't working from outside - router>router. The odd thing is that the wifi router reports the "internet" (external) IP as  	92.236.180.133.

Hm. I'll take a look at that link you gave, thanks muchly.

---

