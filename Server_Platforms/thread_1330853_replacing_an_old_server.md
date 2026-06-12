---
title: "replacing an old server"
date: 2009-11-18
forum: Server Platforms
---

### Post by eremyja on 2009-11-18
i think i posted this in the wrong place... [http://ubuntuforums.org/showthread.php?p=8343513](http://ubuntuforums.org/showthread.php?p=8343513)

heres the down low:
have an old junky server acting as the pdc
wanting to put in a new pdc and want to know how to change it easily

---

### Post by Vegan on 2009-11-18
I recently did a forklift upgrade of my server, and I only changed the NIC to the assigned IP address and it was good to go. If you want to use a new disk, you will have to save all the config files you are using.

Saving /etc is not a bad idea.

---

### Post by eremyja on 2009-11-19
ok so would changing the ip and name to match the old one do the trick you think?

---

### Post by spikyjt on 2009-11-19
If its a samba pdc you might have a nightmare, because the new PDC will have a different domain SSID (even if you call it the same name, IP etc). I suggest you keep the current one running, setup the new one as a BDC and then remove the old one and promote the new one to PDC. That's all theory though, as I've never done that myself! Basically Windows networking is a barrell of crap and is a nightmare if you need to change anything. If you used LDAP auth however, it might be easier, as you could backup the LDAP DB and re-instate it on the new machine. Extensive reading of the Samba HowTos may be necessary! Good luck

---

