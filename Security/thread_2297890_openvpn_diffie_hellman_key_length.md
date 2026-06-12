---
title: "openvpn diffie hellman key length?"
date: 2015-10-07
forum: Security
---

### Post by Drenriza on 2015-10-07
Hi all

When setting up an openvpn server, what is an appropriate length for the DH key negotiation?
Standard is 1024 bits, but from what i can tell [http://www.keylength.com/en/8/](http://www.keylength.com/en/8/) recommend 2048 bits?

What do you guys use
1024?
2048?
Something else?

And why do you either use a small or large key?

Thanks on advance
Kind regards

---

### Post by Drenriza on 2015-10-08
Anyone with that would / could give some feedback?

---

### Post by Azdour on 2015-10-09
This should give you a reason why you should choose 2048:

[https://community.openvpn.net/openvpn/wiki/Hardening](https://community.openvpn.net/openvpn/wiki/Hardening)

I always use 2048 with OpenVPN.

---

### Post by CharlesA on 2015-10-09
> **Azdour said:**
> This should give you a reason why you should choose 2048:

[https://community.openvpn.net/openvpn/wiki/Hardening](https://community.openvpn.net/openvpn/wiki/Hardening)

I always use 2048 with OpenVPN.

Vouching for that. I always use 2048 bits for the DH key.

---

### Post by Drenriza on 2015-10-19
Thanks

---

