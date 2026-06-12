---
title: "Static IP Address Not Working"
date: 2009-01-25
forum: Server Platforms
---

### Post by jbiggs12 on 2009-01-25
hello all, 
I have an ubuntu server (x64) and I'm having trouble connecting to the internet with a static ip. I've tried editing /etc/network/interfaces, and even tried editing resolv.conf, to no avail. I'm hooked up to a linksys switch that connects both my server and my airport extreme (for my lan) to the internet, and nothing's working. Could it be that I'm trying to share the same ip with the airport, and it's not letting me? I can connect to the internet on my lan just fine, but when I try to connect to the internet on my server, it doesn't work. Is there something I'm doing wrong here?

Also: I can't get PHP to work on my Apache server. Whenever I go to an index.php page, I download the file instead of viewing it. Same goes for when I try to access the directory.

---

### Post by jbiggs12 on 2009-01-25
By the way, I'm on my mac on my LAN so I dont think I'll be able to post much output.

Update: I've hooked up my mac to my switch, so now I can vnc via ethernet.

---

### Post by spynappels on 2009-01-25
When you say static IP, do you mean a static external IP, given to you by your ISP, or a static local IP on your local LAN?

 Can you also explain your set up? Is the Linksys switch a router or a switch? Does it act as a DHCP server, or does your Airport Extreme do this? 

 Normally, your ISP gives you either a static or dynamic IP. This points to your modem/router, and the router then handles the local IPs and sending the "internet" to all other computers on the network. Alternatively your ISP may give you multiple static IPs which a WAN router sends to selected computers, such as your server and the Airport. This then forwards the traffic to your Mac(s).

 Depending on your setup, you need to do different things to get it working.

Stefan.

---

### Post by trentscott4 on 2009-01-25
> **jbiggs12 said:**
> hello all, 
I have an ubuntu server (x64) and I'm having trouble connecting to the internet with a static ip. I've tried editing /etc/network/interfaces, and even tried editing resolv.conf, to no avail. I'm hooked up to a linksys switch that connects both my server and my airport extreme (for my lan) to the internet, and nothing's working. Could it be that I'm trying to share the same ip with the airport, and it's not letting me? I can connect to the internet on my lan just fine, but when I try to connect to the internet on my server, it doesn't work. Is there something I'm doing wrong here?


1. Modify the /etc/network/interfaces file.
     sudo vi /etc/network/interfaces
2. Press 'Insert' to edit the file and enter the following
(customized to your network):
     # The primary network interface
     auto eth0
     iface eth0 inet static
     address 192.168.x.xxx
     netmask 255.255.255.0
     gateway 192.168.x.x
3. Hit 'Esc' and type ':wq' to save the file and quit.
4. Modify your DNS servers.
     sudo vi /etc/resolv.conf
5. Delete any existing lines and replace with your router's IP:
     nameserver xxx.xxx.x.x
6. Hit 'Esc' and type ':wq' to save the file and quit.
7. Restart your networking.
     sudo /etc/init.d/networking restart
8. Test your new settings:
     sudo ifconfig
The outpott should reflect the changes we just made(proper IP, gateway, etc.)

> Also: I can't get PHP to work on my Apache server. Whenever I go to an index.php page, I download the file instead of viewing it. Same goes for when I try to access the directory.

