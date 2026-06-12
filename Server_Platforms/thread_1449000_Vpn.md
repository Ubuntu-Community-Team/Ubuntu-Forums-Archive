---
title: "Vpn"
date: 2010-04-07
forum: Server Platforms
---

### Post by bluedrakonis on 2010-04-07
I have an ubuntu 9.1 system setup with ftp,apache and all that good stuff, but how can i add a vpn to it, and use my  domain name as the way to connect to it over the internet, like i do with ftp?

---

### Post by spynappels on 2010-04-07
Are you asking two separate questions? 

For the VPN you could use OpenVPN to access the server from outside your LAN, but that would not require your domain name except in the config file.

To access your webserver etc from outside your LAN, you would need to set up port-forwarding in your gateway router and forward ports 80 and whatever else to the LAN IP of the server.

If you give us a little more information on what you want to achieve and what your network is like, we can probably give some better answers.

---

### Post by bluedrakonis on 2010-04-07
sorry about that, i was wanting to add VPN to my server so that I could network some of the files on that drive. My goal is to setup a shortcut or something that leads to folder X and have it to where when I update the file on say my lappy it automatically updates it on my server. I had someone else say VPN was the best way to go about doing this.

---

### Post by spynappels on 2010-04-07
OK, this we can do quite simply. I am going to make some assumptions here, so if I am wrong correct me.

OpenVPN will do what you want, and I'll try to help you set it up.

First, you need to install OpenVPN.

```
sudo apt-get install openvpn
```

I suggest you set it up following this how-to:

[http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)

and set it up as a routed VPN.

When you have this set up and working, we can start getting the VPN subnet talking to the server's subnet.

As a general rule, it is probably better to have your home LAN set up with a non-standard subnet such as 192.168.150.x The reason for this is that the 192.168.1.x subnet which is in use by default on many routers can cause problems if your home LAN and the LAN you are connecting from have the same subnet.

More to follow, just have to go for now. The above should keep you going for a while anyway.

---

### Post by spynappels on 2010-04-08
You need to alter your server.conf file to push a static route to VPN clients, telling them that all traffic which is directed at the home LAN (using home LAN IPs) must be routed through the VPN tunnel.
You need to add the following line to your server.conf

```
push "route 192.168.x.0 255.255.255.0" # substitute your home LAN IP subnet here
```

This is where it is important that your home LAN subnet is one that is different to any others you are likely to be connecting from. If your home LAN was 192.168.1.x and you were connecting from another 192.168.1.x LAN, this pushed route would cause big problems as the computer would not know if you were trying to access the local LAN or the LAN routed through the tunnel.

You also need to enable ip forwarding in the server itself.

I found this helpful for that:
[http://ubuntuforums.org/showpost.php?p=9035195&postcount=7](http://ubuntuforums.org/showpost.php?p=9035195&postcount=7)

The last thing you need to do is to Connect your Samba Shares as network drives (in Windows) using the IP address such as \\192.168.x.x\share so when you access the mapped drive from outside your home LAN, it will automatically route the request through the VPN tunnel.

Hope this was helpful, let me know if you have any further problems.

---

### Post by bluedrakonis on 2010-04-08
ill give this a look and let you all know how it goes

---

### Post by bluedrakonis on 2010-04-08
im following that guide and i get down to the part
yum install -y nail and it says no package named nail found

any ideas

---

### Post by doogy2004 on 2010-04-08
> **bluedrakonis said:**
> I have an ubuntu 9.1 system setup with ftp,apache and all that good stuff, but how can i add a vpn to it, and use my  domain name as the way to connect to it over the internet, like i do with ftp?

I use OpenVPN AS, it is easy to install and setup, the client is also easy to get installed and working.

[http://openvpn.net/index.php/access-server/access-server-overview.html](http://openvpn.net/index.php/access-server/access-server-overview.html)

---

### Post by bluedrakonis on 2010-04-23
ok man, that might be easy for you but i got lost right after i got it to install since it didnt ask for me to configure anything

---

### Post by AzharHafiz.com on 2010-04-24
does this help one to remain anonymous on the internet?

---

