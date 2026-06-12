---
title: "Searching for a free VPN-Server"
date: 2009-10-14
forum: Security
---

### Post by K. Hendrik on 2009-10-14
Hi,
i need a free VPN-Server to secure my wifi like you can do it with Hotspot Shield in Windows. Does anybody know if such a thing does exist for ubuntu? I don't want to set up my own VPN Server.

---

### Post by CharlesA on 2009-10-14
Quick google returned "OpenVPN"

Check here:

[http://openvpn.net/](http://openvpn.net/)
[http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu](http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu)

The second one is specific to hulu, but it might work.

There is also AlwaysVPN. Check them out here: [http://www.mydigitallife.info/2008/11/11/alwaysvpn-free-us-based-vpn-service-as-hotspotshield-alternative/](http://www.mydigitallife.info/2008/11/11/alwaysvpn-free-us-based-vpn-service-as-hotspotshield-alternative/)

---

### Post by __p1n__ on 2009-10-14
Can your AP run a custom firewall such as openwrt?  You could run a vpn service on the device and put the access point into its own vlan.

---

### Post by K. Hendrik on 2009-10-15
@CharlesA:
I know about OpenVPN, and thats not what i search for i know how to setup a vpn but i search for a existing server in the US.
I looked at AlwaysVPN and its no longer free to use.
@__p1n__:
I think you've got the question wrong I'm just searching for a free to use VPN Server in the US.

---

### Post by HermanAB on 2009-10-15
Just use SSH.

---

### Post by CharlesA on 2009-10-15
> **HermanAB said:**
> Just use SSH.

How would that work? SSH to localhost or what?

Thanks.

---

### Post by HermanAB on 2009-10-15
Configure your WiFi router to allow anything out to the Wild Wild World, but only allow SSH on port 22 TCP in to a server on your LAN.  You don't need to encrypt a connection to the WWW - it is public information anyway and it should use HTTPS when needed, but to your LAN, everything should be encrypted.

---

### Post by scorp123 on 2009-10-15
> **K. Hendrik said:**
>  I think you've got the question wrong I'm just searching for a free to use VPN Server in the US. I think the problem here is "free". Most services are commercial these days.

Picking up Herman's suggestion here: Wouldn't SSH access into the USA be enough? There are several SSH account providers, most of them are not "free" ... but at least they're rather cheap, like 10$ one-time fee. Depends on where you look. So you'd have a SSH account, you'd login into your US SSH server, and for all matters and purposes whatever you do or don't do there would originate from an US IP address. And all of a sudden services such as Hulu, Last.FM, Pandora and many others who lock out us European users are available again .... Been there done that. The wonders of SSH port-forwarding.

**_BUT BEWARE:_** Some SSH providers specifically state that they DO NOT allow port forwarding, proxying and any such activities ... So you'd have to find one that does. Google and reading the terms and conditions are your best bet here.

And yes, they kick+ban you if you try to setup port-forwarding even though it's forbidden ... Happened to me as well :lol:


Another possibility:

Do you have friends or relatives in the USA? Maybe it would be possible for them to setup a SSH or VPN server for you, so you'd be able to access that server remotely? Just an idea.

---

### Post by K. Hendrik on 2010-06-05
Solved with HideIPVPN. 25 free acount giveaway every week.

---

### Post by Castorpoluks on 2010-06-05
I am using Open VPN which have perfect 2048 bit encryption.Also all working fast and i tested him on all computer and mobile platforms. It didn't work only on newest Android mobile software but Open VPN support told that they will soon solve that.
So i think this is the best open source solution for VPN.

---

### Post by ojmc on 2010-06-12
Hi all,

I am using Ubuntu for a year now. I absolutly love it but am not adept at fiddling with stuff in the backround. I just don't have time.

I wasted a aweful amount of time tring to get a free VPN and later when that failed a cheap VPN set up, and was eventually about to give up, when i found something really cool.

Firstly I do not use heavy resource sites like HULU or YouTube.
I use my PC Mostly for work reasons, browsing and email.

Most paid VPN providers offer monthly packages where you have unlimited bandwidth and are linux restricted.

But if you are a user like me (12hr day 200MB traffic max) I find Ivacy a great deal.

For $10 they also have a package for 20GB of traffic (no expiry limit). For me, this means 100 days minimum and as i only use it for part of my day, (when in the bosses office or  on some WIFI signal I don't like) I fully expect that to be nearer 200 days.

Now I know that people say you can't really have true faith in a third party VPN but it does the job for me as I don't really have anything confidential passing through. For me it's just a matter of I don't want to be snooped on by people around me. With this new setup I can also easily between IPs in the US,UK and RU, so if I really need to all blocked content is available to me (but  will use a god bit of bandwidth I think).

Oh, and its easy to set up (5mins) in Ubuntu even if you are on your first day.

Here's the link if it's any good to any one.

<snip>

---

