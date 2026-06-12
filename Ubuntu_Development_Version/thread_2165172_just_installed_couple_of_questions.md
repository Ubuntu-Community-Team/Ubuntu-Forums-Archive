---
title: "just installed couple of questions"
date: 2013-08-03
forum: Ubuntu Development Version
---

### Post by terry_gardener on 2013-08-03
i have just installed from the daily build and i have couple of questions. 

i thought mir came as default, i seem to be using xorg. 
also the screen seems slow compared to normal (drawing objects and scrolling) is this because i am using the open source nvidia driver and not the nvidia one.

---

### Post by mc4man on 2013-08-03
> **terry_gardener said:**
> i have just installed from the daily build and i have couple of questions. 

i thought mir came as default, i seem to be using xorg. 

You won't likely see mir on a desktop install until 14.10, though they may set xmir as default in 13.10 whether it's working well or not.

---

### Post by grahammechanical on 2013-08-05
At the moment xmir does not work with proprietary video drivers. And, as some of us are finding out, whether we get xmir running or not also depends on the graphic adapters we have. There are a couple of threads about this in this section.

I have no problem getting Ubuntu running on xmir. I have a Nvidia GT220 and I am using Nouveau open source drivers. Follow the instructions here

[http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

Here are some commands to check if xmir is active

```
ps aux | grep unity-system-compositor
```
```
 grep -i xmir /var/log/Xorg.0.log
```

I cannot provide examples of what you should see as at the moment I am not on my saucy+mir installation. I did post examples in the thread asking about seeing improvements in xmir.
 
Two weeks ago a sure sign that xmir was running was seeing two cursors but the bug has been fixed. You may see a little lag on window movements and if you move the insertion point through a line of text and then stop the insertion point it will jump ahead one character. This bug may not be noticeable at first but over time it will become noticeable.

Others among us have seen other more pronounced issues.

Regards.

---

### Post by terry_gardener on 2013-08-05
> **grahammechanical said:**
> At the moment xmir does not work with proprietary video drivers. And, as some of us are finding out, whether we get xmir running or not also depends on the graphic adapters we have. There are a couple of threads about this in this section.

I have no problem getting Ubuntu running on xmir. I have a Nvidia GT220 and I am using Nouveau open source drivers. Follow the instructions here

[http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

Here are some commands to check if xmir is active

```
ps aux | grep unity-system-compositor
```
```
 grep -i xmir /var/log/Xorg.0.log
```

I cannot provide examples of what you should see as at the moment I am not on my saucy+mir installation. I did post examples in the thread asking about seeing improvements in xmir.
 
Two weeks ago a sure sign that xmir was running was seeing two cursors but the bug has been fixed. You may see a little lag on window movements and if you move the insertion point through a line of text and then stop the insertion point it will jump ahead one character. This bug may not be noticeable at first but over time it will become noticeable.

Others among us have seen other more pronounced issues.

Regards.

i tried the above guide using the nouveau open source driver and when i rebooted all i got was a black screen with cursor nothing else.

---

### Post by grahammechanical on 2013-08-05
> all i got was a black screen with cursor nothing else

I get that on Ubuntu saucy+xmir and a Ubuntu saucy without xmir. It may be an issue with Ubuntu saucy and not xmir. It is possible to boot. Sometimes it will load from the main Ubuntu option. Then it might work with Advance Options Ubuntu. Earlier in the day it took three attempts to load Ubuntu saucy without xmir. And it also took two attempts to get into Ubuntu saucy+xmir. 

Regards.

---

### Post by Berry Greene on 2013-08-11
Are you the same chap who once worked for BEA at West London Air Terminal?

---

### Post by terry_gardener on 2013-08-11
> **Berry Greene said:**
> Are you the same chap who once worked for BEA at West London Air Terminal?

no

---

### Post by Mateusz Stachowski on 2013-08-11
The guide posted in this thread is now obsolete because XMir and unity-system-compositor are available through universe repository (no more need for PPA). Anyone that want to test those new developments should refer to the new guide.

[https://wiki.ubuntu.com/Mir/Installing](https://wiki.ubuntu.com/Mir/Installing)

Commands for checking if XMir is active remain the same.

---

