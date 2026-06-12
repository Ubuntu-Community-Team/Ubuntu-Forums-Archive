---
title: "Specs and hardware for a firewall/router box?"
date: 2007-03-24
forum: Server Platforms
---

### Post by newbie22 on 2007-03-24
I heard that a computer can be used as a firewall and router.  How does that work?  Does anyone know of a very user-friendly tutorial on building one?

I have an old computer that I would like to play around with.  But not sure if it meets the requirements.

500MHz with 128SDRAM.  Specs too low?

And what other additional hardware would I need?

---

### Post by 1/0 on 2007-03-24
I'm running [smoothwall]("http://www.smoothwall.org/") and its great so I recommend that one. Only problem is that you'll have to do some tweaking to set up a VPN tunnel over PPTP but there are tonnes of homebrew applications that makes SWE2 great plus its secure and solid as a rock.

Mine runs fine on a P3/600 with 256 Mb RAM. You'll need two NICs though and might consider getting an extra 128 or 256 Mb RAM if there's a dumpster or a scrap computer next to you.

---

### Post by Kissack on 2007-03-24
ipcop is also very good (like smoothwall).  Both good for low spec machines
-- 
Allan

---

### Post by nix4me on 2007-03-24
I've used IPCOP and M0n0wall.  They both are very good.  Your machine is plenty capable.  You will just need to make sure that it has 2 network cards.

IPCOP is linux based and m0n0wall is BSD based.

nix4me

---

### Post by Mr. C. on 2007-03-24
I'll second the smoothwall recomendation.  Your hardware is sufficient.

MrC

---

