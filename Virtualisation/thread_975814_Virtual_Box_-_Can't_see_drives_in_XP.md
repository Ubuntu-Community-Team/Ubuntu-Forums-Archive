---
title: "Virtual Box - Can't see drives in XP"
date: 2008-11-08
forum: Virtualisation
---

### Post by flatlinecoder on 2008-11-08
Hi there

I am running Ubuntu 8.10 and virtualization all works fine, expect if I put a cd in my drive xp doesn't see it.How can I use the drives for ubuntu and xp? 

Thanks
Ciaran

---

### Post by Cresho on 2008-11-08
virtualbox has I think a gtk version and the regular sun's gui.  you can launch it in your accessories.  I was playing with intrepid and ran accross some problems because of the way its heading.  in anycase, you can launch it in terminal with command VirtualBox  case sensitive.

Now for the cd portion:
Launch virtualbox.  In the lower right hand corner, you will see icons.  This also has a cd icon.  right click on it and unmount an image.  when you install sun's virtualbox additions, it stays mounted.  the way I described it to you, you can unmount.   after this is done, you can have access to your cd drive.  I expirienced this as well.  If this does not solve your problem, there is another option.

---

### Post by flatlinecoder on 2008-11-09
> **Cresho said:**
> virtualbox has I think a gtk version and the regular sun's gui.  you can launch it in your accessories.  I was playing with intrepid and ran accross some problems because of the way its heading.  in anycase, you can launch it in terminal with command VirtualBox  case sensitive.

Now for the cd portion:
Launch virtualbox.  In the lower right hand corner, you will see icons.  This also has a cd icon.  right click on it and unmount an image.  when you install sun's virtualbox additions, it stays mounted.  the way I described it to you, you can unmount.   after this is done, you can have access to your cd drive.  I expirienced this as well.  If this does not solve your problem, there is another option.

Yea thanks that did it, although I can only see one of my 2 drives, but thats ok I wont be needing the 2 of them working for xp. 
Thanks

---

### Post by Cresho on 2008-11-09
Let me know if you have problems with sharing folders or other stuff

---

