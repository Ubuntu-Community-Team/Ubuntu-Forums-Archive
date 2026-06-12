---
title: "Unity 5.6 - launcher bar will not reveal in autohide"
date: 2012-03-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by TBABill on 2012-03-12
So I updated 12.04 beta 2 today and it pulled in Unity 5.6 updates. Looks great, but I have to leave the launcher always exposed because in autohide I cannot get it to show by setting to moving the cursor all the way to the left (and slamming it left over and over) or using the top left corner setting. Either setting keeps it hidden with no way to use it so the only recourse is to set it to show all the time, which is not ideal.

Anyone have a fix or different experience with it? I've restarted and checked all the basics. Worked fine before the update to 5.6.

---

### Post by sammiev on 2012-03-12
I need to move mine to the left about 1/2 down the screen and slide it up or down when you reach the left.

---

### Post by TBABill on 2012-03-12
Tried everything I can think of so far tonight, including changing all sorts of compiz settings, but nothing helps. The launcher works great when always showing, but will not show if put on autohide. Heading to bed but may need to report as a bug.

---

### Post by alphacrucis2 on 2012-03-12
I'm seeing the same problem after the latest updates, I have to turn autohide off to get the launcher to appear. Also getting random segfault in compiz.

---

### Post by sacridex on 2012-03-13
I have the same problem. The Launcher appears when i hold the super key.
[Here]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/953671") is the bugreport for it.

---

### Post by alphacrucis2 on 2012-03-13
Seems to be fixed by another update. Package libxfixes3. Hmmm

---

