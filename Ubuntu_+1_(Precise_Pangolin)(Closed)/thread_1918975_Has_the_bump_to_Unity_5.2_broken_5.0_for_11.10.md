---
title: "Has the bump to Unity 5.2 broken 5.0 for 11.10"
date: 2012-02-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sffvba[e0rt on 2012-02-02
Hi,

Not 100% a question about +1, but as you guys are active on the latest and greatest Unity 5.x I was wondering if you knew if the bump to 5.2 has ended the ability to update to Unity 5 in 11.10.

Just before the update I successfully upgraded to Unity 5.0 and since 5.2 my Unity doesn't upgrade to 5.0 (in fact when I add the PPA and do a dist-upgrade only one file gets upgraded (memory fails me now to which one) and nothing else).


Cheers
404

---

### Post by kaldor on 2012-02-02
> **not found said:**
> Hi,

Not 100% a question about +1, but as you guys are active on the latest and greatest Unity 5.x I was wondering if you knew if the bump to 5.2 has ended the ability to update to Unity 5 in 11.10.

Just before the update I successfully upgraded to Unity 5.0 and since 5.2 my Unity doesn't upgrade to 5.0 (in fact when I add the PPA and do a dist-upgrade only one file gets upgraded (memory fails me now to which one) and nothing else).


Cheers
404

5.2 does require Ubuntu 12.04. I don't think it'll be backported to Oneiric either.

---

### Post by xyzzyman on 2012-02-02
They removed the Oneiric 5.0 files from the PPA when they jumped to 5.2... As they removed them PPA purge didn't work for me. After manually resolving dependancies and version problems I wound up reinstalling 11.10. The issue with the launcher opacity changing the opacity of docky and terminal and system monitor were too annoying.

---

### Post by t1497f35 on 2012-02-02
> **kaldor said:**
> 5.2 does require Ubuntu 12.04. I don't think it'll be backported to Oneiric either.
I wonder why.. Is there some package dependence which can't be installed/upgraded in 11.10 for Unity 5.2 to work?

---

### Post by grahammechanical on 2012-02-02
There is this comment in the link requesting testers for Unity 5.2:

> **Prerequisites:** Make sure you are running the latest version of precise, and all your packages are up to date. Unfortunately this cannot be installed on oneiric or any previous ubuntu release. 

It is also incompatible with the Heads Up Display testing ppa. When I installed the HUD it removed Unity 5.0. I had to purge the HUD to get Unity 5 back.

I guess the answer is - it is still under development and there were plenty moans about 11.04 not being fully functional. So, these new feature are not being released into the wild (as it is called) until fully tested and fixed. The priority, it seems is to get things working in 12.04 by release day and not updating 11.10, in my opinion.

Regards.

---

### Post by philinux on 2012-02-02
> **grahammechanical said:**
> There is this comment in the link requesting testers for Unity 5.2:



It is also incompatible with the Heads Up Display testing ppa. When I installed the HUD it removed Unity 5.0. I had to purge the HUD to get Unity 5 back.

I guess the answer is - it is still under development and there were plenty moans about 11.04 not being fully functional. So, these new feature are not being released into the wild (as it is called) until fully tested and fixed. The priority, it seems is to get things working in 12.04 by release day and not updating 11.10, in my opinion.

Regards.

I guess they might backport to 11.10 later. Or just an SRU.

---

### Post by castrojo on 2012-02-02
> **not found said:**
> Just before the update I successfully upgraded to Unity 5.0 and since 5.2 my Unity doesn't upgrade to 5.0 (in fact when I add the PPA and do a dist-upgrade only one file gets upgraded (memory fails me now to which one) and nothing else).

You're hitting a combination of an archive freeze, the acceptance criteria, and an auto build.

 * The PPA autobuilds Unity based on commits, that means if something lands in Unity upstream you get a new PPA build. This is currently 5.2+ and updates based on when something lands in trunk and works. 

 * Unity doesn't get uploaded in the distro until it passes acceptance criteria. (It needs to work solidly etc.) so that 12.04 is useable for day to day work. It's still 5.0.something in the distro.

 * Even if it was all ready to go we're in soft freeze for Alpha 2 so not much is going on in archive until that's released todayish. 

I'd expect after Alpha 2 is out you'll see 5.2 make it into 12.04.

---

### Post by sffvba[e0rt on 2012-02-02
Wow, thanks for all the replies and info... it isn't a biggy (Unity 5 is just so much faster than 4.x and it is nice on a 11.10 system)...


404

---

### Post by castrojo on 2012-02-02
Ah nuts I just realized you're talking for 11.10 and my answer is for 12.04. 

Yeah someone will need to do a backport there, I doubt it will come in an SRU for 11.10.

---

### Post by cariboo on 2012-02-02
@not found, Precise will probably run perfectly on the new system you just got. :)

---

### Post by kaldor on 2012-02-02
> **cariboo907 said:**
> @not found, Precise will probably run perfectly on the new system you just got. :)

Feel free to join in on all the breakage we're getting!

---

### Post by sffvba[e0rt on 2012-02-03
Hehe... well took the new system back to the guy I bought it from (as much as I love using Ubuntu I still use Windows for some games etc.) and the shop I got it from installed a "downloaded" version of Windows so I told them to get knotted.

So I am back to one system for now, will live in Unity 2D on 11.10 until the PP drops, which I can't wait for because it seems to be shaping up to be EPIC.


404

---

