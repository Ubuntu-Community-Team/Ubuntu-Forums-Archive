---
title: "a  question about mess networking,"
date: 2009-01-29
forum: The Cafe
---

### Post by Xbehave on 2009-01-29
with mesh networking now in the kernel, I have a couple of questions about it in theory (obviously none of this is practical yet):

I have a router(r) and 3 laptops (a,b,c)

If I want to send a file from a -> b , atm it goes
a -> r -> b 
With c -> r interfering so slowing down the transfer to less than 11mbs (802.11g)

Is this correct?

If I were to use a wireless mesh, would there be any advantage to sending a file a -> b ?
c -> r (is still on the same frequency, but now the whole thing takes 1/3 less time)
If a and b are closer to each other than r or c, could they reduce the power of their signals and allow a -> b while c->r can continue without interfering?

Does the router need to be mesh aware for a laptop to extend the wireless range (at a cost of bandwidth) or can a cheap router be used with a clever laptop to send wireless signals further?

If any of the above situations are practical is there any effort to get these into userspace applications? even NetworkManager? 
Could use of wireless meshs boost linux networking into the future :cool:? even NetworkManager :P?

---

