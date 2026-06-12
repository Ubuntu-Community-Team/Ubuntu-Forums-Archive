---
title: "mouse and windows settings mysteriously changed!"
date: 2012-11-13
forum: Ubuntu Studio
---

### Post by thornepalmer on 2012-11-13
I just received my new laptop from Zareason with Ubuntu Studio installed 3 weeks ago and it's been amazing. This morning, however, i logged on and the buttons at the upper right of the screen to maximize/minimize/close any window are now gone! My mouse pad settings are different too. Whenever I click a menu and move the mouse to click a menu item, the menu closes! And the last thing i noticed is that the open windows are no longer represented in the top bar as they were. I've searched through the settings to try to correct these issues with no success, but i'm more curious about why this may have happened. I haven't changed anything setting-wise in the past week or so!

Thanks!
thorne

---

### Post by dannyboy79 on 2012-11-13
sounds like your window manager got hosed. does ubuntu studio use metacity or compiz or what?

---

### Post by jejeman on 2012-11-13
It uses pure xfwm4.

---

### Post by thornepalmer on 2012-11-13
hmmm... so how do i fix the windows manager?

---

### Post by dannyboy79 on 2012-11-14
trying running this within a terminal session

```
xfwm4 --replace
```

there's a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/1055424](https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/1055424)

---

### Post by thornepalmer on 2012-11-14
it seems to have worked! awesome!!! thank you!!!

---

### Post by dannyboy79 on 2012-11-14
awesome, mark the thread as solved

---

### Post by thornepalmer on 2012-11-14
HA! How do i mark it as solved?!?

---

### Post by vasa1 on 2012-11-15
Click on the little arrow next to Thread Tools

---

### Post by thornepalmer on 2012-11-15
oh wait... seems to be just a temporary fix! at least i know how to fix it when it happens, but it happens every time i turn of the machine.

---

### Post by jejeman on 2012-11-15
Probably something went wrong with config. Try adding another user and see how it works.

---

### Post by dannyboy79 on 2012-11-15
> **thornepalmer said:**
> oh wait... seems to be just a temporary fix! at least i know how to fix it when it happens, but it happens every time i turn of the machine.
did you save your session? i am not sure honestly how to make it permanent. You could perhaps try googling it and trying the various solutions I happen to graze at. Good luck

---

