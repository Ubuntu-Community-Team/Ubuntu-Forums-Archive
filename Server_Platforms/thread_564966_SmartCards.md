---
title: "SmartCards"
date: 2007-10-01
forum: Server Platforms
---

### Post by quark_77 on 2007-10-01
Hi All,

I apologise this doesn't really relate to servers (except for accessing them) but it DOES relate to security.

My question is - how feasible would it be for me to store my private keys for OpenPGP, SSH and X.509 on a smartcard of some sort. What sort of costs are involved and most importantly, will it work on Linux?

I'm not asking that question without having researched an answer or two myself. I'm aware of the M.U.S.C.L.E. project and of the US DoD's CAC project and have looked into smart card specifications, vendors etc.

I'm trying to find out, in plain English, what sort of card would achieve the above and what sort of card reader/writer it would require in order to do so. 

Specific gaps in my understanding include:
[LIST]
[*]How information is kept secure on the card. If I put my .pfx file on it as is, I'll still need the password to decrypt it? What about PINs?
[*]Application compatibility - OK, so I have these files on a card, how do I show ssh/thunderbird how to get them? What sort of format be expected by said applications?
[*]What represents a good value smartcard? To what extent do I NEED onboard processing when really I'm trying to provide identity information and keep it safe? If so, how much?
[/LIST]
I'd appreciate any feedback you have, particularly further reading. I don't expect anyone to do my research for me but I'd appreciate being pointed in the right direction! Has anybody else tried this scheme / works anywhere that implements this sort of access control?

Thanks in advance for any info you can provide.

Quark_77

---

