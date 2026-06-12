---
title: "Home wireless network security"
date: 2010-02-06
forum: Security
---

### Post by dogdo on 2010-02-06
Hi

I know this topic is not Ubuntu specific but rather platform agnostic but i would just like to know if there is any point for home wireless networks to have security beyond WPA2 PSK AES? I know that enterprise networks use different measures like LEAP and RADIUS-but do home users have to use this?

---

### Post by CharlesA on 2010-02-06
You don't really need it as a home user, but if you really want to impliment it, you can always do so. Just make sure all the wireless devices you have support it.

---

### Post by Pjotr123 on 2010-02-06
Quite useless for home use. WPA2 PSK is fine for home use, provided it's "AES only". And provided you use a strong key, with letters, numbers and special signs (#,*,$ etcetera).

---

### Post by dogdo on 2010-02-06
> **Pjotr123 said:**
> Quite useless for home use. WPA2 PSK is fine for home use, provided it's "AES only". And provided you use a strong key, with letters, numbers and special signs (#,*,$ etcetera).

Funny you should mention that. On the router i have the WPA2 PSK AES Key set to not be compatible with the older WPA TKIP mode, but on the ubuntu 9.10 comptuter when i enter the key it asks for a 'WPA/WPA2' key?

---

### Post by CharlesA on 2010-02-06
> **dogdo said:**
> Funny you should mention that. On the router i have the WPA2 PSK AES Key set to not be compatible with the older WPA TKIP mode, but on the ubuntu 9.10 comptuter when i enter the key it asks for a 'WPA/WPA2' key?

Generic message. I can connect to my WPA2 AES network fine in Ubuntu 9.10.

---

### Post by dogdo on 2010-02-06
Thanks:lolflag:

---

### Post by HermanAB on 2010-02-07
Howdy,

I put WiFi devices outside my firewall on their own connection and leave them completely unsecured. That way, a passing Realtor can check his email, I have no trouble connecting myself and if I need to access a home or office machine, I use SSH as normal.

However, the above requires you to have at least two IP addresses for your home setup and that is not common anymore.

---

### Post by Sporkman on 2010-02-08
> **HermanAB said:**
> Howdy,

I put WiFi devices outside my firewall on their own connection and leave them completely unsecured. That way, a passing Realtor can check his email, I have no trouble connecting myself and if I need to access a home or office machine, I use SSH as normal.

However, the above requires you to have at least two IP addresses for your home setup and that is not common anymore.

What if a passerby does something illegal over your internet connection?

---

### Post by CharlesA on 2010-02-08
> **Sporkman said:**
> What if a passerby does something illegal over your internet connection?

Then you, sir, are boned.

---

### Post by doas777 on 2010-02-08
yep,. the us courts have shown disdain for the "unsecured wifi" defense, but it appears to be holding ground in france.

when people tell me that they don't have any computing resources worth protecting, I always ask if that includes their reputation and legal status. 
(if anyone tells me "if you've got nothing to hide, then you have no need for privacy", I ask them if I can see their wallet. )

@op: no radius won't really help you, since wifi is not like RAS, and there is no network level login that you are wanting to integrate.

---

### Post by Bachstelze on 2010-02-08
> **HermanAB said:**
> Howdy,

I put WiFi devices outside my firewall on their own connection and leave them completely unsecured. That way, a passing Realtor can check his email, I have no trouble connecting myself and if I need to access a home or office machine, I use SSH as normal.

However, the above requires you to have at least two IP addresses for your home setup and that is not common anymore.

Actually, a couple ISPs over here have that feature built-in with the routers they provide. For example, the router provided by my ISP (Free) broadcasts two networks: one is "ichigo", which is my private network, protected with WPA2-AES and a 64-character key, and the other one is "FreeWifi", which allows any other Free subscriber to connect to the Internet from my router with his Free login and password (and likewise, when I'm away from home, I can usually find a "FreeWifi" network nearby).

Now I don't know (and care very little) about the legal implications, but from a "community" point of view, I find that really neat.

---

### Post by dogdo on 2010-02-09
> **Bachstelze said:**
> Actually, a couple ISPs over here have that feature built-in with the routers they provide. For example, the router provided by my ISP (Free) broadcasts two networks: one is "ichigo", which is my private network, protected with WPA2-AES and a 64-character key, and the other one is "FreeWifi", which allows any other Free subscriber to connect to the Internet from my router with his Free login and password (and likewise, when I'm away from home, I can usually find a "FreeWifi" network nearby).

Now I don't know (and care very little) about the legal implications, but from a "community" point of view, I find that really neat.

In a ideal world it would be nice to have people give out free wifi-alas most crackers would probably abuse this with obvious implications-while i commend you for your community spirit i think you should be more realistic.

---

### Post by HermanAB on 2010-02-09
If and when my free WiFi becomes a problem, I'll throttle or filter it with Squid-cache.  While it is working fine, I see no reason why not to leave it free and open.

---

### Post by doas777 on 2010-02-10
> **HermanAB said:**
> If and when my free WiFi becomes a problem, I'll throttle or filter it with Squid-cache.  While it is working fine, I see no reason why not to leave it free and open.


lol, look into a ternet server
[http://www.ex-parrot.com/~pete/upside-down-ternet.html](http://www.ex-parrot.com/~pete/upside-down-ternet.html)

---

