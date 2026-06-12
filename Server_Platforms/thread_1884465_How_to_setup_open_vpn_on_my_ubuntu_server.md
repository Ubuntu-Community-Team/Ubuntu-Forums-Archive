---
title: "How to setup open vpn on my ubuntu server?"
date: 2011-11-21
forum: Server Platforms
---

### Post by Nailox on 2011-11-21
Hi. I need to setup a VPN on my server. And I need to rotate the IPs of the VPS so all of them are part of the VPN and can be rotated. I found some tutorials about how to setup the VPN under ubuntu but what about the IP rotation? PLS give me some directions - what should search for ? Or if you can point me to some tutorials about IP rotation that would be great. Another option maybe Squid but Im not familiar with it? So what should I be looking for ? Where to start? tnx

---

### Post by toshko3 on 2011-11-21
What is IP rotation?:confused:

---

### Post by Nailox on 2011-11-21
The vpn can be setup to use many IPs and switch one after another on a time interval.

---

### Post by SeijiSensei on 2011-11-21
> **Nailox said:**
> The vpn can be setup to use many IPs and switch one after another on a time interval.

And why would you need to do this?  I couldn't understand your original query and still don't really understand what you're trying to do now.

I suppose you could run a cron job that starts OpenVPN with a different configuration file every X minutes, but I must say this seems like a very convoluted arrangement.  Are you hoping this provides you some type of added security?  Frankly I don't see why.

---

### Post by Nailox on 2011-11-22
> **SeijiSensei said:**
> And why would you need to do this?  I couldn't understand your original query and still don't really understand what you're trying to do now.

I suppose you could run a cron job that starts OpenVPN with a different configuration file every X minutes, but I must say this seems like a very convoluted arrangement.  Are you hoping this provides you some type of added security?  Frankly I don't see why.


You are right. That's too complicated. I was using HMA VPN. Their client has the option to rotate IP every X minutes, but sometimes the connection is lost and it doesnt reconnect at all. So instead of making my own VPN Id rather find another VPN provider that won't drop the connection. But I need their client to support scheduled IP rotation. Can anyone recommend such VPN provider?

---

### Post by spynappels on 2011-11-22
It's hard to say whether it is a good idea or if there is a better way of doing it without understanding WHY you want to rotate the IPs on the server end periodically a little better.

---

### Post by Nailox on 2011-11-22
> **spynappels said:**
> It's hard to say whether it is a good idea or if there is a better way of doing it without understanding WHY you want to rotate the IPs on the server end periodically a little better.

Im using a program to generate hits to my website. Thats why i need to rotate IPs. With Hide My *** (HMA) VPN I can do it - their client has the option to cycle through IPs every X minutes. But sometimes the vpn craches and doesnt reconnect at all. So the program for hits starts using my own IP and after sometime it crashes too and I have to restart the PC. Also I have to sit by the PC all day to monitor it. So the options I can think of are:
-get a new vpn provider which wont crash (maybe all of them crash after continuous usage)
- make my own VPN 
- get some VPN connection monitoring program that would restart the HMA client
- upload my program for hits on a Windows VPS and use the IPs of the server and rotate them
-install a proxy switcher, but the ones I know are only for browsers. Im on LAN so I need a proxy for every connection not just for browsers

Any suggestions are welcome

Thanks for your time!

---

### Post by SeijiSensei on 2011-11-22
I don't know if this falls under the Forum Rules, but it sounds to me like you're trying to spam search engines or generate phony advertising hits.  I think I'll pass on helping you accomplish that.

---

### Post by spynappels on 2011-11-22
ok, let me check if I've understood this correctly:

You are creating hits on your own website, hosted at location A from a range of 5 IPs at location B. You want the IP to be rotated on a specific schedule.

What makes you think you need a VPN to do this? You could simply set up a remote explicit proxy and cycle the IP addresses for it's outbound connection. 

Having said that, I'm still confused why you want to rotate the IPs. I don't want to help you DDoS your (own) server, and the VPN reference makes me wary, sorry to be suspicious.

Some more information may be helpful.

---

### Post by spynappels on 2011-11-22
SeijiSensei beat me to it. Hadn't even considered the advertising dimension. Unless there is a clear kosher explanation, I'm out too.

---

### Post by toshko3 on 2011-11-23
[-x

---

