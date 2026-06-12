---
title: "Unable to change default session"
date: 2012-01-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2012-01-27
I hadn't tried in some time to change DE sessions in Precise because I have one Unity-2D install and one Classic-no-effects install that I've just been updating and using, but this AM I wanted to try the "3D" versions of each to have a look at CCSM and the "cog" is gone in lightdm.

I know I probably just missed some silly change, but that's how it goes sometimes. I'm not the brightest bulb on the tree :oops:

---

### Post by dino99 on 2012-01-27
which greeter is (are) installed on your system ? and which one is used into /etc/lightdm/lightdm.conf ?

(im using lightdm-greeter-gtk as i've completly purged unity, and i can choose the session while logging)

---

### Post by mc4man on 2012-01-27
> **kansasnoob said:**
> the "cog" is gone in lightdm.

I know I probably just missed some silly change, but that's how it goes sometimes. I'm not the brightest bulb on the tree :oops:
There is a current unity-greeter bug - to get the 'cog' back you need to scroll users at the login screen. 
[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918657](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918657)

---

### Post by Quackers on 2012-01-27
If I press the down arrow and go to the Guest Session, then go back up, the cog appears :-)  Like magic!

---

### Post by kansasnoob on 2012-01-27
> **mc4man said:**
> There is a current unity-greeter bug - to get the 'cog' back you need to scroll users at the login screen. 
[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918657](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918657)

Thanks, I me-too'ed, and subscribed.

---

### Post by kansasnoob on 2012-01-27
Thanks all, marking this solved.

---

### Post by mc4man on 2012-01-27
> **kansasnoob said:**
> Thanks, I me-too'ed, and subscribed.
I've applied the fix here & it works fine, there are a few other minor issues but would expect something to be released shortly. Atm it's just a bit of an inconvience rahter than something broken.

---

### Post by zika on 2012-01-27
There was a whole thread about that: [http://ubuntuforums.org/showthread.php?t=1913141](http://ubuntuforums.org/showthread.php?t=1913141) ... ;)

---

### Post by kansasnoob on 2012-01-27
> **zika said:**
> There was a whole thread about that: [http://ubuntuforums.org/showthread.php?t=1913141](http://ubuntuforums.org/showthread.php?t=1913141) ... ;)

I was asleep at the wheel. Basically, if it's not effecting me I may miss it :D

Since I'd not been changing sessions I missed it, sorry.

---

