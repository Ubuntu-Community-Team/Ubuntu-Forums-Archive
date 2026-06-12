---
title: "Tutorial - Install OpenVPN on Ubuntu 10.04"
date: 2011-05-18
forum: Server Platforms
---

### Post by Zenguy on 2011-05-18
I've created a very detailed howto guide on installing OpenVPN server and client on Ubuntu 10.04. The instructions should also work with newer versions. 

It's designed for a casual user who has a Ubuntu server and wants to set up a VPN so they can safely access the Internet from an insecure hotspot.

It's currently in the form of an 11 page PDF located here:

[http://madisonlinux.org/InstallingOpenVPNOnUbuntu10.04]("http://madisonlinux.org/InstallingOpenVPNOnUbuntu10.04")

Comments welcome.

---

### Post by brettg on 2011-05-21
That's a nice guide, very comprehensive and well laid out. Congrats.

Not a fan of having it in a PDF though, but maybe that's just me.  

As an alternative, I have created a fully interactive script to build PPP over SSH based VPNs. 

A five minute setup guide can be found [here]("http://tuxnetworks.blogspot.com/2011/05/howto-easiest-vpn-setup-ever.html")

---

### Post by Zenguy on 2011-05-21
Yeah, PDF was the quickest way to get it out there. I'll probably covert it to a web page in the future. Our LUG's website is under construction and I didn't want to do it twice.

Your script looks like a great idea. Does it work properly with Network Manager on the client?

---

### Post by rayman1366 on 2011-07-02
hello;i have   a Ubuntu 11.04  ; any guys can  setup a openvpn server for me?
thanks

---

### Post by jakupl on 2011-07-03
> **Zenguy said:**
> I've created a very detailed howto guide on installing OpenVPN server and client on Ubuntu 10.04. The instructions should also work with newer versions. 

It's designed for a casual user who has a Ubuntu server and wants to set up a VPN so they can safely access the Internet from an insecure hotspot.

It's currently in the form of an 11 page PDF located here:

[http://madisonlinux.org/InstallingOpenVPNOnUbuntu10.04]("http://madisonlinux.org/InstallingOpenVPNOnUbuntu10.04")

Comments welcome.

Awesome. I've tried a bunch of other tutorials, and this one is the only one that did it for me.
However, I have a problem.
I can successfully connect to the openVPN server at home, but only for like 20 seconds at the time. The internet connection drops after that, but the vpn connection stays up.
Any help on that would be much appreciated.

---

### Post by LtPitt on 2011-07-04
I'm lovin'it!

Thanks a lot :)

---

### Post by Mythix on 2011-07-07
This did the trick for me (client wise):
sudo apt-get install network-manager-openvpn
more specific:
sudo apt-get install network-manager-openvpn-gnome

---

### Post by ercolino on 2011-09-26
Hi!
While I´m reading you guide. I have a private VPN subscription service running in Windows and I want to install it in Ubuntu (natty).
The company has a downloadable file in which the relevan info is included, for example:

dev tap
remote 88.XX.XX.X
float XX.XX.XX.X
port 5210
ifconfig, etc.

How can I put all this info in my vpn configuration?

I am sorry but I am completely new to linux and it's becoming very difficult for me just to follow general guides.

Many thanks in advance for your help

---

### Post by Zenguy on 2011-09-27
ercolino - You have to take the settings from you subscription and set up a VPN profile in Network Manager. The last part of my guide that deals with the Client setup shows you the way to do it, but your settings will be different. Good luck.

---

### Post by SOMDdan on 2011-10-21
ZENGUY: your PDF instructions were admittedly better than all the others I have found so far, including the official guide from OpenVPN, as well as the Ubuntu guide, but................there are still some significant  questions that have yet to be answered.   My first attempt at using your guide was a failure, and I hope you can help me clear them up. Here they are:

Does your guide work for a standard-issue distribution of Ubuntu desktop, or does it have to specifically be Ubuntu *Server? *(I have been trying to install OpenVPN on a newly installed Ubuntu 10.4 Desktop virtual Machine running on VMWare workstation, with a bridged interface to the host)
When I run an ***ifconfig ***command after the VPN server is running (or at least I assume it is), I get listings for eth0, br0, and tap0. Both eth0 and br0 have ethernet addresses on the same subnet, but they are different (192.168.102.36 and 192.168.102.38, respectively), and tap0 does not have an address. Is this what I am supposed to be seeing?

A part of your instruction involves installing network manager. Prior to installing and configuring OpenVPN on my Ubuntu box, I was using Wicd to manage my network connections. Does the Wicd application interfere with the proper operation of NetworkManager or the configurations that are part of configuring the OpenVPN server? 

Does this work with an installation of Ubuntu that has only one NIC? 


I have been trying for a week to make OpenVPN work, and your instructions have gotten me further than any other instructions have, but there still are some gaps in my understanding of exactly how it should look and work when properly configured and running. I will keep trying, but any help you could provide answering those questions would be a big help - Thanks

---

### Post by Zenguy on 2011-10-22
SOMDdan,

The guide should work in the very specific configuration that I've listed. When you add variable like desktop vs. server installation, then there are no guarantees. It introduces more variables to the mix. I think it should work, but there might be some issue with some version of some file.

Regarding your ifconfig question, something might be wrong. On my server when I ifconfig, only the br0 has an IPv4 address. The eth0 and tap0 do not.

Wicd is another variable. I don't know how it handles VPN clients. If it has no provision for them, then you will need to find a guide that tells you how to install a VPN client without network manager. You will have to ensure that all settings match the default client settings that I show in the guide.

The guide was written and is running on a machine that has only one NIC.

A few more thoughts for you...

1) If you are setting up virtual machines, then setup a server instead of a desktop. It only takes a few minutes and will remove any doubt about the configuration.

