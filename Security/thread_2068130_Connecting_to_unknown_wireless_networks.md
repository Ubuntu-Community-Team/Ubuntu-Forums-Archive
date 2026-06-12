---
title: "Connecting to unknown wireless networks"
date: 2012-10-08
forum: Security
---

### Post by mr-woof on 2012-10-08
Hi all,

If I connected my netbook to a wireless network in some sort of event where they put on free wifi for you, what in theory could someone do to my netbook? Firewall would be on, fully updated Ubuntu 12.04.

I realise that in a wpa/wpa2 network that is using a key, the data between me and the router/ap is encrypted. Am I missing something else that is obvious and a security risk?

I’m interested to see what sort of answers come back, I feel I have a good handle on wireless security but this question has just popped into my head.

---

### Post by sammiev on 2012-10-08
I have used free wifi but only through a VPN with FF. I have add-ons like No Script and Better Privacy. I usually disable Java as well. I had no issues to date.

---

### Post by samiux on 2012-10-08
> **mr-woof said:**
> Hi all,

If I connected my netbook to a wireless network in some sort of event where they put on free wifi for you, what in theory could someone do to my netbook? Firewall would be on, fully updated Ubuntu 12.04.

I realise that in a wpa/wpa2 network that is using a key, the data between me and the router/ap is encrypted. Am I missing something else that is obvious and a security risk?

I’m interested to see what sort of answers come back, I feel I have a good handle on wireless security but this question has just popped into my head.

WPA/WP2 can be brute force without dictionary [(proof is here)]("http://samiux.blogspot.hk/2012/05/howto-cracking-wpawpa2-without.html").

Once the hacker associated with the wifi router, s/he can attack any computer within the subnet with [Man-in-the-Middle attack]("http://samiux.blogspot.hk/2011/05/howto-sniffing-ssl-with-ettercap-on.html") (MiTM). Or, by other means.

Meanwhile, it is also risky to use so-called "Free wifi" in the public area when you do not sure the said "Free wifi" is setup by the hacker or not.

In additon, hackers can bypass the firewall too.

Samiux

---

### Post by mr-woof on 2012-10-08
Interesting, thanks for the links. So, how would an attack bypass your firewall?

---

### Post by samiux on 2012-10-08
> **mr-woof said:**
> Interesting, thanks for the links. So, how would an attack bypass your firewall?

Firewall is very easy to bypass.

Samiux

---

### Post by mr-woof on 2012-10-08
So you said, how though? Web Exploit? Drive by download ?

---

### Post by Cheesemill on 2012-10-08
One of the main worries would be session hijacking.

This means that anyone using the same network (whether secured or not) can gain access to any of the websites that you are currently logged into using your username without knowing your password if the sites don't use https throughout. From there it is easy enough to change your password or use your online accounts for any purpose they wish.

---

### Post by mr-woof on 2012-10-08
good point cheesemill, id forgotten about firesheep. I thought that only worked on an open wireless network, not when it's encrypted and using a key?

---

### Post by Cheesemill on 2012-10-08
> **mr-woof said:**
> good point cheesemill, id forgotten about firesheep. I thought that only worked on an open wireless network, not when it's encrypted and using a key?
I believe that it works on any wireless network that you are ***connected*** to. Even if the network is encrypted everyone shares the same encryption keys so Firesheep will work the same as being connected to an open network.

---

### Post by Hungry Man on 2012-10-08
Things they can do:

1) SSL-Strip to bypass non-HSTS HTTPS websites and read encrypted messages etc.

2) Intercept any unencrypted messages (even easier). This includes unencrypted session cookies (I see Firesheep has already been mentioned), IM conversations, etc.

3) Interact with any local services running on your system (cups, dhclient).

---

### Post by rookcifer on 2012-10-08
> **samiux said:**
> WPA/WP2 can be brute force without dictionary [(proof is here)]("http://samiux.blogspot.hk/2012/05/howto-cracking-wpawpa2-without.html").

Brute-forcing only works if the AP uses a weak password.  Good luck brute forcing my router, which has a random 128 bit password.  

In any case, your point is moot with public open Wifi since it is *supposed* to allow everyone to connect.  No brute forcing or WPA cracking necessary.

> Once the hacker associated with the wifi router, s/he can attack any computer within the subnet with [Man-in-the-Middle attack]("http://samiux.blogspot.hk/2011/05/howto-sniffing-ssl-with-ettercap-on.html") (MiTM). Or, by other means.

This is true.  That's why when on public Wifi you must take extra care when visiting sensitive sites (banks and the like).  You must ensure the certificate you are seeing really is the bank's certificate.  Probably the easiest way to do this is with Firefox add-ons.  Certificate Patrol will store certs you trust and then alert you whenever they change.  That would be one method of detecting MiTM.  Another is Convergence.  A third option would be to bypass the Wifi and only use it to connect to your own private VPN.  You can set one of these up on your home router and then ssh into it whenever away from home.  This will give you a secure tunnel.

> Meanwhile, it is also risky to use so-called "Free wifi" in the public area when you do not sure the said "Free wifi" is setup by the hacker or not.

In additon, hackers can bypass the firewall too.

Samiux

Puiblic Wifi is fine.  I would just be careful about doing online banking or any other private stuff unless you are connecting to a private VPN or are very careful with certificate checking.

---

### Post by mr-woof on 2012-10-09
Thanks for the info guys, I'll have to look into Firesheep in more depth. 

Regarding the ssh tunnel, I've got a ssh server that I can use as a secure tunnel for web browsing etc, I think I'll get that ready if I need to connect to any event wifi.

I've not heard of ssl-strip before, this seems to clear things up a bit:

[http://security.stackexchange.com/questions/10989/how-to-thwart-sslstrip-attack](http://security.stackexchange.com/questions/10989/how-to-thwart-sslstrip-attack)

Edit: Reading Hungry mans comments again, how would it be possible for an attacker to interact with any local services running on your system if your firewall etc is up and running?

---

### Post by Lyfang on 2012-11-04
> **mr-woof said:**
> Edit: Reading Hungry mans comments again, how would it be possible for an attacker to interact with any local services running on your system if your firewall etc is up and running?
By packet sniffing? I would use encryption to prevent an unauthorized user intercepting network traffic, especially on a public Wi-Fi network. As mentioned by rookcifer its safer to connect through a private VPN on a public Wi-Fi network.

---

