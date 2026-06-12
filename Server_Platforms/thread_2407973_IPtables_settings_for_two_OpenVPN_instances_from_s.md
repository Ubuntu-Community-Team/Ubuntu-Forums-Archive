---
title: "IPtables settings for two OpenVPN instances from same server"
date: 2018-12-11
forum: Server Platforms
---

### Post by vellofrell on 2018-12-11
I am attempting to have two separate OpenVPN client configurations, one for each laptop I route back to my server. I have two tunnels, with a tun0 and tun1 interface as shown below.

```
ifconfig
enp2s0    Link encap:Ethernet  HWaddr 1c:1b:0d:ff:25:ae  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 64 Scope:Link
          inet6 addr: /64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:178251 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177653 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:173172344 (173.1 MB)  TX bytes:175274230 (175.2 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:12500 (12.5 KB)  TX bytes:12500 (12.5 KB)


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:74561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:49039430 (49.0 MB)  TX bytes:114558513 (114.5 MB)


tun1      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:12679 (12.6 KB)  TX bytes:0 (0.0 B)

```

I can see that both of my OpenVPN instances are working correctly, by way of 

sudo systemctl status openvpn@server
and
sudo systemctl status openvpn@server2

...but my problem is I have no connectivity using my tun1 for openvpn@server2. 

Is there a proper iptables configuration I should use for full connectivity into my server with my enp2s0 ethernet interface - while keeping both VPN tunnels tun0 and tun1 working properly with their respective client config files?

---

### Post by darkod on 2018-12-12
Don't use the same IP (10.8.0.1) for both instances. Why would you even try that?

Each instance needs it's own IP. Sort that out and after that we can talk about iptables. But if you know how to set up iptables for tun0, you would know to set it up for tun1 too. It's the same.

The part that is not working for you probably is because of the same IP.

---

### Post by The Cog on 2018-12-12
It's worse than that. It seems that both servers are 10.8.0.2. So what you actually have is two tunnels to the same server 10.8.0.2. And it seems (quite reasonably) from your post that it has chosen to use tun0 to talk to that server. There is no reason why it should choose to use one tunnel on some occasions and the other tunnel on other occasions.

So don't use the same IP address on both servers either.
Using 10.8.0.3 and 10.8.0.4 should be OK. You may also need to worry about what routes the servers are pushing to the client though, so without double-checking, using 10.9.0.1 and 10.9.0.2 for the other tunnel might be safer.

---

### Post by volkswagner on 2018-12-12
I'm confused.

Does the ifconfig output come from server or client (I assume it's the server).

It seems you SHOULD have one server with two (laptop) clients (not two server instances).
The server only needs/should have one TUN interface and one instance of OpenVPN.



Additional Suggestion:
you should change OpenVPN to "[topology subnet]("https://community.openvpn.net/openvpn/wiki/Topology")" as it's more robust
and less confusing by only using one ip address for each client and the server.

---

### Post by vellofrell on 2018-12-12
**Darko & Cog** - I overlooked the part about the two OpenVPN instances tunneling to the same server IP due to still being such a novice with things like private networking. I will try to change them. 

**Volkswagner** - I may still be incorrect, but the reason I set up two separate OpenVPN instances was so I could use separate certificate and key files for each laptop. I want the two laptop clients to not share the same keys and client config files - and became under the impression I would need two separate OpenVPN instances running simultaneously in order for this to work. Please correct me if I'm wrong (I often am!).

---

### Post by darkod on 2018-12-12
You can create different certificate for each client. If that is all you need, then you don't need two OpenVPN server instances.

I am talking about a client certificate, as explained here: [https://help.ubuntu.com/lts/serverguide/openvpn.html.en-GB](https://help.ubuntu.com/lts/serverguide/openvpn.html.en-GB)

PS. Not only that the second instance will need to have unique server IP, it will also need to be listening on different port compared to tun0. Do not forget that the server will be listening on its public IP, so you can't have both tun0 and tun1 on the same port. Change the port in the server conf file.

---

### Post by vellofrell on 2018-12-14
My problem is I often don't know the correct question to ask and end up making my configging attempts more complicated than they need to be. I currently have two of my own client config files for OpenVPN each with unique CA and key files. 

Could someone point me to some suggested reading on how to make my two existing client configs files I have generated work properly with a single OpenVPN instance on my server?

---

### Post by darkod on 2018-12-15
If you want two clients to connect to the same OpenVPN instance, it is very easy.

1. On the OpenVPN server create the client certificate for each client (you probably already have this, it is not instance related I think).
2. In the clients conf files, use the same details for the remote server (the instance it connects to, because they will connect to the same one).
3. Use the same CA cert and server key in both client conf files (again, because they connect to the same instance/server). You do not need unique CA and key files. On the contrary.
4. The only difference in the files is the client cert.

That's it.

---

### Post by vellofrell on 2018-12-26
Darko thanks for the advice on the OpenVPN configs - finally got multiple config files for different devices all working through one single instance of OpenVPN. Free time around Christmas allowed me to tackle this.

<solved> was asking the wrong questions to start - I didn't need multiple instances of OpenVPN, I just needed one instance with multiple config files as seen in step 4 of this tutorial: [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04)
Specifically - starting with new client requests after my CA cert is already in place, as mentioned here:

[LIST]
[*]cd ~/EasyRSA-[COLOR=#E94849]3.0.4[/COLOR]/
[*]./easyrsa gen-req client1 nopass
[/LIST]



 </solved>

---

### Post by wildmanne39 on 2018-12-27
Please use thread tools to mark at the top of the page to nark the thread solved, will you please post what solved your issue so all searchers with the same issue that find this thread may benefit.

Thanks

---

### Post by vellofrell on 2018-12-27
thx for the heads up - done.

---