2) Make sure your test machine connecting into the VPN is on a different network. (i.e. ifconfig reports different 192.168.x.x for the server and client before the connection is made.)

3) Check the server and client VPN logs. Let me know if you get specific error messages.

I'm traveling this weekend, so it may be difficult for me to respond timely. Good luck. I know how frustrating this can be.

---

### Post by SOMDdan on 2011-10-22
> **SOMDdan said:**
> ZENGUY: your PDF instructions were admittedly better than all the others I have found so far, including the official guide from OpenVPN, as well as the Ubuntu guide, but................there are still some significant  questions that have yet to be answered.   My first attempt at using your guide was a failure, and I hope you can help me clear them up. Here they are:

Does your guide work for a standard-issue distribution of Ubuntu desktop, or does it have to specifically be Ubuntu *Server? *(I have been trying to install OpenVPN on a newly installed Ubuntu 10.4 Desktop virtual Machine running on VMWare workstation, with a bridged interface to the host)
When I run an ***ifconfig ***command after the VPN server is running (or at least I assume it is), I get listings for eth0, br0, and tap0. Both eth0 and br0 have ethernet addresses on the same subnet, but they are different (192.168.102.36 and 192.168.102.38, respectively), and tap0 does not have an address. Is this what I am supposed to be seeing?

A part of your instruction involves installing network manager. Prior to installing and configuring OpenVPN on my Ubuntu box, I was using Wicd to manage my network connections. Does the Wicd application interfere with the proper operation of NetworkManager or the configurations that are part of configuring the OpenVPN server? 

Does this work with an installation of Ubuntu that has only one NIC? 


I have been trying for a week to make OpenVPN work, and your instructions have gotten me further than any other instructions have, but there still are some gaps in my understanding of exactly how it should look and work when properly configured and running. I will keep trying, but any help you could provide answering those questions would be a big help - Thanks


OK, I think I got it figured out now. I had a couple of typos that were screwing me up.:D

---

### Post by KRL_UK on 2012-01-05
Great guide thank you,

I have been trying to get openvpn server running on my Ubuntu Desktop 11.04.  I am having a problem with bridging the network interface.  When I try to bridge br0 to wlan0 I get an error saying:

 * Reconfiguring network interfaces...                                                                                                                        can't add wlan0 to bridge br0: Operation not supported

I am guessing this is because Ubuntu does not like trying to bridge the wlan interface.  Does anyone know how to get round this as using eth0 is not an option for me at the moment?

---

### Post by Zenguy on 2012-01-05
> **KRL_UK said:**
> Great guide thank you,

I have been trying to get openvpn server running on my Ubuntu Desktop 11.04.  I am having a problem with bridging the network interface.  When I try to bridge br0 to wlan0 I get an error saying:

 * Reconfiguring network interfaces...                                                                                                                        can't add wlan0 to bridge br0: Operation not supported

I am guessing this is because Ubuntu does not like trying to bridge the wlan interface.  Does anyone know how to get round this as using eth0 is not an option for me at the moment?

I don't know if there is a way to bridge to a wireless interface, but a quick, cheap and easy way to bypass this obstacle would be to purchase a network gaming adapter or a network powerline adapter. It will plug into your existing wired Ethernet port and allow you to configure as a wired connection.

