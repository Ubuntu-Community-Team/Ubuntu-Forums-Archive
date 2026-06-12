---
title: "public WiFi"
date: 2009-04-20
forum: Security
---

### Post by danrako on 2009-04-20
Hello,

I'm using the public, unprotected wireless network @ the hospital.  What risks exist?  What actions should I take?  I'm sure this is covered in a sticky or faq somewhere, but it's been a long day.

Thanks in advance.

Oh, 9.04 on a Dell mini 9.  Cheers.

---

### Post by TigerCR1200 on 2009-04-20
Well I probably wouldn't put my credit card into any websites while I was on it or anything like that. But for general browsing I wouldn't expect there to be to much risk.

---

### Post by danrako on 2009-04-20
So the https:// & the padlock icon do not indicate reliable protection on public WiFi, correct?  I was hoping to access my online banking, but if it's a genuine risk, I won't expose myself.

---

### Post by tubbygweilo on 2009-04-20
danrako, It is never a good idea to expose oneself.

---

### Post by brian_p on 2009-04-20
> **danrako said:**
> So the https:// & the padlock icon do not indicate reliable protection on public WiFi, correct?

No, incorrect. The browser does strong encryption. Just make sure you go to the correct banking site.

---

### Post by cprofitt on 2009-04-20
If there is an unscrupulous person in the hospital IT staff or a person has setup a 'fake' AP then you can not trust the https://

Personally I would not access any sites that had financial data being transmitted.

----
The premise is that if a person were privy to both sides of the initial 'conversation' to negotiate the encryption they would be able to 'decrypt' the traffic.

---

### Post by kevdog on 2009-04-20
With public WifFi I always tunnel an ssh connection to home and then run a Firefox socks5 proxy through the tunnel.  Makes me feel better about security.

---

### Post by Dr Small on 2009-04-20
> **kevdog said:**
> With public WifFi I always tunnel an ssh connection to home and then run a Firefox socks5 proxy through the tunnel.  Makes me feel better about security.
And that is probably the safest way to do it, too.

---

### Post by danrako on 2009-04-20
> **kevdog said:**
> With public WifFi I always tunnel an ssh connection to home and then run a Firefox socks5 proxy through the tunnel.  Makes me feel better about security.

No clue what this means, but now I've got a research project to occupy my time!  Thanks!

---

### Post by anystupidname on 2009-04-20
Check out [http://en.wikipedia.org/wiki/Hamachi](http://en.wikipedia.org/wiki/Hamachi)
(think free VPN server)

---

### Post by cdenley on 2009-04-21
> **cprofitt said:**
> If there is an unscrupulous person in the hospital IT staff or a person has setup a 'fake' AP then you can not trust the https://

Personally I would not access any sites that had financial data being transmitted.

----
The premise is that if a person were privy to both sides of the initial 'conversation' to negotiate the encryption they would be able to 'decrypt' the traffic.

If someone setup a fake AP, or spoofed your DNS, or attempted some kind of MITM attack, then the certificate would not be signed by a trusted certificate authority using the correct domain name, and the user would be warned accordingly. Certificate authorities are used to prevent from this kind of threat. In my opinion, if you're using https, you don't receive any warning from firefox, and you're accessing the correct domain, then you're safe. Unless, of course, your banking site's SSL certificate has been compromised, but that wouldn't matter where you're accessing it from.

---

### Post by cdenley on 2009-04-21
> **anystupidname said:**
> Check out [http://en.wikipedia.org/wiki/Hamachi](http://en.wikipedia.org/wiki/Hamachi)
(think free VPN server)

That uses P2P tunneling, correct? So instead of someone capturing your network traffic over the air at the hotspot, you get a peer running Hamachi capturing your network traffic?

---

### Post by slowth5 on 2009-04-21
I'm with cdenley; if it were otherwise, then why would browsers use public key crypto and certificates?

---

### Post by Ubuntification on 2009-04-22
> **brian_p said:**
> No, incorrect. The browser does strong encryption. Just make sure you go to the correct banking site.

SSL isn't invincible:

[http://www.thoughtcrime.org/software/sslstrip/](http://www.thoughtcrime.org/software/sslstrip/)

With a MITM attack and sslstrip an attacker could fake your banking site and have it look legit.

---

### Post by slowth5 on 2009-04-22
> **Ubuntification said:**
> SSL isn't invincible:

[http://www.thoughtcrime.org/software/sslstrip/](http://www.thoughtcrime.org/software/sslstrip/)

With a MITM attack and sslstrip an attacker could fake your banking site and have it look legit.

It's also vulnerable if the root Certificate Authorities use MD5, which we all know has been broken for years.

If implemented properly (not MD5), and the user confirms he is on the correct site and verifies the certificate, then the information is safe, even on public wifi.

---

### Post by JK3mp on 2009-04-23
At max you might get a underpaid system admin or a snoopy bored teen. At worste? I think if you just run it through ssh as suggested b4 you'll be fine. And https is not always able to be trusted and if they really want sensative information they'll have the software and capability of getting around that encryption etc. sinc a majority of anything important runs through it it would be pointless for them to sniff your traffic if they couldn't crack it anywho.

---

### Post by SpyroViper on 2009-04-24
I personally, would not use anything that involves my card details or banking details.  Even if I was running a %100 secure system, open hotspots are just too tempting for people to use.  There is one guy who lives near my dad and he has an unsecured wireless..  very tempting to ssh into, don't let people do the same to you.

---

### Post by kevdog on 2009-04-25
How do you ssh into an unsecured wireless connection?  Id be curious to know of the details!

---

