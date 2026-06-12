---
title: "Linux VPN"
date: 2007-07-07
forum: Server Platforms
---

### Post by moosetan on 2007-07-07
hey everyone, 

i recently switched from windows to Ubuntu and have a question about personal vpn on Linux. I'm on the road a lot and used personal vpn software with windows such as [hotspot shield]("http://www.anchorfree.com/hotspot-shield/") and [hotspot vpn]("http://www.hotspotvpn.com/"). Are any programs like this available on linux? i have heard of openvpn and i want to try it out and any other software like this, please give recommendations. please give me instructions on how to install. also with openvpn does it start automatically or do i have to connect everytime, how will i know if im connected?



thanks

---

### Post by koenn on 2007-07-07
coming from windows, you were probably using pptp, microsoft's vpn protocol of choice. There's a pptp-implementation for Linux. In Ubuntu 6.06 the package is called pptp-config, i think. 
You can start and stop it manually (make a launcher/menu item/panel icon/...) so you'll know when you're connected. 

openvpn is a SSL-VPN implementation, which your "HotSPot VPN" seems to offer as well. 
It's extremely useful for transparent site-to-site vpn's but can also be used from 1 PC, such as your laptop, although I've never set it up like that. 
your "hotspot shield" doesn't say what technology they're using but I guess it's pptp as they seem to focus on Windows users. 

Personally I'd prefer SSL-VPN because it's an open standard and tunnels trough firewalls easily, where as opening a firewall to allow GRE and pptp to pass through, can be tricky

---

### Post by sfenton on 2008-03-15
There are a couple of services based on Openvpn. They cost some money a month, but worth it. 

surfbouncer.com and I think wetopia.com.  I know that Surfbouncer has a linux configuration. Just use synaptics to load the openvpn plug in for network manager. 

Cheers,

---

### Post by abo_shreek11 on 2008-03-25
Hi

click Applications>>Add/Remove

then search for "KVpnc". Download it.

It's seems its a ubuntu alternative for hotspot free. but i still working 

on who to cinfigure it out 

wish me luck.

---

### Post by andguent on 2008-03-26
I just posted this to another thread, but will post it here too.

Another VPN option is Hamachi from LogMeIn.com. It's free for 16 computers. If you need to connect more than 16 computers together you need to pay for it. I've used OpenVPN and pptp on Linux and Windows, Hamachi is by far the easiest to setup.

[https://secure.logmein.com/products/...pn.asp?lang=en](https://secure.logmein.com/products/...pn.asp?lang=en)


Also, moosetan, can we assume you are planning on configuring your own VPN server? If this is connecting to a company VPN you might be very restricted to what they support.

---

### Post by celliott on 2008-03-26
Hi,

I know this is old, but can anyone shed some light on this thread as i would like to implement VPN myself.


Thanks

---

### Post by sfenton on 2008-07-05
Here is an example, I'm out of town with the family last weekend. We're staying at a hotel where they provide free wifi. 

I see all these people there for a meeting, with their laptops. All surfing the web. I pop up my laptop put my wireless card in monitor mode, and fire up wireshark. 


Any traffic not protected by a VPN or SSL web page, I see. Login's for email. IM transactions, email messages. 

A VPN is just what you need if you have an unsecure wireless connection. It encrypts all the packets from your PC to the internet somewhere. 

If you don't use  free wifi connections, it's probably not useful. 

I'm seen some issues with Linux and these guys, the resolv.conf application tries to rewrite your DNS entries, so DNS may stop working when you load these up. It's an easy fix, but a pain to troubleshoot the first time.

---

