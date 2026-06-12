---
title: "Tor and Evolution"
date: 2011-09-04
forum: Security
---

### Post by haqking on 2011-09-04
Anyone got any good input on using TOR with Evolution ?

Is there a way to add a IMAP proxy to Evolution ?

I use IMAP for all my accounts bar one which is POP.

Do you suggest using Evolution preferences or System Wide settings ?

Cheers

---

### Post by Dangertux on 2011-09-04
> **haqking said:**
> Anyone got any good input on using TOR with Evolution ?

Is there a way to add a IMAP proxy to Evolution ?

I use IMAP for all my accounts bar one which is POP.

Do you suggest using Evolution preferences or System Wide settings ?

Cheers

IMO -- just set the local network settings to use the SOCKS 5

---

### Post by haqking on 2011-09-04
> **Dangertux said:**
> IMO -- just set the local network settings to use the SOCKS 5


yeah thats what i thought, i wasnt sure if the default was SOCKS5, as the network settings does not let you allow a change only host and port

cheers

---

### Post by Dangertux on 2011-09-04
> **haqking said:**
> yeah thats what i thought, i wasnt sure if the default was SOCKS5, as the network settings does not let you allow a change only host and port

cheers

I am pretty sure the configuration file can be edited to define an alternate port as well you can determine if you want 4 or 5.

---

### Post by haqking on 2011-09-04
> **Dangertux said:**
> I am pretty sure the configuration file can be edited to define an alternate port as well you can determine if you want 4 or 5.


yeah that makes sense, i will look into it.

Cheers bud

---

### Post by Dangertux on 2011-09-04
> **haqking said:**
> yeah that makes sense, i will look into it.

Cheers bud

Try running it with something like polipo and a setting like this.

```

 socksParentProxy = "192.168.1.2:9050" socksProxyType = socks5

```

---

