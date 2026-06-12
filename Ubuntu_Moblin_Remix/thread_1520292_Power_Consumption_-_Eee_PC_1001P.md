---
title: "Power Consumption - Eee PC 1001P"
date: 2010-06-29
forum: Ubuntu Moblin Remix
---

### Post by Anessen on 2010-06-29
Hey
I have a new Asus Eee PC 1001P netbook, which came with Windows 7 Starter. I just installed Ubuntu Netbook Remix on there as well to give it a go.

At the moment I am getting over 3 hours of light use out of it on windows and just over 2 hours on Ubuntu. This is basically just web browsing and using the wireless.

Are there any ways of getting more battery life out of the Ubuntu install?

---

### Post by muleyyy on 2010-07-18
I have had a similar experience with my samsung n150

i fixed it somewhat by lowering the brightness of the screen a little, switching off bluetooth (i gain an hour of extra just for doing that!) and fiddling with the power settings

---

### Post by joshruehlig on 2010-08-08
Windows has better power optimizations then ubuntu, but I know the ubuntu team is working on this either in 10.10 or 11.04. You can try using powertop which will give you suggesstions on what to do. 

sudo apt-get install powertop
sudo powertop

You can also get rid of startup programs that may be making your processor come out of sleep modes. Try installing and using bum

sudo apt-get install bum
sudo bum


This should help alot too since you have an eeepc
[http://www.webupd8.org/2010/06/jupiter-take-advantage-of-asus-super.html](http://www.webupd8.org/2010/06/jupiter-take-advantage-of-asus-super.html)

---

### Post by Bealer on 2010-08-22
- Plenty you can do. If you're using Ubuntu 10.04 you'll need to install laptop tools.

```

sudo apt-get install laptop-mode-tool

```

- Google about turning on Usb Autosuspend, there are plenty of articles on it.
- Install eee-applet

```

sudo apt-get install eee-applet

```

Installing powertop can help make suggestions and show power consumption. Mine is typically around 6W an hour and lower, and I get around 9 hours, sometimes more from my 1001P.

---

