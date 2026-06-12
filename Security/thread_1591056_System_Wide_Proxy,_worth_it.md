---
title: "System Wide Proxy, worth it?"
date: 2010-10-08
forum: Security
---

### Post by RunForIt222 on 2010-10-08
Well I finally took the plunge and installed a Ubuntu partition on my HDD last week.

While messing around I noticed that I could change the entire systems proxy settings. 

So let's say I were to change my system proxy to use an SSH connection, would this be as effective as setting firefox's proxy to the SSH server?

Would it provide the same SSH tunnel for all of my network traffic as firefox does for it's traffic when proxied?

---

### Post by scrooge_74 on 2010-10-09
I think you answer the question yourself.

Anyway, why you need to use proxies? Are you hidding just like me  ;) ?

---

### Post by RunForIt222 on 2010-10-09
I use the SSH proxy to secure data on Open wifi networks.

I guess my question was, if I do a system wide proxy, will it work the same as setting up firefox proxied, but for the whole system?

---

### Post by scrooge_74 on 2010-10-09
That is the idea, cant test it today only proxy I have available is outside my network and then the only ssh server I have is inside my network. If I was out on the street I could try it

---

### Post by wacky_sung on 2010-10-09
Actually i got confuse over the statement of proxy and SSH.SSH provide a layer of encryption acting as a sock proxy for tunneling in the browser.I will still recommended you to use SSH along with squid and privoxy which will boost your browser experience with speed,ads blocking and security. 

Sad to say i have not be able to get my own SSH server to tunnel through my browser.

---

### Post by SeijiSensei on 2010-10-09
> **RunForIt222 said:**
> I use the SSH proxy to secure data on Open wifi networks.

What's at the other end of the proxy when you're using it to secure data on open wifi networks?  Are you connecting to another machine you own?  If that's the case, you're probably better off using OpenVPN and setting the remote end of your VPN as your default gateway.

---

### Post by RunForIt222 on 2010-10-10
> **SeijiSensei said:**
> What's at the other end of the proxy when you're using it to secure data on open wifi networks?  Are you connecting to another machine you own?  If that's the case, you're probably better off using OpenVPN and setting the remote end of your VPN as your default gateway.

Yea I'm using it to connect to my home PC.

Just with some testing while on my Home network, (using EtherApe to monitor) my system wide SSH tunnel was routing all of my traffic through the SSH server except for Evolution, which appeared to be doing it's own thing. I think switching to Thunderbird for email should fix that though.

As far as VPN, whats the best way to go about it, and/or how do I set it up with SSH?

---

### Post by SeijiSensei on 2010-10-10
I'd use OpenVPN (in the repositories) with the machine at home configured as a server and the laptop configured as a client.  The simplest solution is to use a shared key which you can generate with OpenVPN and copy to both machines. Once the tunnel is set up, OpenVPN can run a script that would change your laptop's routing table so that all traffic goes through the tunnel.

Here's the OpenVPN HOWTO page: [http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html).  However I'd suggest you start with the [Static Key Mini HOWTO](http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html).

One nice thing about OpenVPN is that it uses SSL and can connect through routers.  So even if you were in a cafe, you could still set up the tunnel.

---

### Post by RunForIt222 on 2010-10-10
> **SeijiSensei said:**
> I'd use OpenVPN (in the repositories) with the machine at home configured as a server and the laptop configured as a client.  The simplest solution is to use a shared key which you can generate with OpenVPN and copy to both machines. Once the tunnel is set up, OpenVPN can run a script that would change your laptop's routing table so that all traffic goes through the tunnel.

Here's the OpenVPN HOWTO page: [http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html).  However I'd suggest you start with the [Static Key Mini HOWTO](http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html).

One nice thing about OpenVPN is that it uses SSL and can connect through routers.  So even if you were in a cafe, you could still set up the tunnel.

So using OpenVPN is at least as secure as SSH?

*Also, would OpenVPN still allow me to bypassfilters and hide my net traffic from people sniffing?

---

