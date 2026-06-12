---
title: "Fully logout from SAMBA from windows environment"
date: 2008-11-20
forum: Server Platforms
---

### Post by artilheiro.mz on 2008-11-20
hello all

i've recently configured a small samba server in my office network

everything is working well

the thing is, there is one computer that anyone can use, when they are in a rush.

i want to be able to have anyone log in and logout from that computer with their normal user account

say john logs in the samba server from pc1, when john finished working, how can bob log in on the same pc1 without restarting the pc?

is there an easy way to do this?

the only solution i found, was to restart the pc, but thats not a pratical solution

any ideias?

many thanks

---

### Post by renzokuken on 2008-11-20
is the server a domain controller? if it is you can simply add the pc to the domain, then log in and out of it as normal

---

### Post by artilheiro.mz on 2008-11-21
no, its not in any domain.

were just all in the same workgroup.

is there anyway possible?

i've heard of trying to mount PDC, but i dont want to have to much trouble with this..

any ideias?

cheers

---

### Post by Thirtysixway on 2008-11-21
Looking through options on webmin, I saw under Unix Networking there was an option that said "Idle time before disconnect".  Perhaps you could disconnect idle users (say after 10 minutes or so?  I'll keep looking around as I've also wondered about this.

---

