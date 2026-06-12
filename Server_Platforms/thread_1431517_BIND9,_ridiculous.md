---
title: "BIND9, ridiculous"
date: 2010-03-16
forum: Server Platforms
---

### Post by captainjy on 2010-03-16
Wow, just crazy.  I have spent hours trying to figure out how to get BIND working and it's no wonder why people use Windows!!!  It really shouldn't be this hard at all.  Across the board there are 50,000 different solutions for one simple problem it seems.  

Can someone please shed some light on this for me?  I followed the guide on these forums, getting hung up on:


Loading configuration file from /etc/bind/named.conf
unknown option 'zone'

If I edit named.conf and remove zone, I get no errors except for:

Loading configuration file from /etc/bind/named.conf
'}' expected near '"'

Everything is closed, checked 15 times.  Is there a better guide out there?

**UPDATE**: Unreal.  Unreal.  Guess all I needed to do was bitch and moan.  Up and working now.  Crazy!  Wouldn't be able to really say how I did it, but it's working.

---

### Post by ratcheer on 2010-03-16
It is a mystery to me, too. I just use OpenDNS.

Tim

---

### Post by KB1JWQ on 2010-03-16
If you'd like to paste your config, I'll go over it with you to explain the moving pieces; that way when it breaks next time you'll have some idea of where to look.

Windows hides a lot behind a pretty GUI, but when it goes wrong that acts to insulate you from what's really going on.  There's always a trade-off.

---

### Post by the yawner on 2010-03-16
Bind really has a steep learning curve. But it's not the industry standard for nothing. Funny that, even Windows users are more likely sending DNS queries to a Bind server somewhere, so your rant had been entertaining at least.

---

### Post by HermanAB on 2010-03-17
The Windows DNS is actually an ancient copy of BIND8 behind a GUI.

Why don't you use Webmin?  It has a BIND plugin.

---