---

### Post by kevdog on 2012-01-26
Not to resurrect a dead thread, however I was setting up the server on 10.10.

Within your up.sh and down.sh scripts:
/usr/sbin/brctl addif $BR $DEV

The brctl executable is located at /sbin/brctl for me, not /usr/sbin.  I'm sure however this may vary depending on people's installation.

---

### Post by c-m on 2012-01-26
Can anyone help me. 

I followed the server side instructions of this guide to the letter.

I can make a successful vpn connection, but I can't now access my router page at 192.168.0.1 from my server (192.168.0.100)

---

### Post by Zenguy on 2012-01-26
c-m,

I suspect that you are pretty close to being successful. Here are some things to check (*in no particular order*):

[LIST=1]
[*]Can you ping your router or your server? If not, then the VPN connection has not been made correctly.

[*]You can also check to make sure your connection looks good. Establish a VPN connection and enter a terminal and type: **ifconfig**       (You should see your tap0 device and it's IP address should be on your network's subnet 192.168.0.x.)

[*]Check your client and server VPN logs. You will probably find a clue there.

[*]Double check all your settings and configuration files. Make sure you didn't turn on any extra features, other than the ones listed in the guide.

[*]Your router isn't doing any fancy security that would prevent you from accessing it from any machine on your network, right?

[*]What error are you getting when the router tries to resolve? Timeout? Is there another webserver on your LAN that is closed to the internet, but you can try to hit from your VPN connection?

[*]The network that you are connecting from is a different subnet from the one you are VPNing to, right? You may have problems if they are both on 192.168.0.x, even if they have different external IP addresses.
[/LIST]

Let us know if you find the solution.

---

### Post by c-m on 2012-01-27
My VPN server is my ubuntu box at 192.168.0.100

My router is at 192.168.0.1

My client is my android mobile via HSDPA. When connected it is receiving the ip 192.168.0.200

When trying to access the router in the web browser of any device it times out. 

If i ping the router I get "destination host unreachable"

Yet I can access the internet just fine on both server and client

The android device although connected to the VPN doesn't seem to be using the hosts connection (though i've read that some additional commands in the host server config are needed for that)

I also run NXserver of ssh - the changes i've made to setup VPN seem to have made the nxclient on my windows machine disconnect more frequently.

Just ran ifconfig on the host. I can see the following adapters:

br0
eth1 (hmm i selected eth0 in config)
lo
tap0
vmnet1
vmnet8

---

### Post by Zenguy on 2012-01-27
c-m,

As a quick test, can you try to connect to the VPN from an Ubuntu client? Preferably 10.04. Since you are using an Android client it is possible that some something is not configured correctly.

What indications do you have that the VPN connection is successful? From your description, it sounds like it is not. The Android device might still be using its own Internet gateway, instead of the VPN to access the Internet. If it was using the VPN gateway, you would be able to ping other devices on the LAN.

Run ifconfig on the client to see the results.

I suspect that the server VPN logs will show you the failed connection. Check the timestamps to see if you can locate the failure. I don't know much about Android, but there should be a client log somewhere on the device.

This is an obvious point, but there are a few VPN protocols. Make sure that you are using an OpenVPN client. If it is using one of the other VPN protocols then it won't work.

---

### Post by c-m on 2012-01-27
Thanks, but it's on the server that i can't connect to my router 192.168.0.1

I'm not concerned about the android client just yet, just want to make sure that I can access my router from my server machine, which is running 11.11

I will have another ubuntu client to test with next week, but right now, just want to make sure the server is set up correctly.

Where do i find the server side logs?

Thanks

---

### Post by Zenguy on 2012-01-27
c-m,

Ok, I think that I understand your situation now.

It is possible that 11.11 has a different setup from 10.04. You will probably have to search for a tutorial that specifically addresses how to install OpenVPN on 11.11.

I designed the guide around 10.04, because it is the long term release. I plan on revising it when the next long term release comes out, 12.04 is released. I figure that most people will probably use an LTS for their servers.

Kevdog has a comment above that discusses a change in 10.10 that might impact you.

Look in the Troubleshooting section of the guide. It will show you how to enable server side logging.

---

