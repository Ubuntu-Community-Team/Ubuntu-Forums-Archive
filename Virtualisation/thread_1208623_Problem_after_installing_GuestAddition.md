---
title: "Problem after installing GuestAddition"
date: 2009-07-09
forum: Virtualisation
---

### Post by boeing777 on 2009-07-09
After I installed the GuestAddition in my Ubuntu Guest OS, I could not access ubuntu anymore.  After the Ubuntu loading screen, it goes like this.

It looked like everything is squeezed to the top???

---

### Post by uidb4056 on 2009-07-10
I've had the same problem after test upgrade Virtualbox 3.0 and install GuestAdditions on a Karmic Guest. I've not found a solution and going backwards again to Virtualbox 2.2.4

---

### Post by uidb4056 on 2009-07-17
> **boeing777 said:**
> After I installed the GuestAddition in my Ubuntu Guest OS, I could not access ubuntu anymore.  After the Ubuntu loading screen, it goes like this.

It looked like everything is squeezed to the top???

If you have set the video memory to 128K, try to reduce to 64K, it worked for me.

---

