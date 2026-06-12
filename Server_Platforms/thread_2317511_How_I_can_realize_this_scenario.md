---
title: "How I can realize this scenario"
date: 2016-03-17
forum: Server Platforms
---

### Post by YaPaY on 2016-03-17
First of all I am sorry for my poor English

My IP information: (em1)
external: 217.168.x.x
nameserver1 62.2.x.x
nameserver2 62.2.x.x.
nameserver3 62.2.x.x
nameserver4 62.2.x.x
internal: 172.30.14.6
gw: 172.30.14.1

This server works without any problem. Now I connected another device (IPTV Stream server). This device has got 2 Ethernets.

I can access the server from Internet with IP:8000 
The new device has got web interface and port is 80

I would like to access it from Internet with 80 and at the same time connect with my server. 

Cable connections:
Main server: em1 --->connected and work internet
Mainserver em2---->IPTV Stream Server Ethernet1
Mainserver em3---->IPTV Stream Server Ethernet 2

How should I set uo the ifconfig for IPTV Stream to 
1.access from Internet with port 80 via Mainserver
2.send the data to Mainserver through em3

many thanks your helps to in advance

---

### Post by YaPaY on 2016-03-17
Here is the ifconfig output:

em1       Link encap:Ethernet  HWaddr xx:4b:e1:0c:xx:xx
          inet addr:172.30.14.6  Bcast:172.30.14.255  Mask:255.255.255.0
          inet6 addr: fefe::9a41:e1ff:fe0c:7ca2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:748429149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270454996 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1117273883135 (1.1 TB)  TX bytes:25890430053 (25.8 GB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:16708 (16.7 KB)  TX bytes:16708 (16.7 KB)

---

### Post by volkswagner on 2016-03-17
Are you using your server as a router?

Why not use a router instead?

It kind of sounds like you need a reverse proxy like [described here]("http://ubuntuforums.org/showthread.php?t=1920715"), but you will want to setup subdomains if you only have one public ip address.  Main server will have Apache or Nginx running the reverse proxy and direct web calls to your IPTV server.

Just to be clear, the IPTV device is a separate stand alone device, yes?

---

### Post by YaPaY on 2016-03-18
> **volkswagner said:**
> Are you using your server as a router?

Why not use a router instead?

It kind of sounds like you need a reverse proxy like [described here]("http://ubuntuforums.org/showthread.php?t=1920715"), but you will want to setup subdomains if you only have one public ip address.  Main server will have Apache or Nginx running the reverse proxy and direct web calls to your IPTV server.

Just to be clear, the IPTV device is a separate stand alone device, yes?

I am not using my server as a router. I haven't got any router.

IPTV device separate stand alone device, yes.

---

### Post by volkswagner on 2016-03-19
Well, I would simply purchase an inexpensive router. I'm really liking the [MikroTik offerings]("http://www.amazon.com/s/ref=nb_sb_noss_2?url=search-alias%3Daps&field-keywords=miktrotik") lately.  If you don't need gigabit you can get [one for under $30us]("http://www.amazon.com/Mikrotik-RB941-2nD-TC-Lite-2-4Ghz-802-11b/dp/B016E93MX2/ref=sr_1_4?ie=UTF8&qid=1458384223&sr=8-4&keywords=mikrotik").

If you don't want to use a router you have a little work ahead.

I'm no expert in this area, hopefully someone else can chime in, or the following should be enough to research on your own.

You have at least two basic options: 
(1) create a DHCP server on your server and allow [ip-forwarding of traffic]("http://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent")
(2) create an [ad hoc network with static addresses]("http://askubuntu.com/questions/104264/mobile-broadband-sharing-over-adhoc-wireless"), allow ip-forwarding as above and use iptables to direct traffic.

With the above two solutions you'll still need Apache reverse proxy as linked in my first post.

---

### Post by darkod on 2016-03-19
I could help you quite a bit with the networking but I don't understand what are you trying to achieve...

In your first post you say the server has external (public) IP, right? If you don't have ISP router, how are you connecting to the internet? Directly through some kind of ISP modem?

Also, your server has public IP set on one of the interfaces but it is also connected to a GW 172.30.14.1. Why? Or that GW is the route to the internet and the server has no public IP?

Lets clear out first how you are connecting the main server to the internet, and then I assume you are trying to connect the IPTV server to the second LAN port of the main server? If you need other devices in your network to have internet also and without a router, you have to configure the main server to act as a router. Otherwise, if all devices only need to "talk" between them, there is no need for configuring the server as router...

PS. I just reread it again... So the server has an IP on em1 of 172.30.14.6 and it uses GW 172.30.14.1 to go out to the internet, right?

---

### Post by darkod on 2016-03-19
I think I am understanding what you want to do, so to add to my previous post...

You say you connected Main server em2 to IPTV port1 and Main server em3 to IPTV port 2. That is not necessary, to connect them with two connections... Only one is enough...

First of all, are you using some kind of a switch or you are connecting them directly with a cable between the two machines? In most cases in local networks a switch is used which does correct connections. To connect two machines directly you usually have to use cross-over cable. Most network cables sold are direct (straight) cables and are not designed for direct connections between machines. Also, using a switch will allow you to add more devices to the same subnet. Using direct connection is a connection only between those two machines.

So, if you are using a switch you can go on...

You say you can access your server from the internet using the public IP and port 8000. Does that mean the GW has that public IP, and you have configured port forwarding for port 8000 towards 172.30.14.6 (the server private IP)? Do you have control of the GW port forwarding options? Because port 80 will also need to be forwarded so you can reach the IPTV over the internet. It will need to be forwarded on the GW and on the main server because the IPTV is not connected directly to the GW.

---

### Post by YaPaY on 2016-03-21
Thanks darkod you have been wrotten very clear,

I haven't got switch or router. I haven't got  configuration option on GW port forwarding. I think cross-over cable makes the work more complicated. I think I can get second cable from main switch + new external IP.

How can I realize this with install DHCP server and activate for em2?

---

