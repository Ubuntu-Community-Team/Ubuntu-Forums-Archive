---
title: "Public Wifi Security"
date: 2012-03-04
forum: Security
---

### Post by Ganeshx on 2012-03-04
Hey guys.
 

 In order to save money, the internet in my house is getting cut.  I have always had a steady internet connection, so this will be quite a change.  Needless to say, I'll be spending a ton of time at the local public library.  I'm just a little concerned about security.  I usually don't connect to any networks other than my home.  The library's wireless is unsecured, and I was just wondering what precautions I can take to protect myself.  I've never really worried about this, but I figure this is something to be concerned about.  Any advice appreciated.

---

### Post by doorknob60 on 2012-03-04
Use HTTPS whenever possible, use this: [https://www.eff.org/https-everywhere](https://www.eff.org/https-everywhere) Anything you do over HTTPS should be secure, but any not encrypted (just [http://)](http://)) can potentially be seen by others.

---

### Post by Smilax on 2012-03-04
openVPN

---

### Post by sammiev on 2012-03-04
I use a VPN service myself.

---

### Post by 3rdalbum on 2012-03-04
In Australia we have a mobile phone carrier called Amaysim, which gives you 4 gigs of data on their Unlimited plan. I just tether my phone rather than pay for a separate connection. Amaysim doesn't mind. Is there anything similar in your country? Public wifi is insecure and sometimes might be less reliable than 3G.

---

### Post by kevdog on 2012-03-04
VPNs are great -- it just depends whose is running it and over what type of connection.  I run an OpenVPN server at my house, however the up speed is so limited, its really painful to run the thing. 

If doing web only, I really prefer to do http over a socks proxy that runs over ssh.  Really I think of this as a poor man's vpn, however it requires little overhead, and I really find it to be a lot faster.

---

### Post by Nixarter on 2012-03-05
Make sure whatever you do is end-to-end encryption (esp if you are sending credit card info for purchases, for example).  Services like tor (vidalia bundle) are great, but exit nodes can still pose mitm attack threats without end-to-end encryption.

---

### Post by Eiji Takanaka on 2012-03-06
Some companies use https for the login, but then revert back to plain old http once you've logged in.
Hotmail used to do this, don't know if they still do. 

The result is your password is safe, but people can still see inside your account so to speak, any e-mails sent e.t.c

Be aware google search has a https function, but if you link to any pages that arent https, well your out in the open again sunny jim. Saying that i know they use https encryption throughout your session to both youtube and googlemail...which is good practice. 
. 

Like the other dudes/ettes have suggested running a vpn is defo an idea.

Might be an idea to get yoself a copy of wireshark to see what info your bleeding. 

If youve got the means to test this with 2 computers all the better. 

Use one to innocently browse around and the other to monitor via wireshark.

I tested this with my sister she was shocked when i told her exactly what people were typing to her over msn messenger in real-time. 

Hoho.

Bottom line is every site you visit, should in this day and age be https throughout. I'm guessing its probably some how more expensive or some other limiting factor though, which is why it isn't the norm.

---

### Post by lisati on 2012-03-06
*Thread moved to **Security Discussions**.*

---

### Post by tubbygweilo on 2012-03-07
Ganeshx, may be worth considering having your machine with full disk encryption. I'm thinking that if using it in a public place you may have more chance of it being stolen than when using at home. If stolen then the bad guys may well have your kit but they may find your data a harder nut to crack.

---

### Post by Ms. Daisy on 2012-03-07
> **tubbygweilo said:**
> Ganeshx, may be worth considering having your machine with full disk encryption. I'm thinking that if using it in a public place you may have more chance of it being stolen than when using at home. If stolen then the bad guys may well have your kit but they may find your data a harder nut to crack.
Good point. 

It's also important to note (because it seems to be misunderstood elsewhere) that encryption won't help security while you're surfing on public wifi. As soon as the volume is mounted it is in plain text.

---

### Post by tubbygweilo on 2012-03-07
> **Ms. Daisy said:**
> Good point. 

It's also important to note (because it seems to be misunderstood elsewhere) that encryption won't help security while you're surfing on public wifi. As soon as the volume is mounted it is in plain text.

Good point, I may also suggest keeping data within Truecrypt containers so that if your kit is stolen while you are signed on then data within unopened Truecrypt containers may still be safe.

Be paranoid but better still chain the laptop to your wrist:P

---

