---
title: "ubuntu 10.04 security in virtualbox"
date: 2010-05-20
forum: Virtualisation
---

### Post by wah fun on 2010-05-20
Noob question. When ubuntu (10.04 32 bit specifically) is installed as a guest OS in virtualbox (using vb 3.1.8 for windows, does it provide the same level of security as it does when installed to its own partition?

thx

---

### Post by beavis5551 on 2010-05-20
Can you please be more specific?
What is your exact question / concern?
 
cheers,

---

### Post by TheFu on 2010-05-20
Sadly, security questions like this can only be answered with "it depends."  It depends on hundreds (if not thousands) if settings, programs, and behaviors.

If the Linux OS is only available remotely, then I'd say yes, it is just as secure remotely as another physical install would be. But when physical access is allowed to any system, virtual or not, then there are always additional concerns.

Can I "certify" my statements? No.  If you allow the Linux client to access host resources like the local disk, then it is not as secure.  I'd also be concerned about the security of your host OS since any security issue there may impact all the client OS installations too. If the host OS gets hacked, I wouldn't trust any clients.

I hope that helps with the "it depends" answer given above.

---

