---
title: "How to get rid of mpm-itk in Ubuntu 14.04"
date: 2014-05-22
forum: Server Platforms
---

### Post by Ulf_Dunkel on 2014-05-22
I have updated one of my Ubuntu servers to 14.04 LTS today, but then Apache2 complained that it missed an mpm-itk module. I fixed this issue in order to have my Apache2 be able to restart properly.

But while 14.04 had been installed, I was informed that mpm-itk is no longer part of the default distribution. I wonder if I really need it and if I should better remove it (probably with the mpm-prefork module which it depends on).

Can I remove both modules without any issues?
And if so, how do I remove Apache2 modules the correct way?

Thanks, Ulf Dunkel

---

### Post by cariboo on 2014-05-25
Moved to server platforms, as this question is more advanced than a absolute beginner question.

---

### Post by Ulf_Dunkel on 2014-06-06
I found (still being a beginner) that **a2dismod** seems to properly disable Apache2 modules. Then I can remove them using apt-get.

But as long as I haven't switched to mpm-worker, I will keep the mpm-itk module.

---

