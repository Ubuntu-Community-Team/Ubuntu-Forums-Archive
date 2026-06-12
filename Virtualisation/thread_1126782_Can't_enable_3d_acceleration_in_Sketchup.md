---
title: "Can't enable 3d acceleration in Sketchup"
date: 2009-04-15
forum: Virtualisation
---

### Post by jlbr21 on 2009-04-15
Hi there folks,
I've got a Windows xp guest running in Virtualbox 2.2 (with Ubuntu 8.10 as host), one of the main reasons for this is I need sketchup for my job, so then I went on and checked the 3d acceleration option under the general settings of vbox.
I went on and installed sketchup 7, went to the preferences window and the 3d acceleration is not even available, meaning it's shaded.

If you know sketchup, then you will know that w/out 3d acceleration the program will become horribly sluggish with an elaborate file.

Please help if you can!

Thanks!

---

### Post by Dedoimedo on 2009-04-16
Did you install the guest addons first?
Dedoimedo

---

### Post by jlbr21 on 2009-04-16
Hi Dedoimedo,

I have read your tutorials by the way, very good ones I must say. To answer your question, yes, guest addons were installed previously and then I enabled 3d acceleration, and then I installed Sketchup.

Does the problem lie there you think?

---

### Post by Dedoimedo on 2009-04-16
No problem then ... simply 3d acceleration in virtual machines is not up to the level you need ... But it will be soon, in a year or so.
Dedoimedo

---

### Post by jlbr21 on 2009-04-16
will try running it under wine I suppose...

thanks for the help!

---

### Post by Perryg on 2009-04-16
I have to ask this!
Did you install the "new" guest additions?
If so are you able to turn on enhanced graphics in Ubuntu?

---

### Post by jlbr21 on 2009-04-16
Wow!!!

I reinstalled the guest addons, that did the trick, now the 3d acceleration works!!!

Thanks a lot!!!

---

### Post by Dedoimedo on 2009-04-17
Sorry, I should have mentioned it, both 2.1 and 2.2 require new addons to get things going properly. Good one, Perryg.
Dedoimedo

---

