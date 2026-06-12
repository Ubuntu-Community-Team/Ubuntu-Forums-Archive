---
title: "Display shows black screen starting live system of Ubuntu 12.04 beta"
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Ondrasek on 2012-03-11
Some days ago I tried to start the live system of ubuntu 12.04 beta but when i start  my pc it shows a black screen and my display turns of. The same thing  happened when I tried Ubuntu 11.10. Does anyone know a solution?
 I've got AMD A6-3500 APU with Radeon(tm) HD Graphics, AMD Radeon HD 6530 D, 8GB Ram

---

### Post by 2F4U on 2012-03-11
Did you try to press F6 at the grub boot screen and select nomodeset?

---

### Post by howefield on 2012-03-11
Thread moved to "*Ubuntu +1 (Precise Pangolin)*" forum.

---

### Post by Ondrasek on 2012-03-13
Yes, I already tried the nomodeset option before starting the live-system. But as I am an absolute beginner in ubuntu, i don't know what to do after having started the text mode. 
Please give me a simple solution that also the greatest dummy will understand =)

---

### Post by GerMulvey on 2012-03-30
same issue with beta2
nomodeset reaches desktop but after install system stops before login screen

---

### Post by 2F4U on 2012-03-30
The nomodeset option is not carried over from the liveCD to the installed system. You will have to edit /etc/default/grub and add the nomodeset parameter to kernel parameters and then execute

```
sudo update-grub
```

---

