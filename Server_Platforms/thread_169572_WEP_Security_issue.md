---
title: "WEP Security issue"
date: 2006-05-02
forum: Server Platforms
---

### Post by DrewThePirate on 2006-05-02
I was messing around in my computer class today at school, on the one computer that I have been granted permission to use linux on. I was working on getting a new wireless card up and running, when I stumbled across /etc/network/interfaces. I saw a line there that I could not believe, right before my eyes was the WEP key that my teacher had been nice enough to type in the day before. I called him over and asked him if indeed the string of characters I had just found was indeed the only thing keeping our school's network safe, and he kind of had a minor heart attack because he was afriad I was gonna spread it around (it had already been hacked once earlier in the year, my school upgraded its security after that.) I convinced him that I wouldn't spread it around and that I was probably one of five people that knew anything about Linux so no one else would be able to find it either.

Basically, here's my question: Am I supposed to be able to view my school's WEP key from a file that anyone who knows what they're doing can find? Granted, there is a login password, but at my school all the login passwords are the same. Is this a security issue?

---

### Post by auroraborealis on 2006-05-02
You should not be able to read WEP keys. They need to change the permissions for that file.

And WEP can be cracked with ~4 million packets anyway.

---

### Post by LordHunter317 on 2006-05-02
Who cares?  WEP requires a shared key infrastructure, ultimately, everyone who has access to the network must know it.

More importantly, anyone can penetrate WEP in minimial amounts of time with trivial tools.

So no one cares.  It's not best practice, but it doesn't matter one lick.

---

### Post by nocturn on 2006-05-03
It doesn't matter much indeed, but still, there is no good reason why non-admin users should be able to read that file.
So if we apply the principle of least-privilege, it should be protected.

---

### Post by johnnymac on 2006-05-05
Relying on WEP is icky if your worried about security.  Sure it will deter most "passer-bys" but anyone with a wep-crack will break it without a sweat.  What you should do is try WPA if you dont' have a AP that's WAP compliant - use MAC filtering.

---

### Post by LordHunter317 on 2006-05-05
[QUOTE=johnnymac]What you should do is try WPA if you dont' have a AP that's WAP compliant - use MAC filtering.[/QUOTE]MAC filtering adds no security.  Unless you're not using the network, I can hijack a valid MAC.

---

