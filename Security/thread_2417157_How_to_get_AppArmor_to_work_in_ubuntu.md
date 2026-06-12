---
title: "How to get AppArmor to work in ubuntu?"
date: 2019-04-21
forum: Security
---

### Post by jebi on 2019-04-21
hi

how do you get apparmor to work in ubuntu do you have to make every and each app a profile or is there a way to just say give everything a low privilege state? so that nothing is able to do anything strange say if a hacker gained control of an app (if a hacker is able to do that not sure).

are you able to get apparmor to warn you if an app starts doing something that it would not normally need or should do?

i am trying to lock down ubuntu i enabled ufw and now am looking at apparmor..

is there anything else you could do you lock down ubuntu but with or without effecting functionality?

thx

---

### Post by Frogs Hair on 2019-04-21
I find ufw sufficient after 9 years of running Ubuntu for private use. I have never experienced any sort of malware,virus, or hacking though if I were running a sever my security model would likely change. I can only offer documentation links.   

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)
[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

---

### Post by Rubi1200 on 2019-04-21
+1 to everything Frogs Hair said.

Out of the box, Ubuntu is already secure for home users. Server is another matter.

Another AppArmor tutorial: [https://ubuntuforums.org/showthread.php?t=1008906](https://ubuntuforums.org/showthread.php?t=1008906)

There is also something called Firejail, which uses sandboxing, if you are interested in reading more: [https://firejail.wordpress.com/](https://firejail.wordpress.com/)

---

