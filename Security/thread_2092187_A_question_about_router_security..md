---
title: "A question about router security."
date: 2012-12-07
forum: Security
---

### Post by jsvidyad on 2012-12-07
Hi!!

   This post is not directly related to ubuntu. It is indirectly related in the sense that I use ubuntu. 

   The issue I have was that the internet in my place was not working for some time. They fixed it, but reset the router and changed all the passwords. Now, I don't think that the default configuration of that router is secure. They have changed the default password and set a password for the wireless. But, that's all. They haven't disabled UPnP. To get an idea of why this is bad, look here: [https://www.kb.cert.org/vuls/id/347812](https://www.kb.cert.org/vuls/id/347812) and here: [http://www.gnucitizen.org/blog/hacking-the-interwebs](http://www.gnucitizen.org/blog/hacking-the-interwebs) . Then, they haven't set wireless security to WPA2-AES. They have set to use both WPA & WPA2 with both TKIP&AES. Their passwords are only 8 characters long. By default, the firewall is disabled. When I told my landlord that this configuration was not secure, I was told that I would have to live with it and they wouldn't give me the passwords to make the necessary changes. Now, in this scenario, can I connect to that network in a way such that my computer and my personal info are secure and safe?

---

### Post by chadk5utc on 2012-12-07
1

---

### Post by OpSecShellshock on 2012-12-07
If you don't control the network then you have no way to absolutely ensure the integrity of communications between your computer and the internet.

Best thing is probably to contact an ISP and get your own internet service if the property owner is OK with it.

---

### Post by CharlesA on 2012-12-07
> **OpSecShellshock said:**
> If you don't control the network then you have no way to absolutely ensure the integrity of communications between your computer and the internet.

Best thing is probably to contact an ISP and get your own internet service if the property owner is OK with it.

Pretty much this. It is up to the network owner to secure their gear, not the user.

---

### Post by dannyboy79 on 2012-12-07
since the router doesn't have a firewall, then simply run a firewall on the computer you use to connect to the internet.

I wonder if you could install a router and use it's firewall capabilities only, not it's DHCP server.

---

### Post by jsvidyad on 2012-12-08
I am actually more concerned about the fact that UPnP is enabled.

---

### Post by CharlesA on 2012-12-08
If you cannot secure something that is not yours, then try not to worry about it. Either secure your machine to the best of your ability, or get internet elsewhere.

---

### Post by haqking on 2012-12-08
> **jsvidyad said:**
> I am actually more concerned about the fact that UPnP is enabled.

Though i disable it myself as i prefer to configure my own ports it is not as a big a deal as people make out, it is not commonly exploited and if it was it would be done through malware which you should be locally protected from anyways.  There was a buffer exploit associated with XP however though that was a while ago.  There was the Flash attack too but if you tightly controlled outboudn rules on your local machine again its not too much of an issue

Wouldnt worry about it too much, if you have the option then disable it, if you dont I wouldnt overly panic.  That being said I always recommend secure as much as possible where possible of course, but dont get too worried.

---

### Post by sandyd on 2012-12-09
This is what I do on my company laptop when traveling - I do not trust the security of other people's networks with my work documents, which are worth quite a lot.

1. IPTables set to block everything, except for DHCP and traffic from a single IP hosting a VPN server.
2. VPN Connection Established.

Well, the only way that traffic is traveling into my computer is through the VPN, so I wouldn't be worried.....

---

### Post by CharlesA on 2012-12-09
> **sandyd said:**
> this is what i do on my company laptop when traveling - i do not trust the security of other people's networks with my work documents, which are worth quite a lot.

1. Iptables set to block everything, except for dhcp and traffic from a single ip hosting a vpn server.
2. Vpn connection established.

Well, the only way that traffic is traveling into my computer is through the vpn, so i wouldn't be worried.....

+9000.

---

### Post by s1baker on 2012-12-09
This might be a dummy question because I'm new at this, but in the case of the OP, if a person lived in an apartment where the landlord has a router that one would think as not to secure, could that person have a router in their apartment with its own network/security, that connected to the landlord's router?

---

### Post by CharlesA on 2012-12-09
> **s1baker said:**
> This might be a dummy question because I'm new at this, but in the case of the OP, if a person lived in an apartment where the landlord has a router that one would think as not to secure, could that person have a router in their apartment with its own network/security, that connected to the landlord's router?

Yes, but it would basically just be daisy chained and all traffic would go thru their connection.

Basically it all falls back to: Their network, their rules. If they don't want to listen to security advice, get your own connection or just deal with it as is.

---

### Post by s1baker on 2012-12-09
> @ CharlesA
Yes, but it would basically just be daisy chained and all traffic would go thru their connection.




but would not any security the apartment dweller added to his own router be in addition to the landlord's router?

---

### Post by CharlesA on 2012-12-09
> **s1baker said:**
> but would not any security the apartment dweller added to his own router be in addition to the landlord's router?

It depends. If it's a solution like sandyd suggested - a VPN, the traffic would be unreadable, but if you are just hooking another router to an existing one, whoever controls the network could be able to read your traffic.

Not saying a landlord was go thru the trouble of doing so, but it's a possibility.

---