### Post by c-m on 2012-01-27
```
carl@mine ~ $ ifconfig
br0       Link encap:Ethernet  HWaddr 52:b5:7d:44:2a:2c  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::8865:2eff:fec2:b991/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28 (28.0 B)  TX bytes:34635 (34.6 KB)

eth1      Link encap:Ethernet  HWaddr 00:22:4d:54:86:c1  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:4dff:fe54:86c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13599 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4906449 (4.9 MB)  TX bytes:1646911 (1.6 MB)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40881 (40.8 KB)  TX bytes:40881 (40.8 KB)

tap0      Link encap:Ethernet  HWaddr 52:b5:7d:44:2a:2c  
          inet6 addr: fe80::50b5:7dff:fe44:2a2c/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1934 (1.9 KB)  TX bytes:35239 (35.2 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.186.1  Bcast:172.16.186.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.110.1  Bcast:192.168.110.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

Server is 192.168.100
Gateway is 192.168.1

On the server pinging 192.168.1 fails.

It must be something to do with the bridge, as before i did that, I could ping from the server, to the gateway.

Despite not being able to ping the gateway, the server still has full internet access.

---

### Post by kevdog on 2012-01-27
My ifconfig statement is slightly different than yours.  

I'm not getting any IP address assigned on eth0 (I think this is the correct outcome)  I'm running 10.0.1.199 as my server address however the actual IP address isn't really that important.  You should be able to access your router and within the clients table you should see the local ip address of your router actually listed:
```

br0       Link encap:Ethernet  HWaddr 00:15:60:9c:06:ec  
          inet addr:10.0.1.199  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::215:60ff:fe9c:6ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8946767 (8.9 MB)  TX bytes:2855486 (2.8 MB)

