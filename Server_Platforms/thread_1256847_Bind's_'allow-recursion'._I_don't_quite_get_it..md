---
title: "Bind's 'allow-recursion'. I don't quite get it."
date: 2009-09-03
forum: Server Platforms
---

### Post by PryGuy on 2009-09-03
Hello all! Please explain me the meaning of the 'allow-recursion' param in Bind. I read info, but I can't quite understand it. Thank you in advance.

---

### Post by KiLaHuRtZ on 2009-09-15
It allows the server to lookup domains it is not authoritative for.  For example, my DNS servers deny recursion for the public which only allows public hosts to ask my DNS to lookup hosts that it is authoritative for (i.e. my domains).  If someone were to ask my DNS to lookup "google.com" they would get "no answer".  However, my servers allow recursion for my internal/private hosts so they can lookup all other domains (i.e. browse the internet).  Does this make sense to you?

---

### Post by PryGuy on 2009-09-15
So in other words I should allow recursion for my local network and disallow it for the requests coming from the Internet?

What if I have two views in my DNS configuraton (one for localhost and one for the local network) and DNS server does not listen to the interface that is connected to the Internet at all?

---

### Post by KiLaHuRtZ on 2009-09-15
First question; yes.
Second question; you should be safe with global recursion.

---

### Post by PryGuy on 2009-09-16
> **KiLaHuRtZ said:**
> Second question; you should be safe with global recursion.Global recursion allows us to ask all not authoritative servers?

---

### Post by KiLaHuRtZ on 2009-09-16
In respect to question 2, you would want recursion.  Otherwise, your clients will only be able to resolve for domains you host.

---

