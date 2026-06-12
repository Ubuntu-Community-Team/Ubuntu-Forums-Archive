---
title: "DosBox crappy performance on Ubuntu 12.04"
date: 2012-05-07
forum: Virtualisation
---

### Post by AleCes on 2012-05-07
Hi there

After a fresh install of 12.04 (64 bit), DosBox doesn't work as good as it used to be. First of all, I cannot switch to full screen with ALT+ENTER, if I set the full screen by default, the program makes the whole system crash. :frown: The only solution is then a reset.  But even if I dispense with the full screen, my games won't run at all, even in a window. I can't even manage to install Alone in the Dark, the installation program just freezes! ](*,)

Thanks for your help.

---

### Post by kostkon on 2012-05-07
Actually, there is a solution you can try that may fix all of these problems.

Open your home folder, press CTRL+H (or select View &#8594; Show Hidden Files from its menu), select the .dosbox folder and in it you should find a file named
```
dosbox-0.74.conf
```
Open the file with your text editor and change the line
```
output=surface
```
to
```
output=opengl
```
You will find other configurations there you might want to change.

That's the default conf file that dosbox uses when it's called without a custom conf file, like in your case.

Hope that helps.

---

### Post by AleCes on 2012-05-08
Hi kostkon, I tried this but it doesn't work. I cannot get the full screen working yet.

Thanks anyway.

---

