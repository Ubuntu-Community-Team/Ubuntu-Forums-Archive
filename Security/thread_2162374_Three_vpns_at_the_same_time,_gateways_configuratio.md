---
title: "Three vpns at the same time, gateways configuration question"
date: 2013-07-14
forum: Security
---

### Post by WhiteHatGuy on 2013-07-14
Hi

I was able to connect three vpns. The only thing I need is to configure properly the gateways. I am getting this message error or warning when I connect them. Even then I am able to connect to websites like google or any other. But I am not able to see videos on youtube because I dont have the vpns properly configured I suppose. So I though that if a fix the gateways, I could be able to watch youtube videos without problems. Right now I dont care if they are free vpns or paid. I just want to make them work together with no warnings.

Sun Jul 14 07:06:01 2013 NOTE: unable to redirect default gateway -- Cannot read current default gateway from system
Sun Jul 14 07:06:01 2013 /sbin/route add -net 10.9.0.1 netmask 255.255.255.255 gw 10.9.1.25
Sun Jul 14 07:06:01 2013 Initialization Sequence Completed

I connect to the vpns in this order:

First vpn, it uses vpnc (cisco) (This one connects with no errors at all)
Second vpn uses openvpn (I get the message error above)
Third vpn uses openvpn. (I get the message error above)

The vpns work fine without any errors or warnings if I use them separtly. The warning appears only when I use multiple vpns.
I know I could use just one vpn. But I am doing this just for educational purposes. And I like to learn about this stuff. I am taking some courses of cisco ccna, I already finish module 1. But we havent seen anything about vpns configuration. That will be in ccna security, and I havent gone that far.

I know I have to set properly the gateways. I know what is a gateway and how to configure it. But only in routers cisco and xp. I dont know where to start on Lubuntu 13.04. I am kinda confused. What ip's numbers should I look for? What do I have to do with them? Where should I put them? In the ovpn file of openvpn? Or via Lubuntu terminal?

Thanks

---

