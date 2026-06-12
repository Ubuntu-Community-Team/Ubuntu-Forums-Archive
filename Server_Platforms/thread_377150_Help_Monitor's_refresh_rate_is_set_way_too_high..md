---
title: "Help: Monitor's refresh rate is set way too high."
date: 2007-03-05
forum: Server Platforms
---

### Post by BongoBob on 2007-03-05
Hello all.

I recently installed the 6.06.1 Server onto a spare computer I have. When I first put in the cd it brought up the install menu just fine. But then after selecting Install, it messes up the graphics. I then checked the monitors refresh rate, and it was showing it at 70hz, 10 above what it's max is.After installing, it does the same thing. I don't have X, so I can't edit xorg.conf like I do with my desktop installation.

Please, any help is greatly appreciated.

Thank you in advance :)

---

### Post by konungursvia on 2007-03-05
sudo nano /etc/X11/xorg.conf

---

### Post by BongoBob on 2007-03-06
There is no xorg.conf file.

---

### Post by e1geo on 2007-03-06
Where does it show 70Hz?

---

### Post by BongoBob on 2007-03-06
When I click the menu button on my monitor. I just hooked it up to my other monitor, and it also shows 70hz, but it shows everything just fine.

On the other one it horribly distorts the image. It even looks like it is in an oval shape instead of a square. If I can find my camera I'll take a picture of it.

---

### Post by e1geo on 2007-03-06
Hmmm...I am not sure how the monitor can show a refresh rate that is above its limit? Not sure that this is the problem. Can you manually change the refrresh rate on the monitor?

---

