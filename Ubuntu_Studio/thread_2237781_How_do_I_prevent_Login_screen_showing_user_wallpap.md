---
title: "How do I prevent Login screen showing user wallpaper"
date: 2014-08-03
forum: Ubuntu Studio
---

### Post by jjo3 on 2014-08-03
Hi All,

I have just installed Ubuntu Studio for the first time, added users and was surprised to find the users wallpaper appear at the login screen. I would lke to be able to prevent that from happening system wide. I have searched for solutions but only found those relatng to Unity greeter which I believe UbStu doesn't use, correct?

I find it concerning that there appears to be in an inbuilt lack of privacy in Ubuntu Studio. Not only can users see other's wallpaper at login, but can also access other users files easily through Thunar. This also leads to concerns about security.

Is there any way to prevent these issues system wide?

Thanks

---

### Post by jejeman on 2014-08-04
Better ask at Xubuntu forum.

---

### Post by gdesilva on 2014-08-23
Hi, login is handled by lightdm and the settings for lightdm can be found in /etc/lightdm directory. I would suspect you would need to change the background in users.conf file.

Hope this works.

---

### Post by Dennis N on 2014-08-23
This behvior of the lightdm greeter background in Xubuntu was the topic of this thread:
[http://ubuntuforums.org/showthread.php?t=2232430](http://ubuntuforums.org/showthread.php?t=2232430)
An answer is given in post #4 using the version from daily ppa.
(By contrast, in Lubuntu the greeter is configured by default so that the background is the same for all users.)

---

