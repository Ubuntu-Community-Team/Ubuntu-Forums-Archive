---
title: "VPN's , which offers the highest security?"
date: 2010-07-29
forum: Security
---

### Post by stvdel on 2010-07-29
If I wanted to set up a VPN what currently offers the highest level of security as far as VPN's are concerned?

---

### Post by Bachstelze on 2010-07-29
Define "the highest level of security"? ;)

There is no answer to such vague questions.

---

### Post by wacky_sung on 2010-07-29
See below.

[http://en.wikipedia.org/wiki/Virtual_private_network](http://en.wikipedia.org/wiki/Virtual_private_network)
[http://en.wikipedia.org/wiki/Point-to-Point_Tunneling_Protocol](http://en.wikipedia.org/wiki/Point-to-Point_Tunneling_Protocol)
[http://en.wikipedia.org/wiki/OpenVPN](http://en.wikipedia.org/wiki/OpenVPN)

---

### Post by espressobeanie on 2010-07-29
I don't think you know too much about VPN's. OpenVPN is the software that makes VPN's happen. The highest level of security for anything over the internet is pulling out the ethernet cable and wireless cards from your computer.

If you're referring to level of security in VPN, well, enable link encryption, use AES if it gives you encryption options, try using higher bit keys, but remember this:

*"security is only* as strong as the [I]weakest link"
[/I]

---

### Post by Bachstelze on 2010-07-29
> **espressobeanie said:**
> OpenVPN is the software that makes VPN's happen.

There's a lot of other VPN solutions...

---

### Post by Velnias on 2010-07-29
IPSEC, but its not for newbes.

---

### Post by stvdel on 2010-07-29
What I mean is PPTP, L2TP,IPsec, SSL these types of VPN protocols and others. I am wondering which ones seems to have a more secure protocol against attacks. I am not really talking about the encryption strength because it seems most attacks don't target breaking the encryption but try to find other flaws to attack with. I know everything can be attacked but which ones seem to be more difficult in executing an attack against.

---

### Post by cdenley on 2010-07-29
> **stvdel said:**
> What I mean is PPTP, L2TP,IPsec, SSL these types of VPN protocols and others. I am wondering which ones seems to have a more secure protocol against attacks. I am not really talking about the encryption strength because it seems most attacks don't target breaking the encryption but try to find other flaws to attack with. I know everything can be attacked but which ones seem to be more difficult in executing an attack against.

In my opinion, the best thing you can do to eliminate attacks is not use password authentication. It is much more difficult to crack a certificate or key than it is a password. The user's password is usually the weakest link.

---

### Post by wacky_sung on 2010-07-30
> **cdenley said:**
> In my opinion, the best thing you can do to eliminate attacks is not use password authentication. It is much more difficult to crack a certificate or key than it is a password. The user's password is usually the weakest link.
I do agree.Inregardless of how weak is user's password is still require for authentication for the certificate or key to function.Therefore it is always a good office practice to have a secure password. 

[http://en.wikipedia.org/wiki/Password_policy](http://en.wikipedia.org/wiki/Password_policy)
[http://www.cmu.edu/iso/governance/guidelines/password-management.html](http://www.cmu.edu/iso/governance/guidelines/password-management.html)

---

