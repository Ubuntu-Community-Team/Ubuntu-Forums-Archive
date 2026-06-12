---
title: "WotLK opening screen problem....directrendering says yes."
date: 2009-10-18
forum: Wine
---

### Post by r4itei on 2009-10-18
i can get to the logon screen but it looks like this  =S

[http://photos-d.ak.fbcdn.net/hphotos..._3975248_n.jpg]("http://photos-d.ak.fbcdn.net/hphotos-ak-snc1/hs279.snc1/10630_168821523304_502678304_2746487_3975248_n.jpg")

im using ati video card open source drivers

direct rendering is yes
gears work fine, 700fps...
using wine 1.0   [1.27 doesnt let the program execute.]


any other info necessary?

---

### Post by r4itei on 2009-10-18
i can get to the logon screen but it looks like this  =S

[http://photos-d.ak.fbcdn.net/hphotos..._3975248_n.jpg]("http://photos-d.ak.fbcdn.net/hphotos-ak-snc1/hs279.snc1/10630_168821523304_502678304_2746487_3975248_n.jpg")

im using ati video card open source drivers

direct rendering is yes
gears work fine, 700fps...
using wine 1.0   [1.27 doesnt let the program execute.]


any other info necessary?

---

### Post by hikaricore on 2009-10-18
700fps in glxgears is not good, I get over 25,000 with desktop effects and several applications using my video card.
Also it should be mentioned that glxgears is not a benchmark.
This is a decent one: [http://www.mediafire.com/file/wjzozg0mgth/glxdragon.tar](http://www.mediafire.com/file/wjzozg0mgth/glxdragon.tar) ([original post]("http://ubuntuforums.org/showthread.php?p=8127136"))

It should also be mentioned that having to use the open drivers is a major setback for you.
These drivers are not yet mature and if I'm not mistaken do 3d very badly.
Don't take my word for it but the things i've heard about them are not amazing.

---

### Post by edin9 on 2009-10-18
> **hikaricore said:**
> 700fps in glxgears is not good, I get over 25,000 with desktop effects and several applications using my video card.
Also it should be mentioned that glxgears is not a benchmark.
This is a decent one: [http://www.mediafire.com/file/wjzozg0mgth/glxdragon.tar](http://www.mediafire.com/file/wjzozg0mgth/glxdragon.tar) ([original post]("http://ubuntuforums.org/showthread.php?p=8127136"))

It should also be mentioned that having to use the open drivers is a major setback for you.
These drivers are not yet mature and if I'm not mistaken do 3d very badly.
Don't take my word for it but the things i've heard about them are not amazing.

What card do you have?

---

### Post by r4itei on 2009-10-18
ati radeon x1100 xpress, a shitty acer aspire laptop T_T

---

### Post by edin9 on 2009-10-18
> **r4itei said:**
> ati radeon x1100 xpress, a shitty acer aspire laptop T_T

 Oh your using the opensource ATi drivers? Those are useless for 3D. They are still being made :(

---

### Post by r4itei on 2009-10-19
so is there a way where i can get WoW to run on this shitbox or just not bother?
theres apparently no proprietary drivers...

---

### Post by edin9 on 2009-10-19
> **r4itei said:**
> so is there a way where i can get WoW to run on this shitbox or just not bother?
theres apparently no proprietary drivers...

 You could install Hardy Heron which you can use the official 9.3 Catalyst driver with, but they are so buggy it hurts. The opensource drivers are better in nearly everyway except 3D, but that's always improving. If you really want to play WoW, I would go back to Windows.

---

### Post by r4itei on 2009-10-19
but im in hardy right now....ah screw it. haha, thanks for the info anyway.

guess its my hardware's fault and not ubuntu's.
dont really wanna go back to bill gates. gotta check for viruses all the time and such

---

### Post by edin9 on 2009-10-19
> **r4itei said:**
> but im in hardy right now....ah screw it. haha, thanks for the info anyway.

guess its my hardware's fault and not ubuntu's.
dont really wanna go back to bill gates. gotta check for viruses all the time and such

 Oh you're in Hardy? I wasn't aware that they shipped the opensource 3D driver for that. You may actually want to try Catalyst 9.3 then, it has much better 3D :)

---

### Post by cariboo on 2009-10-19
Please don't create multiple threads on the same subject, I have merged your two threads.

---

