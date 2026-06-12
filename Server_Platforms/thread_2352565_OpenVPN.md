---
title: "OpenVPN"
date: 2017-02-13
forum: Server Platforms
---

### Post by sixgunSal on 2017-02-13
I'm not sure I'm in the right place for this, and if it's not let me know where it would go and I'll start it there. I'm still pretty new to Ubuntu and still learning but....This month MAXIMUMPC has an article regarding using OpenVPN to connect securely to the net.  I have a few questions after following all the directions and getting it all installed.
First one is can I use this to connect securely using the same pc I have it installed/setup on?  If so, how do I know I'm connected securely thru the tunnel(?)  These are going to be some pretty newby questions I know.  Do I now use this OpenVPN to sign in with the pc I have connected to this one by wifi?  How about my tablet and phone (both android).  I have a few more but I can wait on them for now - thanks for any help ahead of time.
SgS

---

### Post by bearlake on 2017-02-13
Hi,

There is a few types of VPN services.

Some are for use in public wifi places as to protect you from hackers at that location. ( hotels, coffee shops and so on )

Others are for networks to tunnel your device from device to device.

Here is a few addresses for testing your connection.

[https://ipleak.net/](https://ipleak.net/)

or

[http://dnsleak.com/](http://dnsleak.com/)

---

### Post by wildmanne39 on 2017-02-13
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2017-02-14
Don't believe everything you read... :)

Sit down and think about your usage of the internet. A VPN connection does not raise the security on the internet so much, in my personal opinion. For example, if you are downloading suspicious emails and programs and catch a trojan, you will still be infected. Only the traffic flow is different, the route your traffic takes on the internet. So how did the vpn protect you?

Answering more directly some of your questions...
Whether all traffic goes through the tunnel or not depends on how the openvpn server is set up and which commands it sends to the client (your PC). If you followed tutorial to create the connection, they should have given more info what you will actually achieve with it.
To make all your home devices use vpn tunnel, you need at least one device to be connected to the tunnel (like your PC for example) and also be enabled to do routing of traffic. Then in each other device you have to tell them to use that PC and that tunnel as default gateway. And that PC has to stay powered on 24/7 if you want any device to use it at any time. Only in that case all devices will be using the tunnel. If you want to do that it might be better to think about the option of buying a router that you can connect to the vpn and tell it to use the tunnel for all traffic. Then all devices using this router as their gateway will automatically use the vpn.

Also don't forget that depending on the exact situation, a vpn will almost always introduce latency (delay). That is because instead of the traffic taking the shortest route from your home to the destination, it first goes to the vpn server and then takes the shortest route from there.
Also, does the vpn server limit your traffic total? What if you want to download couple of ubuntu ISOs and then watch your Netflix? Will they allow you unlimited traffic? That is something you have to take into consideration before connecting your whole home to it...

---

### Post by sixgunSal on 2017-02-17
I've been trying for over 2 days to get that *.ovpn file over to my windows 10 partition...no joy so far.   Gave up on it.   I am trying to find a secure way to do online banking.   My bank quit recognizing my tor login and they tell me I have to do it from a normal browser.  I do no downloading of suspicious emails, programs movies, etc. So, thats why I'm trying to set up OpenVPN.  My home PC is on all the time, The MaximumPC tutorial was for setting it up on my home pc but like I said I can not figure out how to move the client* it to my windows 10 side or going another step - getting it on my phone or tablet.  Thanks for your help, this forum has lots of help, I just need to ask the rite questions in search.
SgS

---

### Post by darkod on 2017-02-17
You can get a file from the linux box to windows using WinSCP (freeware) on the windows box. Put the file in your home folder (best), and login using WinSCP and you can copy it.

But you can create the ovpn file on windows itself. The only important thing is to have the correct parameters, it doesn't need to be created on linux. But you will have to download the ca.crt and the client certificate (if you are using such) from the openvpn server, so we go back to the WinSCP story...

---

### Post by SeijiSensei on 2017-02-17
Surely your bank uses SSL and an https:// URL.  OpenVPN isn't any more secure than that.  In fact it, too, uses SSL to create the tunnel.

Unless you **really** trust the upstream VPN provider, you have no reason to think they might not decrypt your traffic as it arrives over the tunnel and capture sensitive information.

I use OpenVPN all the time to connect to my servers in the cloud, but I control both ends of the connection.

---

