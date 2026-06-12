---
title: "system restore as it is previous day"
date: 2008-10-08
forum: The Cafe
---

### Post by ursmouli on 2008-10-08
hi


  i am new to linux and i made a drastic changes to os ....can any one help me to restore my ubuntu as  it is previous day .......

thanks for ur time



                                                     yours,
                                                     mouli

---

### Post by Trail on 2008-10-09
"System Restore" is not directly supported in Linux.

You'd have to tell us what your "drastic change" is and try to reverse it manually (or reformat if it's not worth the effort?).

---

### Post by Johnsie on 2008-10-09
This is one of the features I've missed from Windows during my last few years of  using Linux. It made it very simple for joe six-pack and the hockey moms to undo damage without needing to have any  IT skills. It also speeded up the process of fixing some problems. Fixing some problems in Ubuntu can still take a good degree of computing knowledge. I've been using Linux for 3 years, studied software engineering at uni and can program. I still had to re-install a machine a few days ago because I couldn't solve a problem with apt. If someone with a computing background can fix things then how can we expect the average joe to fix things? In Intrepid they've added a "last successful boot" option in Grub. Hopefully they will start looking at backtracking techniques in the future.

---

### Post by Sealbhach on 2008-10-09
There's something called Time Vault, which can restore parts of your system in a limited way.

[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)

Not as good a solution as System Restore though.


.

---

### Post by BigSilly on 2008-10-09
Never had any care for System Restore in Windows. It never worked properly for me. One of the first things I did with a fresh XP install when I used to use it, was turn off system restore. It takes up a lot of resources, and when you need it, it borks.

---

### Post by Johnsie on 2008-10-09
Sorry it didn't work for you. It's always worked great for me. Helped me save a few peoples systems.

---

### Post by fjf on 2008-10-09
If you have your home in a different partition, booting from a Ubuntu live CD, formatting the / partition and installing a new system takes like 30 minutes.  Not worth the trouble of any system restore.


> **ursmouli said:**
> hi


  i am new to linux and i made a drastic changes to os ....can any one help me to restore my ubuntu as  it is previous day .......

thanks for ur time



                                                     yours,
                                                     mouli

---

### Post by LaRoza on 2008-10-09
What did you do? System Restore on Windows works with the registry mostly, and the registry is the cause of most problems.

sysres is pretty close though, although you'd have needed to have made a restore point to use it: [https://launchpad.net/sysres](https://launchpad.net/sysres)

---

