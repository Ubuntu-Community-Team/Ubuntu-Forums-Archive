---
title: "Fresh OO install included Nvidia 173 driver but it should not have done."
date: 2011-10-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Quackers on 2011-10-16
A brand new installation of OO (which will become PP shortly) during which I checked the boxes for updates and 3rd party stuff has installed ok. Everything works, but somehow the Nvidia 173 driver has been installed. 
Not a problem, you might say, but it is. My graphics card uses the Nvidia-current driver.
Why has the system detected and installed the wrong driver?

In fairness it seems to be working ok :-) Maybe I'll leave it :-)

Is this happening to others too?
Thanks.

---

### Post by oldfred on 2011-10-16
Same for me with 9600GT.

I noticed in alpha or beta it only offered the 173 driver. Then then final added another choice of most current or updated which I installed and then uninstalled 173. Not sure I noticed a lot of difference but I am not using Unity.

---

### Post by Quackers on 2011-10-16
Thanks oldfred. It seems an odd thing for the installer to do.
I haven't ticked those boxes during installation for quite some time, so it hasn't happened to me before.

---

### Post by rtalcott on 2011-10-16
Same here except maybe for me it wasn't working well...I was getting regular lock-ups till I discovered the 173 and installed a more appropriate driver...maybe there was no cause and effect but the machine certainly runs better now.
rt

---

### Post by ronacc on 2011-10-17
this started for me in the later daily's  173 gets installed by the installer even though I had not requested it and nvidia current is correctly shown as "recommended" by additional drivers .

---

### Post by Quackers on 2011-10-17
Should I file a bug against ubiquity? Would that be correct?

---

### Post by ronacc on 2011-10-17
if it isn't , who ever triages it will reassign it to the right package .

edit:  go ahead and ifle , I'll me-too and confirm .

---

### Post by Quackers on 2011-10-17
Thanks. I just tried to file a bug but it appears the Launchpad login system is having a problem :-)

---

### Post by Quackers on 2011-10-17
Voila  :-) Is that enough info? Well, they know where I am  :-)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/876499](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/876499)

---

### Post by rtalcott on 2011-10-17
Confirmed...
rt

---

### Post by ronacc on 2011-10-17
me-too'd and added comment .

---

### Post by Quackers on 2011-10-17
Thanks peeps :-)

---

### Post by oldfred on 2011-10-17
I joined the crowd. So we are up to 4 posted with the issue.

---

### Post by sant on 2011-10-20
Same issue here for Nvidia GeForce 9400 GT.

---

### Post by Quackers on 2011-10-20
The bug is still "undecided/unassigned".

---

### Post by philinux on 2011-10-20
Yep same here 8600gt.

---

### Post by Quackers on 2011-10-26
Still no movement on the bug - maybe they don't care :-)

---

