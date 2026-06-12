---
title: "OpenVPN speed problems"
date: 2012-07-09
forum: Server Platforms
---

### Post by jwright8 on 2012-07-09
I have one OpenVPN client connected to my network from another network that I'm testing at the moment.  I'm mapping a network drive, then trying to transfer from a network drive (on the LAN that the OpenVPN server is on) to the client on the remote network's C:\ to test speed.

Server speedtest.net results:
ping 15ms
download speed 24.38 mbps
upload speed 17.04 mbps

Client speedtest.net results:
ping 8 ms
download speed 35.60 mbps
upload speed 5.44 mpbs

However, when I start the transfer, it starts at only around 1.0 mbps and falls in the first 45 seconds or so to anywhere from 280 to 320 kb/s and stays that way.  

This is my server.conf:
```

port 5556
proto udp
dev tap0
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh /etc/openvpn/dh1024.pem
ifconfig-pool-persist ipp.txt
server-bridge 10.1.10.70 255.255.255.0 10.1.10.150 10.1.10.165
push "route 10.1.10.1 255.255.255.0"
push "dhcp-option DNS 10.1.10.1"
client-to-client
keepalive 10 120
tls-auth ta.key 0 
user nobody
group nogroup
persist-key
persist-tun
status /var/log/openvpn-status.log 5
status-version 2
log-append /var/log/openvpn.log
verb 4

```Thanks in advance for any help/advice!  I know it might not be exactly suited to this site to ask about a direct problem with OpenVPN alone, but I feel I typically get more thorough assistance and help here.

EDIT: 

It might also be worth noting that my setup is:

Remote client -> Internet -> Router with port 5556 forwarded to the Linux box IP -> eth1 Linux box -> eth0 Linux Box -> LAN clients

---

### Post by SeijiSensei on 2012-07-09
You must be using SMB/CIFS, yes?  I'd suspect it has more to do with the overhead of the file transfer than any problems with the speed of OpenVPN.  

Do you have a machine running Linux at the remote site that you can see over the tunnel?  If so, what kind of performance do you observe when using something like rsync or scp to transfer files from that box?

If that's not an option, what about testing with something like HTTP or FTP against a server on the remote site?

---

### Post by jwright8 on 2012-07-09
> **SeijiSensei said:**
> You must be using SMB/CIFS, yes?

Yes, I believe I am, if you're referring to simple file/folder/etc. sharing in Windows.  Is there another way that would be more efficient?  


> **SeijiSensei said:**
> 
Do you have a machine running Linux at the remote site that you can see  over the tunnel?  


I'll start testing on the box I have on the remote site this evening.

The general problem here, though, is that all of the activities over the VPN will be using mounting network drives from Windows machine to Windows machine, typically 7 x86 to 7 x86.

Is there something that I'm doing wrong that I shouldn't be in regards to file sharing and mounting the network drives?  By that I mean, is there some alternative I can configure to at least begin to utilize the bandwidth?  I'd honestly be happy with something like 2-3 mb/s, 250-300 kb/s just kills me though.

---

### Post by SeijiSensei on 2012-07-09
> **jwright8 said:**
> Yes, I believe I am, if you're referring to simple file/folder/etc. sharing in Windows.  Is there another way that would be more efficient?

I'll start testing on the box I have on the remote site this evening.

Not really if we're talking about Windows-to-Windows.  However let's see what happens when you try a different protocol.  It's pretty hard to know where the bottlenecks might be without some comparative testing.

If all you want to do is to connect two sites, then I'd go with a static-key implementation as described in this [HOWTO]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html").  Put a Linux box in both locations, set up a static-key tunnel between them, then configure routing on each network to push traffic for the other site through the tunnel.  

Since I keep seeing these configuration files like yours, there must be some widely-read tutorials out there that suggest using all this stuff with bridging, certificates, and the like.  That may make sense when you have a server that supports roaming clients.  For inter-office communications a simple static-key arrangement makes a lot more sense.  I have static connections to client sites, and I can typically get close to wire speed when transferring files using something like scp.

---

### Post by koenn on 2012-07-09
I'll second SeijiSensei in that you should verify if it's an network problem or a cifs problem. 
To do so, you could transfer 1 reasonably big file by, say, ftp or rsync (with an option te get stats), then copy the same file from a windows share, and compare times/speeds
This will show you the difference between protocols, if any.

then you should factor in that transferring 1 big file is more efficient than transferring lots of small files, due to protocol overhead. Windows file sharing has quite a bit of overhead and you're typically dealing with lots of files, directory listings, etc, so the reality will be still far worse than your "1 big file' test. 


For file sharing over slow links, microsoft is now pushing DFS - I take this as a sign that they realize their file sharing (CIFS) doesn't really work well over anything slower than common LAN speeds. 
It works and is probably what you need but I'm not sure they have it on their desktop systems, you might have to get Windows Server 2008 or something for that.

---

### Post by jwright8 on 2012-07-09
> **SeijiSensei said:**
> Not really if we're talking about Windows-to-Windows.  However let's see what happens when you try a different protocol.  It's pretty hard to know where the bottlenecks might be without some comparative testing.

If all you want to do is to connect two sites, then I'd go with a static-key implementation as described in this [HOWTO]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html").  Put a Linux box in both locations, set up a static-key tunnel between them, then configure routing on each network to push traffic for the other site through the tunnel.  

Since I keep seeing these configuration files like yours, there must be some widely-read tutorials out there that suggest using all this stuff with bridging, certificates, and the like.  That may make sense when you have a server that supports roaming clients.  For inter-office communications a simple static-key arrangement makes a lot more sense.  I have static connections to client sites, and I can typically get close to wire speed when transferring files using something like scp.

There is one in particular (I forget the link).  I've admittedly been repeatedly dissuaded from using the tap0 interface, but it seemed like the only option at the time for what I needed, particularly since I also wanted to filter ALL traffic behind that box. 

I had actually looked at the how-to that you referenced at one point, but decided against it since it said that only one-one... I actually want to eventually connect around 4 or 5 remote clients.

Although, curiously, should I be using this in my cfg?

```
ping-timer-rem

```

I keep seeing it a lot, but admittedly I have no idea what it is/does.

> **koenn said:**
> 
For file sharing over slow links, microsoft is now pushing DFS - I take this as a sign that they realize their file sharing (CIFS) doesn't really work well over anything slower than common LAN speeds. 

Thank you for this, I'll be looking into that as well.

Thanks for all the help so far guys!

---

### Post by koenn on 2012-07-09
and +1 on the simple and effictive approach.
I never understood what all that bridging and stuff was about when all you need us a tun device, a key, and maybe an extra route or two if you're doing a LAN-toLAN setup.

---

### Post by jwright8 on 2012-07-09
Well, the bridging was due to my setup.  Everything coming from the router goes into eth1 in my Ubuntu server, then out of eth0 into a switch (which all the LAN clients are connected to).  I did this primarily to use IPTables filtering of traffic in and out.

---

### Post by koenn on 2012-07-09
that's perfectly possible without bridging, but to do it you need to understand how routing works, so you can set up routes through the tunnel. That's also how you'd convert a host-to-host setup like the one Sensei showed to a LAN-to-LAN setup. 


Here are some proof of concept notes:
[http://users.telenet.be/mydotcom/howto/linux/openvpn.htm](http://users.telenet.be/mydotcom/howto/linux/openvpn.htm)
You might want to play with that in VMware or a test environment first.

---

