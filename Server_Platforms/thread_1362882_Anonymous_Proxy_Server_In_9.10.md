---
title: "Anonymous Proxy Server In 9.10"
date: 2009-12-23
forum: Server Platforms
---

### Post by Evildemon989 on 2009-12-23
I'm looking to get an anonymous proxy server running in 9.10 to mask my IP. I'd like to know what software you recommend, and any other advice that you have to offer. The computer I'm running it on is a 2.4GHz celeron, 512 RAM(Will probably upgrade to 1GB.), integrated Intel GFX(Shouldn't matter), which is running Ubuntu Karmic. Thanks.

---

### Post by msw on 2009-12-23
While this can be done, you need to consider if it is worth it.

If you setup your own proxy server, the IP address of the proxy server will still be known and it does not take a website (or authorities) long to figure this out and trace it back.

If you really want to hide your IP, look at any of the proxy server websites out there that already provide this service and also look into TOR.

---

### Post by kewlrichie on 2009-12-24
You can take a look at this guide (yes I know it's for centos) for referrence on configuring squid only and the rest your going to have to wing it or look it up else where  [http://www.howtoforge.com/anonymous-proxy-using-squid-3-centos-5.x]("http://www.howtoforge.com/anonymous-proxy-using-squid-3-centos-5.x")

---

### Post by BkkBonanza on 2009-12-24
By far the easiest proxy to run is with ssh. Any server that you have ssh access to can be used as a proxy for you and as a free bonus you get an encrypted tunnel too.

On your local machine prompt type, 

ssh -f -D 8080 user@remote_ip_or_name -N

This will setup a SOCKS5 proxy on "remote" at the end of an encrypted tunnel.
Now tell Firefox or whatever program you want to use a SOCKS5 proxy at localhost:8080.

ssh will now proxy your requests out from the remote server and the IP logged will of that server. You can use this for any program, email, skype, torrents etc that can use a SOCKS proxy.

All you need is some remote machine with ssh access. You can get a VPS or rent a ssh proxy account for this purpose for $3-4/mo. Google that or check out Santrex.

You can install gstm (Gnome Secure Tunnel Manager) using Synaptics if you want a gui interface to this setup.

---

### Post by msw on 2009-12-24
> **kewlrichie said:**
> You can take a look at this guide (yes I know it's for centos) for referrence on configuring squid only and the rest your going to have to wing it or look it up else where  [http://www.howtoforge.com/anonymous-proxy-using-squid-3-centos-5.x](http://www.howtoforge.com/anonymous-proxy-using-squid-3-centos-5.x)

While this howto does explain how to setup Squid as an anonymous proxy, it is misleading in nature. 

Here is why as this typical home network shows below

user pc 192.168.2.100 >>>squid proxy server 192.168.2.101>>>router 192.168.2.1>>>Internet>24.xxx.xx.xx

With Squid acting as the proxy, the user at 192.168.2.100 will not ever have his LAN (pc) IP revealed to the internet, also,  because the Router is doing NAT his pc IP is also shielded even without the proxy server

The user navigates to say google.com. Google has to know where the request came from and will obtain the public IP of the router which then NAT's back to the proxy server then the user's pc. 

Point is, a proxy server on a home network to "protect your IP" is useless, the public IP is not behind a proxy and thusly no anonymous surfing.

Hope this explains why a home anonymous proxy is not what the OP needs.

---

