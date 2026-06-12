---
title: "how you make wireless internet open and encrypted still?"
date: 2009-05-21
forum: The Cafe
---

### Post by Part Of What on 2009-05-21
hi  using tomato firmware.  can you put the password with the network name then share it and keep the connection with the encrition?  see you

---

### Post by Warpnow on 2009-05-21
If you open it...what would the encryption do?

---

### Post by t0p on 2009-05-21
> **Part Of What said:**
> can you put the password with the network name then share it and keep the connection with the encrition?

I don't get what you mean.  If you want it encrypted but "open" to other users who know the "password"... why don't you use wpa and supply the key to the other users?

If your network is open, it's not encrypted.  If it's encrypted, it's not open.

**EDIT:** Having said that: you see wifi hotspots that airodump-ng reports as "open" yet which require a password/account.  That works through http redirection, I think.  Not sure how you could emulate that.

---

### Post by LookTJ on 2009-05-21
you mean like packets encrypted?

---

### Post by dragos240 on 2009-05-21
> **Part Of What said:**
> hi  using tomato firmware.  can you put the password with the network name then share it and keep the connection with the encrition?  see you

That's pretty vague.... could you elaborate a bit?

---

### Post by gletob on 2009-05-21
I think he wants encryption of wireless packets with no password to access the network.

---

### Post by pwnst*r on 2009-05-21
or perhaps he wants the password to be either the or part of the SSID, which the "public" can use, but still be encrypted traffic.

---

### Post by Xbehave on 2009-05-21
He wants a safe method of communication for himself and an open one for other users. I don't know much about tomato, it may be possible to either
1) setup to APs on the same card
2) setup a VPN on the router, and then autoconenct to that vpn from your computers while leaving the AP unencrypted (you could even offer some sort of vpn-portal to all users so thier connections will be hidden from wireless sniffing*, if your router was powerful enough)


*Guest would be vulnerable to a clever MITM active-attack using airpwn, but that is much better than WEP/WPA(psk) with a shared password and the attack is pretty hard to pull of given airpwn no longer compiles (and only runs on linux), the attacker has to be closer (faster to respond) to the victim than the AP.

---

