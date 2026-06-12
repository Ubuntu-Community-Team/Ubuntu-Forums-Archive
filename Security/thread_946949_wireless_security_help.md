---
title: "wireless security help"
date: 2008-10-13
forum: Security
---

### Post by brandon88tube on 2008-10-13
I wanted to know what I could do to protect myself from others on the network when I connect to wireless access points and hotspots etc. I read you could use some service that does this, but it costs money and I wanted to have a free secure solution. I need this info because I might be traveling in a few weeks where I will be bringing my laptop with me; its also just info thats good to know in general.

---

### Post by pytheas22 on 2008-10-13
The best thing to do is to use a VPN connection, which would encrypt all of your data when it's being transferred.  But you will need credentials to connect to a VPN server somewhere, and you'll need to install a VPN client on your computer (Network Manager has a plugin that works nicely and is easy to install).  I don't know of any free services offering VPN connections, but most universities and many businesses have VPN servers that you could probably use if you're affiliated with them.

If you can't get access to a VPN, you can at least make sure that any routers that you connect to are legitimate, not bogus access points set up by crackers (this is a problem in airports especially).  There's no concrete way to tell what's legitimate, but above all, you should avoid ad-hoc networks.  You can run the command:
```

sudo iwlist scan
```

to see a list of wireless networks in your area.  Avoid any networks whose mode is listed as 'ad-hoc', as in the following example:
```

ath0      Scan completed :
          Cell 01 - Address: 00:12:0E:41:EC:33
                    ESSID:"Canada House"
                    **Mode:Ad-Hoc**
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-50 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
```

Also, avoid networks with names like 'free wifi' or 'public wifi' unless you can verify that they're legitimate.

Otherwise, I can't think of very much else you can do to be safe in these environments.  Your best bet is just to avoid transferring important information over an unencrypted connection under any circumstances.

---

### Post by djhedges on 2008-10-13
I use ssh & squid.  I have a box at home that is running squid.

Open a ssh tunnel for port 3128
```
ssh name@mybox -L 3128:localhost:3128
```

Then just set firefox as if the localhost was running a proxy even though it isn't.  All your proxy traffic will get encrypted and tunneled through the ssh connection.

---

### Post by iponeverything on 2008-10-13
I like practical solutions.

brandon88tube -- Setting up a squid server on home box is pretty strait forward.  When I set it up as a transparent proxy a couple of months ago, it took me under an hour.

apt-get install squid 

then edit /etc/squid/squid.conf .. I don't think that you will need 
the our_networks acl as for the squid box -- you ssh'ed tunneled traffic will appear to be coming from the local host.

```
acl our_networks src 192.168.0.0/24 192.168.1.0/24 172.16.0.0/16
http_access allow our_networks
http_access allow localhost
http_access deny all
icp_access allow all
http_port 3128 transparent

```

---

### Post by brandon88tube on 2008-10-13
I will keep the squid idea in mind, but when I am leaving I won't have a computer at home that will be running, so setting up a squid server wouldn't work here.

---

### Post by kevdog on 2008-10-13
Why the socks proxy?  If you tunnel through ssh, will not the outgoing packets from the connected ssh server, appear to be coming from the ssh server?

One other note --

Tunneling ssh is probably a really good solution.  Its easy to setup and use and very reliable

Option #2
I just set this up the other day and have not tested it, however another solution.  I'm running a Linksys WRT54GL with the dd-wrt firmware vpn solution (You can use other router types besides linksys -- check the dd-wrt home page for compatibility).  Anyway, because the OpenVPN server is contained in the firmware, all I needed to do was to alter the router server setup file, create a corresponding client config file -- and presto -- instant VPN.  Ok it wasn't instant, and it took me hours to tweak the config file, but you get the idea.  Now from either a windows,linux, or MAC Im capable of tunneling all traffic through the VPN back to the home linksys router and out to the internet

