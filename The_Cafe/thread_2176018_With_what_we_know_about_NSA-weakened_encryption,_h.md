---
title: "With what we know about NSA-weakened encryption, how safe is openvpn?"
date: 2013-09-22
forum: The Cafe
---

### Post by Docaltmed on 2013-09-22
I don't want a political discussion. I want a technical one. I'm using openvpn, has it, too, been compromised?

---

### Post by 1clue on 2013-09-22
A political discussion would be rapidly shut down anyway, so the only discussion that makes sense is a technical one.

First thing to say, I'm not an encryption expert.  I've tried to follow the math, but it's way beyond me.

Terms specific to this discussion:
Black hat:  Somebody you don't want to share information with.
White hat:  Somebody you do want to share information with.
Brown hat:  An involved but presumed to be neutral party whom you don't want to share data with but entrust it to anyway.

The truth is, security is about more than just a VPN.  If the black hat can get into your network by some other means, then they don't have to get into your VPN.  If the black hat can get into the remote network, they don't need to hack your VPN.  My point is that you'd better have a good firewall setup and probably not use a consumer-grade firewall/router.

About the VPN and encryption:
Half of the battle for the black hat is to get access to the entire data stream.  Theoretically you would have to be able to tap into the data stream at one end or the other, which means either have a tap inside one of the endpoint networks, or at the ISP's router for one of those networks.

One thing that surprised me about September 11 is how fast, how hard and how long the Internet went down.  Theoretically TCP/IP reroutes itself pretty much automatically, which should have caused the Internet to automatically recover at least some of its function after most of its main routes were removed.  In truth, the Internet stayed down for days, and the routes had to be manually restored.

I wondered about that ever since.  It might be that the actual implementations of routing protocols are not as advertised, and that core routing is tightly controlled by some group.  In that case, perhaps a VPN stream could be tapped at some remote location?

As for hacking the encryption, I think it's still as it always has been.  If you throw enough resources at it, you can crack any encryption.  Time estimates given are based on an arbitrary and theoretical maximum amount of computing power available to the black hat, and on some theoretical strength of the key.  In the case of a black-hat government, that theoretical maximum amount of computing power is pretty big, and probably much larger than we've been led to believe.

I'm guessing though that you should try to pick an encryption algorithm which was not developed in the nation occupied by the black hats though.  And do way more reading about encryption than you really want to.

---

### Post by Docaltmed on 2013-10-02
An informative and entertaining reply! Thank you.

---

