---
title: "Non-Static IP Web Hosting"
date: 2008-01-28
forum: The Cafe
---

### Post by Black Mage on 2008-01-28
Hi,

I am trying to host a web site off a server I built at home. The operating system is Ubuntu thus the web server is Apache.

There is a ISP around me that gives a static ip address for $100 dollars a month but 5 megs download, but I'd rather just stick with my current cable internet access.

So is there something I can use that will automatically update my domain when the ip changes? Something like what they use at [www.no-ip.org?](www.no-ip.org?) And right now my current domain was purchased from yahoo.

Thnx.

---

### Post by CheShA on 2008-01-28
you can install a no-ip compatible client from the repos and then run the config script 

```
sudo apt-get install no-ip
no-ip -c
```

---

### Post by mips on 2008-01-28
dynDNS comes to mind.

Alternatively just google: dynamic ip dns

---

### Post by Black Mage on 2008-01-28
But will that work for any domain or only domains at [www.no-ip.com](www.no-ip.com), because I have my own domain that I want to use.

---

### Post by mips on 2008-01-28
> **Black Mage said:**
> But will that work for any domain or only domains at [www.no-ip.com](www.no-ip.com), because I have my own domain that I want to use.

Sorry, no idea as I have never had a need for a service like this.

---

### Post by CheShA on 2008-01-28
> **Black Mage said:**
> But will that work for any domain or only domains at [www.no-ip.com](www.no-ip.com), because I have my own domain that I want to use.

Set your domain DNS records to be a CNAME that points to your no-ip  address.

---

### Post by stalker145 on 2008-01-29
> **CheShA said:**
> Set your domain DNS records to be a CNAME that points to your no-ip  address.

I, too, run several web sites from my residential (dynamic) connection. I used this route (except with DynDNS) and it works flawlessly. No-IP should be no different nor should any of the other dynamic hosts out there.

As mentioned, just 
1. go into your control panel for your domain and change where your www is now pointing to instead point to whatever dynamic name you choose. 
2. Update. 
3. Wait a few minutes/hours/days (last I did this it was minutes). 
4. Enjoy.

---

### Post by CheShA on 2008-01-29
> 3. Wait a few minutes/hours/days (last I did this it was minutes). 

This will depend on how your DNS is configured for TTL.  Commonly recommended TTL is 24hours, and most DNS hosts will use TTL of 24 hours ( = 86400    -> TTL is measured in seconds) so your propagation should take no more than 48 hours before the new DNS records are available everywhere.  If you want your DNS to propagate quickly drop the TTL on your DNS to e.g. 30 minutes, wait 48 hours for this change to propagate, then update your DNS, wait another hour or so for this to propagate and then revert your TTL setting.

---

### Post by Black Mage on 2008-01-29
Alright, thnx, I'll try once I get my question actually answered by TimeWarner.

---

### Post by stalker145 on 2008-01-29
> **Black Mage said:**
> Alright, thnx, I'll try once I get my question actually answered by TimeWarner.

Depending on how TWC is in your area, I don't know if I'd volunteer too much information about your setup. When I first got to my current residence, they explicitly disallowed running any sort of server on your residential line. 

Fast forward 4 years of TWC service and 4 years of me running a server on my residential connection... I had to move across town and reapply for service. I didn't read anything in the TOS that disallowed servers any longer.

The moral of this story: If they are going to charge you more for a static IP and/or transfer volume, just stick with the residential package if money is important.

That's my story and I'm sticking to it.

---

### Post by xmimanchix on 2008-01-31
hi
is it possible to have web server running behind the Adsl modem ? how ? my adsl modem ip is static thanks

---

### Post by stalker145 on 2008-01-31
> **xmimanchix said:**
> hi
is it possible to have web server running behind the Adsl modem ? how ? my adsl modem ip is static thanks

It should be as simple as having your web server listen on port 80 and any IP.

Are you using a router or a direct connection to the MODEM? If you're directly connected, you should be done. If you're using a router, make sure to forward port 80 to the web server's IP.

---

