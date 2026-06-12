---
title: "How do you get an USB controller to work?"
date: 2010-02-07
forum: Wine
---

### Post by demonic_crow on 2010-02-07
I installed Duke Nukem on my pc and want to use my PS3 controller using usb attachment to play it or any other games.  I have install the joystick package.  I looked in my dev and notice that my usb was coming up as hidraw2.  So I try running the calibrater by typing:
sudo jscal -c /dev/hidraw2 
it show jscal: error getting version: Invalid argument

Any thoughts on how to get this running.  Would be cool to use this controller with SuperTux2 also.

---

### Post by demonic_crow on 2010-02-07
I ran this:

jscal -c /dev/input/js0

```
Joystick has 28 axes and 112 buttons.
Correction for axis 0 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 1 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 2 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 3 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 4 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 5 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 6 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 7 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 8 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 9 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 10 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 11 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 12 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 13 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 14 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 15 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 16 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 17 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 18 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 19 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 20 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 21 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 22 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 23 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 24 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 25 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 26 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 27 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751

Calibrating precision: wait and don't touch the joystick.
Segmentation fault

```

---

### Post by Tahakki on 2010-02-08
A segfault usually means that a program is installed incorrectly.

---

### Post by hikaricore on 2010-02-08
> **Tahakki said:**
> A segfault usually means that a program is installed incorrectly.

This is not helpful in any way to the OP nor is it accurate.

@Op: Why are you trying to run jscal?  Are you not able to configure the controller inside the games/programs in question?  Most devices of this nature don't need additional configuration they just need to be mapped in the game's setup.

---

### Post by sp0tz on 2010-02-14
Yeah my ps3 controller acts the same way when I use jscal:

```
tails@tv:~$ jscal -c /dev/input/js0
Joystick has 28 axes and 112 buttons.
Correction for axis 0 is none (raw), precision is 0.
Correction for axis 1 is none (raw), precision is 0.
Correction for axis 2 is none (raw), precision is 0.
Correction for axis 3 is none (raw), precision is 0.
Correction for axis 4 is none (raw), precision is 0.
Correction for axis 5 is none (raw), precision is 0.
Correction for axis 6 is none (raw), precision is 0.
Correction for axis 7 is none (raw), precision is 0.
Correction for axis 8 is none (raw), precision is 0.
Correction for axis 9 is none (raw), precision is 0.
Correction for axis 10 is none (raw), precision is 0.
Correction for axis 11 is none (raw), precision is 0.
Correction for axis 12 is none (raw), precision is 0.
Correction for axis 13 is none (raw), precision is 0.
Correction for axis 14 is none (raw), precision is 0.
Correction for axis 15 is none (raw), precision is 0.
Correction for axis 16 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 17 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 18 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 19 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 20 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 21 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 22 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 23 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 24 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 25 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 26 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 27 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751

Calibrating precision: wait and don't touch the joystick.
Segmentation fault

```


I'm only in jscal because I can't map the buttons to anything in zsnes or mednafen. In zsnes, as soon as the dialog box to map a button appears, it disappears. I think what is happening is the analog sticks are constantly providing input, so the dialog boxes close before I can provide the wanted input. I can't calibrate the joystick either, since every time I run "jscal -c /dev/input/js0" I get a segfault back.

I've reinstalled jscal a number of times.

---

