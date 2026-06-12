---
title: "What do you imagine is better: setting up WEP or using a MAC access list on my r"
date: 2007-10-24
forum: The Cafe
---

### Post by JacobRogers on 2007-10-24
I just set up an access list and typed in all the MAC addresses of my computers. That seemed like an easier alternative than having a really long password to type in on every computer.

What do you think is more secure?

---

### Post by p_quarles on 2007-10-24
Neither. There are tools available to automate the process of cracking WEP passkeys, and it's easy to spoof MAC addresses. The safest thing is to use WPA or WPA2. And you don't need to type the passkey every time: you can just store it in your keyring.

EDIT: jinx! lol

---

### Post by n3tfury on 2007-10-24
why aren't you using WPA/2?

WEP *can* be cracked in less than a minute now.  mac addresses can easily be spoofed, etc.





*edit* p_quarles damn you

---

### Post by Crashmaxx on 2007-10-24
I just do mac address filtering as I am way in the suburbs. Just to keep neighbors from grabbing it. Sure its easy to spoof mac addresses, but its not like people are war driving through my neighborhood. WPA is such a pain to setup, I just grew tired of dealing with it. 90% of people will leave it alone as soon as they see they can't access it.

---

### Post by n3tfury on 2007-10-24
it's not a pain at all in gutsy.

---

### Post by Crashmaxx on 2007-10-24
> **n3tfury said:**
> it's not a pain at all in gutsy.

Its not Gutsy. Its XP mostly. POS won't connect for no reason and the only thing that fixes it is to re-setup the profile. Then I got to go find the 54 or whatever character hex key and put it back in, twice. Gets old very fast.

---

### Post by original_jamingrit on 2007-10-24
> **Crashmaxx said:**
> Its not Gutsy. Its XP mostly. POS won't connect for no reason and the only thing that fixes it is to re-setup the profile. Then I got to go find the 54 or whatever character hex key and put it back in, twice. Gets old very fast.

For WPA, keep it on a text file on your desktop, your my documents, or if you're feeling really insecure, a floppy disk hidden underneath a magazine stack.

Maybe there's an application similar to the GNOME keyring manager for windows, that you could download?

Simply because WEP is broken.  Very.

Although, for what it's worth, if you have to use WEP, use mac filtering as well as a decent pass.

---

### Post by n3tfury on 2007-10-24
> **Crashmaxx said:**
> Its not Gutsy. Its XP mostly. POS won't connect for no reason and the only thing that fixes it is to re-setup the profile. Then I got to go find the 54 or whatever character hex key and put it back in, twice. Gets old very fast.

eh? wpa/2 is even easier to set up in XP.  my post was directed at the OP anyway.

---