### Post by SeijiSensei on 2010-10-10
It uses SSL with a variety of encryption ciphers; Bruce Schneier's [Blowfish]("http://www.schneier.com/blowfish.html") is the default.  There are about 40 ciphers supported ("openvpn --show-ciphers" for a list).  I use AES256 for tunnels that are governed by US Federal law (a health center I work with as an example).  Otherwise I use Blowfish.

---

### Post by BkkBonanza on 2010-10-10
When you set the system proxy you still need to set Firefox to use the system proxy otherwise it goes direct or uses whatever setting it has currently. Also the system proxy only works for apps that are written to use it - usually just gnome/gui apps. It won't affect command line apps and apps that don't have proxy support built in.

For commandline tools you usually have to set environment variables or use tsocks to emulate socks support if needed.

---

### Post by RunForIt222 on 2010-10-10
> **BkkBonanza said:**
> When you set the system proxy you still need to set Firefox to use the system proxy otherwise it goes direct or uses whatever setting it has currently. Also the system proxy only works for apps that are written to use it - usually just gnome/gui apps. It won't affect command line apps and apps that don't have proxy support built in.

For commandline tools you usually have to set environment variables or use tsocks to emulate socks support if needed.

Ahh ok thanks... I usually turn my GUI apps on to System Proxy settings for the ones that support it. Email and Chrome/Firefox were the things I was mainly concerned about.

---

### Post by bodhi.zazen on 2010-10-10
> **RunForIt222 said:**
> Well I finally took the plunge and installed a Ubuntu partition on my HDD last week.

While messing around I noticed that I could change the entire systems proxy settings. 

So let's say I were to change my system proxy to use an SSH connection, would this be as effective as setting firefox's proxy to the SSH server?

Would it provide the same SSH tunnel for all of my network traffic as firefox does for it's traffic when proxied?

I saw your post yesterday, but did not have time to respond.

Your question is quite broad and I am not sure what you are wanting and what you do (or do not) understand about setting a proxy.

Normally, when you use Firefox to browse "the internet", your computer uses a random high port to connect to port 80 on the server (or port 443 if it is https).

When you set a proxy, you tell Firefox to use a proxy server, it makes the request to the proxy and the proxy makes the request to the internet.

At any rate, setting the "System proxy" merely sets an environmental variable, "http_proxy". Changing this proxy does not make firefox, or any other client, actually use the proxy nor does it establish a proxy.

To make firefox use the system proxy you still need to configure firefox (and select use system proxy rather then enter a proxy manually).

In order to "force" your clients to use the proxy you need to either use iptables or configure what is called a "transparent proxy".

You would still, of course, need to set up a proxy.

And of course this covers only web servers, ie http and https. It does not cover ftp, ssh, VNC, etc, etc.

Hope that information helps, but I am guessing you are not fully understanding what a proxy is, what protocols you want to proxy, nor what setting a system proxy means. If you do not understand these things, you are unlikely to get the results you seek.

For what you are asking I think you want a VPN. Take a look at OpenVPN.

---

### Post by RunForIt222 on 2010-10-10
> **bodhi.zazen said:**
> I saw your post yesterday, but did not have time to respond.

Your question is quite broad and I am not sure what you are wanting and what you do (or do not) understand about setting a proxy.

Normally, when you use Firefox to browse "the internet", your computer uses a random high port to connect to port 80 on the server (or port 443 if it is https).

When you set a proxy, you tell Firefox to use a proxy server, it makes the request to the proxy and the proxy makes the request to the internet.

At any rate, setting the "System proxy" merely sets an environmental variable, "http_proxy". Changing this proxy does not make firefox, or any other client, actually use the proxy nor does it establish a proxy.

To make firefox use the system proxy you still need to configure firefox (and select use system proxy rather then enter a proxy manually).

In order to "force" your clients to use the proxy you need to either use iptables or configure what is called a "transparent proxy".

You would still, of course, need to set up a proxy.

And of course this covers only web servers, ie http and https. It does not cover ftp, ssh, VNC, etc, etc.

Hope that information helps, but I am guessing you are not fully understanding what a proxy is, what protocols you want to proxy, nor what setting a system proxy means. If you do not understand these things, you are unlikely to get the results you seek.

For what you are asking I think you want a VPN. Take a look at OpenVPN.

This ans the other responses have answered my question perfectly, Thanks!

---

