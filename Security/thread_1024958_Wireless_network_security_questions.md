---
title: "Wireless network security questions"
date: 2008-12-29
forum: Security
---

### Post by Tom--d on 2008-12-29
Hello,

I have some questions regarding a home wireless network.

At the moment I have:

WEP 64bit key
MAC filtering on 
ssid is broadcasting.

There is a bug in my wireless driver which won't allow me to connect through Network Manager. (I use commands to get a connection).
I hear all the time that WEP is rubbish but I can't have WPA because my router doesn't support it and I cannot upgrade it (Its not mine).

Do you think it would be ok, as a security point of view, that I have this set up.

No WEP
Hidden SSID
MAC filtering on

Would that be ok? Is there any point in having WEP?

Thanks,
Tom

---

### Post by damis648 on 2008-12-29
That would be fine, as long as nobody knows your SSID you are safe. BUT your connection would not be encrypted, so be aware any sniffers could listen in.

---

### Post by howefield on 2008-12-29
I disagree with the above, it might only take 10 minutes to break WEP but it takes almost nothing to break a hidden ssid.

I'd say use the WEP.

---

### Post by Tom--d on 2008-12-29
> **howefield said:**
> I disagree with the above, it might only take 10 minutes to break WEP but it takes almost nothing to break a hidden ssid.

I'd say use the WEP.

But what about MAC filtering? I have it so it only accepts the mac address's I put in.
Is that enough?

---

### Post by howefield on 2008-12-29
> **Tom--d said:**
> But what about MAC filtering? I have it so it only accepts the mac address's I put in.
Is that enough?

Mac filtering will ensure no one connects to your router unintentionally., but the determined will easily spoof your mac and get in, further security in the form of WEP, even if it is weaker than WPA or its variants, means they will need to spend an amount of time on getting in.

What you are proposing is merely to obscure your system, not secure it.

But hey, maybe hidden ssid and mac filtering is all you need, you know the risks more than we do in terms of who is around you that might want in.

All anyone can give you is an opinion, mine is not to play hide and seek but to secure your system.

---

### Post by Tom--d on 2008-12-29
> **howefield said:**
> Mac filtering will ensure no one connects to your router unintentionally., but the determined will easily spoof your mac and get in, further security in the form of WEP, even if it is weaker than WPA or its variants, means they will need to spend an amount of time on getting in.

What you are proposing is merely to obscure your system, not secure it.

But hey, maybe hidden ssid and mac filtering is all you need, you know the risks more than we do in terms of who is around you that might want in.

All anyone can give you is an opinion, mine is not to play hide and seek but to secure your system.

I see your point of view on this.
Its a tough one because I want to use Network Manager but there is a bug in Network Manager which will not allow me to connect to WEP.
Maybe I'm being too picky. Is it worth to upgrade the router to support WPA?

---

### Post by damis648 on 2008-12-31
WPA is a much better than WEP, I would recommend that. If Network Manager is giving you trouble, just try Wicd. That might be the easiest solution.

---

### Post by Rob_H on 2009-01-01
> **howefield said:**
> Mac filtering will ensure no one connects to your router unintentionally., but the determined will easily spoof your mac and get in, further security in the form of WEP, even if it is weaker than WPA or its variants, means they will need to spend an amount of time on getting in.

What you are proposing is merely to obscure your system, not secure it.

But hey, maybe hidden ssid and mac filtering is all you need, you know the risks more than we do in terms of who is around you that might want in.

All anyone can give you is an opinion, mine is not to play hide and seek but to secure your system.
Completely agree with this. MAC filtering, hidden SSID, and WEP will deter only the most casual hackers or prevent your neighbors from accidentally connecting. But for real wireless security, WPA with a long, random passphrase is the ONLY solution.

---

### Post by Vantrax on 2009-01-01
In terms of security Ill give you one rule:
Obscurity is not security.

WEP is more or less pointless and while hiding an SSID is nice, most people who look at jumping onto networks are running a product like ethereal that will have no problems finding your wireless. 

MAC filtering is a nice idea, but unfortunately as soon as I have a single packet of authorized data I can spoof an allowed mac address.

In answer to your question its OK, but keep a very close eye on your network usage, and never do netbanking at home.

I would suggest trying WICD and running at least WPA/WPA2 with a 16 character key.

---

### Post by Tom--d on 2009-01-02
I cannot have WPA on my router. There is no update for it either. Its a Linksys HG200

---

### Post by Rob_H on 2009-01-02
> **Tom--d said:**
> I cannot have WPA on my router. There is no update for it either. Its a Linksys HG200

Then you'll need to decide if your security is worth the $50 or so it will cost to purchase a new router.

---

### Post by Vantrax on 2009-01-02
> **Rob_H said:**
> Then you'll need to decide if your security is worth the $50 or so it will cost to purchase a new router.

I would recommend it highly.

---

### Post by insane_alien on 2009-01-03
he already said he couldn't upgrade it.

well, if you can't get a new one with WPA/WPA2(remember to use AES as there is a TKIP vulnerability) and you can't connect to WEP(which is as useful as a bit of wet toilet paper against a browning .50 cal at point blank range) then no encryption is your only choice, hiding SSID's is similarly useless. guess you are just going to have to go in the open unless you can convince whoever is in charge of the router to buy a decent one.

---

### Post by Tom--d on 2009-01-04
> **insane_alien said:**
> he already said he couldn't upgrade it.

well, if you can't get a new one with WPA/WPA2(remember to use AES as there is a TKIP vulnerability) and you can't connect to WEP(which is as useful as a bit of wet toilet paper against a browning .50 cal at point blank range) then no encryption is your only choice, hiding SSID's is similarly useless. guess you are just going to have to go in the open unless you can convince whoever is in charge of the router to buy a decent one.

mm... I could convince my dad to get a new one :D

---

### Post by insane_alien on 2009-01-04
offer to pay for a bit of it yourself. even set up a demonstration to show him how useless WEP encryption is.

---

### Post by euler_fan on 2009-01-04
Before you spend $50 on a new router, why are you worried about it? If you say you want your privacy, then I'd say go for it. Any site where you should be worried about sensitive information <cough>banks, investment firms, you school<\cough> should already be providing SSL/TLS connectivity where needed and are probably required to secure personal data by law.

Admittedly, there are universities who don't do SSL/TLS secured access to their email accounts (I used to go to one) so that may be a great reason. But you didn't indicate you had such concerns, so it kind of begs the question . . . why are you worried about it?

On an aside, just because you want to play with it is also cool :)

---

### Post by Rob_H on 2009-01-04
SSL/TLS is not a substitute for a secure wireless network. Allowing anyone into your LAN opens up the connected PCs to all kinds of attacks, especially if you have file/printer sharing or other local services enabled between PCs. It also allows others to consume your bandwidth and do illegal things on the Internet that can be traced back to your IP address. Spend the 50 bucks.

---

### Post by euler_fan on 2009-01-04
[Bruce Schneier's Open Wifi Commentary]("http://www.schneier.com/blog/archives/2008/01/my_open_wireles.html")

Offered as an FYI. Bottom line: If you see it as worth it, go for it.

---

### Post by bodhi.zazen on 2009-01-04
IMO WEP is probably sufficient for casual home use. Yes it can be quickly cracked, but who cares?

Now if you are conducting banking or financial transactions or if you have unfriendly tech savy neighbors then upgrade your router.

---

