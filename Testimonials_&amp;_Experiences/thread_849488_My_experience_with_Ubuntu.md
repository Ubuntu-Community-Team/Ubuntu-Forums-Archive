---
title: "My experience with Ubuntu"
date: 2008-07-04
forum: Testimonials &amp; Experiences
---

### Post by slavka012 on 2008-07-04
Installed Ubuntu last week. I'm impressed-- intsall was easier than XP. No messing with drivers at all. Everything on my laptop (HP dv6000 series) was working out of the box -- sound, network, touchpad, even quicklaunch buttons.

Power management was also working, display dimming on batteries etc.

It's great. Not perfect, though. Hibernate, suuspend, takes much longer than XP. I guess I'll search solutions for that.

Also, when I boot the machine my wireless card is messed up -- I have to execute ifdown wlan0, ifup wlan0 to make it work.

Small issues with gnome-panel. It has tendency to hang when you mess with the clock plugin.

Other than that, I'm very happy with it and I will be recommending it to everybody.

---

### Post by hansdown on 2008-07-04
Hope You stay,I know I will! hansdown.

---

### Post by DocYoung on 2008-07-04
> **slavka012 said:**
> ...(HP dv6000 series)...

Also, when I boot the machine my wireless card is messed up -- I have to execute ifdown wlan0, ifup wlan0 to make it work.


Can you explain a little more on this for a new *nix user. I've run ubuntu as a liveCD run and it doesnt notice the wireless card. 

Everything else seems to run fine, and the wireless card thing is the only reason I havent installed Ubuntu completely.

Thank you very much in advance.
-Doc

---

### Post by bikeboy on 2008-07-04
> **DocYoung said:**
> Can you explain a little more on this for a new *nix user. I've run ubuntu as a liveCD run and it doesnt notice the wireless card. 

Everything else seems to run fine, and the wireless card thing is the only reason I havent installed Ubuntu completely.

Thank you very much in advance.
-Doc

This is very much individual, depending on the wireless card you have. Some will 'Just Work', others are a lot more difficult. It really depends on how helpful the manufacturer of the card is.

If you run into difficulty with yours, first try searching the forums for information about your card, then start a new thread if necessary.

---

### Post by Teber on 2008-07-05
as to the wireless card: check out the hardware pages on the ubuntu site? or check out other links you will find on the ubuntu site?

you came to the right place for support. welcome aboard!

---

### Post by Martje_001 on 2008-07-05
> **slavka012 said:**
> Also, when I boot the machine my wireless card is messed up -- I have to execute ifdown wlan0, ifup wlan0 to make it work.
Go to a terminal and type:
```
sudo gedit /etc/init.d/network-custom
```
and paste the following code:
```
#!/bin/bash
ifdown wlan0
ifup wlan0

exit 0
```
save and exit. Now type:
```
sudo chmod +x /etc/init.d/network-custom
sudo update-rc.d -f network-custom defaults
```

Now the commands start at bootup :).

---

### Post by jualin on 2008-07-05
Welcome to the community! Your computer experience will change dramatically and you will become another hardcore "ubunturero" in a short time. Welcome to a world without limits and with endless posibilities, Welcome to Linux!

---

### Post by aysiu on 2008-07-05
Probably won't make much of a difference in the case of Gedit, but you should get in the habit of using *gksudo* with graphical applications instead of *sudo*. More details here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by nickdbliss on 2008-07-05
Welcome to the world of open source. Happy Independence!!

---

### Post by steveneddy on 2008-07-05
I'm sure that the foruns could help you with the wireless issue.

---

