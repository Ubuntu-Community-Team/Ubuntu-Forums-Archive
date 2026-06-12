---
title: "stupid beryl question"
date: 2006-10-24
forum: The Cafe
---

### Post by fuscia on 2006-10-24
i tried beryl on a live cd of sabayon linux and it worked very well. does this mean my machine is set up to use beryl, or are there likely drivers in the sabayon cd that make it work? i have a nvidia card and no idea what drivers i have for it (i have a system76 laptop).

---

### Post by .t. on 2006-10-24
You should check out the nVidia beta drivers. With those, AIGLX should work out of the box with Edgy. Once you've got GLX_texture_from_pixmap and some kind of accelerated indirect rendering system, you should be good to go. nVidia drivers provide both of those features.

---

### Post by mips on 2006-10-24
Just check your xorg.conf and if it says "nvidia" you have a nvidia driver. If it says "nv" then you have the generic 2d opensource driver.

---

### Post by fuscia on 2006-10-24
> **mips said:**
> Just check your xorg.conf and if it says "nvidia" you have a nvidia driver. If it says "nv" then you have the generic 2d opensource driver.

thanks. it said nvidia.

.t., i'm not sure i'm feeling that adventurous.

---

### Post by PriceChild on 2006-10-24
You might want to check out my sig.

It contains a link to a post with a guide for almost every situation.

---

### Post by chaosgeisterchen on 2006-10-24
If you're running nVidia beta drivers and AIGLX the likelihood of getting Beryl to run all fine is about 95%, steadily rising.

---

### Post by .t. on 2006-10-24
I don't see why the nVidia beta drivers shouldn't provide AIGLX under Dapper. Is this the case? If so, then it should be easy for every nVidia user, willing to upgrade or not.

---

### Post by darkhatter on 2006-10-24
if you use the nvidia 9-series of drivers there is no need to use XGL or AIGLX

---

### Post by mips on 2006-10-24
> **fuscia said:**
> thanks. it said nvidia.

.t., i'm not sure i'm feeling that adventurous.

let us know how it goes if you decide to go down that path.

I just finised a fresh edgy+kde-core install 5mins ago and still have to add apps and customise it to my liking. last thing on my mind now is beryl, would hate for my fresh install to be borked.

---

### Post by chaosgeisterchen on 2006-10-24
> **.t. said:**
> I don't see why the nVidia beta drivers shouldn't provide AIGLX under Dapper. Is this the case? If so, then it should be easy for every nVidia user, willing to upgrade or not.

It does not because AIGLX and nVidia is only working on XOrg 7.1 which is NOT available for Dapper.

---