I know this solution was mentioned before, however I thought I would throw in some more specifics about how I did it.  A good reference page for this is here:[http://blog.zenone.org/2008/01/openvpn-and-dd-wrt-on-linksys-wrt54gl.html](http://blog.zenone.org/2008/01/openvpn-and-dd-wrt-on-linksys-wrt54gl.html)

I'd like to run some bandwidth testing so I could determine which tunneling method is faster.  Maybe if someone could give me some ideas on this.

---

### Post by brandon88tube on 2008-10-13
The vpn confuses me and I doubt my wireless router would support anything like that. So it seems I am left to just be careful or not use the internet. :(

---

### Post by kevdog on 2008-10-14
Ok, so use ssh -- this is easy to setup, quick, and painless, and its very easy to allow firefox to tunnel all of its connections through the ssh encrypted channel.  Setup of this is not intimidating and you will actually learn a lot -- its fun too -- if you are into such things :)

---

### Post by brandon88tube on 2008-10-15
Well I would have to learn about ssh and just by quickly browsing around I see that if you don't know what you are doing ssh is a big security risk. In my case I would probably fall under that category and have security issues.

Edit: Also is this for a server or something? I don't have a computer to use as a server or anything so if thats what this does its of no use to me.

---

### Post by kevdog on 2008-10-15
That is correct -- in order to tunnel ssh connections you need a second computer somewhere.  Whether this be a computer you own at home, or a university computer, you need a second ssh computer acting as a server.  This would be the same requirement for example if you were running a vpn.

Short of access to a second computer, your only other recourse is to restrict your usage to non-public encrypted networks.  So stop using public wifi cafes.

---

### Post by pytheas22 on 2008-10-15
There are some services that offer free ssh accounts that you can find if you google 'free ssh accounts'.  I've never used them myself and don't know what their motives are for handing out free accounts (so I personally would be reluctant to trust them too far), but if you don't have access to a university server, you could try using one of these services.

I'm not sure where you read that ssh can be a security risk if not set up properly, but as far as I know ssh is probably one of the most secure protocols out there, and not really too hard to configure, especially if all you're doing is using it as a proxy for Firefox.

---

### Post by brian_p on 2008-10-15
> **brandon88tube said:**
> I wanted to know what I could do to protect myself from others on the network when I connect to wireless access points and hotspots etc. I read you could use some service that does this, but it costs money and I wanted to have a free secure solution. I need this info because I might be traveling in a few weeks where I will be bringing my laptop with me; its also just info thats good to know in general.

You do not say it what way you want to protect yourself from others so I'm going to assume you mean prevent outside access to your laptop while on a network. If outgoing data are a concern you might want to be specific about your concerns in that regard.

Furthermore I'm going to assume you are offering no services, which means there is no possible way for connections to be made to your machine. Any requests for a connection are not accepted because there will be nothing listening to process them.

That applies whether you are on a wired or a wireless network. If it's a wireless network it applies whatever the encryption used or even if there is no encryption. It applies whether you are at home or away from home.

So your free, secure course of action is: Pack your laptop, take it with you and use it in the same way as you would at home.

---

### Post by Gamma746 on 2008-10-15
If you want secure browsing, I'd suggest Tor.  ([https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR))  Your browsing might be a bit slower, but neither anyone on your network nor the site you're connecting to will be able to know where you're connecting from.

---

### Post by pytheas22 on 2008-10-15
> If you want secure browsing, I'd suggest Tor. ([https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)) Your browsing might be a bit slower, but neither anyone on your network nor the site you're connecting to will be able to know where you're connecting from.

Does tor actually encrypt data?  I thought it didn't.  Unless the data is encrypted (as with ssh and VPN), people will still be able to sniff your packets in order to read your email, steal credit card numbers, etc.

---

### Post by Gamma746 on 2008-10-15
> **pytheas22 said:**
> Does tor actually encrypt data?  I thought it didn't.  Unless the data is encrypted (as with ssh and VPN), people will still be able to sniff your packets in order to read your email, steal credit card numbers, etc.

It's encrypted from the your computer to the exit node.  Someone could sniff it there, but there's no reason you can't run SSH or HTTPS over Tor.

---

### Post by brandon88tube on 2008-10-15
Thanks everyone for trying to help me out here. I might have to look into these things in the future, but right now without another computer to use as a server I don't have really any options.

---

### Post by kevdog on 2008-10-16
Tor would be the only way if you don't have another computer.  You will find speed or bandwidth to be a limiting factor.

---

### Post by update_manager on 2008-10-17
> **iponeverything said:**
> I like practical solutions.

brandon88tube -- Setting up a squid server on home box is pretty strait forward.  When I set it up as a transparent proxy a couple of months ago, it took me under an hour.


You don't really need Squid for this, just SSH.

From the man page:

-D [bind_address:]port
             Specifies a local &#8220;dynamic&#8221; application-level port forwarding. This works by allocating a socket to listen to port on the local side, optionally bound to the specified bind_address.  Whenever a connection is made to this port, the connection is forwarded over the secure channel, and the application protocol is then used to determine where to connect to from the remote machine.  Currently the SOCKS4 and SOCKS5 protocols are supported, and ssh will act as a SOCKS server.


On your local machine:
1. ssh -D 9991 <IP address> -l <username>
2. Point Firefox's SOCKS proxy to 127.0.0.1 port 9991
3. Optionally, you can tunnel DNS (check about:config)

Any application (Thunderbird, some torrent clients) can use this proxy since it uses SOCKS not HTTP/HTTPs.

>  Thanks everyone for trying to help me out here. I might have to look into these things in the future, but right now without another computer to use as a server I don't have really any options.

There are VPNs or SSL tunnels you can purchase/rent access to. I've never used any of them:
[http://www.megaproxy.com/](http://www.megaproxy.com/)
[http://www.surfbouncer.com](http://www.surfbouncer.com)

---

