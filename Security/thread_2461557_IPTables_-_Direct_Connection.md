---
title: "IPTables - Direct Connection"
date: 2021-05-03
forum: Security
---

### Post by Geoff_Lane on 2021-05-03
Folks,

Many of us tend to be a little complacent regarding firewall security when we are working behind a router so just want to ask opinions.

If I directly connect a Linux Ubuntu computer to the internet is the following iptables rules sufficient for basic use?

sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT 
sudo iptables -I INPUT 1 -i lo -j ACCEPT
sudo iptables -A INPUT -j DROP

No servers being run on this machine and ssh access not required.

Geoff

---

### Post by The Cog on 2021-05-03
In my opinion you would be better setting a policy of DROP than putting a DROP at the end. A DROP at the end makes it difficult to append new rules (will never be reached), or might be deleted in error. 

Of course, if you do this and later install a service that you want to be accessible, then you will have to add permit rules for it. If you don't install any services, then the above rules aren't going to help at all because there's nothing anyone can connect to anyway. Maybe you should ask yourself what you are trying to block. If you install services that should only be accessible from the local LAN then you need a firewall to do that, but the above rules would need additional entries. If you install a service that is only for local (same PC) use then configure it to only listen on loopback (127.0.0.1 or ::1) address and it doesn't need a firewall.

Windows users will tell you you always need a firewall, but they don't know why other than that windows has lots of services that you can't disable.

---

### Post by Geoff_Lane on 2021-05-03
Thanks for quick reply,

It is more a learning curve than an actual requirement for this device.  Appreciate I said no servers running on this computer but netstat -l shows up quite a few various services.

I run a network with three Raspberry Pi devices all running various servers, only an https is open to public and comes in on a different port (not 443).  I occasionally temporarily open up other ports as required but generally all hide behind the router.

My question arose only because I had network issues and was checking a few things and tried setting router as a modem then connecting just one computer, tried with Tails first, seemed to connect but couldn't access anything, probably down to the complexity of tails.

I did manage though on my Ubuntu laptop and was able to access web sites but just wanted to know how to stop any uninvited access for peace of mind really.  Don't know enough to realise what is not a danger :rolleyes:

Geoff

---

### Post by slickymaster on 2021-05-03
*Thread moved to **Security**.*

---

### Post by The Cog on 2021-05-03
For sure, if you are messing around and trying things out, there is a possiblilty of leaving a service open that you overlook. Using iptables as well means extra protection against such errors. And just using iptables as a learning excercise is a Good Thing anyway. I would still suggest using a DROP policy for anything packets that drop off the end of the chain, which means your chain really just becomes a whitelist. 

Just to throw confusion in, iptables is being succeeded by nftables [https://www.nftables.org/](https://www.nftables.org/) which is somewhat different. It doesn't seem that many people are using nftables yet, but I think it will slowly replace iptables. I use nftables rather than iptables at home, but only really for my own interest.

---

### Post by Geoff_Lane on 2021-05-03
Thanks for advice,

An article I read did explain the difference between POLICY DROP and appending the DROP rule at the end.

Recall once locking myself out of a Raspberry Pi by changing the default option, it was headless so at the time unable to access SSH but guess as the laptop is always direct access then the POLICY change not an issue.

Geoff

---

### Post by Geoff_Lane on 2021-05-03
Can nftables and iptables conflict with each other?

Read up that nftables syntax easier to understand, I'm OK with iptables for simple rules but I tried to follow the read out from the Linux **Tails** distro and got completely lost.

Geoff

---

### Post by The Cog on 2021-05-03
I gather their NAT can conflict, and there are warnings not to configure NAT in both. Otherwise, I think they operate independently though I haven't tried. What would happen if one says DROP a packet and the other says ACCEPT it? I have no idea. Using both sounds like a recipe for confusion to me.

---

### Post by Geoff_Lane on 2021-05-03
> **The Cog said:**
> I gather their NAT can conflict, and there are warnings not to configure NAT in both. Otherwise, I think they operate independently though I haven't tried. What would happen if one says DROP a packet and the other says ACCEPT it? I have no idea. Using both sounds like a recipe for confusion to me.

Yes, guess that very likely. 

For time being I shall stay with IPTables, hidden behind my router I feel fairly safe ;)

Geoff

---

