---
title: "Strange system monitor reports"
date: 2010-03-01
forum: Security
---

### Post by skippy_dude on 2010-03-01
System monitor displays itself as using about 16% (others are all 0) or whatever processer power but if I look at the resources page, it shows about 30.
The amount varies but the processors are always taking way more than the list of processes indicate.
What's that?

---

### Post by uRock on 2010-03-01
Best way to truly find out how much CPU you are using is to open a terminal and enter top. You can even do this right beside System Monitor and compare what they show.

---

### Post by cariboo on 2010-03-01
System monitor adds it's own overhead to the display, as iRock said, use either top, or htop. Top is installed by default, and htop is in the repositories.

---

### Post by uRock on 2010-03-01
> **cariboo907 said:**
> System monitor adds it's own overhead to the display, as iRock said, use either top, or htop. Top is installed by default, and htop is in the repositories.

Thanks for posting about htop. Just installed it and I like it. Very good for control when things are going wrong.

---