[http://ubuntuforums.org/archive/index.php/t-910554.html](http://ubuntuforums.org/archive/index.php/t-910554.html)
[http://ubuntuforums.org/showthread.php?t=942805](http://ubuntuforums.org/showthread.php?t=942805)

1. Clear your browser cache.
2. Check permissions to the directory on the server (www-data).
3. Set it up as a module.

---

### Post by spynappels on 2009-01-25
> **trentscott4 said:**
> 1. Modify the /etc/network/interfaces file.
     sudo vi /etc/network/interfaces
2. Press 'Insert' to edit the file and enter the following
(customized to your network):
     # The primary network interface
     auto eth0
     iface eth0 inet static
     address 192.168.x.xxx
     netmask 255.255.255.0
     gateway 192.168.x.x
etc.
etc.


This will only work if the Linksys box is a router rather than a switch. Else you are trying to mix local (192.168.xxx.xxx) and Global IP addresses.

That is why I asked the OP to explain his setup a little better.

Also, depending on how comfortable the OP is with Linux, Nano might be an easier editor to use...

---

### Post by jbiggs12 on 2009-01-25
thanks guys... i've tried all of that for the static ip... but still no dice. could it be that it's because i'm sharing the ip with my airport router, or that i'm using a switch?

---

### Post by jbiggs12 on 2009-01-25
> **spynappels said:**
> When you say static IP, do you mean a static external IP, given to you by your ISP, or a static local IP on your local LAN?

 Can you also explain your set up? Is the Linksys switch a router or a switch? Does it act as a DHCP server, or does your Airport Extreme do this? 

 Normally, your ISP gives you either a static or dynamic IP. This points to your modem/router, and the router then handles the local IPs and sending the "internet" to all other computers on the network. Alternatively your ISP may give you multiple static IPs which a WAN router sends to selected computers, such as your server and the Airport. This then forwards the traffic to your Mac(s).

 Depending on your setup, you need to do different things to get it working.

Stefan.

The Linksys is a switch. We have 1 static IP, and the airport leases IP's via DHCP to our macs.
(excuse my short messages, attempting to type in dvorak.)

---

### Post by gombadi on 2009-01-25
Can I just highlight what others have said -
> 
That is why I asked the OP to explain his setup a little better.


We are still waiting for more detail on your network so we can help.


> 
When you say static IP, do you mean a static external IP, given to you by your ISP, or a static local IP on your local LAN?

Can you also explain your set up? Is the Linksys switch a router or a switch? Does it act as a DHCP server, or does your Airport Extreme do this?


> 
The Linksys is a switch. We have 1 static IP, and the airport leases IP's via DHCP to our macs.


Ok so now we know the lynksys is a switch. so what does it connect to to get to the Internet - You don't say.

> 
could it be that it's because i'm sharing the ip with my airport router, or that i'm using a switch


What is the static IP address - you don't say (hide the last section if you want but it would be a big help if you could tell us.)

Why do you think it could be shared with the airpoint - you don't say - we have to guess what you may be thinking.


> 
I can connect to the internet on my lan just fine, but when I try to connect to the internet on my server, it doesn't work.


Again no details provided - what is the layout of your LAN - ip address ranges etc.

We are only to pleased to help but you need to give us some information to work on like -

What is the static IP address.
Why do you think it is shared.
What is actually wrong - all I see is that you can't connect. Get timeouts, get connection refused, can't ping these ip addresses etc.
What is the output of ifconfig command.
What does the /etc/network/interface file contain.

---

### Post by Hobgoblin on 2009-01-26
> **jbiggs12 said:**
> thanks guys... i've tried all of that for the static ip... but still no dice. could it be that it's because i'm sharing the ip with my airport router, or that i'm using a switch?

You can't have 2 devices with the same IP on one network.

Post the IP you are trying to assign, it will help greatly.

---

### Post by spynappels on 2009-01-26
Ok, that's a little clearer. You have a static IP, assigned by your ISP. Is there a Cable or DSL modem between the internet and the Linksys switch? Or is the IP address of the Airport set to your external IP? If that is the case, you can plug the switch into an RJ45 on the Airport and plug your server into the switch, (or directly into the Airport).

Then the server should have a static local IP with the edited /interfaces file you have created. This should give you internet access from the server. If you want to serve web pages etc. from the server, you will need to set up port forwarding on your Airport to pass port 80 requests to the static local IP assigned to your server.

If you have a cable or DSL modem which acts as a DHCP server too, this changes things a bit, but try the above and see if it works first.

Stefan.

---

### Post by spynappels on 2009-01-27
Did you get the issue fixed?

---

### Post by jbiggs12 on 2009-01-27
ok, thanks very much stefan.
by the way, here's the output of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:88:47:1a  
          inet addr:209.145.171.45  Bcast:209.145.171.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe88:471a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7577 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:791401 (791.4 KB)  TX bytes:6169648 (6.1 MB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3608 (3.6 KB)  TX bytes:3608 (3.6 KB)

```
and the layout of my network:
[[img]http://img1.hidemyass.com/img/LI2dM.jpg[/img]](http://www.hidemyass.com/img/LI2dM)

---

### Post by jbiggs12 on 2009-01-27
also, it appears that whenever I start up the computer it gives me these constant "DHCPDISCOVER" messages then appears to give up. Even though I set /etc/network/interfaces to tell the system otherwise, it still wants a leased IP. This is spooky.
@Stefan: I've moved my server into my LAN, but it's still not working. o.O this is weird.

Update: This might be important: I have a printer connected to the switch that is connected to the router, along with the server. Would that do any harm?

---

### Post by spynappels on 2009-01-28
> **jbiggs12 said:**
> also, it appears that whenever I start up the computer it gives me these constant "DHCPDISCOVER" messages then appears to give up. Even though I set /etc/network/interfaces to tell the system otherwise, it still wants a leased IP. This is spooky.
@Stefan: I've moved my server into my LAN, but it's still not working. o.O this is weird.



There is a problem with your /interfaces file if it still tries to obtain a DHCP lease. If it is not correct, moving the server to the LAN is not going to make any difference.
 Could you post your /etc/network/interfaces file so we can see what it says?

Also, having the printer attached to the switch, what is the IP of the printer set to? or is it DHCP, in which case what DHCP server is it using?

---

### Post by Iowan on 2009-01-28
I've seen a couple of threads where dhclient refuses to "disable".  Solution/recommendation was to uninstall dhclient (I think). I'll try to find the thread.
[Here]("http://ubuntuforums.org/showthread.php?t=842443") is one.

---

### Post by jbiggs12 on 2009-01-28
In response to a network crash :( I updated my network. My printer is now connected to my Airport router via USB, and the switch has evaporated from the whole mess. I can get DHCP just fine, but still no dice with a static IP. Editing /etc/network/interfaces still doesn't do anything, so I revert it every time that my internet doesn't work and stick with DHCP. Here it is anyways:
> auto lo
iface lo inet dhcp


---

### Post by jbiggs12 on 2009-01-28
> **Iowan said:**
> I've seen a couple of threads where dhclient refuses to "disable".  Solution/recommendation was to uninstall dhclient (I think). I'll try to find the thread.
[Here]("http://ubuntuforums.org/showthread.php?t=842443") is one.
Thanks. I did that, I'll see what I come up with.

---

### Post by spynappels on 2009-01-29
> **jbiggs12 said:**
> In response to a network crash :( I updated my network. My printer is now connected to my Airport router via USB, and the switch has evaporated from the whole mess. I can get DHCP just fine, but still no dice with a static IP. Editing /etc/network/interfaces still doesn't do anything, so I revert it every time that my internet doesn't work and stick with DHCP. Here it is anyways:

This looks like your network card is not even being enabled automatically. There should be something like the following in that file, as well as the lo (loopback) interface:

```
auto eth0
iface eth0 inet static

address 192.168.x.x (static LAN IP of your server)
netmask 255.255.255.0
gateway 192.168.xx.xx (normally the LAN IP of your router)
```

This at least would enable the NIC at boot and assign it the static IP.

Try that and let us know what happens.

---

