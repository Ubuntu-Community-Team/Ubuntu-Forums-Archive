---
title: "Critical Error"
date: 2012-07-15
forum: Virtualisation
---

### Post by degarb on 2012-07-15
I have new Ubuntu 12.04 never installed virtual box before.

Now, on first launch after installing virtual box virtualbox-4.1_4.1.18-78361~Ubuntu~precise_i386.deb, I get "Critical Error-Failed to create com object. "  Details: 
Callee RC: 
NS_ERROR_FACTORY_NOT_REGISTERED (0x80040154)


I uninstalled it, and downgrade installed 4.1.4.1.12 and it won't launch at all,  I uninstalled it, and tried the newer version. But still getting the same error message.

---

### Post by Dedoimedo on 2012-07-17
Google says /tmp permissions. See this:
[https://www.virtualbox.org/ticket/2335](https://www.virtualbox.org/ticket/2335)

Dedoimedo

---