eth0      Link encap:Ethernet  HWaddr 00:15:60:9c:06:ec  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9391994 (9.3 MB)  TX bytes:2909188 (2.9 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10814 (10.8 KB)  TX bytes:10814 (10.8 KB)


```

---

### Post by Zenguy on 2012-01-28
c-m,

I'm sorry, but I don't have much to offer you in the form of a solution.

I think that you are right about the bridge. In my ifconfig br0 has a fair amount of traffic on RX and TX, but yours appears to be low.

On my system the eth0 device does **not** have an assigned inet addr. (It does an inet6 addr though.). So this implies that something was set up incorrectly. The TX/RX rate is roughly the same as for my br0 interface. My system also shows an "Interrupt"


eth0      Link encap:Ethernet  HWaddr 12:34:56:78:90:12  
          inet6 addr: 1111:2222:3333:4444:5555/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13132618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12410527 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3746613941 (3.7 GB)  TX bytes:2929200526 (2.9 GB)
          Interrupt:18 

I'm not really a VPN expert, so at this point it will come down to some good web searching.

---

### Post by kenji_08 on 2012-01-29
I found this tutorial very helpful. It is easy to follow and well explained. Our company is planning to build our own openvpn server as a failover . Because we are not satisfied to the service of our VPN provider though they happens to be the leading provider in the phillipines. I was using Ubuntu for almost 2 years now. Because of intermittent and slow connection speed.  so I somehow understand the flow of your wonderful procedure. great help.. thanks

---

### Post by c-m on 2012-01-29
Got my bridge sorted now.

The server can access the router and can ping other computers on the network.

Setup an ubuntu client on my netbook following the guide. It connects ok, but can't access the internet or ping my network.

In my server config, i've got:

push "route 192.168.0.1 255.255.255.0"

That is my gateway, should that be the server (192.168.0.100) instead?


EDIT: The client can now access the internet via vpn. On restart it seems network manager is no longer managing the server connection. I had to manually set the DNS (i used googles's) in /etc/resolv.conf

The only remaining issue now, is that the client can't access samba shares, but that's a samba issue i think.

---

### Post by Zenguy on 2012-01-29
> **c-m said:**
> 

In my server config, i've got:

push "route 192.168.0.1 255.255.255.0"

That is my gateway, should that be the server (192.168.0.100) instead?

You have it correct. It should be pointed to your router, *not* the server that is running OpenVPN.

It sounds like something is not set up correctly on the client. What version of Ubuntu are you using on the client? Double check all the settings, especially that the ta.key and its direction are set correctly. 

On the client, OpenVPN will send its log messages to /var/log/syslog. There will probably be a good clue in there.

If you can't get it working, send me an ifconfig from the client when it has a VPN connection.

What did you do to fix the bridge?

---

### Post by c-m on 2012-01-29
For the bridge i just followed a few different guides and did a bit of trial and error.

The ifconfig of the netbook (11.10), is:

```
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:9d:25:85  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:23:08:78:f2:ad  
          inet addr:192.168.100.199  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8ff:fe78:f2ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27194 errors:0 dropped:0 overruns:0 frame:1580427
          TX packets:27367 errors:50 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20145367 (20.1 MB)  TX bytes:5678500 (5.6 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53525 (53.5 KB)  TX bytes:53525 (53.5 KB)

tap0      Link encap:Ethernet  HWaddr 12:bd:21:34:57:93  
          inet addr:192.168.0.200  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::10bd:21ff:fe34:5793/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:3182 (3.1 KB)  TX bytes:11600 (11.6 KB)

  
```

as you can see tap0 is given a an ip on my home network, so that appears ok.

---

### Post by Zenguy on 2012-01-29
The ifconfig looks good.

It is probably something in your server.conf. The fact that the client is not retrieving DNS entries is a red flag. You shouldn't have to set these manually.

It sounds like one of the changes that you made in order to get the server working, broke the ability of the client to traffic trough the VPN.

Was there any info in the server log?

---

### Post by oct on 2012-02-08
Hello,

I also have used your guide, in combination with official OpenVPN HOWTO, to create a VPN between two Ubuntu servers. However, I'm a little concerned about security. I have tried to copy the entire easy-rsa/keys folder and the client.conf file to another Ubuntu computer and was able to start the VPN connection. The original VPN client went down.

Does anybody know what's the best way to prevent private keys copy to another system? I have tried encfs and openssl commands, but I can't use them as we start the OpenVPN client as a server.

Thanks

Oct

---

### Post by SeijiSensei on 2012-02-08
> **oct said:**
> Does anybody know what's the best way to prevent private keys copy to another system? I have tried encfs and openssl commands, but I can't use them as we start the OpenVPN client as a server.

Protect them from whom exactly?  Anyone with root privileges can copy those files, so the question you ask is really a question about access to the machine itself.  If there are people who have physical access to the machine, and know how to reboot the machine into "recovery mode," all your keys can be copied.  If someone has root or sudo privileges on the machine, that person can walk off with all the keys.  If you can't trust the people who have root on the machine, then all bets are off in terms of security.

I make sure all the keys have 600 permissions so they are only readable by the root user.  If you place the keys in a directory like I do (/etc/openvpn/keys), then that directory needs to have 0700 permissions.  All the keys and associated directories should be owned by root:root.

---

### Post by oct on 2012-02-09
Well, I was thinking in the case a "bad" user picks the client hard disk, and tries to read the information from another computer, via USB or installing it on the other computer. I'd like to prevent this user to copy the keys so that he/she can use them on another machine.

I'm working on a project where we will deploy several computers with OpenVPN connection to a central server and I want to be sure nobody else can access that server.

Thanks

Oct

---

### Post by SeijiSensei on 2012-02-09
Then make sure it's in a locked facility and don't give anyone sudo or root privileges but yourself.  Also apply the restricted permissions on the key files I described above. 

Knowledgeable users with physical access can do anything once they gain root.  Rebooting into "recovery mode" is one such method, so you need to insure no one can sit at the keyboard but you.  Adding a BIOS password can help protect against this method of attack as can locking the server case.  Nearly any full-fledged server will come with a case lock.

As for enforcing client security, it appears that OpenVPN has some mechanisms for permitting connections only from specified MAC addresses.  That would provide some protection against stealing the keys and connecting from somewhere else.  Also you can restrict inbound connections so they can come only from specified client IP addresses.  I do that via iptables, but there are also mechanisms to restrict connections by IP in the [OpenVPN configuration]("http://openvpn.net/index.php/open-source/documentation/manuals/openvpn-22.html") as well.

---

### Post by Zenguy on 2012-02-09
I'm not an expert on encryption strategies, but it looks like that is the proper solution to your problem. If you can do full disk encryption via truecrypt or encrypt the sensitive folder using another EncFS, then even if someone pulls the drive they can't access the data.

This problem may be beyond the scope of this thread at this point, since it deals more with securing data on the drive rather than VPN issues.

---

### Post by shreepads on 2012-04-09
Just wanted to say thanks for this guide... Not doing anything complicated, just connecting to a public VPN server but your PDF was helpful....

Steps (in case anyone else looking)

a. Install openvpn, bridge-utils (probably not required) and network-manager-openvpn-gnome in admin

b. In ordinary user mode, register for VPN service and download .ovpn file, save securely. At this point you could use the 'Import' feature in the VPN connections tab but that doesn't work in 10.04 (at least with the file I had)

c. Open the file (say client.ovpn) and extract the following sections and save as separate files:
[INDENT]
File 1: ca.cert: All the text between the <ca> </ca> tags i.e. somthing like this

```
-----BEGIN CERTIFICATE-----
MIIBszCCARygAwIBAgIETYOipDANBgkqhkiG9w0BAQUFADAVMRMwEQYDVQQDEwpP
...
rxjDjIJbAQ==
-----END CERTIFICATE-----
```

File 2: user.crt: All the test between the <cert> </cert> tags i.e.
```

-----BEGIN CERTIFICATE-----
MIIB1TCCAT6gAwIBAgIDBS88MA0GCSqGSIb3DQEBBQUAMBUxEzARBgNVBAMTCk9w
...
bsjnopP4G0idNeJ5TY60gK9FqCkcUY7Qd6ggLvLXh/KvtExRCfhAO5w=
-----END CERTIFICATE-----
```

File 3: private.key: All the text between the <key> </key> tags i.e.

```
-----BEGIN RSA PRIVATE KEY-----
MIICXQIBAAKBgQDHxMtnxqpJsy/eLWud03uk6V+Ot73YzOTmR/mUpq1TmdQrAHgn
...
bW5+zawHMOoH0BMzLy9TlP/bIAarrynqRcffc+k8Rzcl
-----END RSA PRIVATE KEY-----
```

File 4: tlsauth.key: All the text between the <tls-auth> </tls-auth> tags i.e.

```
-----BEGIN OpenVPN Static key V1-----
4f65292e639c83574026ab790f67257b
...
521021b9e6d45cdee7bfd22fce270a49
-----END OpenVPN Static key V1-----
```
[/INDENT]
d. Use these files while setting up the VPN connection in Network Manager as described in pgs 8, 9, 10 of the guide.

e. Look for the following bits in the .ovpn file (or may be given in documentation from the VPN provider) and setup accordingly

```
remote us.shieldexchange.com 1194 udp  # Map to Gateway, Port & 'Use a TCP Connection' field (Advanced... in this case, no)
dev tun
dev-type tun       # Map to 'Use a TAP device' field in Advanced... (in this case, no)
key-direction 1   # Map to Key Direction in Advanced -> TLS Authentication along with the tlsauth.key
```

e. In addition to the above fields make sure you use the Cipher and Hash function (under Advanced -> Security) prescribed by the VPN provider. In my case it's BF-CBC (Blowfish-CBC) and SHA1.

---

### Post by wlraider70 on 2012-05-08
It appears that my openvpn wont open.

server@philo:/etc/openvpn$ sudo sockstat
USER     PROCESS              PID      PROTO  SOURCE ADDRESS            FOREIGN ADDRESS           STATE
avahi    avahi-daemon         724      udp4   *:5353                    *:*                       CLOSED
root     openvpn              8053     udp4   *:1194                    *:*                       CLOSED
(clipped)


I'm not entirely sure where my error is, but this seems like a good place to start.

---

### Post by kevdog on 2012-05-10
This almost sounds like a firewall issue.

---

### Post by ibrahim.k on 2012-05-23
Hi,
Can I connect to this VPN Via my Ipad? 
thnx

---

### Post by Zenguy on 2012-06-05
> **ibrahim.k said:**
> Hi,
Can I connect to this VPN Via my Ipad? 
thnx

Yes. I believe there are OpenVPN clients for the iPad.

---

### Post by Spartan117413 on 2012-06-23
Zenguy I just want to say thanks for the excellent guide. I've been working steadily for about three days on ironing out the issues for creating a bridged VPN server on Precise. You have my appreciation for cranking out this guide.

---

### Post by kashif_max on 2012-07-08
It is indeed very detailed guide.

Thanks for the guide...

One question. Can I allow only specific vpn user (ip) to access only specific servers/machines.

Is this rule is correct ?
```
iptables -A INPUT/OUTPUT -p tcp -s ClientIP -d ServerIP --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
```

---

### Post by shreepads on 2012-07-10
@Zenguy

Can we have an alternate to using the Network Manager OpenVPN plug-in on the Client side? 

That has a number of limitations which I've started to find out
- A number of OpenVPN params can't be configured
- There is an issue with ping-restart that causes it to drop the connection

The native OpenVPN option seems better...

---

### Post by heiNey on 2013-01-30
the guide states that ALL network traffic will go through the vpn.  is it possible to modify it so that only specified computers go through the vpn?  if so, which part would i have to change?  i can't seem to figure it out.

---

